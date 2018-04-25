---
title: New-CsArchivingPolicy
TOCTitle: New-CsArchivingPolicy
ms:assetid: e7c9b310-fbd0-4793-90ef-c752b941e02f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399032(v=OCS.15)
ms:contentKeyID: 49305372
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsArchivingPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 메신저 대화 세션 보관 정책을 만듭니다. 이러한 정책을 통해 내부 사용자 간에 실행되는 모든 메신저 대화 세션 및/또는 내부 사용자와 외부 파트너 간에 실행되는 모든 메신저 대화 세션을 보관할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsArchivingPolicy -Identity <XdsIdentity> [-ArchiveExternal <$true | $false>] [-ArchiveInternal <$true | $false>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 **New-CsArchivingPolicy** cmdlet을 사용하여 ID가 site:Redmond인 새 보관 정책을 만듭니다. 또한 ArchiveInternal 매개 변수를 True로 설정합니다. 이는 이 새 정책이 내부 메신저 대화 세션 및 전화 회의를 보관하는 데 사용됨을 의미합니다.

    New-CsArchivingPolicy -Identity site:Redmond -ArchiveInternal $True

## 예제 2

예제 2에서는 InMemory 매개 변수를 사용하여 처음에 메모리에만 존재하는 보관 정책을 만듭니다. 이 명령 집합에서는 먼저 InMemory 매개 변수와 함께 **New-CsArchivingPolicy** cmdlet을 호출하여 ID가 site:Redmond인 새 사이트 정책을 만듭니다. 메모리에만 나타나는 이 새 정책은 $x 변수에 저장됩니다. 두 번째 및 세 번째 명령은 이 가상 정책의 속성 값을 수정합니다. 즉, 두 번째 명령은 ArchiveInternal 속성 값을 True로 설정하고, 세 번째 명령은 ArchiveExternal 속성을 True로 설정합니다.

끝으로, 이 예제의 마지막 명령은 **Set-CsArchivingPolicy** cmdlet을 사용하여 가상 정책 site:Redmond를 실제 메신저 대화 세션 보관 정책으로 변환합니다.

    $x = New-CsArchivingPolicy -Identity site:Redmond -InMemory
    $x.ArchiveInternal = $True
    $x.ArchiveExternal = $True
    Set-CsArchivingPolicy -Instance $x

## 자세한 정보

대부분의 조직에서는 조직의 사용자가 참가하는 모든 메신저 대화 세션을 보관하는 것이 유용하다는 것을 인지하고 있습니다. 다른 조직의 경우 법적으로 메신저 대화 세션을 보관해야 하기도 합니다. Lync Server를 사용하여 메신저 대화 세션을 보관하려면 두 가지 단계를 수행해야 합니다. 먼저 **Set-CsArchivingConfiguration** cmdlet을 사용하여 전역 및/또는 사이트 범위에서 보관을 설정해야 합니다. 이렇게 하면 메신저 대화 세션을 보관할 수 있지만 자동으로 이러한 세션의 보관이 시작되지는 않습니다.

대신 메신저 대화 세션의 대화 내용을 실제로 저장하려면 2단계를 완료해야 합니다. 자신의 메신저 대화 세션을 녹음해야 하는 사용자 및 보관할 메신저 대화 세션의 유형(내부 및/또는 외부)을 결정하는 메신저 대화 세션 보관 정책을 하나 이상 만들어야 합니다. 내부 메신저 대화 세션은 모든 참가자가 사용자 조직 내의 Active Directory 계정을 가진 인증된 사용자인 경우를 의미하고, 외부 메신저 대화 세션은 적어도 한 명의 참가자가 사용자 조직 내의 Active Directory 계정이 없는 인증되지 않은 사용자인 경우를 의미합니다. 내부 세션만 보관하거나, 외부 세션만 보관하거나, 내부 세션과 외부 세션을 둘 다 보관하도록 선택할 수 있습니다.

보관 정책은 전역 범위 또는 사이트 범위에 할당할 수 있습니다. 또한 이러한 정책을 사용자별 범위에 할당한 다음 특정 사용자나 특정 사용자 집합에 적용할 수도 있습니다. 예를 들어 전역 정책에서 모든 사용자의 내부 메신저 대화 세션만 보관하는 경우를 가정해 보겠습니다. 이 경우 내부 및 외부 세션을 모두 보관하는 두 번째 정책을 만들고 해당 정책을 영업 사원에게만 적용할 수 있습니다. 사용자별 정책은 전역 및 사이트 정책에 우선하기 때문에 영업 직원의 모든 메신저 대화 세션이 보관됩니다. 다른 사용자(영업 부서에 속하지 않으므로 영업 정책의 영향을 받지 않는 사용자)는 내부 메신저 대화 세션만 보관됩니다.

**New-CsArchivingPolicy** cmdlet을 사용하여 사이트 또는 사용자별 범위에서 새 보관 정책을 만들 수 있습니다. 사이트 범위에서 만든 정책은 해당 정책을 만들 때마다 사이트에 자동으로 적용됩니다. 반면, 사용자별 범위에서 만든 정책은 **Grant-CsArchivingPolicy** cmdlet을 호출하여 사용자 또는 사용자 집합에 명시적으로 할당할 때까지 적용되지 않습니다. 전역 범위에는 새 정책을 만들 수 없습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsArchivingPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsArchivingPolicy"}

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
<td><p>정책에 할당할 고유 ID를 나타냅니다. 새 보관 정책은 사이트 범위나 사용자별 범위에서 만들 수 있습니다. 새 사이트 정책을 만들려면 &quot;site:&quot; 접두사와 그 뒤에 사이트 이름이 와야 합니다. 예를 들어 Redmond 사이트의 새 정책을 만들려면 -Identity site:Redmond 구문을 사용하고, 새 사용자별 정책을 만들려면 -Identity SalesArchivingPolicy와 유사한 ID를 사용합니다.</p>
<p>전역 정책은 새로 만들 수 없습니다. 대신 <strong>Set-CsArchivingPolicy</strong> cmdlet을 사용하여 전역 정책을 변경할 수는 있습니다. 마찬가지로 ID가 같은 정책이 이미 있는 경우에는 새 사이트 또는 사용자별 정책을 만들 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ArchiveExternal</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>외부 메신저 대화 세션을 보관할지 여부를 나타냅니다. 외부 메신저 대화 세션은 적어도 한 명의 참가자가 사용자 조직 내의 Active Directory 계정이 없는 인증되지 않은 사용자인 세션입니다. 기본값은 False입니다. 즉, 외부 사용자가 포함된 메신저 대화 세션을 보관하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ArchiveInternal</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>내부 메신저 대화 세션을 보관할지 여부를 나타냅니다. 내부 메신저 대화 세션은 모든 참가자가 사용자 조직 내의 Active Directory 계정을 가진 인증된 사용자인 세션입니다. 기본값은 False입니다. 즉, 내부 메신저 대화 세션을 보관하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>관리자가 보관 정책에 대한 간략한 설명을 제공하는 데 사용됩니다. 예를 들어 Description을 사용하여 정책을 적용해야 하는 사용자에 대해 자세히 설명할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
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

없음. **New-CsArchivingPolicy** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsArchivingPolicy** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.IM.IMArchivingPolicy 개체의 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsArchivingPolicy](get-csarchivingpolicy.md)  
[Grant-CsArchivingPolicy](grant-csarchivingpolicy.md)  
[Remove-CsArchivingPolicy](remove-csarchivingpolicy.md)  
[Set-CsArchivingPolicy](set-csarchivingpolicy.md)

