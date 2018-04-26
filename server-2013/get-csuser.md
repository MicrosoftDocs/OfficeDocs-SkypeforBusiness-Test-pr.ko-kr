---
title: Get-CsUser
TOCTitle: Get-CsUser
ms:assetid: 06f36c53-3a5e-4e79-b4f2-8c1aa7e6bf71
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398125(v=OCS.15)
ms:contentKeyID: 49302699
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsUser

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 또는 이전 버전의 소프트웨어(예: Microsoft Office Communications Server 2007 R2)를 사용할 수 있는 조직 내 모든 사용자에 대한 정보를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsUser [-Identity <UserIdParameter>] [-Credential <PSCredential>] [-DomainController <Fqdn>] [-Filter <String>] [-LdapFilter <String>] [-OnLyncServer <SwitchParameter>] [-OnOfficeCommunicationServer <SwitchParameter>] [-OU <OUIdParameter>] [-ResultSize <Unlimited>] [-UnassignedUser <SwitchParameter>]

## 예제

## 예제 1

위 예제에서는 Lync Server 또는 Office Communications Server를 사용할 수 있는 모든 도메인 사용자 컬렉션을 반환하기 위해 매개 변수 없이 **Get-CsUser** cmdlet을 호출합니다.

    Get-CsUser

## 예제 2

예제 2에서는 **Get-CsUser** cmdlet을 사용하여 Lync Server 또는 Office Communications Server를 사용할 수 있는 모든 도메인 사용자 컬렉션을 반환합니다. 기본적으로 **Get-CsUser** cmdlet은 많은 속성 및 속성 값을 반환하며, 이 중 대부분은 지정된 상황에 그다지 관계가 없습니다. 따라서 이 예제에서는 검색된 데이터가 **Format-Table** cmdlet에 파이프됩니다. **Format-Table** cmdlet은 Property 매개 변수를 사용하여 DisplayName, SipAddress 및 EnterpriseVoiceEnabled 속성을 선택하고 이러한 속성과 해당 값을 테이블에 표시합니다.

    Get-CsUser | Format-Table -Property DisplayName, SipAddress, EnterpriseVoiceEnabled -AutoSize

## 예제 3

예제 3에서는 Identity 매개 변수를 사용하여 Identity(이 경우 표시 이름)가 Pilar Ackerman인 사용자 계정에 대한 데이터만 반환되도록 제한합니다.

    Get-CsUser -Identity "Pilar Ackerman"

## 예제 4

예제 4에서는 사용자 ID를 지정할 때 와일드카드 문자(\*)가 사용됩니다. 이 경우 **Get-CsUser** cmdlet은 ID가 문자열 값 "Pilar"로 시작하는 모든 사용자를 반환합니다.

    Get-CsUser -Identity "Pilar*"

## 예제 5

예제 5에 표시된 명령은 사용자별 음성 정책이 할당되어 있지 않은 사용자 컬렉션을 반환합니다. 이 작업을 수행하기 위해 Filter 매개 변수 뒤에 VoicePolicy -eq "$Null 필터를 사용합니다. **Get-CsUser** cmdlet에 사용할 필터를 작성할 때 속성 이름(VoicePolicy) 뒤에 비교 연산자(이 경우 "같지 않음"을 의미하는 비교 연산자 "eq")를 지정해야 합니다. 비교 연산자 바로 뒤에는 테스트할 값이 옵니다. 이 예제에서는 null 값을 나타내는 Windows PowerShell 명령줄 인터페이스 변수인 $Null을 사용합니다.

음성 정책이 할당되지 않은 사용자 컬렉션을 반환하려면 다음 명령을 사용합니다.

Get-CsUser -Filter {VoicePolicy -ne $Null}

    Get-CsUser -Filter {VoicePolicy -eq $Null}

## 예제 6

