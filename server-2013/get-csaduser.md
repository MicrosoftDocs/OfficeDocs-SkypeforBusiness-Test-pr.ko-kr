---
title: Get-CsAdUser
TOCTitle: Get-CsAdUser
ms:assetid: 787f0ccf-3ac3-4a2b-8407-cff5e988b9b4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398592(v=OCS.15)
ms:contentKeyID: 49304102
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsAdUser

 

_**마지막으로 수정된 항목:** 2015-03-09_

Active Directory 도메인 서비스의 모든 사용자 계정에 대한 정보를 반환합니다. 여기에는 Lync Server를 사용하도록 설정된 사용자 계정뿐만 아니라 Lync Server를 사용하도록 설정되지 않은 계정도 포함됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsAdUser [-Identity <UserIdParameter>] [-Credential <PSCredential>] [-DomainController <Fqdn>] [-Filter <String>] [-LDAPFilter <String>] [-OU <OUIdParameter>] [-ResultSize <Unlimited>]

## 예제

## 예제 1

예제 1에 표시된 명령은 Active Directory 도메인에 있는 모든 사용자 계정의 컬렉션을 반환합니다.

    Get-CsAdUser

## 예제 2

예제 2에서 **Get-CsAdUser** cmdlet은 Pilar Ackerman에 대한 사용자 계정 정보를 반환합니다. 이 예제에서는 사용자의 표시 이름을 사용하여 사용자의 ID를 지정합니다.

    Get-CsAdUser -Identity "Pilar Ackerman"

## 예제 3

예제 3에서는 Finance 조직 구성 단위의 모든 사용자에 대한 사용자 계정 정보를 반환합니다. 이 작업을 수행하려면 OU의 DN을 OU 매개 변수에 전달해야 합니다.

    Get-CsAdUser -OU "ou=Finance,dc=litwareinc,dc=com"

## 예제 4

예제 4에서는 Lync Server 또는 Office Communications Server를 사용하도록 설정되지 않은 모든 사용자를 반환합니다. 이 작업을 수행하기 위해 Filter 매개 변수를 **Get-CsAdUser** cmdlet과 함께 사용하여 Enabled 속성이 True와 같지 않은 사용자 계정 데이터만 반환되도록 제한합니다. 이 필터는 Lync Server 또는 Office Communications Server를 사용하도록 설정되지 않은 사용자 계정만 반환하도록 **Get-CsAdUser** cmdlet에 지시합니다. 데이터가 검색된 후 해당 정보는 **Select-Object** cmdlet에 파이프되며 이 cmdlet은 화면에 실제로 표시될 유일한 속성(이 경우에는 DisplayName)을 식별합니다.

    Get-CsAdUser -Filter {Enabled -ne $True} | Select-Object DisplayName

## 예제 5

예제 5에서는 Finance 부서에서 근무하는 사용자에 대한 데이터만 반환하도록 제한하기 위해 LdapFilter 매개 변수를 사용합니다. 이 작업은 LDAP 필터 값 "Department=Finance"를 사용하여 수행합니다.

    Get-CsAdUser -LdapFilter "Department=Finance"

## 자세한 정보

**Get-CsAdUser** cmdlet은 Lync Server를 사용하도록 설정된 사용자 계정 및 사용하도록 설정되지 사용자 계정을 비롯하여 Active Directory의 모든 사용자 계정에 대한 정보를 반환합니다. 이는 Lync Server 또는 이전 버전의 소프트웨어(예: Microsoft Office Communications Server 2007 R2)에 대해 활성화된 계정을 가진 사용자에 대한 정보만 반환하는 **Get-CsUser** cmdlet과 다릅니다.

두 cmdlet 사이에 서로 겹치는 부분은 있지만 **Get-CsAdUser** cmdlet과 **Get-CsUser** cmdlet은 반환하는 정보의 유형이 다릅니다. 일반적으로 **Get-CsUser** cmdlet은 특히 Lync Server에 관련된 Active Directory 특성 값을 반환합니다. 예를 들어 **Get-CsUser** cmdlet은 사용자에게 할당된 Lync Server 정책 및 줄 URI(Uniform Resource Identifier)를 알려 주고, 사용자가 Enterprise Voice를 사용하도록 설정되었는지 여부를 나타냅니다. 사용자가 Lync Server를 사용하도록 설정되지 않은 경우 이러한 특성은 사용자 계정의 일부가 아닙니다.

