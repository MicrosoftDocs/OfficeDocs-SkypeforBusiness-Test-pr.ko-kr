---
title: Remove-CsArchivingPolicy
TOCTitle: Remove-CsArchivingPolicy
ms:assetid: 41f11a99-14f1-4292-9d58-eb7a7761b829
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425924(v=OCS.15)
ms:contentKeyID: 49303445
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsArchivingPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정한 메신저 대화 보관 정책을 제거합니다. 메신저 대화 보관 정책은 Lync Server에서 내부 사용자 간 및/또는 내부 사용자와 페더레이션 파트너 간에 발생하는 모든 메신저 대화 세션을 자동으로 저장할지 여부를 결정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsArchivingPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 **Remove-CsArchivingPolicy** cmdlet을 사용하여 ID가 site:Redmond인 정책을 삭제합니다. 사이트 범위에서 구성된 정책을 삭제하면 이전에 사이트 정책으로 관리된 사용자가 자동으로 전역 보관 정책을 대신 적용합니다.

    Remove-CsArchivingPolicy -Identity site:Redmond

## 예제 2

예제 2에서는 사이트 범위에서 구성된 모든 보관 정책이 제거됩니다. 사이트 범위에서 할당된 모든 보관 정책 컬렉션을 검색하기 위해 **Get-CsArchivingPolicy** cmdlet 및 Filter 매개 변수가 사용됩니다. 이 작업을 수행하기 위해 필터 값 "site:\*"를 사용합니다. 이 값은 ID가 문자열 값 "site:"으로 시작하는 정책만 반환하도록 **Get-CsArchivingPolicy** cmdlet에 지시합니다. 반환된 컬렉션은 컬렉션의 모든 정책을 삭제하는 **Remove-CsArchivingPolicy** cmdlet에 파이프됩니다.

    Get-CsArchivingPolicy -Filter site:* | Remove-CsArchivingPolicy

## 예제 3

예제 3에서는 ArchiveExternal 속성이 False로 설정된 모든 보관 정책을 삭제합니다. 이 작업을 수행하기 위해 먼저 **Get-CsArchivingPolicy** cmdlet을 사용하여 조직에서 사용하도록 구성된 모든 보관 정책 컬렉션을 반환합니다. 이 컬렉션은 ArchiveExternal 속성이 False와 같은 정책만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 정책을 삭제하는 **Remove-CsArchivingPolicy** cmdlet에 전달됩니다.

    Get-CsArchivingPolicy | Where-Object {$_.ArchiveExternal -eq $False} | Remove-CsArchivingPolicy 

## 자세한 정보

대부분의 조직은 사용자가 참가하는 모든 메신저 대화 세션을 보관하는 것이 유용함을 인식하며, 법적으로 이러한 보관을 유지해야 하는 조직도 있습니다. Lync Server를 사용하여 메신저 대화 세션을 보관하려면 두 가지 단계를 수행해야 합니다. 먼저 **Set-CsArchivingConfiguration** cmdlet을 사용하여 전역 및/또는 사이트 범위에서 보관을 설정해야 합니다. 이렇게 하면 메신저 대화 세션을 보관할 수 있지만 자동으로 이러한 세션의 보관이 시작되지는 않습니다.

메신저 대화 세션 내용을 실제로 저장하려면 2단계: 하나 이상의 보관 정책 만들기를 수행해야 합니다. 이러한 정책은 메신저 대화 세션이 기록되는 사용자와 보관할 메신저 대화 세션 유형(내부 및/또는 외부)을 결정합니다. 내부 메신저 대화 세션은 모든 참가자가 조직 내에 Active Directory 계정이 있는 인증된 사용자인 세션입니다. 외부 메신저 대화 세션은 참가자 중 한 명 이상이 조직 내에 Active Directory 계정이 없는 인증되지 않은 사용자인 세션입니다. 내부 세션만 보관하거나, 외부 세션만 보관하거나, 내부 및 외부 세션을 모두 보관할 수 있습니다.