예제 6에서는 LdapFilter 매개 변수를 사용하여 Finance 부서에서 근무하는 사용자에 대한 데이터만 반환되도록 제한합니다. 이 작업은 LDAP 필터 값 "Department=Finance"를 사용하여 수행합니다.

    Get-CsUser -LdapFilter "Department=Finance"

## 예제 7

예제 7에서는 LdapFilter 매개 변수와 함께 AND 쿼리를 사용하는 방법을 보여 줍니다. 앰퍼샌드 문자 "&"을 사용하여 AND 쿼리를 표시하는 이 쿼리는 "Department=Finance" 및 "Title=Manager"의 두 조건을 지정합니다. 이 쿼리에서 반환될 사용자 계정은 사용자가 Finance 부서에서 근무하고 Manager여야 한다는 두 조건이 모두 true여야 합니다.

    Get-CsUser -LdapFilter "&(Department=Finance)(Title=Manager)"

## 예제 8

예제 8에 표시된 명령에서는 LdapFilter 매개 변수와 함께 OR 쿼리(파이프 기호 "|"로 표시됨)가 사용됩니다. 예제 7에 표시된 AND 쿼리에서는 사용자 계정이 반환되기 위해 두 조건이 모두 true여야 했습니다. OR 쿼리에서는 계정이 반환되기 위해 한 조건만 true이면 됩니다. 이 경우 사용자가 Supervisor인 경우 또는 사용자가 Manager인 경우이면 사용자 계정이 반환됩니다.

    Get-CsUser -LdapFilter "|(Title=Supervisor)(Title=Manager)"

## 예제 9

예제 9에서는 Finance OU에 계정이 있는 모든 사용자에 대한 사용자 계정 정보를 반환합니다.

    Get-CsUser -OU "ou=Finance,ou=North America,dc=litwareinc,dc=com"

## 예제 10

예제 10에서는 Lync Server 또는 Office Communications Server를 사용할 수 있지만 현재 등록자 풀에 할당되어 있지 않은 모든 사용자 컬렉션을 반환합니다.

    Get-CsUser -UnassignedUser

## 자세한 정보

**Get-CsAdUser** cmdlet 및 **Get-CsUser** cmdlet을 함께 사용하면 모든 Active Directory 사용자 계정에 대한 자세한 정보를 가져올 수 있습니다. **Get-CsAdUser** cmdlet은 Lync Server 또는 Office Communications Server를 사용할 수 있는 사용자와 Lync Server 또는 Office Communications Server를 사용할 수 없는 사용자를 포함하여 모든 사용자 계정에 대한 정보를 반환합니다. 이 cmdlet은 Lync Server 또는 Office Communications Server를 사용할 수 있는 계정의 사용자에 대한 정보만 반환하는 **Get-CsUser** cmdlet과 다릅니다.

두 cmdlet 사이에 서로 겹치는 부분은 있지만 **Get-CsUser** cmdlet과 **Get-CsAdUser** cmdlet은 반환하는 정보의 유형이 다릅니다. 일반적으로 **Get-CsUser** cmdlet은 특히 Lync Server에 관련된 Active Directory 특성 값을 반환합니다. 예를 들어 **Get-CsUser** cmdlet은 사용자에게 할당된 Lync Server 정책, 사용자에게 할당된 URI(Uniform Resource Identifier) 행, 사용자가 Enterprise Voice를 사용할 수 있는지 여부에 대한 세부 정보 등의 정보를 반환합니다. Lync Server에 대해 사용자가 활성화되지 않은 경우 이러한 특성은 사용자 계정의 일부가 아닙니다.

반면, **Get-CsAdUser** cmdlet은 기본 Active Directory 사용자 계정의 일부이며 사용자가 Lync Server를 사용할 수 있는지 여부에 관계없이 존재하는 특성인 제네릭 Active Directory 특성 값을 반환합니다. 예를 들어 **Get-CsAdUser** cmdlet은 사용자가 근무하는 부서 및 조직, 직함, 전화 번호, 사무실 주소 등의 정보를 반환합니다.

