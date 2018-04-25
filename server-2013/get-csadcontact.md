---
title: Get-CsAdContact
TOCTitle: Get-CsAdContact
ms:assetid: a5f599fb-8ede-432d-a6bf-c850c68fc71e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412776(v=OCS.15)
ms:contentKeyID: 49304616
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsAdContact

 

_**마지막으로 수정된 항목:** 2015-03-09_

다중 포리스트 토폴로지에서 홈 포리스트와 다른 포리스트의 사용자 계정에 대한 정보를 반환합니다. 이러한 사용자는 Microsoft Forefront Identity Manager 2010 또는 이전 버전의 제품에서 대화 상대 개체로 복제된 사용자입니다. **Get-CsAdContact** cmdlet은 msRTCSIP-OriginatorSid 특성에 대해 구성된 값이 있는 모든 사용자를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsAdContact [-Identity <UserIdParameter>] [-Credential <PSCredential>] [-DomainController <Fqdn>] [-Filter <String>] [-LDAPFilter <String>] [-OU <OUIdParameter>] [-ResultSize <Unlimited>]

## 예제

## 예제 1

예제 1에 표시된 명령은 Active Directory 도메인 서비스에서 찾은 모든 다중 포리스트 대화 상대의 컬렉션을 반환합니다. **Get-CsAdContact** cmdlet을 추가 매개 변수 없이 호출하면 모든 Active Directory 대화 상대의 모든 속성 값이 반환됩니다.

    Get-CsAdContact

## 예제 2

예제 2에서도 모든 Active Directory 대화 상대의 컬렉션을 반환합니다. 그러나 이 경우에는 해당 컬렉션이 화면에 표시되는 두 특성(DisplayName 및 SIPAddress)만을 지정하는 **Select-Object** cmdlet에 파이프됩니다.

    Get-CsAdContact | Select-Object DisplayName, SipAddress

## 예제 3

예제 3에서는 ID가 "fabrikam\\kenmyer"인 단일 Active Directory 대화 상대에 대한 정보를 반환합니다.

    Get-CsAdContact -Identity "Ken Myer"

## 예제 4

예제 4의 명령은 Fabrikam에서 근무하는 모든 Active Directory 대화 상대를 반환합니다. 이 작업을 수행하기 위해 LdapFilter 매개 변수와 함께 **Get-CsAdContact** cmdlet을 호출합니다. 이 예제에서는 Organization 특성이 "Fabrikam"으로 설정된 대화 상대만 반환되도록 제한합니다.

    Get-CsAdContact -LdapFilter "Organization=Fabrikam"

## 예제 5

예제 5에 표시된 두 명령은 대체 자격 증명으로 **Get-CsAdContact** cmdlet을 실행할 수 있는 Credential 매개 변수의 사용법을 보여 줍니다. 첫 번째 명령에서는 litwareinc\\administrator 계정의 PSCredential 개체를 만들기 위해 **Get-Credential** cmdlet을 호출합니다. 이 명령은 litwareinc\\administrator 사용자에게 자격 증명 요청 대화 상자를 표시합니다. 이 계정의 암호를 입력하면 해당 자격 증명 정보가 변수 $x에 저장됩니다. 두 번째 명령은 Credential 매개 변수와 함께 **Get-CsAdContact** cmdlet을 호출합니다. 매개 변수 값 $x는 **Get-CsAdContact** cmdlet을 litwareinc\\administrator 계정으로 실행해야 함을 나타냅니다.

    $x = Get-Credential -Credential "litwareinc\administrator"
    Get-CsAdContact -Credential $x

## 자세한 정보