보관 정책은 전역 범위 또는 사이트 범위에 할당할 수 있습니다. 또한 이러한 정책을 사용자별 범위에 할당한 다음 특정 사용자나 특정 사용자 집합에 적용할 수도 있습니다. 예를 들어 전역 정책에서 모든 사용자의 내부 메신저 대화 세션만 보관하는 경우를 가정해 보겠습니다. 이 경우 내부 및 외부 세션을 모두 보관하는 두 번째 정책을 만들고 해당 정책을 영업 사원에게만 적용할 수 있습니다. 사용자별 정책이 전역 및 사이트 정책보다 우선하므로 영업 팀 구성원의 모든 메신저 대화 세션이 보관됩니다. 다른 사용자(즉, 영업 부서에 속하지 않으므로 영업 정책의 영향을 받지 않는 사용자)는 내부 메신저 대화 세션만 보관됩니다.

**Remove-CsArchivingPolicy** cmdlet을 통해 조직에서 사용하기 위해 만든 보관 정책을 삭제할 수 있습니다. 사용자별 정책을 삭제하면 해당 정책이 할당된 모든 사용자에게 자동으로 관련 사이트 정책이 적용됩니다. 사이트 정책이 없으면 해당 사용자가 전역 정책으로 제어됩니다. 사이트 정책을 제거하면 해당 정책의 영향을 받은 사용자에게 자동으로 전역 정책이 적용됩니다.

전역 정책에 대해 **Remove-CsArchivingPolicy** cmdlet을 실행할 수도 있지만 전역 정책은 제거할 수 없습니다. 대신 전역 정책에 대해 **Remove-CsArchivingPolicy** cmdlet을 실행하면 해당 정책의 모든 속성이 기본값으로 다시 설정됩니다. 따라서 내부 메신저 대화 세션과 외부 메신저 대화 세션 모두 보관되지 않습니다. 이것은 두 속성(ArchiveInternal 및 ArchiveExternal)의 기본값이 모두 False이기 때문입니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsArchivingPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsArchivingPolicy"}

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
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>제거할 보관 정책의 고유 식별자입니다. 보관 정책은 전역, 사이트 또는 사용자별 범위에서 구성할 수 있습니다. 전역 정책을 제거하려면 -Identity global 구문을 사용합니다. 전역 정책은 실제로 제거할 수 없습니다. 대신, 모든 정책 속성이 기본값으로 다시 설정됩니다.</p>
<p>사이트 정책을 제거하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. 사용자별 정책을 제거하려면 -Identity SalesArchivingPolicy와 유사한 구문을 사용합니다.</p>
<p>ID를 지정할 때는 와일드카드를 사용할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 현재 하나 이상의 사용에 할당된 경우에도 정책이 자동으로 제거됩니다. 이 매개 변수가 없으면 <strong>Remove-CsArchivingPolicy</strong> cmdlet에서 하나 이상의 사용자에 할당된 사용자별 정책을 자동으로 제거하지 않습니다. 대신 정책을 제거할 것인지 확인하는 확인 메시지가 표시됩니다. Y 키를 눌러 예라고 응답해야 명령이 계속되고 정책이 제거됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.WritableConfig.Policy.IM.IMArchivingPolicy 개체입니다. **Remove-CsArchivingPolicy** cmdlet은 보관 정책 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

**Remove-CsArchivingPolicy** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.IM.IMArchivingPolicy 개체의 인스턴스를 제거합니다.

## 참고 항목

#### 기타 리소스

[Get-CsArchivingPolicy](get-csarchivingpolicy.md)  
[Grant-CsArchivingPolicy](grant-csarchivingpolicy.md)  
[New-CsArchivingPolicy](new-csarchivingpolicy.md)  
[Set-CsArchivingPolicy](set-csarchivingpolicy.md)

