---
title: Move-CsUser
TOCTitle: Move-CsUser
ms:assetid: 6fbdbab6-8a8c-421c-b16c-2319be4b8915
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398528(v=OCS.15)
ms:contentKeyID: 49303987
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Move-CsUser

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server에 대해 사용하도록 설정된 하나 이상의 사용자 계정을 새 등록자 풀로 이동합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Move-CsUser -Identity <UserIdParameter> -Target <Fqdn> [-Confirm [<SwitchParameter>]] [-Credential <PSCredential>] [-DomainController <Fqdn>] [-Force <SwitchParameter>] [-HostedMigrationOverrideUrl <String>] [-IgnoreBackendStoreException <SwitchParameter>] [-MoveConferenceData <SwitchParameter>] [-PassThru <SwitchParameter>] [-ProxyPool <Fqdn>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 **Move-CsUser** cmdlet을 사용하여 ID가 Pilar Ackerman인 사용자 계정을 등록자 풀 atl-cs-001.litwareinc.com으로 이동합니다.

    Move-CsUser -Identity "Pilar Ackerman" -Target "atl-cs-001.litwareinc.com"

## 예제 2

예제 2에서는 Finance OU(조직 구성 단위)의 모든 사용자 계정을 등록자 풀 atl-cs-001.litwareinc.com으로 이동합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsUser** cmdlet 및 OU 매개 변수를 사용하여 Finance OU에 있는 모든 사용자 계정의 컬렉션을 검색합니다. 데이터가 검색된 후에는 해당 컬렉션의 각 계정을 등록자 풀 atl-cs-001.litwareinc.com으로 이동하는 **Move-CsUser** cmdlet에 정보가 파이프됩니다.

    Get-CsUser -OU "ou=Finance,dc=litwareinc,dc=com" | Move-CsUser -Target "atl-cs-001.litwareinc.com"

## 예제 3

예제 3에서는 **Move-CsUser** cmdlet을 사용하여 ID가 Pilar Ackerman인 사용자 계정을 등록자 풀 atl-cs-001.litwareinc.com으로 이동합니다. 또한 계정 자체만 이동하도록 Force 매개 변수를 사용합니다. 즉, 해당 계정과 연결된 데이터(예: Pilar가 예약한 전화 회의)는 이동되지 않고 삭제됩니다. Force 매개 변수는 매개 변수 없이 **Move-CsUser** cmdlet을 호출하려고 했지만 이동에 실패한 경우에만 사용해야 합니다.

    Move-CsUser -Identity "Pilar Ackerman" -Target "atl-cs-001.litwareinc.com" -Force

## 자세한 정보

**Move-CsUser** cmdlet을 사용하면 Lync Server에 대해 활성화된 사용자 계정을 한 등록자 풀에서 다른 등록자 풀로 이동할 수 있습니다. **Move-CsUser** cmdlet은 사용자의 Lync Server 계정 위치에만 영향을 주며, 사용자의 Active Directory 계정을 새 OU(조직 구성 단위) 또는 다른 새 위치로 이동하지는 않습니다.

Lync Server가 Office Communications Server 2007 R2 또는 Office Communications Server 2007과 공존하는 경우에는 **Move-CsUser** cmdlet을 사용하여 Lync Server에서 레거시 Office Communications Server 설치로 사용자를 다시 이동할 수 있습니다. Office Communications Server로 사용자를 다시 이동하려면 레거시 풀의 FQDN(정규화된 도메인 이름)을 Target 매개 변수에 할당합니다. 이 경우 Office Communications Server로 다시 이동된 사용자에게 기능 및 데이터 손실이 발생할 수 있는데, 이는 Lync Server의 기능이 Office Communications Server 2007 또는 Office Communications Server 2007 R2보다 많기 때문입니다. 또한 다시 이동된 사용자가 이전 버전의 클라이언트 소프트웨어를 설치하고 사용자 계정이 Lync Server에 속해 있을 때 만든 모임을 다시 예약할 수도 있습니다.

Communications Server 2007 또는 Communications Server 2007 R2에서 Lync Server로 사용자를 이동하려면 **Move-CsLegacyUser** cmdlet을 사용합니다. **Move-CsUser** cmdlet은 특정 Lync Server에서 다른 Lync Server 풀로 사용자를 이동하거나 Lync Server 풀에서 Office Communications Server 풀로 사용자를 이동하도록 설계되었습니다. Move-CsLegacyUser는 Office Communications Server에서 Lync Server로 사용자를 이동합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 그룹의 구성원은 **Move-CsUser** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Move-CsUser"}

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
<td><p>이동할 사용자 계정의 ID를 나타냅니다. 사용자 ID는 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 사용자의 SIP 주소, 2) 사용자의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그온 이름(예: litwareinc\kenmyer) 및 4) 사용자의 Active Directory 표시 이름(예: Ken Myer)입니다. 또한 사용자의 Active Directory 고유 이름을 사용하여 사용자 ID를 참조할 수도 있습니다.</p>
<p>표시 이름을 사용자 ID로 사용할 경우 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어 &quot;* Smith&quot;라는 ID는 표시 이름이 &quot;Smith&quot; 문자열 값으로 끝나는 모든 사용자를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Target</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>사용자 계정을 이동해야 하는 등록자 풀의 FQDN(예: atl-cs-001.litwareinc.com)입니다. 등록자 풀 이외에 Target은 레거시 Office Communications Server 프런트 엔드 서버 또는 호스팅 공급자의 FQDN일 수 있습니다. 호스팅 공급자로 이동된 계정(예: Microsoft Lync Online 2010)은 연결된 모든 사용자 데이터가 손실됩니다. 예를 들어 사용자가 예약한 전화 회의가 삭제되고 Lync Online 2010에서 사용할 수 없게 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>사용자를 이동하려고 할 때 나타나는 확인 메시지를 건너뛰는 데 사용됩니다. 확인 메시지를 건너뛰려면 다음 구문과 같이 Confirm 매개 변수를 포함합니다.</p>
<p>-Confirm:$False</p>
<p>확인 메시지를 표시하려면 다음 구문을 사용합니다.</p>
<p>-Confirm</p></td>
</tr>
<tr class="even">
<td><p><em>Credential</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSCredential</p></td>
<td><p>대체 자격 증명으로 Move-CsUser cmdlet을 실행할 수 있습니다. Windows에 로그온하는 데 사용한 계정에 사용자 개체를 사용하는 데 필요한 권한이 없는 경우 이 기능이 필요할 수 있습니다.</p>
<p>Credential 매개 변수를 사용하려면 먼저 <strong>Get-Credential</strong> cmdlet을 사용하여 PSCredential 개체를 만들어야 합니다. 자세한 내용은 <strong>Get-Credential</strong> cmdlet 도움말 항목을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>대화 상대 정보를 검색하기 위해 지정된 도메인 컨트롤러에 연결하는 데 사용됩니다. 특정 도메인 컨트롤러에 연결하려면 DomainController 매개 변수 뒤에 컴퓨터 이름(예: atl-cs-001) 또는 FQDN(예: atl-cs-001.litwareinc.com)을 포함합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 사용자 계정을 이동하지만 연결된 데이터(예: 사용자가 예약한 전화 회의)를 모두 삭제합니다. 이 매개 변수가 없으면 계정 및 연결된 데이터가 둘 다 이동됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>HostedMigrationOverrideUrl</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>사용자를 비즈니스용 Skype Online으로 이동할 때 사용되는 호스트된 마이그레이션 서비스의 URL입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>IgnoreBackendStoreException</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 백 엔드 데이터베이스에서 발생했을 수 있는 모든 오류를 무시하고 오류가 발생했더라도 사용자 이동을 시도하도록 컴퓨터에 명령합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MoveConferenceData</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 전송되는 사용자에 대한 모임 및 전화 회의 데이터를 다른 등록자 풀로 이동합니다. 재해 복구 절차의 일부분으로 사용자를 이동하는 경우에는 MoveConferenceData 매개 변수를 사용하면 안 됩니다. 대신 백업 서비스를 통해 재해 복구 절차의 일부분으로 전화 회의 데이터를 이동해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이동할 사용자 계정을 나타내는 사용자 개체를 파이프라인을 통해 전달하는 데 사용됩니다. 기본적으로 <strong>Move-CsUser</strong> cmdlet은 파이프라인을 통해 개체를 전달하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ProxyPool</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>이 매개 변수는 Lync Online에만 사용됩니다. Lync Server의 온-프레미스 구현에 사용하면 안 됩니다.</p></td>
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

문자열 또는 Microsoft.Rtc.Management.ADConnect.Schema.ADUser 개체입니다. **Move-CsUser** cmdlet은 Lync Server를 사용하도록 설정된 사용자 계정의 ID를 나타내는 파이프라인된 문자열 값을 허용합니다. 또한 Active Directory 사용자 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Move-CsUser** cmdlet은 값이나 개체를 반환하지 않습니다. 대신에 이 cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.ADUser 개체의 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsUser](get-csuser.md)  
[Move-CsLegacyUser](move-cslegacyuser.md)

