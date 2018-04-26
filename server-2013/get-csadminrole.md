---
title: Get-CsAdminRole
TOCTitle: Get-CsAdminRole
ms:assetid: ea15ee37-f7a1-4e67-afe8-08e63e8ca765
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399050(v=OCS.15)
ms:contentKeyID: 49305409
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsAdminRole

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용되는 RBAC(역할 기반 액세스 제어) 역할에 대한 정보를 반환합니다. RBAC 역할은 사용자가 수행할 수 있는 관리 작업을 지정하고 사용자가 이러한 작업을 수행할 수 있는 범위를 결정하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsAdminRole [-Identity <String>] <COMMON PARAMETERS>

    Get-CsAdminRole [-Sid <String>] <COMMON PARAMETERS>

    Get-CsAdminRole [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 사용하도록 구성된 모든 RBAC 역할에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 매개 변수 없이 **Get-CsAdminRole** cmdlet을 호출합니다.

    Get-CsAdminRole

## 예제 2

예제 2에서는 RBAC 역할 하나, 즉, ID가 CsHelpDesk인 역할이 반환됩니다.

    Get-CsAdminRole -Identity "CsHelpDesk"

## 예제 3

예제 3에서는 ID에 "Voice"라는 문자열 값이 포함된 RBAC 역할(예: CsVoiceAdministrator, RedmondVoiceAdministrators)을 모두 반환합니다. 이 작업을 수행하기 위해 **Get-CsAdminRole** 및 Filter 매개 변수를 호출합니다. 필터 값 "\*Voice\*"는 반환되는 데이터를 ID에 "Voice"라는 문자열 값이 포함된 RBAC 역할로 제한합니다.

    Get-CsAdminRole -Filter "*Voice*"

## 예제 4

예제 4에서는 조직에서 사용하기 위해 만든 모든 사용자 지정 RBAC 역할을 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsAdminRole** cmdlet을 사용하여 현재 사용 중인 모든 RBAC 역할의 컬렉션을 반환합니다. 이 컬렉션은 IsStandardRole 속성이 False와 같은 역할만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 정의에 따라 해당 조건을 충족하는 모든 역할이 사용자 지정 RBAC 역할입니다.

    Get-CsAdminRole | Where-Object {$_.IsStandardRole -eq $False}

## 예제 5

예제 5에 표시된 명령은 **Set-CsUser** cmdlet이 포함된 모든 RBAC 역할을 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsAdminRole** cmdlet을 호출하여 조직의 모든 RBAC 역할의 컬렉션을 반환합니다. 이 컬렉션은 Cmdlets 속성이 문자열 값 "Set-CsUser\\b"를 포함하는 모든 역할을 선택하는 **Where-Object** cmdlet에 파이프됩니다. \\b는 "Set-CsUser"가 전체 문자열 값을 나타낸다는 의미의 단어 경계 표시입니다.

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsUser\b"}

## 예제 6

예제 6에서는 UserScopes 속성에 지정된 OU(ou=Redmond, dc=litwareinc, dc=com)를 포함하는 모든 RBAC 역할에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsAdminRole** cmdlet을 호출하여 현재 사용하도록 구성된 모든 RBAC 역할의 컬렉션을 반환합니다. 그러면 이 컬렉션은 UserScopes 속성에 문자열 값 "OU:ou=Redmond,dc=litwareinc,dc=com"을 포함하는 역할을 모두 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsAdminRole | Where-Object {$_.UserScopes -match "OU: ou=Redmond,dc=litwareinc,dc=com"}

## 예제 7

예제 7에 표시된 명령은 CsVoiceAdministrator 역할에 포함된 모든 cmdlet의 목록을 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsAdminRole** cmdlet을 사용하여 CsVoiceAdministrator의 모든 속성 및 속성 값을 반환합니다. 이 정보는 ExpandProperty 매개 변수를 사용하여 Cmdlets 속성에 포함된 모든 항목을 표시하는 **Select-Object** cmdlet에 파이프됩니다.

    Get-CsAdminRole -Identity "CsVoiceAdministrator" | Select-Object -ExpandProperty Cmdlets

## 자세한 정보

RBAC(역할 기반 액세스 제어)를 사용하면 관리자가 Lync Server에서 특정 관리 작업에 대한 제어를 위임할 수 있습니다. 예를 들어 조직의 지원 센터에 전체 관리자 권한을 부여하지 않고 사용자 계정만 관리하는 권한, Enterprise Voice 구성 요소만 관리하는 권한, 그리고 보관 및 보관 서버만 관리하는 권한과 같은 구체적인 권한을 지원 센터 담당자에게 부여할 수 있습니다. 또한 이러한 권한은 특정 범위로 제한될 수 있습니다. 어떤 사람에게는 Redmond 사이트에 대해서만 Enterprise Voice 관리 권한을 부여하고, 또 다른 사람에게는 Finance OU(조직 구성 단위)에 있는 사용자 계정에 대해서만 사용자 관리 권한을 부여할 수 있습니다.

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

위의 목록은 사용자가 가상 RBAC 역할을 할당한 cmdlet만 Windows PowerShell 명령줄 인터페이스의 원격 세션에서 실행할 수 있음을 나타냅니다. 사용자가 **Disable-CsUser** cmdlet을 실행하려고 하면 가상 역할이 할당된 사용자에게 **Disable-CsUser** cmdlet 실행 권한이 없으므로 명령이 실패합니다. 이는 Lync Server 제어판에도 적용됩니다. 예를 들어 Lync Server 제어판에서 RBAC 역할을 준수하기 때문에 보관 관리자는 Lync Server 제어판을 사용하여 사용자를 비활성화할 수 없습니다. Lync Server 제어판에서 명령을 실행할 때마다 실제로 Windows PowerShell cmdlet이 호출됩니다. **Disable-CsUser** cmdlet을 실행할 수 없는 경우 Windows PowerShell의 원격 세션에서 cmdlet을 직접 실행하는지, 아니면 Lync Server 제어판 내에서 cmdlet을 간접적으로 실행하는지에 관계없이 명령이 실패합니다.

RBAC는 원격 관리에만 적용됩니다. Lync Server를 실행 중인 컴퓨터에 로그온하고 Lync Server 관리 셸을 열면 RBAC 역할이 적용되지 않습니다. 대신, 주로 RTCUniversalServerAdmins, RTCUniversalUserAdmins 및 RTCUniversalReadOnlyAdmins 보안 그룹을 통해 보안이 적용됩니다.

Lync Server를 설치할 때 설치 프로그램에서 여러 개의 기본 제공 RBAC 역할을 만듭니다. 이러한 역할에는 음성 관리, 사용자 관리, 응답 그룹 관리 등 일반적인 관리 분야를 담당하는 역할이 포함됩니다. 이러한 기본 제공 역할은 어떠한 방법으로도 수정할 수 없습니다. 즉, 이러한 역할에 cmdlet을 추가하거나 제거할 수 없고 이러한 역할을 삭제할 수 없습니다. 기본 제공 역할을 삭제하려고 하면 오류 메시지가 나타납니다. 그러나 기본 제공 역할을 사용하여 사용자 지정 RBAC 역할을 만들 수는 있습니다. 그러면 관리 범위를 변경하여 이러한 사용자 지정 역할을 수정할 수 있습니다. 예를 들어 특정 Active Directory OU를 사용하여 사용자 계정을 관리하도록 역할을 제한할 수 있습니다.

**Get-CsAdminRole** cmdlet은 조직에서 사용할 수 있는 모든 RBAC 역할에 대한 정보를 반환합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 TCUniversalUserAdmins, RTCUniversalServerAdmins, RTCUniversalReadOnlyAdmins 그룹의 구성원은 **Get-CsAdminRole** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 가져오려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsAdminRole\\b"}

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
<td><p>와일드카드를 사용하여 반환할 RBAC 역할을 하나 이상 지정할 수 있습니다. 예를 들어 ID에 &quot;Redmond&quot;라는 문자열 값이 포함된 역할을 모두 반환하려면 다음 구문을 사용할 수 있습니다. -Filter &quot;*Redmond*&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>반환할 RBAC 역할의 고유 식별자입니다. RBAC 역할의 ID는 해당 역할에 연결된 Active Directory 유니버설 보안 그룹의 SamAccountName과 같아야 합니다. 예를 들어 Help Desk 역할의 ID는 CsHelpDesk와 같습니다. CsHelpDesk는 해당 역할에 연결된 Active Directory 보안 그룹의 SamAccountName이기도 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 RBAC 데이터를 검색합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Sid</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>SID(보안 식별자)를 사용하여 검색할 RBAC 역할을 지정할 수 있습니다. SID는 RBAC 역할이 만들어질 때 Lync Server에 의해 할당되며 S-1-5-21-1573807623-1597889489-1765977225-1145와 유사한 형태입니다.</p>
<p>이와 같은 SID는 해당 Active Directory 보안 그룹에서도 찾을 수 있습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

**Get-CsAdminRole** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Roles.Role 개체의 인스턴스를 반환합니다.

