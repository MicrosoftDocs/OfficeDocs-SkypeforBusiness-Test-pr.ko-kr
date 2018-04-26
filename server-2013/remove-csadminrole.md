---
title: Remove-CsAdminRole
TOCTitle: Remove-CsAdminRole
ms:assetid: f676d3d5-2d4c-4095-a174-9278bc0852df
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413036(v=OCS.15)
ms:contentKeyID: 49305549
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsAdminRole

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 RBAC(역할 기반 액세스 제어) 역할을 제거합니다. RBAC 역할은 사용자가 수행할 수 있는 관리 작업을 지정하고 사용자가 이러한 작업을 수행할 수 있는 범위를 결정하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsAdminRole -Identity <String> <COMMON PARAMETERS>

    Remove-CsAdminRole -Sid <String> <COMMON PARAMETERS>

    Remove-CsAdminRole [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 RedmondHelpDesk인 RBAC 역할을 삭제합니다.

    Remove-CsAdminRole -Identity "RedmondHelpDesk"

## 예제 2

예제 2에서는 ID에 "Redmond"라는 문자열 값이 포함된 RBAC 역할을 모두 삭제합니다.

    Remove-CsAdminRole -Filter "*Redmond*"

## 예제 3

예제 3에서는 명령이 조직에서 사용하기 위해 만들어진 모든 사용자 지정 RBAC 역할을 삭제합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsAdminRole** cmdlet을 매개 변수 없이 호출합니다. 그러면 RBAC 역할 컬렉션이 반환됩니다. 이 컬렉션은 IsStandardRole 속성이 False와 같은 역할만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 정의에 따라 이러한 기준을 충족하는 모든 역할은 사용자 지정 역할입니다. 그리고 이러한 사용자 지정 역할이 **Remove-CsAdminRole** cmdlet에 파이프되고 이 cmdlet에 의해 삭제됩니다.

    Get-CsAdminRole | Where-Object {$_.IsStandardRole -eq $False} | Remove-CsAdminRole

## 자세한 정보

RBAC를 통해 관리자는 Lync Server에서 특정 관리 작업의 제어권을 위임할 수 있습니다. 예를 들어 조직의 지원 센터에 모든 관리자 권한을 부여하는 대신, 사용자 계정만 관리할 권한, Enterprise Voice 구성 요소만 관리할 권한, 보관 및 보관 서버만 관리할 권한 등의 특정 권한을 이러한 직원에게 부여할 수 있습니다. 또한 이러한 권한은 특정 범위로 제한될 수 있습니다. 어떤 사람에게는 Redmond 사이트에 대해서만 Enterprise Voice 관리 권한을 부여하고, 또 다른 사람에게는 Finance OU(조직 구성 단위)에 있는 사용자 계정에 대해서만 사용자 관리 권한을 부여할 수 있습니다.

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

위의 목록은 사용자가 가상 RBAC 역할을 할당한 cmdlet만 Windows PowerShell 명령줄 인터페이스의 원격 세션에서 실행할 수 있음을 나타냅니다. 사용자가 **Disable-CsUser** cmdlet을 실행하려고 하면 해당 명령이 실패합니다. 가상 역할이 할당된 사용자는 **Disable-CsUser** cmdlet을 실행할 권한이 없기 때문입니다. 이는 Lync Server 제어판에도 마찬가지로 적용됩니다. 예를 들어 Lync Server 제어판에서 RBAC 역할을 준수하기 때문에 보관 관리자는 Lync Server 제어판을 사용하여 사용자를 비활성화할 수 없습니다. Lync Server 제어판에서 명령을 실행할 때마다 실제로 Windows PowerShell cmdlet이 호출됩니다. **Disable-CsUser** cmdlet을 실행할 수 없는 경우 Windows PowerShell에서 cmdlet을 직접 실행하는지, 아니면 Lync Server 제어판 내에서 cmdlet을 간접적으로 실행하는지에 관계없이 명령이 실패합니다.

RBAC는 원격 관리에만 적용됩니다. Lync Server를 실행 중인 컴퓨터에 로그온하고 Lync Server 관리 셸을 열면 RBAC 역할이 적용되지 않습니다. 대신, 주로 RTCUniversalServerAdmins, RTCUniversalUserAdmins 및 RTCUniversalReadOnlyAdmins 보안 그룹을 통해 보안이 적용됩니다.

Lync Server를 설치할 때 설치 프로그램에서 여러 개의 기본 제공 RBAC 역할, 즉 음성 관리, 사용자 관리, 응답 그룹 관리 등 일반적인 관리 분야를 담당하는 역할을 만듭니다. 이러한 기본 제공 역할은 어떠한 방법으로도 수정할 수 없습니다. 즉, 이러한 역할에 cmdlet을 추가하거나 제거할 수 없고 이러한 역할을 삭제할 수 없습니다. 기본 제공 역할을 삭제하려고 하면 오류 메시지가 나타납니다. 그러나 기본 제공 역할을 사용하여 사용자 지정 RBAC 역할을 만들 수는 있습니다. 그러면 관리 범위를 변경하여 이러한 사용자 지정 역할을 수정할 수 있습니다. 예를 들어 특정 Active Directory OU를 사용하여 사용자 계정을 관리하도록 역할을 제한할 수 있습니다.

사용자가 만든 모든 사용자 지정 역할은 **Remove-CsAdminRole** cmdlet을 사용하여 삭제할 수 있습니다. **Remove-CsAdminRole** cmdlet은 사용자 지정 역할에 해당하는 Active Directory 보안 그룹을 삭제하지 않으며, 그룹에 할당된 구성원도 제거하지 않습니다. 대신에 이 사용자 지정 역할을 사용하여 Lync Server의 제어를 위임할 수 있는지만 확인합니다.

RBAC 역할을 삭제하면 Windows PowerShell이 이 역할을 삭제할 것인지 묻는 메시지를 표시합니다. 이 메시지에 응답하지 않거나 '예'를 클릭하지 않으면 역할이 삭제되지 않습니다. 이러한 확인 메시지가 표시되지 않게 하려면 Confirm 매개 변수를 사용하여 매개 변수 값을 $False로 설정합니다.

Remove-CsAdminRole RedmondAdministrators –Confirm:$False

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 Remove-CsAdminRole cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 가져오려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsAdminRole"}

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
<td><p>삭제할 RBAC 역할의 고유 식별자입니다. RBAC 역할의 ID는 해당 역할에 연결된 Active Directory 유니버설 보안 그룹의 SamAccountName과 같아야 합니다. 예를 들어 Help Desk 역할의 ID는 CsHelpDesk와 같습니다. CsHelpDesk는 해당 역할에 연결된 Active Directory 보안 그룹의 SamAccountName이기도 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Sid</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>SID(보안 식별자)를 사용하여 삭제할 RBAC 역할을 지정하는 데 사용됩니다. SID는 RBAC 역할이 만들어질 때 Lync Server에 의해 할당되며 S-1-5-21-1573807623-1597889489-1765977225-1145와 유사합니다. 지정된 RBAC 역할의 SID는 <strong>Get-CsAdminRole</strong> cmdlet을 사용하여 검색할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>RBAC 역할을 삭제하려고 할 때 나타나는 확인 메시지를 무시하는 데 사용됩니다. 메시지가 표시되지 않게 하려면 Confirm 매개 변수를 포함하고 매개 변수 값을 $False로 설정합니다.</p>
<p>Remove-CsAdminRole RedmondAdministrators –Confirm:$False</p></td>
</tr>
<tr class="even">
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>와일드카드를 사용하여 제거할 사용자 지정 RBAC 역할을 지정하는 데 사용됩니다. 예를 들어 ID에 &quot;Redmond&quot;라는 문자열 값이 포함된 사용자 지정 역할을 모두 반환하려면 -Filter &quot;*Redmond*&quot; 구문을 사용하면 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
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

Microsoft.Rtc.Management.ADConnect.Schema.ADUser 개체. **Remove-CsAdminRole** cmdlet은 사용자 개체의 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Remove-CsAdminRole** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Roles.Role 개체의 기존 인스턴스를 삭제합니다.