반대로 **Get-CsAdUser** cmdlet은 일반 Active Directory 특성 값을 반환합니다. 즉, 기본 Active Directory 사용자 계정의 일부이며 사용자가 Lync Server를 사용하도록 설정되었는지 여부에 상관없이 존재하는 특성에 대한 정보를 반환합니다. 예를 들어 **Get-CsAdUser** cmdlet은 사용자가 근무하는 부서 및 조직, 직위, 전화 번호, 사무실 주소 등의 정보를 반환합니다. **Get-CsAdUser** cmdlet이 반환하는 특성 값의 전체 목록을 보려면 Windows PowerShell 프롬프트에서 다음 명령을 입력합니다.

Get-CsAdUser | Get-Member

**Get-CsAdUser** cmdlet을 실행할 때 반환되는 사용자의 컬렉션을 여러 가지 방법으로 필터링할 수 있습니다. 예를 들어 일부 Active Directory 사용자 계정을 보려는 경우 선택적 매개 변수인 Filter 또는 LDAPFilter를 적용할 수 있습니다. 이러한 매개 변수는 함께 사용할 수 없습니다. 즉, 명령에서 Filter를 사용할 경우 동일한 명령에서 LdapFilter를 사용할 수 없고 그 반대의 경우도 마찬가지입니다. Filter 매개 변수를 사용하면 Lync Server별 특성에 대해 지정된 조건을 충족하는 사용자에 대한 데이터만 반환하도록 제한할 수 있습니다. 예를 들어 Lync Server를 사용하도록 설정되었거나 설정되지 않은 사용자 컬렉션을 반환하려는 경우 Filter 매개 변수를 사용할 수 있습니다. LdapFilter 매개 변수를 사용하면 일반적인 Active Directory 특성을 기반으로 하는 다른 조건을 충족하는 사용자에 대한 데이터만 반환하도록 제한할 수 있습니다. 예를 들어 지정한 주 또는 시/도에서 일하는 사용자, 호출기가 있거나 없는 사용자, 지정한 직위를 가진 사용자 등입니다.

**Get-CsAdUser** cmdlet에 대해 알고 있어야 할 한 가지 중요한 사항은 사용자가 Lync Server를 사용하도록 설정되어 있는지 여부를 결정하는 Enabled 특성이 부울 값이더라도 이 속성은 실제로 다음과 같은 세 개의 유효한 값을 가진다는 점입니다.

True. 사용자가 Lync Server를 사용하도록 설정되어 있습니다.

False. 사용자의 Lync Server 계정이 임시로 사용하지 않도록 설정되어 있습니다. 이렇게 하려면 대개 **Set-CsUser** cmdlet을 사용하고 Enabled 매개 변수를 $False로 설정합니다.

Null. 사용자가 Lync Server를 사용하도록 설정되어 있지 않습니다.

따라서 Lync Server를 사용하도록 설정되지 않은 사용자 목록을 반환하려면 Enabled 특성이 Null인 모든 사용자를 반환하는 명령을 사용해야 합니다.

Get-CsAdUser –Filter {Enabled –eq $Null}

이와 반대로 다음 명령은 해당 Lync Server 계정이 임시로 사용하지 않도록 설정된 사용자만 반환합니다.

Get-CsAdUser –Filter {Enabled –eq $False}

