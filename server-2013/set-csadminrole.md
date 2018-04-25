---
title: Set-CsAdminRole
TOCTitle: Set-CsAdminRole
ms:assetid: ec927ce6-a37b-4876-a6df-a347404f4e84
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399066(v=OCS.15)
ms:contentKeyID: 49305437
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsAdminRole

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 RBAC(역할 기반 액세스 제어) 역할을 수정합니다. RBAC 역할은 사용자가 수행할 수 있는 관리 작업을 지정하고 사용자가 이러한 작업을 수행할 수 있는 범위를 결정하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsAdminRole -Identity <String> [-Cmdlets <PSListModifier>] [-ConfigScopes <PSListModifier>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-ScriptModules <PSListModifier>] [-UserScopes <PSListModifier>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 RBAC 역할 RedmondVoiceAdministrators의 UserScopes 속성에 새 OU(Portland)를 추가합니다. 이 작업을 수행하기 위해 명령은 UserScopes 매개 변수 및 @{Add="OU:ou=Portland,dc=litwareinc,dc=com"} 매개 변수 값을 포함합니다. 이 구문은 UserScopes 속성에 이미 있는 OU에 고유 이름이 "ou=Portland,dc=litwareinc,dc=com"인 OU를 추가합니다.

    Set-CsAdminRole -Identity "RedmondVoiceAdministrators" -UserScopes @{Add="OU:ou=Portland,dc=litwareinc,dc=com"}

## 예제 2

예제 2에 표시된 명령은 RBAC 역할 RedmondVoiceAdministrators에서 Portland OU를 제거합니다. 이 작업을 수행하기 위해 명령은 UserScopes 매개 변수 및 @{Remove="OU:ou=Portland,dc=litwareinc,dc=com"} 매개 변수 값을 포함합니다. 이 구문은 UserScopes 속성에 이미 있는 OU 컬렉션에서 고유 이름이 "ou=Portland,dc=litwareinc,dc=com"인 OU를 삭제합니다.

    Set-CsAdminRole -Identity "RedmondVoiceAdministrators" -UserScopes @{Remove="OU:ou=Portland,dc=litwareinc,dc=com"}

## 예제 3

예제 3에서는 RBAC 역할 RedmondVoiceAdministrators의 ConfigScopes 속성에 SiteId가 Redmond인 새 사이트를 추가합니다. 이 작업을 수행하기 위해 명령은 ConfigScopes 매개 변수 및 @{Add="OU:ou=Portland,dc=litwareinc,dc=com"} 매개 변수 값을 포함합니다. 이 구문은 ConfigScopes 속성에 이미 있는 모든 항목에 Redmond 사이트를 추가합니다.

    Set-CsAdminRole -Identity "RedmondVoiceAdministrators" -ConfigScopes @{Add="site:Redmond"}

## 예제 4

예제 4에 표시된 명령은 RBAC 역할 RedmondVoiceAdministrators에서 Redmond 사이트를 제거합니다. 이 작업을 수행하기 위해 명령은 ConfigScopes 매개 변수 및 @{Remove="site:Redmond"} 매개 변수 값을 포함합니다. 이 매개 변수는 ConfigScopes 속성에 이미 있는 항목 컬렉션에서 Redmond 사이트를 삭제합니다. Redmond 사이트가 ConfigScopes 속성에서 유일한 사이트인 경우 이 명령이 실패하게 됩니다. ConfigScopes 속성에서 유일한 사이트를 제거하는 경우 ConfigScopes의 모든 항목을 Global 속성으로 대체하는 다음과 유사한 명령을 사용해야 합니다.

Set-CsAdminRole -Identity "RedmondVoiceAdministrators" -ConfigScopes @{Replace="Global"}

    Set-CsAdminRole -Identity "RedmondVoiceAdministrators" -ConfigScopes @{Remove="siteRedmond"}

## 자세한 정보

RBAC를 통해 관리자는 Lync Server에서 특정 관리 작업의 제어권을 위임할 수 있습니다. 예를 들어 조직의 지원 센터에 전체 관리자 권한을 부여하지 않고 사용자 계정만 관리하는 권한, Enterprise Voice 구성 요소만 관리하는 권한, 그리고 보관 및 보관 서버만 관리하는 권한과 같은 구체적인 권한을 지원 센터 담당자에게 부여할 수 있습니다. 또한 이러한 권한은 특정 범위로 제한될 수 있습니다. 어떤 사람에게는 Redmond 사이트에 대해서만 Enterprise Voice 관리 권한을 부여하고, 또 다른 사람에게는 Finance OU(조직 구성 단위)에 있는 사용자 계정에 대해서만 사용자 관리 권한을 부여할 수 있습니다.

Lync Server의 RBAC 구현은 Active Directory 보안 그룹 및 Windows PowerShell cmdlet의 두 가지 주요 요소를 기반으로 합니다. Lync Server를 설치하면 여러 유니버설 보안 그룹(CsAdministrator, CsArchivingAdministrator 및 CsViewOnlyAdministrator 등)이 만들어집니다. 이러한 유니버설 보안 그룹은 RBAC 역할에 일 대 일로 대응합니다. 즉, CsArchivingAdministrator 보안 그룹에 속한 사용자에게는 CsArchivingAdministrator RBAC 역할에 대한 모든 권한이 부여됩니다. 차례로 RBAC 역할에 부여되는 권한은 해당 역할에 할당된 cmdlet(cmdlet은 여러 RBAC 역할에 할당 가능)을 기반으로 합니다. 예를 들어 역할에 다음 cmdlet이 할당되었다고 가정해 보겠습니다.

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

위의 목록은 사용자가 가상 RBAC 역할을 할당한 cmdlet만 Windows PowerShell 명령줄 인터페이스의 원격 세션에서 실행할 수 있음을 나타냅니다. 사용자가 **Disable-CsUser** cmdlet을 실행하려고 하면 가상 역할이 할당된 사용자에게 **Disable-CsUser** cmdlet 실행 권한이 없으므로 명령이 실패합니다. 이는 Lync Server 제어판에도 적용됩니다. 예를 들어 Lync Server 제어판에서 RBAC 역할을 준수하기 때문에 보관 관리자는 Lync Server 제어판을 사용하여 사용자를 비활성화할 수 없습니다. Lync Server 제어판에서 명령을 실행할 때마다 실제로 Windows PowerShell cmdlet이 호출됩니다. **Disable-CsUser** cmdlet을 실행할 수 없는 경우 Windows PowerShell에서 cmdlet을 직접 실행하는지, 아니면 Lync Server 제어판 내에서 cmdlet을 간접적으로 실행하는지에 관계없이 명령이 실패합니다.

RBAC는 원격 관리에만 적용됩니다. Lync Server를 실행 중인 컴퓨터에 로그온하고 Lync Server 관리 셸을 열면 RBAC 역할이 적용되지 않습니다. 대신, 주로 RTCUniversalServerAdmins, RTCUniversalUserAdmins 및 RTCUniversalReadOnlyAdmins 보안 그룹을 통해 보안이 적용됩니다.

Lync Server를 설치할 때 설치 프로그램에서 여러 개의 기본 제공 RBAC 역할, 즉 음성 관리, 사용자 관리, 응답 그룹 관리 등 일반적인 관리 분야를 담당하는 역할을 만듭니다. 이러한 기본 제공 역할은 어떠한 방법으로도 수정할 수 없습니다. 즉, 이러한 역할에 cmdlet을 추가하거나 제거할 수 없고 이러한 역할을 삭제할 수 없습니다. 기본 제공 역할을 삭제하려고 하면 오류 메시지가 나타납니다. 그러나 기본 제공 역할을 사용하여 사용자 지정 RBAC 역할을 만들 수는 있습니다. 그러면 관리 범위를 변경하여 이러한 사용자 지정 역할을 수정할 수 있습니다. 예를 들어 특정 Active Directory OU에서 사용자 계정을 관리하도록 역할을 제한할 수 있습니다.

새로 만드는 사용자 지정 역할은 템플릿, 즉 기존 RBAC 역할을 기반으로 해야 합니다. 예를 들어 전화 접속 회의 관리자 역할을 만들려면 기존 RBAC 역할을 효과적으로 복제해야 합니다. 예를 들어 전화 접속 회의 관리자 역할은 기존 음성 관리자 역할을 기반으로 할 수 있습니다. 사용자 지정 역할을 만든 후에는 **Set-CsAdminRole** cmdlet을 사용하여 새 역할의 속성을 수정할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsAdminRole cmdlet**을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 가져오려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsAdminRole"}

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
<td><p>수정할 RBAC 역할의 고유 식별자입니다. RBAC 역할의 ID는 해당 역할에 연결된 Active Directory 유니버설 보안 그룹의 SamAccountName과 같아야 합니다. 예를 들어 Help Desk 역할의 ID는 CsHelpDesk와 같습니다. CsHelpDesk는 해당 역할에 연결된 Active Directory 보안 그룹의 SamAccountName이기도 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Cmdlets</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>새 RBAC 역할을 소유할 사용자가 사용할 수 있는 cmdlet을 지정할 수 있습니다. 예를 들어 <strong>Export-CsArchivingData</strong> cmdlet 하나에만 액세스할 수 있도록 하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Cmdlets &quot;Export-CsArchivingData&quot;</p>
<p>위의 구문은 Cmdlets 속성에 현재 저장되어 있는 모든 항목을 단일 항목(Export-CsArchivingData)으로 바꿉니다. <strong>Export-CsArchivingData</strong> cmdlet을 해당 속성에 이미 저장된 cmdlet에 추가하려면 다음 구문을 대신 사용합니다.</p>
<p>-Cmdlets @{Add=&quot;Export-CsArchivingData&quot;}</p>
<p>여러 cmdlet을 추가하려면 다음과 같이 cmdlet 이름을 쉼표로 구분합니다.</p>
<p>-Cmdlets @{Add=&quot;Export-CsArchivingData&quot;,&quot;Invoke-CsArchivingDatabasePurge&quot;}</p>
<p>역할에서 cmdlet을 제거하려면 다음 구문을 사용합니다.</p>
<p>-Cmdlets @{Remove=&quot;Export-CsArchivingData&quot;}</p></td>
</tr>
<tr class="odd">
<td><p><em>ConfigScopes</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>cmdlet의 범위를 지정된 사이트 내의 구성 설정으로 제한합니다. cmdlet 범위를 단일 사이트로 제한하려면 -ConfigScopes site:Redmond와 유사한 구문을 사용합니다. 쉼표로 구분된 목록을 사용하여 여러 사이트를 지정할 수도 있습니다(예: -ConfigScopes &quot;site:Redmond, &quot;site:Dublin&quot;). 또한 ConfigScopes 속성을 &quot;global&quot;로 설정할 수도 있습니다.</p>
<p>ConfigScopes 매개 변수에 값을 할당할 때는 &quot;site:&quot; 접두사를 사용하고 그 뒤에 사이트의 SiteId 속성 값을 제공해야 합니다. SiteId 값은 사이트의 Identity 또는 사이트의 DisplayName과 다를 수도 있습니다. 특정 사이트의 SiteId를 확인하려면 다음과 유사한 명령을 사용하면 됩니다.</p>
<p>Get-CsSite &quot;Redmond&quot; | Select-Object SiteId</p>
<p>ConfigScopes 속성 값과 UserScopes 속성 값 중 하나 또는 둘 다를 지정해야 합니다.</p></td>
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
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ScriptModules</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>Windows PowerShell 스크립트 내에서 함수를 지정할 수 있습니다. 이러한 함수는 새 RBAC 역할을 소유할 사용자가 사용할 수 있게 됩니다. 예를 들어 다음 구문은 UpdateDatabase.ps1 스크립트에서 Reset 함수에 대한 액세스를 허용합니다.</p>
<p>-ScriptCmdlets &quot;UpdateDatabase.ps1:Reset&quot;</p>
<p>위의 명령은 ScriptCmdlets 속성에 현재 저장되어 있는 모든 스크립트를 Reset 함수 및 UpdateDatabase.ps1 스크립트로 바꿉니다. 이 스크립트/함수를 현재 ScriptCmdlets 속성에 저장되어 있는 항목에 추가하려면 다음 구문을 사용합니다.</p>
<p>-ScriptCmdlets @{Add=&quot;UpdateDatabase.ps1:Reset&quot;}</p>
<p>스크립트/함수를 제거하려면 다음 구문을 사용합니다.</p>
<p>-ScriptCmdlets @{Add=&quot;UpdateDatabase.ps1:Reset&quot;}</p>
<p>다음 구문을 사용하면 역할에 할당된 모든 ScriptCmdlets를 삭제할 수 있습니다.</p>
<p>-ScriptCmdlets $Null</p></td>
</tr>
<tr class="odd">
<td><p><em>UserScopes</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>cmdlet의 범위를 지정된 OU 내의 사용자 관리 작업으로 제한합니다. cmdlet 범위를 단일 OU로 제한하려면 -UserScopes &quot;OU:ou=Redmond,dc=litwareinc,dc=com&quot;과 유사한 구문을 사용합니다. 쉼표로 구분된 목록을 사용하여 여러 OU를 지정할 수도 있습니다(예: -UserScopes &quot;OU:ou=Redmond,dc=litwareinc,dc=com&quot;, &quot;OU:ou=Dublin,dc=litwareinc,dc=com&quot;). 역할의 새 범위를 추가하거나 기존 범위를 제거하려면 Windows PowerShell 목록 한정자 구문을 사용합니다. 자세한 내용은 이 도움말 항목의 예제 섹션을 참조하십시오.</p>
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

**Set-CsAdminRole** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Roles.Role 개체의 인스턴스를 구성합니다.

