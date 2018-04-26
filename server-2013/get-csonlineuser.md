---
title: Get-CsOnlineUser
TOCTitle: Get-CsOnlineUser
ms:assetid: 2bfafd70-a7d9-4308-a353-5ecf44249b53
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994026(v=OCS.15)
ms:contentKeyID: 52056810
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsOnlineUser

 

_**마지막으로 수정된 항목:** 2015-03-09_

Microsoft Lync Online에 속한 계정이 있는 사용자의 정보를 반환합니다. 이 cmdlet은 비즈니스용 Skype Online에서만 사용할 수 있습니다.

## 구문

    Get-CsOnlineUser [[-Identity] <UserIdParameter>] [-Filter <String>] [-LdapFilter <String>] [-OnOfficeCommunicationServer] [-OnLyncServer] [-UnAssignedUser] [-OU <OUIdParameter>] [-DomainController <Fqdn>] [-Credential <PSCredential>] [-ResultSize <Unlimited`1>] [-Verbose]

## 예제

## 예제 1

예제 1에 표시된 명령은 온라인 사용자로 구성된 모든 사용자에 대한 정보를 반환합니다.

    Get-CsOnlineUser

## 예제 2

예제 2에서는 단일 온라인 사용자(SIP 주소가 "sip:kenmyer@litwareinc.com"인 사용자)의 정보가 반환됩니다.

    Get-CsOnlineUser -Identity "sip:kenmyer@litwareinc.com"

## 예제 3

예제 3에 표시된 명령은 Lync Online에 대해 활성화되었지만 현재 등록자 풀에 할당되지 않은 모든 온라인 사용자에 대한 정보를 반환합니다.

    Get-CsOnlineUser -UnassignedUser

## 예제 4

예제 4에서는 Filter 매개 변수를 사용하여 사용자별 보관 정책 RedmondArchiving이 할당된 온라인 사용자에 대한 데이터만 반환되도록 제한합니다. 이 작업을 수행하기 위해 필터 값 {ArchivingPolicy -eq "RedmondArchiving"}을 사용하며, 해당 구문은 ArchivingPolicy 속성이 "RedmondArchiving"과 같은(-eq) 사용자에 대한 데이터만 반환되도록 제한합니다.

    Get-CsOnlineUser -Filter {ArchivingPolicy -eq "RedmondArchiving"}

## 예제 5

예제 5에서는 계정이 Microsoft Exchange 주소 목록에 표시되지 않도록 구성된 사용자 계정(즉, Active Directory 특성 msExchHideFromAddressLists가 True인 계정)에 대한 정보만 반환합니다. 이 작업을 수행하기 위해 Filter 매개 변수가 필터 값 {HideFromAddressLists -eq $True}와 함께 포함됩니다.

    Get-CsOnlineUser -Filter {HideFromAddressLists -eq $True}

## 예제 6

예제 6에 표시된 명령은 TenantID가 "bf19b7db-6960-41e5-a139-2aa373474354"인 테넌트에 할당된 모든 온라인 사용자의 정보를 반환합니다. 이 작업을 수행하기 위해 이 명령에는 Filter 매개 변수가 필터 값 {TenantId -eq "bf19b7db-6960-41e5-a139-2aa373474354"}와 함께 포함됩니다. 이 필터는 테넌트 "bf19b7db-6960-41e5-a139-2aa373474354"에 할당된 온라인 사용자에 대한 데이터만 반환되도록 제한합니다.

    Get-CsOnlineUser -Filter {TenantId -eq "bf19b7db-6960-41e5-a139-2aa373474354"}

## 자세한 정보

**Get-CsOnlineUser** cmdlet은 계정이 Microsoft Lync Online에 속한 사용자의 정보를 반환합니다. 반환된 정보에는 표준 Active Directory 계정 정보(사용자가 소속된 부서, 사용자의 주소, 전화 번호 등)뿐 아니라 Lync Server 관련 정보도 포함됩니다. **Get-CsOnlineUser** cmdlet은 사용자가 Enterprise Voice를 사용하도록 설정했는지 여부와 사용자에게 할당된 사용자별 정책(있는 경우)이 무엇인지에 관계없이 이러한 항목에 대한 정보를 반환합니다.

**Get-CsOnlineUser** cmdlet에는 TenantId 매개 변수가 없습니다. 즉, 다음과 유사한 명령을 사용하여 특정 Lync Online 테넌트의 계정을 가진 사용자에 대한 데이터만 반환되도록 제한할 수는 없습니다.

    Get-CsOnlineUser -TenantId "bf19b7db-6960-41e5-a139-2aa373474354"

하지만 Lync Online 테넌트가 여러 개인 경우에는 Filter 매개 변수 및 다음과 유사한 명령을 사용하여 지정된 테넌트의 사용자를 반환할 수 있습니다.

    Get-CsOnlineUser -Filter {TenantId -eq "bf19b7db-6960-41e5-a139-2aa373474354"}

이 명령은 TenantId가 "bf19b7db-6960-41e5-a139-2aa373474354"인 테넌트에 속한 사용자 계정에 대한 데이터만 반환되도록 제한하지 않습니다. 자신의 테넌트 ID를 모르는 경우에는 다음 명령을 사용하여 해당 정보를 반환할 수 없습니다.

    Get-CsTenant

하이브리드 또는 "분할 도메인" 배포(즉, 일부 사용자 계정은 Lync Online에 속하지만 다른 사용자 계정은 온-프레미스 버전의 Lync Server에 속하는 배포)의 경우 **Get-CsOnlineUser** cmdlet이 Lync Online 사용자의 정보만 반환합니다. 하지만 [Get-CsUser](get-csuser.md) cmdlet은 Lync Online 사용자와 온-프레미스 Lync Server 사용자 둘 다의 정보를 반환합니다. **Get-CsUser** cmdlet에 의해 반환되는 데이터에서 Lync Online 사용자를 제외하려면 다음 명령을 사용합니다.

    Get-CsUser -Filter {TenantId -eq "00000000-0000-0000-0000-000000000000"}

정의상 온-프레미스 버전의 Lync Server에 속한 사용자의 TenantId는 항상 00000000-0000-0000-0000-000000000000과 같습니다. Lync Online에 속한 사용자의 TenantId는 00000000-0000-0000-0000-000000000000 이외의 값과 같습니다.

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
<td><p>대체 자격 증명으로 <strong>Get-CsOnlineUser</strong> cmdlet을 실행할 수 있습니다. Windows에 로그온할 때 사용한 계정에 사용자 개체 작업에 필요한 권한이 없는 경우 이 매개 변수가 필요할 수 있습니다.</p>
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
<td><p>Lync Server 관련 특성을 필터링하여 반환되는 데이터를 제한할 수 있습니다. 예를 들어, 특성 음성 정책이 할당된 사용자 또는 특정 음성 정책이 할당되지 않은 사용자에 대한 데이터만 반환하도록 제한할 수 있습니다.</p>
<p>Filter 매개 변수는 Where-Object cmdlet에 사용되는 것과 동일한 Windows PowerShell 필터링 구문을 사용합니다. 예를 들어 Enterprise Voice를 사용하도록 설정된 사용자만 반환하는 필터는 다음과 유사한 형태입니다. 여기서 EnterpriseVoiceEnabled는 Active Directory 특성을 나타내고 -eq는 비교 연산자(같음)를 나타내며 $True(기본 제공 Windows PowerShell 변수)는 필터 값을 나타냅니다.</p>
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
<td><p>Lync Server 이전 버전(예 Microsoft Office Communications Server 2007 R2)에 이동된 사용자 컬렉션을 반환합니다. 이 매개 변수를 사용하는 경우 현재 버전의 소프트웨어에 계정이 있는 사용자는 반환되지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>OU</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.AD.OUIdParameter</p></td>
<td><p>특정 OU(조직 구성 단위) 또는 컨테이너의 사용자 계정에 대한 정보를 반환하는 데 사용됩니다. OU 매개 변수는 지정한 OU 및 모든 하위 OU의 데이터를 반환합니다. 예를 들어 Finance OU에 두 개의 하위 OU인 AccountsPayable 및 AccountsReceivable이 있는 경우 이러한 세 개의 각 OU에서 사용자가 반환됩니다.</p>
<p>OU를 지정할 때는 해당 컨테이너에 대한 DN(고유 이름)을 사용합니다(예: -OU &quot;OU=Finance,dc=litwareinc,dc=com&quot;). Users 컨테이너에서 사용자 계정을 가져오려면 다음 구문을 사용합니다.</p>
<p>-OU &quot;cn=Users,dc=litwareinc,dc=com&quot;</p></td>
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
<td><p>Lync Online에 대해 활성화되었지만 현재 등록자 풀에 할당되어 있지 않은 모든 사용자 컬렉션을 반환할 수 있습니다. 등록자 풀에 할당되지 않은 사용자는 로그온할 수 없습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

**Get-CsOnlineUser** cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.OCSADUser 개체의 파이프라인된 인스턴스뿐 아니라 유효한 사용자 계정 ID(예: "sip:kenmyer@litwareinc.com")를 나타내는 문자열 값도 허용합니다.

## 반환 형식

**Get-CsOnlineUser** cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.ADOCOnlineUser 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsUser](get-csuser.md)

