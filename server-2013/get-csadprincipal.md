---
title: Get-CsAdPrincipal
TOCTitle: Get-CsAdPrincipal
ms:assetid: df2c3714-4064-4113-861f-95ce0ae8da81
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205326(v=OCS.15)
ms:contentKeyID: 49305268
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsAdPrincipal

 

_**마지막으로 수정된 항목:** 2015-03-09_

Active Directory 계정에 대한 정보를 반환합니다. 이러한 계정에는 사용자, 그룹, 연락처, 컨테이너, 조직 구성 단위 등의 Active Directory 개체가 포함됩니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsAdPrincipal [-Identity <UserIdParameter>] [-Credential <PSCredential>] [-DomainController <Fqdn>] [-Filter <String>] [-LDAPFilter <String>] [-OU <OUIdParameter>] [-ResultSize <Unlimited>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직의 모든 Active Directory 계정을 반환합니다.

    Get-CsAdPrincipal

## 예제 2

예제 2에서는 단일 Active Directory 계정, 즉 SIP 주소가 "sip:RedmondMeetingRoom@litwareinc.com"인 계정에 대한 정보를 반환합니다. 이 작업은 SipAddress 속성이 "sip:RedmondMeetingRoom@litwareinc.com"인(-eq) 계정을 찾는 필터 값 및 Filter 매개 변수를 포함하여 수행합니다.

    Get-CsAdPrincipal -Filter {SipAddress -eq "sip:RedmondMeetingRoom@litwareinc.com"}

## 예제 3

위의 예제에서는 모든 Active Directory 개체에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsAdPrincipal** cmdlet을 호출합니다. 그러면 모든 Active Directory 계정의 컬렉션이 반환됩니다. 해당 컬렉션은 **Where-Object** cmdlet에 파이프되며, 이 cmdlet은 ObjectClass 속성에 문자열 값 "contact"가 포함된 계정만 선택합니다.

    Get-CsAdPrincipal | Where-Object {$_.ObjectClass -contains "contact"}

## 자세한 정보

**Get-CsAdPrincipal** cmdlet은 영구 채팅 구성원 목록을 생성할 때 사용할 수 있는 Active Directory 계정 컬렉션을 반환합니다. 자세한 내용은 **Set-CsPersistentChatCategory** cmdlet의 AllowedMembers 및 DeniedMembers 매개 변수에 대한 도움말 정보를 참조하십시오. **Get-CsPrincipal**은 다음과 같은 Active Directory 개체에 대한 정보를 반환합니다.

  - **Users**(개체 클래스 = {top, person, organizationalPerson, user})

  - **Groups**(개체 클래스 = {top, group})

  - **Contacts**(개체 클래스 = {top, person, organizationalPerson, contact})

  - **Containers**(개체 클래스 = {top, container})

  - **Organizational Units**(개체 클래스 = {top, organizationalUnit})

  - **Domains**(개체 클래스 = {top, domain, domainDNS})

따라서 **Get-CsAdPrincipal** cmdlet 및 objectClass 속성을 사용하여 그룹, 조직 구성 단위 등 Active Directory 개체에 대한 정보를 빠르게 반환할 수 있습니다. 예를 들어 다음 명령은 모든 Active Directory OU 이름을 반환합니다.

Get-CsAdPrincipal | Where-Object {$\_.ObjectClass –match "organizationalUnit"} | Select-Object Name

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsAdPrincipal"}

**Lync Server 제어판:** Get-CsAdPrincipal cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>대체 자격 증명으로 <strong>Get-CsAdPrincipal</strong> cmdlet을 실행할 수 있게 합니다. Windows에 로그온하는 데 사용한 계정에 사용자 개체를 사용하는 데 필요한 권한이 없는 경우 이 기능이 필요할 수 있습니다.</p>
<p>Credential 매개 변수를 사용하려면 먼저 <strong>Get-Credential</strong> cmdlet을 사용하여 PSCredential 개체를 만들어야 합니다. 자세한 내용은 <strong>Get-Credential</strong> cmdlet 도움말 항목을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Active Directory 계정 정보를 검색하기 위해 지정된 도메인 컨트롤러에 연결하는 데 사용됩니다. 특정 도메인 컨트롤러에 연결하려면 DomainController 매개 변수 뒤에 컴퓨터 이름(예: atl-dc-001) 또는 FQDN(정규화된 도메인 이름)(예: atl-dc-001.litwareinc.com)을 포함합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>Lync Server 관련 특성을 필터링하여 반환되는 데이터를 제한할 수 있습니다.</p>
<p>Filter 매개 변수는 <strong>Where-Object</strong> cmdlet에 사용되는 구문과 거의 동일한 Windows PowerShell 필터링 구문을 사용합니다. 예를 들어 Lync Server에 대해 사용하도록 설정되지 않은 계정만 반환하는 필터는 다음과 같습니다.</p>
<p>-Filter {Enabled -ne $True}</p>
<p>이 예제에서 Enabled는 Active Directory 특성을, -ne는 비교 연산자(같지 않음)를, $True(기본 제공 Windows PowerShell 변수)는 True 값을 나타냅니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>검색할 계정의 ID를 나타냅니다. ID는 보통 네 가지 형식 중 하나를 사용하여 지정되는데, 이러한 형식은 1) 계정의 SIP 주소, 2) 사용자의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 계정의 도메인 이름 및 로그온 이름(예: litwareinc\kenmyer) 및 4) 계정의 Active Directory 표시 이름(예: Ken Myer)입니다.</p>
<p>또한 사용자의 Active Directory 고유 이름을 사용하여 사용자 계정을 참조할 수도 있습니다.</p>
<p>표시 이름을 ID로 사용할 경우 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어 &quot;* Smith&quot;라는 ID는 표시 이름이 &quot; Smith&quot; 문자열 값으로 끝나는 모든 사용자를 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LDAPFilter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>일반 Active Directory 특성(즉, Lync Server와 관련되지 않은 특성)을 필터링하여 반환되는 데이터를 제한할 수 있습니다. 예를 들어 특정 부서 소속 계정이나 특정 관리자 또는 직위를 가진 계정에 대한 데이터만 반환하도록 제한할 수 있습니다.</p>
<p>필터를 만들 때 LdapFilter 매개 변수는 LDAP 쿼리 언어를 사용합니다. 예를 들어 Redmond 시의 계정만 반환하는 필터는 다음과 같습니다.</p>
<p>-LdapFilter &quot;l=Redmond&quot;</p>
<p>해당 예제에서 &quot;l&quot;(소문자 L)은 Active Directory 특성(구/군/시)을 나타내고 &quot;=&quot;는 비교 연산자(같음)를 나타내며 &quot;Redmond&quot;는 필터 값을 나타냅니다.</p></td>
</tr>
<tr class="even">
<td><p><em>OU</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.AD.OUIdParameter</p></td>
<td><p>특정 OU(조직 구성 단위) 또는 컨테이너의 계정에 대한 정보를 반환하는 데 사용됩니다. OU 매개 변수는 지정한 OU 및 모든 하위 OU의 데이터를 반환합니다. 예를 들어 Finance OU에 두 개의 하위 OU인 AccountsPayable 및 AccountsReceivable이 있는 경우 이러한 세 개의 각 OU에서 계정이 반환됩니다.</p>
<p>OU를 지정할 때는 다음과 같이 해당 컨테이너에 대한 DN(고유 이름)을 사용합니다.</p>
<p>-OU &quot;OU=Finance,dc=litwareinc,dc=com&quot;</p>
<p>Users 컨테이너의 계정을 반환하려면 다음 구문을 사용합니다.</p>
<p>-OU &quot;cn=Users,dc=litwareinc,dc=com&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>ResultSize</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.Unlimited</p></td>
<td><p>cmdlet에서 반환되는 레코드 수를 제한하는 데 사용됩니다. 예를 들어 포리스트에 있는 계정 수에 상관없이 7개의 계정을 반환하려면 ResultSize 매개 변수를 포함하고 매개 변수 값을 7로 설정합니다. 반환될 7개의 계정을 지정하는 방법은 없습니다.</p>
<p>결과 크기는 0에서 2147483647(포함) 사이의 임의 정수로 설정할 수 있습니다. 0으로 설정할 경우 명령이 실행되지만 데이터가 반환되지 않습니다. ResultSize를 7로 설정했지만 포리스트에 보안 주체가 3개만 있는 경우 3개의 보안 주체가 반환된 다음 오류 없이 완료됩니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Active Directory 사용자, 그룹, 연락처, 컨테이너 및 조직 구성 단위를 나타내는 문자열 값 또는 개체입니다. 예를 들어 다음 구문은 Redmond 및 Dublin OU에 대해 Active Directory 계정 정보를 반환합니다.

"OU=Redmond,DC=litwareinc,DC=com", "OU=Dublin,DC=litwareinc,DC=com" | Get-CsAdPrincipal

## 반환 형식

**Get-CsAdPrincipal** cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.OCSADPrincipal 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsPersistentChatCategory](new-cspersistentchatcategory.md)  
[Set-CsPersistentChatCategory](set-cspersistentchatcategory.md)

