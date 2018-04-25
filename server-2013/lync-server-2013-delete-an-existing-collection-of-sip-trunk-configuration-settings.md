---
title: Lync Server 2013에서 SIP 트렁크 구성 설정의 기존 모음 삭제
TOCTitle: Lync Server 2013에서 SIP 트렁크 구성 설정의 기존 모음 삭제
ms:assetid: 3b25f14d-884b-42dd-a866-460d276d3e43
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688024(v=OCS.15)
ms:contentKeyID: 49885726
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 SIP 트렁크 구성 설정의 기존 모음 삭제

 

_**마지막으로 수정된 항목:** 2013-02-22_

SIP 트렁크 구성 설정은 중재 서버와 서비스 공급자 쪽 공중 전화망(PSTN) 게이트웨이, IP-PBX(Public Branch Exchange) 또는 SBC(Session Border Controller) 간의 관계 및 기능을 정의합니다. 이러한 설정은 다음 사항을 지정합니다.

  - 트렁크에 대해 미디어 바이패스를 사용하도록 설정할지 여부

  - RTCP(Real-time Transport Control Protocol) 패킷을 전송할 조건

  - 각 트렁크에 SRTP(Secure Real-Time Protocol) 암호화가 필요한지 여부

Microsoft Lync Server 2013을 설치하면 SIP 트렁크 구성 설정의 전역 컬렉션이 자동으로 만들어집니다. 이 전역 설정 컬렉션은 삭제할 수 없습니다. 그러나 Lync Server 제어판 또는 [Remove-CsTrunkConfiguration](remove-cstrunkconfiguration.md) cmdlet을 사용하여 전역 컬렉션의 속성을 기본값으로 "다시 설정"할 수 있습니다. 예를 들어 Enable3pccRefer 속성을 True로 설정한 경우 전역 컬렉션을 다시 설정하면 Enable3pccRefer 속성이 기본값인 False로 돌아갑니다.

관리자는 개별 PSTN 게이트웨이에 대해 사이트 범위 또는 서비스 범위에서 사용자 지정 트렁크 구성 설정을 만들 수도 있습니다. 이러한 사용자 지정 설정은 제거할 수 있습니다. 이와 같은 사용자 지정 설정을 제거할 때는 다음 사항에 유의하십시오.

  - 서비스 범위 설정을 제거하면 해당 설정에 의해 관리되는 SIP 트렁크는 사이트에 적용되는 설정(있는 경우)에 의해 관리됩니다. 사이트 설정이 없으면 트렁크는 트렁크 구성 설정의 전역 컬렉션에 의해 관리됩니다.

  - 사이트 범위 설정을 제거하면 해당 설정에 의해 관리되는 SIP 트렁크는 트렁크 구성 설정의 전역 컬렉션에 의해 관리됩니다.

## Lync Server 제어판을 사용하여 트렁크 구성 설정 제거

1.  Lync Server 제어판에서 **음성 라우팅**을 클릭하고 **트렁크 구성**을 클릭합니다.

2.  **트렁크 구성** 탭에서 삭제할 SIP 트렁크 구성 설정 컬렉션을 선택하고 **편집**, **삭제**를 차례로 클릭합니다. 같은 작업에서 여러 컬렉션을 삭제하려면 삭제할 첫 번째 컬렉션을 클릭하고 Ctrl 키를 누른 상태로 제거할 추가 컬렉션을 클릭합니다.

3.  컬렉션의 **상태** 속성이 **커밋되지 않음**으로 업데이트됩니다. 변경 내용을 커밋하고 컬렉션을 삭제하려면 **커밋**, **모두 커밋**을 차례로 클릭합니다.

4.  **커밋되지 않은 음성 구성 설정** 대화 상자에서 **확인**을 클릭합니다.

5.  **Microsoft Lync Server 2013 제어판** 대화 상자에서 **확인**을 클릭합니다.

6.  컬렉션을 삭제하지 않으려는 경우 **커밋**을 클릭한 다음 **커밋되지 않은 모든 변경 내용 취소**를 클릭합니다. **Microsoft Lync Server 2013 제어판** 대화 상자가 나타나면 **확인**을 클릭합니다.

## Lync Server PowerShell cmdlet을 사용하여 트렁크 구성 설정 제거

Windows PowerShell 및 Remove-CsTrunkConfiguration cmdlet을 사용하여 다이얼 플랜을 확인할 수도 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 지정한 설정 컬렉션 제거

  - 다음 명령은 Redmond 사이트에 적용된 트렁크 구성 설정을 제거합니다.
    
        Remove-CsTrunkConfiguration -Identity site:Redmond

## 사이트 범위에 적용된 모든 컬렉션 제거

  - 다음 명령은 서비스 범위에 적용된 모든 트렁크 구성 설정을 제거합니다.
    
        Get-CsTrunkConfiguration -Filter "service:*" | Remove-CsTrunkConfiguration

## 미디어 바이패스가 사용하도록 설정된 모든 컬렉션 제거

  - 다음 명령은 미디어 바이패스가 사용하도록 설정된 모든 트렁크 구성 설정을 제거합니다.
    
        Get-CsTrunkConfiguration | Where-Object {$_.EnableBypass -eq $True} | Remove-CsTrunkConfiguration

자세한 내용은 [Remove-CsTrunkConfiguration](remove-cstrunkconfiguration.md) cmdlet에 대한 도움말 항목을 참조하십시오.

