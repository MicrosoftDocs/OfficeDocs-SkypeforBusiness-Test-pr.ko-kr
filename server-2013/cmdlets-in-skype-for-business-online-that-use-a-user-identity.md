---
title: 사용자 ID를 사용하는 cmdlet
TOCTitle: 사용자 ID를 사용하는 cmdlet
ms:assetid: be87409f-6372-4c70-91ac-6ef13dfbe65a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362842(v=OCS.15)
ms:contentKeyID: 56270295
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 사용자 ID를 사용하는 cmdlet

 

_**마지막으로 수정된 항목:** 2015-06-22_

비즈니스용 Skype Online에는 개별 사용자 ID를 참조할 수 있는 여러 가지 방법이 있습니다.

  - 사용자의 Active Directory 도메인 서비스 표시 이름을 사용합니다. 예를 들면 다음과 같습니다.
    
        -Identity "Ken Myer"

  - 사용자의 SIP 주소를 사용합니다. 예를 들면 다음과 같습니다.
    
        -Identity "sip:kenmyer@litwareinc.com"

  - 사용자의 UPN을 사용합니다. 예를 들면 다음과 같습니다.
    
        -Identity " kenmyer@litwareinc.com"

  - 사용자의 Active Directory 도메인 서비스 고유 이름을 사용합니다. 예를 들면 다음과 같습니다.
    
        -Identity "CN=48ebd1ba-95d4-460c-b751-811ebf0c4611,OU=fa8226f5-14fa-46da-8 236-039b25bc7a27,OU=Lync Online Tenants,DC=litwareinc,DC=com"

다음 cmdlet은 사용자 ID를 허용합니다.

  - [Disable-CsMeetingRoom](https://docs.microsoft.com/en-us/powershell/module/skype/Disable-CsMeetingRoom)

  - [Enable-CsMeetingRoom](https://docs.microsoft.com/en-us/powershell/module/skype/Enable-CsMeetingRoom)

  - [Get-CsExUmContact](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsExUmContact)

  - [Get-CsMeetingRoom](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsMeetingRoom)

  - [Get-CsOnlineUser](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsOnlineUser?view=skype-ps)

  - [Get-CsUserAcp](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsUserAcp)

  - [New-CsExUmContact](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsExUmContact)

  - [Remove-CsExUmContact](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsExUmContact)

  - [Remove-CsUserAcp](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsUserAcp)

  - [Set-CsExUmContact](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsExUmContact)

  - [Set-CsMeetingRoom](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsMeetingRoom)

  - [Set-CsUserAcp](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsUserAcp)

**Get-Cs** cmdlet 중 하나를 호출할 때는 사용자 ID를 지정하지 않아도 됩니다. 이 경우 cmdlet은 지정된 항목의 모든 인스턴스를 반환합니다. 예를 들어 다음 명령은 비즈니스용 Skype Online을 사용할 수 있는 모든 사용자에 대한 정보를 반환합니다.

    Get-CsOnlineUser

Identity 매개 변수는 특정 사용자에 대한 정보를 반환하려는 경우에만 필요합니다.

    Get-CsOnlineUser -Identity "Ken Myer"

## 참고 항목

#### 개념

[ID, 범위, 테넌트](identities-scopes-and-tenants-in-skype-for-business-online.md)  
[Lync Online Cmdlet](the-skype-for-business-online-cmdlets.md)

