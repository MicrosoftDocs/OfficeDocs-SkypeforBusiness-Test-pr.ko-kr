---
title: Get-CsArchivingPolicy
TOCTitle: Get-CsArchivingPolicy
ms:assetid: 25d7de86-871d-4f07-8825-028137365435
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425731(v=OCS.15)
ms:contentKeyID: 49303089
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsArchivingPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

메신저 대화 세션 보관 정책에 대한 정보를 반환합니다. 보관 정책을 사용하면 내부 사용자 간에 발생하거나 내부 사용자와 외부 사용자 간에 발생하는 모든 메신저 대화 및 웹 회의 세션을 보관할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsArchivingPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsArchivingPolicy [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에서는 매개 변수 없이 **Get-CsArchivingPolicy** cmdlet을 호출합니다. 이를 통해 조직에서 현재 사용 중인 모든 보관 정책 컬렉션을 반환합니다.

    Get-CsArchivingPolicy

## 예제 2

예제 2에서는 **Get-CsArchivingPolicy** cmdlet을 사용하여 Identity가 site:Redmond인 보관 정책을 반환합니다. ID가 고유해야 하므로 이 명령은 항상 최대 한 개 정책을 반환합니다.

    Get-CsArchivingPolicy -Identity site:Redmond

## 예제 3

예제 3에서는 사용자별 범위에서 구성된 모든 보관 정책 컬렉션을 반환합니다. 이 작업을 수행하기 위해 Filter 매개 변수와 필터 값 "tag:\*"가 포함됩니다. 이 필터 값을 지정하면 **Get-CsArchivingPolicy** cmdlet에서 ID가 문자열 값 "tag:"으로 시작하는 정책만 반환합니다.

    Get-CsArchivingPolicy -Filter tag:*

## 예제 4

예제 4에서는 내부 메신저 대화 세션의 보관이 비활성화된 모든 보관 정책 컬렉션을 반환합니다. 먼저 현재 사용 중인 모든 보관 정책 컬렉션을 반환하기 위해 **Get-CsArchivingPolicy** cmdlet이 사용됩니다. 이 컬렉션은 **Where-Object** cmdlet에 파이프됩니다. **Where-Object** cmdlet은 ArchiveInternal 속성이 False와 같은 정책에 대한 데이터만 반환되도록 제한하는 필터를 적용합니다.

    Get-CsArchivingPolicy | Where-Object {$_.ArchiveInternal -eq $False}

## 예제 5

예제 5는 예제 4와 유사하지만 이 경우에는 명령에서 내부 및 외부 보관이 모두 사용하지 않도록 설정된 모든 보관 정책을 반환합니다. 먼저 현재 사용 중인 모든 보관 정책 컬렉션을 반환하기 위해 **Get-CsArchivingPolicy** cmdlet이 사용됩니다. 이 컬렉션은 ArchiveInternal 및 ArchiveExternal 속성이 모두 False와 같은 정책만 선택하는 **Where-Object** cmdlet에 파이프됩니다. -and 연산자는 지정한 조건을 모두 충족하는 정책만 선택하도록 **Where-Object** cmdlet에 지시합니다. 지정된 조건 중 하나 또는 둘 다를 충족하는 정책을 선택하려면 –or 연산자를 사용합니다.

    Get-CsArchivingPolicy | Where-Object {$_.ArchiveInternal -eq $False -and $_.ArchiveExternal -eq $False}

## 자세한 정보

대부분의 조직에서는 조직의 사용자가 참가하는 모든 메신저 대화 세션을 보관하는 것이 유용하다는 것을 인지하고 있습니다. 다른 조직의 경우 법적으로 메신저 대화 세션을 보관해야 하기도 합니다. Lync Server를 사용하여 메신저 대화 세션을 보관하려면 두 가지 단계를 수행해야 합니다. 먼저 **Set-CsArchivingConfiguration** cmdlet을 사용하여 전역 및/또는 사이트 범위에서 보관을 설정해야 합니다. 이렇게 하면 메신저 대화 세션을 보관할 수 있지만 자동으로 이러한 세션의 보관이 시작되지는 않습니다.

메신저 대화 세션의 대화 내용을 실제로 저장하려면 2단계: 하나 이상의 메신저 대화 세션 보관 정책 만들기를 수행해야 합니다. 이러한 정책은 메신저 대화 세션이 기록되는 사용자와 보관할 메신저 대화 세션 유형(내부 및/또는 외부)을 결정합니다. 내부 메신저 대화 세션은 모든 참가자가 조직 내에 Active Directory 계정이 있는 인증된 사용자인 세션입니다. 외부 메신저 대화 세션은 참가자 중 한 명 이상이 조직 내에 Active Directory 계정이 없는 인증되지 않은 사용자인 세션입니다. 내부 세션만 보관하거나, 외부 세션만 보관하거나, 내부 및 외부 세션을 모두 보관할 수 있습니다.

**New-CsArchivingPolicy** cmdlet을 사용하여 만든 보관 정책을 전역 사이트나 사이트 범위에 할당할 수 있습니다. 이러한 정책을 사용자별 범위에 할당할 수도 있으며, 이 경우 정책을 만든 다음 특정 사용자나 특정 사용자 집합에 적용할 수 있습니다. 예를 들어 모든 사용자에 대해 내부 메신저 대화 세션을 보관하는 전역 정책이 있을 수 있습니다. 또한 내부 및 외부 세션을 모두 보관하는 두 번째 정책을 만들고 해당 정책을 영업 사원에게만 적용할 수 있습니다. 사용자별 정책이 전역 및 사이트 정책보다 우선하므로 영업 팀 구성원의 모든 메신저 대화 세션이 보관됩니다. 다른 사용자(즉, 영업 부서에 속하지 않으므로 영업 정책의 영향을 받지 않는 사용자)는 내부 메신저 대화 세션만 보관됩니다.

**Get-CsArchivingPolicy** cmdlet을 통해 조직에서 사용하도록 구성된 보관 정책에 대한 정보를 반환할 수 있습니다. 이러한 정책은 전역 또는 사이트 범위에서 메신저 대화 세션 보관이 설정된 경우에만 적용됩니다. 메신저 대화 세션 보관이 설정되었는지 여부를 확인하려면 **Get-CsArchivingConfiguration** cmdlet을 사용합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsArchivingPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsArchivingPolicy"}

## 매개 변수


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>매개 변수</th>
<th>필수</th>
<th>유형</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>반환할 정책을 나타낼 때 와일드카드 문자를 사용할 수 있습니다. 예를 들어 사이트 범위에서 구성된 모든 정책을 반환하려면 -Filter &quot;site:*&quot; 구문을 사용합니다. 그러면 Identity 속성(필터링할 수 있는 유일한 속성)이 문자열 값 &quot;site:&quot;으로 시작하는 정책이 반환됩니다. Identity가 &quot;Sales&quot;로 시작하는 모든 사용자별 정책 컬렉션을 반환하려면 -Filter &quot;Sales*&quot; 구문을 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환할 보관 정책의 고유 식별자입니다. 전역 정책을 나타내려면 -Identity global 구문을 사용합니다. 사이트 정책을 나타내려면 -Identity site:Redmond와 유사한 구문을 사용합니다. 사용자별 정책을 나타내려면 -Identity RedmondArchivingPolicy와 유사한 구문을 사용합니다. 이 매개 변수를 생략하면 조직에서 사용하도록 구성된 모든 보관 정책이 반환됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 보관 정책 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsArchivingPolicy** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsArchivingPolicy** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Im.IMArchivingPolicy 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Grant-CsArchivingPolicy](grant-csarchivingpolicy.md)  
[New-CsArchivingPolicy](new-csarchivingpolicy.md)  
[Remove-CsArchivingPolicy](remove-csarchivingpolicy.md)  
[Set-CsArchivingPolicy](set-csarchivingpolicy.md)

