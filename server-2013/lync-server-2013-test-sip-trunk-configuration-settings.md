---
title: Lync Server 2013에서 SIP 트렁크 구성 설정 테스트
TOCTitle: Lync Server 2013에서 SIP 트렁크 구성 설정 테스트
ms:assetid: c8712308-0e2d-4e39-8f90-d1a250487a94
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721880(v=OCS.15)
ms:contentKeyID: 49885978
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 SIP 트렁크 구성 설정 테스트

 

_**마지막으로 수정된 항목:** 2012-11-01_

SIP 트렁크 구성 설정은 중재 서버와 서비스 공급자 측 PSTN(공중 전화망) 게이트웨이, PBX(Public Branch Exchange) 또는 SBC(세션 경계 컨트롤러) 간의 관계 및 기능을 정의합니다. 이러한 작업은 다음을 지정하여 수행됩니다.

  - 미디어 바이패스를 트렁크에서 사용하도록 설정해야 하는지 여부

  - RTCP(Real-time Transport Control Protocol) 패킷을 보낼 조건

  - SRTP(Secure Real-Time Protocol) 암호화가 각 트렁크에 필요한지 여부

Microsoft Lync Server 2013을 설치하는 경우 SIP 트렁크의 전역 구성 설정 컬렉션이 만들어집니다. 관리자는 사이트 범위 또는 서비스 범위(PSTN 게이트웨이 서비스만 해당)에서 사용자 지정 설정 컬렉션을 만들 수도 있습니다. 관리자는 또한 Test-CsTrunkConfiguration cmdlet을 사용하여 사용자가 거는 번호를 게이트웨이에서 처리할 수 있는 번호로 트렁크가 변환할 수 있는지 확인할 수 있습니다.

트렁크 구성 설정은 Windows PowerShell과 [Test-CsTrunkConfiguration](test-cstrunkconfiguration.md) cmdlet을 사용해서만 테스트할 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 원격 세션의 Windows PowerShell에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 트렁크 구성 설정 테스트

  - 다음 명령을 실행하면 레드몬드 사이트의 트렁크 구성 설정이 전화 번호(4255551212)를 올바로 변환할 수 있는지 확인할 수 있습니다.
    
        $trunk = Get-CsTrunkConfiguration -Identity "site:Redmond"
        Test-CsTrunkConfiguration -DialedNumber 4255551212 -TrunkConfiguration $trunk

