---
title: 전역 범위만 사용하는 cmdlet
TOCTitle: 전역 범위만 사용하는 cmdlet
ms:assetid: 0ffd3bc9-a6a1-4c2e-8d52-e599acc49d2d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362771(v=OCS.15)
ms:contentKeyID: 56270215
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 전역 범위만 사용하는 cmdlet

 

_**마지막으로 수정된 항목:** 2015-06-22_

비즈니스용 Skype Online의 여러 가지 설정은 *전역 범위*에서만 사용할 수 있습니다. 이는 해당 테넌트에 할당된 모든 사용자에 적용되는 단일 설정 컬렉션이 있음을 의미합니다(각 테넌트는 고유한 전역 설정 컬렉션을 보유합니다). 전역 범위로 제한된 cmdlet을 사용하는 경우 Identity 매개 변수는 선택 사항입니다. 예를 들어 모임 구성 설정을 검색하려면 다음 명령을 사용할 수 있습니다.

    Get-CsMeetingConfiguration -Identity "global"

또는 Identity 매개 변수를 생략하고 대신 다음과 같은 단순한 명령을 사용할 수도 있습니다.

    Get-CsMeetingConfiguration

모임 구성 설정 전역 컬렉션이 하나만 있으므로 두 명령이 정확이 동일한 정보를 반환합니다. **Set-Cs** cmdlet 중 하나를 사용하는 경우에도 Identity 매개 변수를 생략할 수 있습니다. 다음 두 명령은 동일합니다.

    Set-CsMeetingConfiguration -Identity "global" -AdmitAnonymousUsersByDefault $False
    Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False

Identity 매개 변수를 포함하지 않는 경우 기본적으로 Windows PowerShell에서 전역 컬렉션을 수정하므로 두 명령이 동일한 것입니다.

다음 cmdlet은 전역 범위에서만 작동합니다.

  - [Get-CsImFilterConfiguration](get-csimfilterconfiguration.md)

  - [Get-CsMeetingConfiguration](get-csmeetingconfiguration.md)

  - [Get-CsPrivacyConfiguration](get-csprivacyconfiguration.md)

  - [Get-CsTenantFederationConfiguration](get-cstenantfederationconfiguration.md)

  - [Get-CsTenantHybridConfiguration](get-cstenanthybridconfiguration.md)

  - [Get-CsTenantLicensingConfiguration](get-cstenantlicensingconfiguration.md)

  - [Get-CsTenantPublicProvider](get-cstenantpublicprovider.md)

  - [Remove-CsVoicePolicy](remove-csvoicepolicy.md)

  - [Set-CsMeetingConfiguration](set-csmeetingconfiguration.md)

  - [Set-CsPrivacyConfiguration](set-csprivacyconfiguration.md)

**Remove-CsVoicePolicy** cmdlet은 예외입니다. 먼저, 이 cmdlet에는 Identity 매개 변수를 포함해야 합니다.

    Remove-CsVoicePolicy -Identity "global"

둘째, **Remove-CsVoicePolicy** cmdlet은 실제로 전역 음성 정책을 삭제하지 않습니다. 비즈니스용 Skype Online에서는 전역 정책 또는 구성 설정을 삭제하도록 허용하지 않습니다. 이 cmdlet은 전역 음성 정책의 모든 속성을 기본값으로 다시 설정합니다. 예를 들어 AllowCallForwarding 속성은 기본적으로 False로 설정되어 있습니다. 하지만 AllowCallForwarding 값이 True로 수정되었을 수 있습니다. **Remove-CsVoicePolicy** cmdlet을 실행하면 AllowCallForwarding 속성이 기본값인 False로 돌아갑니다. 다음 표에는 이 시나리오가 요약되어 있습니다.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>AllowCallForwarding 값</th>
<th>시나리오</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>False</p></td>
<td><p>기본값</p></td>
</tr>
<tr class="even">
<td><p>True</p></td>
<td><p>전역 정책이 수정된 후</p></td>
</tr>
<tr class="odd">
<td><p>False</p></td>
<td><p><strong>Remove-CsVoicePolicy</strong> cmdlet이 실행된 후</p></td>
</tr>
</tbody>
</table>


## 참고 항목

#### 개념

[ID, 범위, 테넌트](identities-scopes-and-tenants-in-skype-for-business-online.md)  
[Lync Online Cmdlet](the-skype-for-business-online-cmdlets.md)

