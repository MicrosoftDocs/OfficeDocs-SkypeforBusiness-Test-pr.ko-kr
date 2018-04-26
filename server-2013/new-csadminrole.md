---
title: New-CsAdminRole
TOCTitle: New-CsAdminRole
ms:assetid: 1e46c02e-0937-4e3b-b02e-e7507189f6aa
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398271(v=OCS.15)
ms:contentKeyID: 49303018
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsAdminRole

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 RBAC(역할 기반 액세스 제어) 역할을 만듭니다. RBAC 역할은 사용자가 수행할 수 있는 관리 작업을 정의하고 사용자가 이러한 작업을 수행할 수 있는 범위를 결정하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsAdminRole -Identity <String> -Template <String> [-Cmdlets <PSListModifier>] [-ConfigScopes <PSListModifier>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-ScriptModules <PSListModifier>] [-UserScopes <PSListModifier>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1의 명령은 RBAC 역할 CsVoiceAdministrator를 복제합니다. 추가 매개 변수를 사용하지 않으므로 새 역할 RedmondVoiceAdministrators는 CsVoiceAdministrator의 정확한 복제본이 됩니다. 따라서 여기에는 "global"로 설정되는 UserScopes 및 ConfigScopes 속성이 둘 다 포함됩니다.

    New-CsAdminRole -Identity "RedmondVoiceAdministrator" -Template "CsVoiceAdministrator"

## 예제 2

예제 2에서는 새 RBAC 역할(RedmondVoiceAdministrator)을 만든 다음 Redmond OU라는 단일 사용자 범위를 허용하도록 역할을 구성합니다. 이 작업을 수행하기 위해 UserScopes 매개 변수가 매개 변수 값 "OU:ou=Redmond,dc=litwareinc,dc=com"과 함께 포함됩니다. 이 매개 변수 값은 UserScopes 속성의 현재 값을 한 개 항목(DN(고유 이름)이 "ou=Redmond,dc=litwareinc,dc=com"인 OU)으로 바꿉니다.

    New-CsAdminRole -Identity "RedmondVoiceAdministrator" -Template "CsVoiceAdministrator" -UserScopes "OU:ou=Redmond,dc=litwareinc,dc=com"

## 예제 3

예제 3에 표시된 명령은 예제 2에 표시된 명령의 변형이며, UserScopes 속성에 두 개의 OU가 추가된다는 점만 다릅니다. 이 작업을 수행하려면 Replace 메서드에 쉼표로 구분된 목록을 할당하면 됩니다. 목록의 두 항목은 새 RBAC 역할에 할당한 두 OU(Redmond 및 Portland)의 식별자를 나타냅니다.

    New-CsAdminRole -Identity "RedmondVoiceAdministrator" -Template "CsVoiceAdministrator" -UserScopes "OU:ou=Redmond,dc=litwareinc,dc=com","OU:ou=Portland,dc=litwareinc,dc=com"

## 예제 4

예제 4에서는 SiteId가 Redmond인 사이트를 새 RBAC 역할의 ConfigScopes 속성에 할당합니다. ConfigScopes 속성에 대한 구문에는 "site:" 접두사를 사용하고 추가할 사이트의 SiteId 속성 값이 뒤에 오도록 해야 합니다.

    New-CsAdminRole -Identity "RedmondVoiceAdministrator" -Template "CsVoiceAdministrator" -ConfigScopes "site:Redmond"

## 자세한 정보

RBAC(역할 기반 액세스 제어)를 사용하면 관리자가 Lync Server에서 특정 관리 작업에 대한 제어를 위임할 수 있습니다. 예를 들어 조직의 지원 센터에 모든 관리자 권한을 부여하는 대신, 사용자 계정만 관리할 권한, Enterprise Voice 구성 요소만 관리할 권한, 보관 및 보관 서버만 관리할 권한 등의 특정 권한을 이러한 직원에게 부여할 수 있습니다. 또한 이러한 권한을 범위로 제한할 수 있습니다. 어떤 사람에게는 Redmond 사이트에 대해서만 Enterprise Voice 관리 권한을 부여하고, 또 다른 사람에게는 Finance OU(조직 구성 단위)에 있는 사용자 계정에 대해서만 사용자 관리 권한을 부여할 수 있습니다.

Lync Server의 RBAC 구현은 Active Directory 보안 그룹 및 Windows PowerShell cmdlet의 두 가지 주요 요소를 기반으로 합니다. Lync Server를 설치하면 몇 가지 유니버설 보안 그룹(CsAdministrator, CsArchivingAdministrator, CsArchivingAdministrator, CsHelpDesk 등)이 만들어집니다. 이러한 유니버설 보안 그룹은 RBAC 역할에 일 대 일로 대응합니다. 즉, CsArchivingAdministrator 보안 그룹에 속한 사용자에게는 CsArchivingAdministrator RBAC 역할에 대한 모든 권한이 부여됩니다. 또한 RBAC 역할에 부여되는 권한은 해당 역할에 할당된 cmdlet을 기반으로 합니다. cmdlet은 여러 RBAC 역할에 할당될 수 있습니다. 예를 들어 역할에 다음 cmdlet이 할당되었다고 가정해 보겠습니다.

Get-ArchivingPolicy

Grant-ArchivingPolicy

New-ArchivingPolicy

Remove-ArchivingPolicy

Set-ArchivingPolicy

Get-ArchivingConfiguration

New-ArchivingConfiguration

Remove-ArchivingConfiguration

Set-ArchivingConfiguration

Get-CsUser

Export-CsArchivingData

Get-CsComputer

Get-CsPool

Get-CsService

Get-CsSite

위 목록은 가상 RBAC 역할이 할당된 사용자가 원격 Windows PowerShell 명령줄 인터페이스 세션 동안 실행할 수 있는 cmdlet만 나타냅니다. 사용자가 **Disable-CsUser** cmdlet을 실행하려고 하면 해당 명령이 실패합니다. 가상 역할이 할당된 사용자는 **Disable-CsUser** cmdlet을 실행할 권한이 없기 때문입니다. 이는 Lync Server 제어판에도 마찬가지로 적용됩니다. 예를 들어 Lync Server 제어판에서 RBAC 역할을 준수하기 때문에 보관 관리자는 Lync Server 제어판을 사용하여 사용자를 비활성화할 수 없습니다. Lync Server 제어판에서 명령을 실행할 때마다 실제로 Windows PowerShell cmdlet이 호출됩니다. **Disable-CsUser** cmdlet을 실행할 수 없는 경우 Windows PowerShell에서 cmdlet을 직접 실행하는지, 아니면 Lync Server 제어판 내에서 cmdlet을 간접적으로 실행하는지에 관계없이 명령이 실패합니다.

RBAC는 원격 관리에만 적용됩니다. Lync Server를 실행 중인 컴퓨터에 로그온하고 Lync Server 관리 셸을 열면 RBAC 역할이 적용되지 않습니다. 대신, 주로 RTCUniversalServerAdmins, RTCUniversalUserAdmins 및 RTCUniversalReadOnlyAdmins 보안 그룹을 통해 보안이 적용됩니다.

Lync Server를 설치할 때 설치 프로그램에서 몇 가지 기본 제공 RBAC 역할을 만듭니다. 이러한 역할은 음성 관리, 사용자 관리 및 응답 그룹 관리와 같은 일반 관리 영역에 적용됩니다. 기본 제공 역할은 어떠한 방법으로도 수정할 수 없습니다. 즉, 역할에 cmdlet을 추가하거나 제거할 수 없으며 이러한 역할을 삭제할 수도 없습니다. 기본 제공 역할을 삭제하려고 하면 오류가 발생합니다. 그러나 기본 제공 역할을 사용하여 사용자 지정 RBAC 역할을 만들 수 있습니다. 그러면 관리 범위를 변경하여 이러한 사용자 지정 역할을 수정할 수 있습니다. 예를 들어 특정 Active Directory OU의 사용자 계정을 관리하도록 역할을 제한할 수 있습니다.

새 역할을 만들려면 먼저 Active Directory 도메인 서비스에서 해당 역할과 이름을 공유하는 유니버설 보안 그룹을 만들어야 합니다. 예를 들어 DialInConferencingAdministrator라는 새 역할을 만들려면 SamAccountName이 DialInConferencingAdministrator인 보안 그룹을 만들어야 합니다. **New-CsAdminRole** cmdlet은 이 그룹을 만들지 않습니다. **New-CsAdminRole** cmdlet을 호출할 때 DialInConferencingAdministrator 그룹이 없으면 명령이 실패합니다. 새 역할에 할당하는 ID는 해당 Active Directory 그룹의 SamAccountName이어야 합니다.

Active Directory 보안 그룹을 만든 후 새 사용자 지정 역할의 템플릿으로 사용할 기본 제공 RBAC 역할을 선택해야 합니다. **New-CsAdminRole** cmdlet을 사용하여 빈 RBAC 역할을 만들 수는 없습니다. 모든 사용자 지정 역할은 기본 제공 RBAC 역할 중 한 개를 기반으로 해야 합니다. 즉, 사용자 지정 역할에는 기본 제공 역할 중 한 개와 동일한 cmdlet이 할당되어 있어야 합니다. 그러나 **Set-CsAdminRole** cmdlet을 사용하여 이 사용자 지정 역할의 관리 범위를 변경할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsAdminRole** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 가져오려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsAdminRole"}

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
<td><p>System.String</p></td>
<td><p>만들려는 RBAC 역할의 고유 식별자입니다. RBAC 역할의 ID는 해당 역할에 연결된 Active Directory 유니버설 보안 그룹의 SamAccountName과 같아야 합니다. 예를 들어 Help Desk 역할의 ID는 CsHelpDesk와 같습니다. CsHelpDesk는 해당 역할에 연결된 Active Directory 보안 그룹의 SamAccountName이기도 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Template</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>만들려는 사용자 지정 RBAC 역할의 템플릿으로 사용할 기본 제공 RBAC 역할의 이름입니다. 새 RBAC 역할은 모두 기본 역할을 기반으로 해야 합니다. 할당된 cmdlet이 없거나 ConfigScopes 또는 UserScopes 속성에 지정된 값이 없는 역할인 빈 RBAC 역할을 만들 수는 없습니다. 그러나 사용자 지정 역할을 만든 후 <strong>Set-CsAdminRole</strong> cmdlet을 사용하여 새 역할의 속성을 수정할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Cmdlets</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>새 RBAC 역할을 소유할 사용자가 사용할 수 있는 cmdlet을 지정할 수 있습니다. 예를 들어 <strong>Export-CsArchivingData</strong> cmdlet 하나에만 액세스할 수 있도록 하는 새 역할을 만들려면 다음과 같은 구문을 사용합니다.</p>
<p>-Cmdlets &quot;Export-CsArchivingData&quot;</p>
<p>여러 cmdlet에 대한 액세스를 허용하려면 쉼표를 사용하여 cmdlet 이름을 구분합니다.</p>
<p>-Cmdlets &quot;Export-CsArchivingData&quot;,&quot;Invoke-CsArchivingDatabasePurge&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>ConfigScopes</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>cmdlet의 범위를 지정한 사이트 내의 구성 설정으로 제한하는 데 사용됩니다. cmdlet 범위를 단일 사이트로 제한하려면 -ConfigScopes site:Redmond와 유사한 구문을 사용합니다. 쉼표로 구분된 목록을 사용하여 여러 개의 사이트를 지정할 수 있습니다(예: -ConfigScopes &quot;site:Redmond, &quot;site:Dublin&quot;). 또한 ConfigScopes 속성을 &quot;global&quot;로 설정할 수도 있습니다.</p>
<p>ConfigScopes 매개 변수에 값을 할당할 때는 &quot;site:&quot; 접두사를 사용하고 사이트의 SiteId 속성이 뒤에 오도록 해야 합니다. SiteID 값은 사이트의 Identity 또는 사이트의 DisplayName과 같지 않아도 됩니다. 지정된 사이트의 SiteId를 결정하려면 다음과 유사한 명령을 사용하면 됩니다.</p>
<p>Get-CsSite &quot;Redmond&quot; | Select-Object SiteId</p>
<p>ConfigScopes 속성 값과 UserScopes 속성 값 중 하나 또는 둘 다를 지정해야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
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
<td><p><em>ScriptModules</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>Windows PowerShell 스크립트 내에서 함수를 지정할 수 있습니다. 이러한 함수는 새 RBAC 역할을 소유할 사용자가 사용할 수 있게 됩니다. 예를 들어 다음 구문은 UpdateDatabase.ps1 스크립트에서 Reset 함수에 대한 액세스를 허용합니다.</p>
<p>-ScriptModules &quot;UpdateDatabase.ps1:Reset&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>UserScopes</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>cmdlet의 범위를 지정한 조직 구성 단위 내의 사용자 관리 활동으로 제한하는 데 사용됩니다. cmdlet 범위를 단일 조직 구성 단위로 제한하려면 -UserScopes &quot;OU:ou=Redmond,dc=litwareinc,dc=com&quot;과 유사한 구문을 사용합니다. 쉼표로 구분된 목록을 사용하여 여러 개의 OU를 지정할 수 있습니다(예: -UserScopes &quot;OU:ou=Redmond,dc=litwareinc,dc=com&quot;, &quot;OU:ou=Dublin,dc=litwareinc,dc=com&quot;). 역할의 새 범위를 추가하거나 기존 범위를 제거하려면 Windows PowerShell 목록 한정자 구문을 사용합니다. 자세한 내용은 이 항목의 예제 섹션을 참조하십시오.</p>
<p>ConfigScopes 속성 값과 UserScopes 속성 값 중 하나 또는 둘 다를 지정해야 합니다.</p></td>
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

없음.

## 반환 형식

**New-CsAdminRole** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Roles.Role 개체의 새 인스턴스를 만듭니다.