위의 명령을 실행할 경우 Lync Server를 사용하도록 설정되지 않은 사용자는 반환되지 않습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins, RTCUniversalServerAdmins 및 RTCUniversalReadOnlyAdmins 그룹의 구성원은 **Get-CsAdUser** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsAdUser"}

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
<td><p>대체 자격 증명으로 <strong>Get-CsAdUser</strong> cmdlet을 실행할 수 있게 합니다. Windows에 로그온하는 데 사용한 계정에 사용자 개체를 사용하는 데 필요한 권한이 없는 경우 이 기능이 필요할 수 있습니다.</p>
<p>Credential 매개 변수를 사용하려면 먼저 <strong>Get-Credential</strong> cmdlet을 사용하여 PSCredential 개체를 만들어야 합니다. 자세한 내용은 <strong>Get-Credential</strong> cmdlet 도움말 항목을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>사용자 정보를 검색하기 위해 지정된 도메인 컨트롤러에 연결할 수 있게 합니다. 특정 도메인 컨트롤러에 연결하려면 DomainController 매개 변수 뒤에 FQDN(정규화된 도메인 이름)을 포함합니다(예: atl-cs-001.litwareinc.com).</p></td>
</tr>
<tr class="odd">
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>Lync Server 관련 특성을 필터링하여 반환된 데이터를 제한할 수 있게 합니다.</p>
<p>Filter 매개 변수는 <strong>Where-Object</strong> cmdlet에 사용되는 것과 동일한 Windows PowerShell 필터링 구문을 사용합니다. 예를 들어 Lync Server를 사용하도록 설정된 사용자만 필터는 {Enabled -ne $True}와 유사합니다. 여기서 Enabled는 Active Directory 특성을 나타내고 -ne는 비교 연산자(같지 않음)를 나타내며 $True(기본 제공 Windows PowerShell 변수)는 True 값을 나타냅니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>검색할 사용자 계정의 ID를 나타냅니다. 사용자 ID는 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 사용자의 SIP 주소, 2) 사용자의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그온 이름(예: litwareinc\kenmyer) 및 4) 사용자의 Active Directory 표시 이름(예: Ken Myer)입니다. 또한 사용자의 Active Directory 고유 이름을 사용하여 사용자 계정을 참조할 수도 있습니다.</p>
<p>표시 이름을 사용자 ID로 사용할 경우 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어 ID &quot;* Smith&quot;는 문자열 값 &quot;Smith&quot;로 끝나는 표시 이름을 가진 모든 사용자를 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LDAPFilter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>일반 Active Directory 특성(즉, Lync Server와 관련되지 않은 특성)을 필터링하여 반환되는 데이터를 제한할 수 있습니다. 예를 들어, 특정 부서에서 일하는 사용자나 특정 관리자 또는 직위를 가진 사용자에 대한 데이터만 반환하도록 제한할 수 있습니다.</p>
<p>필터를 만들 때 LdapFilter 매개 변수는 LDAP 쿼리 언어를 사용합니다. 예를 들어, Redmond 도시에 일하는 사용자만 반환하는 필터는 &quot;l&quot;(소문자 L)을 사용하여 &quot;l=Redmond&quot;와 같이 나타납니다. 여기서 &quot;l&quot;는 Active Directory 특성(구/군/시)을 나타내고 &quot;=&quot;는 비교 연산자(같음)를 나타내며 &quot;Redmond&quot;는 필터 값을 나타냅니다.</p></td>
</tr>
<tr class="even">
<td><p><em>OU</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.AD.OUIdParameter</p></td>
<td><p>특정 Active Directory OU(조직 구성 단위) 또는 컨테이너의 사용자를 검색하는 데 사용됩니다. 이 매개 변수는 지정된 OU 및 모든 하위 OU의 데이터를 반환합니다. 예를 들어 Finance OU에 두 개의 하위 OU인 AccountsPayable 및 AccountsReceivable이 있는 경우 이러한 세 개의 각 OU에서 사용자가 반환됩니다.</p>
<p>OU를 지정할 때는 해당 컨테이너에 대한 DN(고유 이름)을 사용합니다(예: OU=Finance,dc=litwareinc,dc=com). Users 컨테이너에서 사용자를 가져오려면 cn=Users,dc=litwareinc,dc=com 구문을 사용합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ResultSize</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.Unlimited</p></td>
<td><p>cmdlet에서 반환되는 레코드 수를 제한할 수 있게 합니다. 예를 들어, 포리스트에 있는 사용자 수에 상관없이 7명의 사용자만 반환하려면 ResultSize 매개 변수를 포함하고 매개 변수 값을 7로 설정합니다. 반환될 7명의 사용자를 지정하는 방법은 없습니다.</p>
<p>결과 크기는 0-2147483647(포함) 사이의 임의 정수로 설정할 수 있습니다. 0으로 설정할 경우 명령이 실행되지만 데이터가 반환되지 않습니다. ResultSize를 7로 설정했지만 포리스트에 사용자가 3명만 있는 경우 3명의 사용자가 반환된 다음, 오류 없이 완료됩니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

문자열. **Get-CsAdUser** cmdlet은 Active Directory 사용자 계정의 ID를 나타내는 파이프라인된 문자열 값을 허용합니다.

## 반환 형식

**Get-CsAdUser** cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.CSADUser 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsUser](get-csuser.md)