다중 포리스트 토폴로지에서는 다른 포리스트의 사용자가 대화 상대로 표시됩니다. 이러한 대화 상대는 Active Directory 대화 상대와 같지 않습니다. Active Directory 사용자 및 컴퓨터를 사용하여 새 대화 상대를 만들면 해당 사용자가 **Get-CsAdContact** cmdlet에 의해 반환되지 않습니다. 대신 **Get-CsAdContact** cmdlet은 홈 포리스트가 아닌 다른 포리스트의 사용자에 대한 정보만 반환합니다. 다중 포리스트 토폴로지가 없는 경우에는 **Get-CsAdContact** cmdlet을 호출할 필요가 없습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsAdContact** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsAdContact"}

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
<td><p>대체 자격 증명으로 <strong>Get-CsAdContact</strong> cmdlet을 실행하는 데 사용됩니다. Windows에 로그온하는 데 사용한 계정에 대화 상대 개체를 사용하는 데 필요한 권한이 없는 경우 이 기능이 필요할 수 있습니다.</p>
<p>Credential 매개 변수를 사용하려면 먼저 <strong>Get-Credential</strong> cmdlet을 사용하여 PSCredential 개체를 만들어야 합니다. 자세한 내용은 Get-Credential 도움말 항목을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>대화 상대 정보를 검색하기 위해 지정된 도메인 컨트롤러에 연결하는 데 사용됩니다. 특정 도메인 컨트롤러에 연결하려면 DomainController 매개 변수 뒤에 정규화된 도메인 이름을 포함합니다(예: atl-cs-001.litwareinc.com).</p></td>
</tr>
<tr class="odd">
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>Lync Server 관련 특성을 필터링하여 반환되는 데이터를 제한할 수 있습니다.</p>
<p>Filter 매개 변수는 <strong>Where-Object</strong> cmdlet에 사용되는 것과 동일한 Windows PowerShell 필터링 구문을 사용합니다. 예를 들어 SIP 주소가 &quot;fabrikam.com&quot;으로 끝나는 대화 상대만 반환하는 필터는 {SipAddress -like &quot;*@fabrikam.com&quot;}과 유사합니다. 여기서 SipAddress는 Active Directory 특성, -like는 비교 연산자, &quot;*@fabrikam.com&quot;은 필터 값을 나타냅니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>반환할 대화 상대의 ID를 나타냅니다. 대화 상대 ID는 1) 대화 상대의 SIP 주소, 2) 대화 상대의 Active Directory 고유 이름 및 3) 대화 상대의 Active Directory 표시 이름(예: Ken Myer) 중 하나의 형식을 사용하여 지정할 수 있습니다.</p>
<p>표시 이름을 대화 상대 ID로 사용할 경우 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어 &quot;* Smith&quot;라는 ID는 표시 이름이 문자열 값 &quot; Smith&quot;로 끝나는 모든 대화 상대를 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LDAPFilter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>일반 Active Directory 특성을 필터링하여 반환되는 데이터를 제한하는 데 사용됩니다. 예를 들어 특정 부서에서 일하는 대화 상대나 지정된 관리자 또는 직위를 가진 대화 상대에 대한 데이터만 반환하도록 제한할 수 있습니다.</p>
<p>필터를 만들 때 LdapFilter 매개 변수는 LDAP 쿼리 언어를 사용합니다. 예를 들어 전화 번호가 1-425-555-1298인 대화 상대를 반환하는 필터는 &quot;telephoneNumber=1-425-555-1298&quot;과 유사합니다. 여기서 &quot;telephoneNumber&quot;는 Active Directory 특성, &quot;=&quot;는 비교 연산자(같음), &quot;1-425-555-1298&quot;은 필터 값을 나타냅니다.</p></td>
</tr>
<tr class="even">
<td><p><em>OU</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.AD.OUIdParameter</p></td>
<td><p>특정 Active Directory OU(조직 구성 단위) 또는 컨테이너에서 검색되는 정보를 제한할 수 있습니다. 이 매개 변수는 지정된 OU 및 모든 하위 OU의 데이터를 반환합니다. 예를 들어 Finance OU에 두 개의 하위 OU인 AccountsPayable 및 AccountsReceivable가 있는 경우 세 OU 각각에서 대화 상대가 반환됩니다.</p>
<p>OU를 지정할 때 해당 컨테이너에 대한 고유 이름을 사용합니다(예: OU=Finance,dc=litwareinc,dc=com).</p></td>
</tr>
<tr class="odd">
<td><p><em>ResultSize</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.Unlimited</p></td>
<td><p>cmdlet에서 반환되는 레코드 수를 제한하는 데 사용됩니다. 예를 들어 포리스트에 있는 대화 상대 수에 상관없이 7명의 대화 상대만 반환하려면 ResultSize 매개 변수를 포함하고 매개 변수 값을 7로 설정합니다. 반환될 7명의 사용자를 지정하는 방법은 없습니다.</p>
<p>결과 크기는 0-2147483647(포함) 사이의 임의 정수로 설정할 수 있습니다. 0으로 설정할 경우 명령이 실행되지만 데이터가 반환되지 않습니다. ResultSize를 7로 설정했지만 포리스트에 연락처가 3개만 있는 경우 3개의 연락처가 반환된 다음 오류 없이 완료됩니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

문자열. **Get-CsAdContact** cmdlet은 사용자 계정의 ID를 나타내는 파이프라인된 문자열 값을 허용합니다.

## 반환 형식

**Get-CsAdContact** cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.ADContact 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsAdUser](get-csaduser.md)  
[Get-CsUser](get-csuser.md)

