---
title: 사용자 ID 및 태그 범위를 사용하는 cmdlet
TOCTitle: 사용자 ID 및 태그 범위를 사용하는 cmdlet
ms:assetid: 344a21b0-5301-4e77-853a-970bb1c11e1d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362781(v=OCS.15)
ms:contentKeyID: 56270227
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 사용자 ID 및 태그 범위를 사용하는 cmdlet

 

_**마지막으로 수정된 항목:** 2015-06-22_

**Grant-Cs** cmdlet(사용자에게 정책을 할당하는 데 사용됨)에는 두 가지 식별자인 사용자 ID(Identity 매개 변수)와 사용자별 정책 ID(PolicyName 매개 변수)가 필요합니다. 예를 들어 RedmondVoicePolicy 음성 정책을 사용자 Ken Myer에게 할당하려면 다음 명령을 사용합니다.

    Grant-CsVoicePolicy -Identity "Ken Myer" -PolicyName "RedmondVoicePolicy"

사용자에게 정책을 할당하는 경우 두 가지 유의 사항이 있습니다. 먼저 사용자별 정책만 할당할 수 있습니다. 사용자에게 전역 정책을 할당할 수는 없습니다. 예를 들어 다음 명령은 실패합니다.

    Grant-CsVoicePolicy -Identity "Ken Myer" -PolicyName "global"

전역 정책을 할당할 필요가 없으므로 이 명령은 실패합니다. 전역 정책을 사용하여 사용자를 관리하려면 해당 사용자에게 사용자별 정책을 할당하지 않도록 합니다. 사용자에게 사용자별 정책이 할당되지 않은 경우 해당 사용자는 자동으로 전역 정책을 사용하여 관리됩니다.


> [!NOTE]
> 이전에 사용자에게 사용자별 정책이 할당된 경우 해당 정책 할당을 취소하고 대신 전역 정책으로 해당 사용자를 관리하려면 먼저 null 정책을 부여하여 사용자별 정책 할당을 취소하는 다음 구문을 사용합니다.<BR>Grant-CsVoicePolicy –Identity "Ken Myer" –PolicyName $Null



두 번째로 사용자별 정책은 태그 범위에서 만들어야 합니다. 하지만 정책 이름을 지정할 때 tag **접두사**는 생략할 수 있습니다. 다음 두 명령은 동일합니다.

    Grant-CsVoicePolicy -Identity "Ken Myer" -PolicyName "tag:RedmondVoicePolicy"
    Grant-CsVoicePolicy -Identity "Ken Myer" -PolicyName "RedmondVoicePolicy"

모든 사용자별 정책에 대한 ID를 반환하거나 적어도 음성 정책 같은 특정 유형의 모든 사용자별 정책을 반환하려면 다음과 비슷한 명령을 사용합니다.

    Get-CsVoicePolicy -Filter "tag:*"

다음 cmdlet에는 사용자 ID와 태그 범위가 모두 사용됩니다.

  - [Grant-CsClientPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsClientPolicy)

  - [Grant-CsConferencingPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsConferencingPolicy)

  - [Grant-CsDialPlan](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsDialPlan)

  - [Grant-CsExternalAccessPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsExternalAccessPolicy)

  - [Grant-CsHostedVoicemailPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsHostedVoicemailPolicy)

  - [Grant-CsVoicePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsVoicePolicy)

## 참고 항목

#### 개념

[ID, 범위, 테넌트](identities-scopes-and-tenants-in-skype-for-business-online.md)  
[Lync Online Cmdlet](https://docs.microsoft.com/en-us/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell)