**Get-CsUser** cmdlet이 반환하는 특성 값의 전체 목록을 보려면 Windows PowerShell 명령 프롬프트에서

Get-CsUser | Get-Member

**Get-CsUser** cmdlet을 통해 cmdlet을 실행할 때 실제로 반환되는 사용자 컬렉션을 필터링할 수 있습니다. 예를 들어 Lync Server 사용자 계정을 모두 반환하지 않으려면 선택적 매개 변수인 Filter 또는 LdapFilter를 적용할 수 있습니다. 두 매개 변수는 함께 사용할 수 없습니다. 명령에서 Filter를 사용하는 경우 동일한 명령에서 LdapFilter는 사용할 수 없으며 그 반대의 경우도 마찬가지입니다. Filter 매개 변수를 사용하면 지정한 Lync Server 조건을 충족하는 사용자에 대한 데이터만 반환되도록 제한할 수 있습니다. 예를 들어 지정한 등록자 풀에 계정이 있는 사용자만 반환하거나 Enterprise Voice를 사용할 수 있는 사용자만 반환할 수 있습니다. LdapFilter 매개 변수를 사용하면 다른 Active Directory 기반 조건에 적합한 사용자에 대한 데이터만 반환하도록 제한할 수 있습니다. 예를 들어 지정한 주 또는 시/도에서 일하는 사용자, 호출기가 있거나 없는 사용자, 지정한 직위를 가진 사용자 등입니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsUser** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsUser\\b"}

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
<td><p><em>Credential</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSCredential</p></td>
<td><p>대체 자격 증명으로 <strong>Get-CsUser</strong> cmdlet을 실행할 수 있습니다. Windows에 로그온할 때 사용한 계정에 사용자 개체 작업에 필요한 권한이 없는 경우 이 매개 변수가 필요할 수 있습니다.</p>
<p>Credential 매개 변수를 사용하려면 먼저 <strong>Get-Credential</strong> cmdlet을 사용하여 PSCredential 개체를 만들어야 합니다. 자세한 내용은 <strong>Get-Credential</strong> cmdlet 도움말 항목을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>사용자 정보를 검색하기 위해 지정한 도메인 컨트롤러에 연결할 수 있습니다. 특정 도메인 컨트롤러에 연결하려면 DomainController 매개 변수 뒤에 FQDN(정규화된 도메인 이름)을 포함합니다(예: atl-cs-001.litwareinc.com).</p></td>
</tr>
<tr class="odd">
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>Lync Server 관련 특성을 필터링하여 반환된 데이터를 제한할 수 있습니다. 예를 들어, 특성 음성 정책이 할당된 사용자 또는 특정 음성 정책이 할당되지 않은 사용자에 대한 데이터만 반환하도록 제한할 수 있습니다.</p>
<p>Filter 매개 변수는 <strong>Where-Object</strong> cmdlet에 사용되는 구문과 동일한 Windows PowerShell 필터링 구문을 사용합니다. 예를 들어 Enterprise Voice를 사용하도록 설정된 사용자만 반환하는 필터는 다음과 유사한 형태입니다. 여기서 EnterpriseVoiceEnabled는 Active Directory 특성을 나타내고 -eq는 비교 연산자(같음)를 나타내며 $True(기본 제공 Windows PowerShell 변수)는 필터 값을 나타냅니다.</p>
<p>{EnterpriseVoiceEnabled -eq $True}</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>검색할 사용자 계정의 ID를 나타냅니다. 사용자 ID는 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 사용자의 SIP 주소, 2) 사용자의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그온 이름(예: litwareinc\kenmyer) 및 4) 사용자의 Active Directory 표시 이름(예: Ken Myer)입니다. 또한 사용자의 Active Directory 고유 이름을 사용하여 사용자 계정을 참조할 수도 있습니다.</p>
<p>표시 이름을 사용자 ID로 사용할 경우 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어 ID &quot;* Smith&quot;는 문자열 값 &quot;Smith&quot;로 끝나는 표시 이름을 가진 모든 사용자를 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LdapFilter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>일반 Active Directory 특성(즉, Lync Server와 관련되지 않은 특성)을 필터링하여 반환되는 데이터를 제한할 수 있습니다. 예를 들어 특정 부서에서 일하는 사용자나 지정된 관리자 또는 직위를 가진 사용자에 대한 데이터만 반환하도록 제한할 수 있습니다.</p>
<p>필터를 만들 때 LdapFilter 매개 변수는 LDAP 쿼리 언어를 사용합니다. 예를 들어, Redmond 도시에 일하는 사용자만 반환하는 필터는 &quot;l&quot;(소문자 L)을 사용하여 &quot;l=Redmond&quot;와 같이 나타납니다. 여기서 &quot;l&quot;는 Active Directory 특성(구/군/시)을 나타내고 &quot;=&quot;는 비교 연산자(같음)를 나타내며 &quot;Redmond&quot;는 필터 값을 나타냅니다.</p></td>
</tr>
<tr class="even">
<td><p><em>OnLyncServer</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Lync Server에 이동된 사용자 컬렉션을 반환합니다. 이 매개 변수를 사용하는 경우 이전 버전의 소프트웨어에 계정이 있는 사용자는 반환되지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>OnOfficeCommunicationServer</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Lync Server 이전 버전(예 Office Communications Server 2007 R2)에 이동된 사용자 컬렉션을 반환합니다. 이 매개 변수를 사용하는 경우 현재 버전의 소프트웨어에 계정이 있는 사용자는 반환되지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>OU</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.AD.OUIdParameter</p></td>
<td><p>특정 OU(조직 구성 단위) 또는 컨테이너의 사용자 계정에 대한 정보를 반환하는 데 사용됩니다. OU 매개 변수는 지정한 OU 및 모든 하위 OU의 데이터를 반환합니다. 예를 들어 Finance OU에 두 개의 하위 OU인 AccountsPayable 및 AccountsReceivable이 있는 경우 이러한 세 개의 각 OU에서 사용자가 반환됩니다.</p>
<p>OU를 지정할 때는 해당 컨테이너에 대한 DN(고유 이름)을 사용합니다(예: -OU &quot;OU=Finance,dc=litwareinc,dc=com&quot;). Users 컨테이너에서 사용자 계정을 가져오려면 -OU &quot;cn=Users,dc=litwareinc,dc=com&quot; 구문을 사용합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ResultSize</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.Unlimited</p></td>
<td><p>cmdlet에서 반환되는 레코드 수를 제한하는 데 사용됩니다. 예를 들어 포리스트에 있는 사용자 수에 상관없이 7명의 사용자만 반환하려면 ResultSize 매개 변수를 포함하고 매개 변수 값을 7로 설정합니다. 반환될 7명의 사용자를 지정하는 방법은 없습니다.</p>
<p>결과 크기는 0-2147483647(포함) 사이의 임의 정수로 설정할 수 있습니다. 0으로 설정할 경우 명령이 실행되지만 데이터가 반환되지 않습니다. ResultSize를 7로 설정했지만 포리스트에 사용자가 3명만 있는 경우 3명의 사용자가 반환된 다음, 오류 없이 완료됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>UnassignedUser</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Lync Server를 사용할 수 있지만 현재 등록자 풀에 할당되어 있지 않은 모든 사용자 컬렉션을 반환할 수 있습니다. 등록자 풀에 할당되지 않은 사용자는 Lync Server에 로그온할 수 없습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

문자열. **Get-CsUser** cmdlet은 Lync Server를 사용하도록 설정된 사용자 계정의 ID를 나타내는 파이프라인된 문자열 값을 허용합니다.

## 반환 형식

**Get-CsUser** cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.ADUser 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Disable-CsUser](disable-csuser.md)  
[Enable-CsUser](enable-csuser.md)  
[Get-CsAdUser](get-csaduser.md)  
[Move-CsUser](move-csuser.md)  
[Set-CsUser](set-csuser.md)

