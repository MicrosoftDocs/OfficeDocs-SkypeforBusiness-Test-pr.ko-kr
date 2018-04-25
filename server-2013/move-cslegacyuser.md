---
title: Move-CsLegacyUser
TOCTitle: Move-CsLegacyUser
ms:assetid: f4b36fc8-17a7-490d-a147-6d77abab0f92
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413025(v=OCS.15)
ms:contentKeyID: 49305536
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Move-CsLegacyUser

 

_**마지막으로 수정된 항목:** 2015-03-09_

Microsoft Office Communications Server 2007 R2에서 하나 이상의 사용자 계정을 Lync Server 2013으로 마이그레이션합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Move-CsLegacyUser -Identity <UserIdParameter> -Target <Fqdn> [-Confirm [<SwitchParameter>]] [-Credential <PSCredential>] [-DomainController <Fqdn>] [-ExcludeArchivingPolicy <SwitchParameter>] [-ExcludeConferencingPolicy <SwitchParameter>] [-ExcludeDialPlan <SwitchParameter>] [-ExcludeExternalAccessPolicy <SwitchParameter>] [-ExcludePresencePolicy <SwitchParameter>] [-ExcludeVoicePolicy <SwitchParameter>] [-Force <SwitchParameter>] [-HostedMigrationOverrideUrl <String>] [-IgnoreBackendStoreException <SwitchParameter>] [-PassThru <SwitchParameter>] [-ProxyPool <Fqdn>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 **Move-CsLegacyUser** cmdlet을 사용하여 ID가 Pilar Ackerman인 사용자 계정을 등록자 풀 atl-cs-001.litwareinc로 마이그레이션합니다. 추가 매개 변수가 포함되지 않았으므로 이전에 이 계정에 할당된 정책 또는 설정도 함께 마이그레이션됩니다. 즉, Pilar Ackerman에게 다이얼 플랜과 같은 레거시 정책이 할당된 경우 Pilar Ackerman의 계정을 이동하면 Lync Server 2013에 해당하는 정책이 할당됩니다.

    Move-CsLegacyUser -Identity "Pilar Ackerman" -Target "atl-cs-001.litwareinc.com"

## 예제 2

예제 2에 표시된 명령은 Pilar Ackerman의 사용자 계정을 마이그레이션하되, 이전에 할당된 다이얼 플랜은 마이그레이션하지 않습니다. 따라서 계정이 마이그레이션된 후에는 Pilar에게 할당된 다이얼 플랜이 없습니다.

    Move-CsLegacyUser -Identity "Pilar Ackerman" -Target "atl-cs-001.litwareinc.com" -ExcludeDialPlan 

## 예제 3

예제 3에서는 Finance OU에 있는 모든 사용자 계정을 등록자 풀 atl-cs-001.litwareinc.com으로 이동합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsUser** cmdlet 및 OU 매개 변수를 사용하여 Finance OU에 있는 모든 사용자 계정의 컬렉션을 검색합니다. 계정이 검색되면 컬렉션이 각 계정을 새 등록자 풀로 이동하는 **Move-CsLegacyUser** cmdlet에 파이프됩니다. 이 명령은 Finance OU의 모든 사용자를 레거시 사용자로 가정합니다.

    Get-CsUser -OU "ou=Finance,dc=litwareinc,dc=com" | Move-CsLegacyUser -Target "atl-cs-001.litwareinc.com"

## 예제 4

예제 4에서는 Move-CsLegacyUser를 사용하여 Lync Server를 사용할 수 있지만 현재 등록자 풀에 할당되지 않은 모든 사용자에게 등록자 풀을 할당합니다. 이 명령에서는 먼저 **Get-CsUser** cmdlet을 UnassignedUser 매개 변수와 함께 호출하여 등록자 풀에 현재 할당되지 않은 모든 사용자의 컬렉션을 반환합니다. 이 컬렉션은 각 사용자를 풀 atl-cs-001.litwareinc.com에 할당하는 **Move-CsLegacyUser** cmdlet에 파이프됩니다. 이 예제에서는 할당되지 않은 모든 사용자를 레거시 사용자로 가정합니다.

    Get-CsUser -UnassignedUser | Move-CsLegacyUser -Target "atl-cs-001.litwareinc.com"

## 자세한 정보

Lync Server 2013을 설치한 많은 조직에서는 이 소프트웨어의 이전 버전도 실행하고 있습니다. 최신 버전의 소프트웨어와 이전 버전의 소프트웨어를 동시에 실행할 수 있으므로 이는 문제가 되지 않습니다. 그리고 나중에 구성 설정, 정책 및 사용자 계정을 차례로 Lync Server 2013으로 마이그레이션할 수 있습니다.

**Move-CsLegacyUser** cmdlet을 사용하면 Lync Server 2013으로 마이그레이션할 수 있을 뿐만 아니라 마이그레이션 프로세스를 효과적으로 제어할 수 있습니다. 예를 들어 가장 간단한 형태로 **Move-CsLegacyUser** cmdlet에 마이그레이션할 사용자의 ID와 사용자 계정을 이동할 Lync Server 등록자 풀의 FQDN(정규화된 도메인 이름)을 제공하면 **Move-CsLegacyUser** cmdlet에서 사용자 계정을 이동하고 해당 계정에 적용된 기존 정책 및 설정을 유지 관리합니다. 예를 들어 Ken Myer의 Communications Server 2007 R2에 다이얼 플랜을 할당한 경우를 가정해 보겠습니다. Ken의 계정을 마이그레이션하면 기본적으로 다이얼 플랜도 마이그레이션됩니다. 따라서 **Move-CsLegacyUser** cmdlet은 이전에 할당된 다이얼 플랜의 Lync Server 2013에 해당하는 버전을 Ken Myer에게 자동으로 할당합니다.

물론, 이는 다이얼 플랜을 마이그레이션했으며 Ken Myer에게 이전에 할당된 다이얼 플랜에 해당하는 Lync Server 2013이 있는 경우에만 발생합니다. 또는 다이얼 플랜을 마이그레이션하지 않도록 선택했을 수도 있습니다. 이 경우에는 ExcludeDialPlan 매개 변수와 함께 **Move-CsLegacyUser** cmdlet을 호출할 수 있습니다. 이 매개 변수를 사용하면 다이얼 플랜이 사용자 계정과 함께 마이그레이션되지 않습니다. 즉, Ken Myer의 사용자 계정은 이동하지만 다이얼 플랜이 할당되지 않습니다. 이는 다이얼 플랜을 마이그레이션한 경우에도 마찬가지입니다. ExcludeDialPlan 매개 변수는 마이그레이션된 사용자 계정에 다이얼 플랜이 할당되지 않도록 합니다. 사용자 계정을 마이그레이션할 때 다른 매개 변수를 통해 음성 정책, 전화 회의 정책, 보관 정책, 외부 액세스 정책 및/또는 현재 상태 정책을 제외할 수도 있습니다.

**Merge-CsLegacyTopology** cmdlet을 실행하려면 먼저 WMI(Windows Management Instrumentation) 이전 버전과의 호환성 인터페이스 패키지를 설치해야 합니다. 설치 DVD의 설치(Setup) 폴더에 있는 OCSWMIBC.msi를 실행하면 이 응용 프로그램이 설치됩니다. 호환성 인터페이스 패키지를 설치한 후에는 **Merge-CsLegacyUser** cmdlet을 호출하여 하나 이상의 사용자 계정을 이동할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 그룹의 구성원은 **Move-CsLegacyUser** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Move-CsLegacyUser"}

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
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>마이그레이션할 사용자 계정의 ID를 나타냅니다. 사용자 ID는 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 사용자의 SIP 주소, 2) 사용자의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그온 이름(예: litwareinc\kenmyer) 및 4) 사용자의 Active Directory 도메인 서비스 표시 이름(예: Ken Myer)입니다. 사용자의 Active Directory 고유 이름을 사용하여 사용자 ID를 참조할 수도 있습니다.</p>
<p>표시 이름을 사용자 ID로 사용할 경우 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어 ID &quot;* Smith&quot;는 표시 이름이 문자열 값 &quot; Smith&quot;로 끝나는 모든 사용자를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Target</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>사용자 계정을 이동할 등록자 풀의 FQDN입니다(예: -Target atl-cs-001.litwareinc.com).</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Credential</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSCredential</p></td>
<td><p>대체 자격 증명으로 Move-CsLegacyUser cmdlet을 실행할 수 있도록 합니다. Windows에 로그온하는 데 사용한 계정에 사용자 개체를 사용하는 데 필요한 권한이 없는 경우 이 기능이 필요할 수 있습니다.</p>
<p>Credential 매개 변수를 사용하려면 먼저 Get-Credential cmdlet을 사용하여 PSCredential 개체를 만들어야 합니다. 자세한 내용은 Get-Credential cmdlet 도움말 항목을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>사용자 계정을 이동하기 위해 지정된 도메인 컨트롤러에 연결하는 데 사용됩니다. 특정 도메인 컨트롤러에 연결하려면 DomainController 매개 변수 뒤에 컴퓨터 이름(예: atl-cs-001) 또는 FQDN(예: atl-cs-001.litwareinc.com)을 포함합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ExcludeArchivingPolicy</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 사용하면 사용자 계정을 마이그레이션할 때 해당 계정에 할당된 보관 정책이 유지되지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ExcludeConferencingPolicy</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 사용하면 사용자 계정을 마이그레이션할 때 해당 계정에 할당된 전화 회의 정책이 유지되지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ExcludeDialPlan</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 사용하면 사용자 계정을 마이그레이션할 때 해당 계정에 할당된 다이얼 플랜이 유지되지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ExcludeExternalAccessPolicy</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 사용하면 사용자 계정을 마이그레이션할 때 해당 계정에 할당된 외부 액세스 정책이 유지되지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ExcludePresencePolicy</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 사용하면 사용자 계정을 마이그레이션할 때 해당 계정에 할당된 현재 상태 정책이 유지되지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ExcludeVoicePolicy</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 사용하면 사용자 계정을 마이그레이션할 때 해당 계정에 할당된 음성 정책이 유지되지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>HostedMigrationOverrideUrl</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>사용자를 Office 365 버전의 Lync Server 2013으로 이동할 때 사용되는 호스트된 마이그레이션 서비스의 URL입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>IgnoreBackendStoreException</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 백 엔드 데이터베이스에서 발생했을 수 있는 모든 오류를 무시하고 오류가 발생했더라도 사용자 이동을 시도하도록 컴퓨터에 명령합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이동할 사용자 계정을 나타내는 사용자 개체를 파이프라인을 통해 전달하는 데 사용됩니다. 기본적으로 <strong>Move-CsLegacyUser</strong> cmdlet은 파이프라인을 통해 개체를 전달하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ProxyPool</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>이 매개 변수는 Communications Server 2007 R2에만 사용됩니다. Lync Server의 온-프레미스 구현에 사용하면 안 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Move-CsLegacyUser** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Move-CsLegacyUser** cmdlet은 값이나 개체를 반환하지 않습니다. 대신에 이 cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.ADUser 개체의 인스턴스를 이동합니다.

## 참고 항목

#### 기타 리소스

[Import-CsLegacyConfiguration](import-cslegacyconfiguration.md)  
[Import-CsLegacyConferenceDirectory](import-cslegacyconferencedirectory.md)  
[Merge-CsLegacyTopology](merge-cslegacytopology.md)  
[Move-CsUser](move-csuser.md)  
[Set-CsUser](set-csuser.md)

