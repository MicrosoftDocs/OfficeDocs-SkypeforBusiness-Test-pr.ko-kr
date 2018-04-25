---
title: Enable-CsUser
TOCTitle: Enable-CsUser
ms:assetid: 8ceed97b-e802-4844-b509-c6ca9619ec55
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398711(v=OCS.15)
ms:contentKeyID: 49304326
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Enable-CsUser

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server에 대해 한 명 이상의 사용자를 활성화합니다. 사용자는 자신의 사용자 계정이 Lync Server를 사용하도록 설정될 때까지 Lync 2013 또는 기타 Lync Server 클라이언트를 사용할 수 없습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Enable-CsUser -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-HostingProviderProxyFqdn <Fqdn>] [-PassThru <SwitchParameter>] [-ProxyPool <Fqdn>] [-RegistrarPool <Fqdn>] [-SipAddress <String>] [-SipAddressType <FirstLastName | EmailAddress | UserPrincipalName | SAMAccountName | None>] [-SipDomain <Fqdn>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 **Enable-CsUser** cmdlet을 사용하여 표시 이름이 Pilar Ackerman인 사용자 계정을 활성화합니다. 이 예제에서 사용자는 atl-cs-001.litwareinc.com 등록자 풀에 할당되며, Lync Server가 SIP 도메인 litwareinc.com이 뒤에 오는 사용자의 SamAccountName(pilar)을 사용하여 SIP 주소를 자동 생성합니다.

    Enable-CsUser -Identity "Pilar Ackerman" -RegistrarPool "atl-cs-001.litwareinc.com" -SipAddressType SamAccountName  -SipDomain litwareinc.com

## 예제 2

예제 2에서는 Pilar Ackerman에 속한 Active Directory 사용자 계정을 Lync Server에서 사용하도록 설정합니다. Lync Server에 대한 계정을 구성하기 위해서는 **Enable-CsUser** cmdlet과 함께 다음과 같은 매개 변수가 사용됩니다. Identity는 사용하도록 설정할 계정을 식별하고, RegistrarPool은 새 사용자의 홈으로 지정할 Standard Edition 서버 또는 Enterprise Edition 프런트 엔드 풀을 나타내며, SipAddress는 새 사용자의 SIP 주소를 지정합니다. 이 경우 SIP 주소가 명시적으로 할당되며, 주소를 자동으로 생성하기 위해 Lync Server가 사용되지 않습니다.

    Enable-CsUser -Identity "Pilar Ackerman" -RegistrarPool "atl-cs-001.litwareinc.com" -SipAddress "sip:pilar@litwareinc.com"

## 예제 3

예제 3에서는 Finance 부서에서 일하는 모든 사용자가 Lync Server를 사용하도록 설정된 계정을 가집니다. 이 작업을 수행하기 위해 먼저 **Get-CsAdUser** cmdlet 및 LdapFilter 매개 변수를 사용하여 Finance 부서에서 일하는 모든 사용자의 컬렉션을 반환합니다. 이 정보는 Lync Server를 사용하도록 컬렉션의 각 계정을 설정하는 **Enable-CsUser** cmdlet에 파이프됩니다.

계정을 활성화하려면 사용자의 등록자 풀과 SIP 주소를 지정해야 합니다. 이 예제에서는 RegistrarPool 매개 변수를 사용하여 등록자 풀을 지정합니다. 그러나 SIP 주소가 직접 할당되지는 않습니다. 대신에 두 개의 매개 변수인 SipAddressType 및 SipDomain이 명령에 추가됩니다. 즉, 사용자의 SamAccountName 및 SIP 도메인 이름으로 구성되는 새 SIP 주소가 각 계정에 대해 자동으로 생성됩니다. 예를 들어, SamAccountName이 kenmyer인 사용자에게 SIP 주소 sip:kenmyer@litwareinc.com이 제공됩니다.

    Get-CsAdUser -LdapFilter "department=Finance" | Enable-CsUser -RegistrarPool "atl-cs-001.litwareinc.com" -SipAddressType SamAccountName  -SipDomain litwareinc.com

## 예제 4

예제 4에서는 Lync Server에 대해 아직 활성화되지 않은 모든 Active Directory 사용자를 활성화합니다. 이 작업을 수행하기 위해 **Get-CsAdUser** cmdlet이 Filter 매개 변수와 함께 호출됩니다. {Enabled -ne $True} 필터는 Lync Server에 대해 활성화되지 않은 모든 사용자의 컬렉션을 반환합니다. 그런 다음 해당 컬렉션은 각 계정을 활성화하여 등록자 풀 atl-cs-001.litwareinc.com에 사용자를 할당하고 각 사용자에 대해 SIP 주소를 자동으로 생성하는 **Enable-CsUser** cmdlet에 파이프됩니다.

    Get-CsAdUser -Filter {Enabled -ne $True} | Enable-CsUser -RegistrarPool "atl-cs-001.litwareinc.com" -SipAddressType SamAccountName  -SipDomain litwareinc.com

## 자세한 정보

Lync Server에 로그온할 수 있으려면 사용자는 두 가지 요구 사항을 충족해야 합니다. 즉, 유효한 Active Directory 도메인 서비스 계정이 있어야 하고 해당 계정이 Lync Server를 사용하도록 설정되어야 합니다. Lync Server에 대해 사용자 계정을 활성화하는 한 가지 방법은 **Enable-CsUser** cmdlet을 사용하는 것입니다. 이 cmdlet을 사용하여 Lync Server에 대해 계정을 활성화하려면 다음을 수행해야 합니다. 1) 활성화할 계정을 선택하고, 2) 계정에 대한 등록자 풀을 선택하고, 3) 계정에 SIP 주소를 할당합니다. 관리자는 Lync Server를 사용하여 사용자에게 특정 SIP 주소를 할당할 수도 있고, Lync Server에서 사용자의 SIP 주소를 자동으로 생성하도록 할 수도 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 그룹의 구성원은 **Enable-CsUser** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Enable-CsUser"}

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
<td><p>Lync Server에 대해 활성화할 사용자 계정의 ID를 나타냅니다. 사용자 ID는 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 사용자의 SIP 주소, 2) 사용자의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그온 이름(예: litwareinc\kenmyer) 및 4) 사용자의 Active Directory 표시 이름(예: Ken Myer)입니다. 또한 사용자의 Active Directory 고유 이름을 사용하여 사용자 계정을 참조할 수도 있습니다.</p>
<p>표시 이름을 사용자 ID로 사용할 경우 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어 &quot;* Smith&quot;라는 ID는 표시 이름이 &quot;Smith&quot; 문자열 값으로 끝나는 모든 사용자를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>사용자 계정을 활성화하기 위해 지정된 도메인 컨트롤러에 연결할 수 있습니다. 특정 도메인 컨트롤러에 연결하려면 DomainController 매개 변수 뒤에 컴퓨터 이름(예: atl-cs-001) 또는 FQDN(정규화된 도메인 이름)(예: atl-cs-001.litwareinc.com)을 포함합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>HostingProviderProxyFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>이 매개 변수는 Lync Online에만 사용됩니다. Lync Server의 온-프레미스 구현에 사용하면 안 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Lync Server를 사용하도록 설정할 사용자 계정을 나타내는 사용자 개체를 파이프라인을 통해 전달할 수 있습니다. 기본적으로 <strong>Enable-CsUser</strong> cmdlet은 파이프라인을 통해 개체를 전달하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ProxyPool</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>이 매개 변수는 Lync Online에만 사용됩니다. Lync Server의 온-프레미스 구현에 사용하면 안 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>RegistrarPool</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>사용자의 Lync Server 계정이 속하는 등록자 풀을 나타냅니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>사용자에게 특정 SIP 주소를 할당할 수 있습니다. SIP 주소를 지정할 때 주소 앞에 접두사 &quot;sip:&quot;이 와야 합니다. 이는 SipAddress 매개 변수에 제공된 값이 다음과 같이 표시됨을 의미합니다.</p>
<p>sip:kenmyer@litwareinc.com</p>
<p>Lync Server에서 SIP 주소를 자동으로 생성하려면 SipAddressType을 사용할 때 SipAddress 매개 변수를 사용하지 않아야 합니다.</p>
<p>여러 사용자를 동시에 활성화하려는 경우에는 SipAddress 매개 변수를 사용할 수 없습니다. 대신 SipAddressType 매개 변수를 사용하여 이러한 사용자의 SIP 주소를 자동 생성해야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SipAddressType</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.AD.Cmdlets.AddressType</p></td>
<td><p>새 사용자에 대한 SIP 주소를 자동으로 생성하도록 Lync Server에 지시합니다. SIP 주소를 Lync Server에서 자동으로 생성하게 하려면 SipAddressType 매개 변수를 포함하고 다음 매개 변수 값 중 하나를 사용해야 합니다.</p>
<p>FirstLastName. SIP 주소는 사용자의 이름, 성 및 SIP 도메인을 순서대로 포함합니다. 예를 들어, 사용자 Ken Myer의 SIP 주소는 Ken.Myer@litwareinc.com과 유사합니다. 이 주소 형식을 사용하는 경우 SipDomain 매개 변수를 포함해야 합니다.</p>
<p>EmailAddress. 사용자의 전자 메일 주소(Active Directory에 정의됨)가 SIP 주소로 사용됩니다.</p>
<p>UserPrincipalName. 사용자의 UPN은 SIP 주소로 사용됩니다.</p>
<p>SamAccountName. SIP 주소는 사용자의 SamAccountName(로그온 이름)과 SIP 도메인을 순서대로 포함합니다. 예를 들어, SamAccountName이 kmyer인 사용자의 SIP 주소는 kmyer@litwareinc.com과 유사합니다. 이 주소 형식을 사용하는 경우 SipDomain 매개 변수를 포함해야 합니다.</p>
<p>SIPAddress 매개 변수를 사용하여 사용자에게 SIP 주소를 명시적으로 할당할 경우 SipAddressType 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SipDomain</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>활성화할 사용자 계정에 대한 SIP 도메인입니다. SIPAddressType 매개 변수를 사용하여 Lync Server에서 사용자의 SIP 주소를 자동으로 생성하게 하고 SIP 주소가 SamAccountName 또는 사용자의 이름과 성을 기반으로 할 경우 이 매개 변수가 필요합니다. SIP 주소가 사용자의 전자 메일 주소 또는 UPN을 기반으로 할 경우 도메인 이름이 이미 해당 특성 값에 포함되어 있기 때문에 이 매개 변수가 필요하지 않습니다.</p></td>
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

문자열 또는 Microsoft.Rtc.Management.ADConnect.Schema.ADUser 개체입니다. **Enable-CsUser** cmdlet은 Lync Server를 사용하도록 설정된 사용자 계정의 ID를 나타내는 파이프라인된 문자열 값을 허용합니다. 또한 Active Directory 사용자 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. **Enable-CsUser** cmdlet은 값이나 개체를 반환하지 않습니다. 대신에 이 cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.ADUser 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[Disable-CsUser](disable-csuser.md)  
[Get-CsUser](get-csuser.md)

