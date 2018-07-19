---
title: Lync Server 2013에서 개별 SIP 트렁크에 대한 정보 보기
TOCTitle: Lync Server 2013에서 개별 SIP 트렁크에 대한 정보 보기
ms:assetid: adfacb74-7ea5-4c53-934e-ba7ec59879eb
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721847(v=OCS.15)
ms:contentKeyID: 49885924
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 개별 SIP 트렁크에 대한 정보 보기

 

_**마지막으로 수정된 항목:** 2013-02-21_

SIP 트렁크는 Microsoft Lync Server 2013 VoIP(Voice over IP) 전화 네트워크를 PSTN(공중 전화망)과 연결하는 데 사용됩니다. 이전 버전의 제품에서는 트렁크가 아웃바운드 통화를 중재 서버에서 PSTN 게이트웨이로 라우팅하는 데 사용되었으며 각 게이트웨이는 하나의 트렁크로 제한되었습니다. 그 결과 PSTN 게이트웨이와 SIP 트렁크가 기본적으로 동일했습니다. 따라서 관리자는 단지 연결된 PSTN 게이트웨이에 대한 정보를 봄으로써 개별 SIP 트렁크에 대한 정보를 볼 수 있었습니다.

그러나 Lync Server 2013에서는 이제 하나의 PSTN 게이트웨이에 여러 트렁크를 할당할 수 있습니다. 이는 게이트웨이와 트렁크가 더 이상 동일한 하나가 아님을 의미합니다. 따라서 관리자는 개별 SIP 트렁크에 대한 정보를 보기 위해 [Get-CsTrunk](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsTrunk) cmdlet을 사용해야 합니다.

Get-CsTrunk cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 모든 SIP 트렁크에 대한 정보 보기

  - 다음 명령은 조직에서 사용 중인 모든 SIP 트렁크에 대한 정보를 반환합니다.
    
        Get-CsTrunk

## 특정 SIP 트렁크에 대한 정보 보기

  - 다음 명령은 ID가 PstnGateway:192.168.0.240인 SIP 트렁크에 대한 정보만 반환합니다.
    
        Get-CsTrunk -Identity "PstnGateway:192.168.0.240"

## 풀에 할당된 모든 SIP 트렁크에 대한 정보 보기

  - 이 예에서는 atl-cs-001.litwareinc.com 풀에 할당된 모든 SIP 트렁크에 대한 정보를 반환합니다.
    
        Get-CsTrunk -PoolFqdn "atl-cs-001.litwareinc.com"

