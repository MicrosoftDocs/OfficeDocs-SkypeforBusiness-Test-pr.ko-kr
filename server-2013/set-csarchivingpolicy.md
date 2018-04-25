---
title: Set-CsArchivingPolicy
TOCTitle: Set-CsArchivingPolicy
ms:assetid: 2213f1e7-ebdb-4a70-83d9-41eee6d0e14f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398294(v=OCS.15)
ms:contentKeyID: 49303043
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsArchivingPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 메신저 대화 보관 정책을 수정합니다. 보관 정책을 사용하면 내부 사용자 간에 수행되는 모든 메신저 대화 세션과 전화 회의를 보관하는 기능을 사용할 수 있고, 내부 사용자와 페더레이션 파트너 간에 수행되는 세션을 보관할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsArchivingPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsArchivingPolicy [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-ArchiveExternal <$true | $false>] [-ArchiveInternal <$true | $false>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 **Set-CsArchivingPolicy** cmdlet을 사용하여 전역 보관 정책을 수정합니다. 이 경우에는 ArchiveInternal 속성을 True로 설정합니다.

    Set-CsArchivingPolicy -Identity global -ArchiveInternal $True

## 예제 2

예제 2는 예제 1에 표시된 명령의 변형입니다. 이번에는 조직의 모든 보관 정책을 메신저 대화 세션의 보관을 허용하도록 구성합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsArchivingPolicy** cmdlet을 사용하여 현재 사용 중인 모든 메신저 대화 세션 보관 정책의 컬렉션을 반환합니다. 이 컬렉션은 각 정책의 ArchiveInternal 속성을 True로 설정하는 **Set-CsArchivingPolicy** cmdlet에 파이프됩니다.

    Get-CsArchivingPolicy | Set-CsArchivingPolicy -ArchiveInternal $True

## 자세한 정보

많은 조직에서 내부 사용자들이 참여하는 모든 메신저 대화 세션을 보관하는 것이 유용하다고 판단하고 있으며, 법률상으로 이러한 보관이 의무화된 조직도 있습니다. Lync Server를 사용하여 메신저 대화 세션을 보관하려면 2단계를 수행해야 합니다. 첫째, **Set-CsArchivingConfiguration** cmdlet을 사용하여 전역 및/또는 사이트 범위에서 보관을 사용하도록 설정해야 합니다. 이렇게 하면 메신저 대화 세션을 보관할 수 있지만, 자동으로 이러한 세션의 보관이 시작되는 것은 아닙니다.

실제로 메신저 대화 세션의 대화 내용을 저장하려면 2단계로 넘어가 어떤 사용자의 메신저 대화 세션을 기록할지, 어떤 유형의 메신저 대화 세션(내부 및/또는 외부)을 보관할 것인지 결정하는 보관 정책을 하나 이상 만들어야 합니다. 내부 메신저 대화 세션은 조직 내에 Active Directory 계정이 있는 인증된 사용자만 참가하는 세션입니다. 외부 메신저 대화 세션은 조직 내에 Active Directory 계정을 가지고 있지 않은 인증되지 않은 사용자가 한 명 이상 참가하는 세션입니다. 내부 세션 또는 외부 세션만 보관하거나 내부 및 외부 세션을 모두 보관하도록 선택할 수 있습니다.

**New-CsArchivingPolicy** cmdlet을 사용하여 만든 보관 정책은 전역 사이트 또는 사이트 범위에 할당할 수 있습니다. 또한 이러한 정책은 사용자별 범위에 할당할 수도 있습니다. 즉, 정책을 만들어 특정 사용자 또는 사용자 그룹에 적용할 수 있습니다. 예를 들어 모든 사용자의 내부 메신저 대화 세션을 보관하는 전역 정책이 있을 수 있습니다. 또한 내부 및 외부 세션을 모두 보관하는 정책을 만들고 해당 정책을 영업 사원에게만 적용할 수 있습니다. 사용자별 정책은 전역 및 사이트 정책보다 우선하므로 영업 사원의 모든 메신저 대화 세션이 보관됩니다. 다른 사용자(즉, 영업 부서에 속하지 않으므로 영업 정책의 영향을 받지 않는 사용자)는 내부 메신저 대화 세션만 보관됩니다.

**Set-CsArchivingPolicy** cmdlet을 사용하면 현재 조직에서 사용 중인 모든 메신저 대화 세션 보관 정책의 속성 값을 수정할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsArchivingPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsArchivingPolicy"}

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
<td><p><em>ArchiveExternal</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>외부 메신저 대화 세션을 보관할지 여부를 나타냅니다. 외부 메신저 대화 세션은 적어도 한 명의 참가자가 사용자 조직 내의 Active Directory 계정이 없는 인증되지 않은 사용자인 세션입니다. 기본값은 False입니다. 즉, 외부 사용자가 포함된 메신저 대화 세션을 보관하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ArchiveInternal</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>내부 메신저 대화 세션을 보관할지 여부를 나타냅니다. 내부 메신저 대화 세션은 모든 참가자가 사용자 조직 내의 Active Directory 계정을 가진 인증된 사용자인 세션입니다. 기본값은 False입니다. 즉, 내부 메신저 대화 세션을 보관하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>관리자가 정책에 대한 추가 텍스트를 제공할 수 있습니다. 예를 들어 정책이 어떤 사용자에게 적용되는지에 대한 설명을 Description 속성에 지정할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>수정할 보관 정책에 대한 고유한 식별자입니다. 보관 정책은 전역, 사이트 또는 사용자별 범위에 구성할 수 있습니다. 전역 정책을 수정하려면 -Identity global 구문을 사용합니다. 사이트 정책을 수정하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. 또한 사용자별 정책을 수정하려면 -Identity SalesArchivingPolicy와 유사한 구문을 사용합니다. 이 매개 변수가 지정되지 않은 경우 전역 정책이 수정됩니다.</p>
<p>ID를 지정할 때는 와일드카드를 사용할 수 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>메신저 대화 보관 정책 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
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

**Set-CsArchivingPolicy** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Policy.IM.IMArchivingPolicy 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[Get-CsArchivingPolicy](get-csarchivingpolicy.md)  
[Grant-CsArchivingPolicy](grant-csarchivingpolicy.md)  
[New-CsArchivingPolicy](new-csarchivingpolicy.md)  
[Remove-CsArchivingPolicy](remove-csarchivingpolicy.md)

