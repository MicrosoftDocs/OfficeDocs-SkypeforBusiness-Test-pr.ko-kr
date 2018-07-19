---
title: 전역 범위 및 태그 범위를 사용하는 cmdlet
TOCTitle: 전역 범위 및 태그 범위를 사용하는 cmdlet
ms:assetid: 1e2bc055-8a72-425e-967b-e253add7018c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362774(v=OCS.15)
ms:contentKeyID: 56270220
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 전역 범위 및 태그 범위를 사용하는 cmdlet

 

_**마지막으로 수정된 항목:** 2015-06-22_

비즈니스용 Skype Online에서는 *전역 범위* 또는 *태그 범위*(또는 *사용자별 범위*)에서 정책을 구성할 수 있습니다. **Get-Cs** cmdlet을 사용하는 경우 범위 또는 ID를 지정하지 않아도 됩니다. 매개 변수를 입력하지 않고 이러한 cmdlet 중 하나를 호출하면 관련된 모든 항목이 반환됩니다. 예를 들어 다음 명령은 모든 외부 액세스 정책에 대한 정보를 반환합니다.

    Get-CsExternalAccessPolicy

반환된 데이터를 제한하려면 Identity 매개 변수 또는 Filter 매개 변수만 포함해야 합니다. 예를 들어 전역 정책만 반환하려면 다음 명령을 사용합니다.

    Get-CsExternalAccessPolicy -Identity "global"

ID가 "RedmondAccessPolicy"인 사용자별 정책을 반환하려면 다음 명령을 사용합니다.

    Get-CsExternalAccessPolicy -Identity "RedmondAccessPolicy"


> [!NOTE]
> 사용자별 정책을 참조할 때 <STRONG>접두사</STRONG> 태그는 선택 사항입니다. 접두사를 포함하는 다음 구문도 유효합니다.<BR>Get-CsExternalAccessPolicy –Identity "tag:RedmondAccessPolicy"



전역 정책을 제외한 모든 정책(즉, 모든 사용자별 정책)을 반환하려면 다음 명령을 사용합니다.

    Get-CsExternalAccessPolicy -Filter "tag:*"

다음 cmdlet은 전역 범위 및 사용자별 (태그) 범위 모두에 대해 실행할 수 있습니다.

  - [Get-CsClientPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsClientPolicy)

  - [Get-CsConferencingPolicy](get-csconferencingpolicy.md)

  - [Get-CsDialPlan](get-csdialplan.md)

  - [Get-CsExternalAccessPolicy](get-csexternalaccesspolicy.md)

  - [Get-CsHostedVoicemailPolicy](get-cshostedvoicemailpolicy.md)

  - [Get-CsPresencePolicy](get-cspresencepolicy.md)

  - [Get-CsVoicePolicy](get-csvoicepolicy.md)


> [!NOTE]
> 다이얼 플랜은 이름에서 시사하는 것과는 달리 기능적 측면에서 정책에 해당합니다. 이전 버전의 Lync Server에서 사용된 용어를 유지하기 위해 다이얼 정책 대신 <EM>다이얼 플랜</EM>이라는 용어가 사용됩니다.



## 참고 항목

#### 개념

[ID, 범위, 테넌트](identities-scopes-and-tenants-in-skype-for-business-online.md)  
[Lync Online Cmdlet](the-skype-for-business-online-cmdlets.md)

