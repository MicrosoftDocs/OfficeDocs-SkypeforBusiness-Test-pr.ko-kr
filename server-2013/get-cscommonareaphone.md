---
title: Get-CsCommonAreaPhone
TOCTitle: Get-CsCommonAreaPhone
ms:assetid: bfb7927b-49a7-4637-a9ff-fd68897efb45
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412934(v=OCS.15)
ms:contentKeyID: 49304896
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsCommonAreaPhone

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server를 사용하여 관리할 수 있는 공통 영역 전화에 대한 정보를 반환합니다. 공통 영역 전화는 건물 로비, 직원 휴게실 또는 다수의 사람들이 사용할 가능성이 높은 기타 영역에 있는 전화로서 다수의 사용자를 위한 것입니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsCommonAreaPhone [-Identity <UserIdParameter>] [-Credential <PSCredential>] [-DomainController <Fqdn>] [-Filter <String>] [-LdapFilter <String>] [-OU <OUIdParameter>] [-ResultSize <Unlimited>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 사용하도록 구성된 모든 공통 영역 전화에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 **Get-CsCommonAreaPhone** cmdlet을 매개 변수 없이 호출합니다.

    Get-CsCommonAreaPhone

## 예제 2

예제 2에서는 Active Directory 표시 이름이 "Building 14 Lobby"인 공통 영역 전화를 반환합니다. 이 작업을 수행하기 위해 Filter 매개 변수와 필터 값 {DisplayName -eq "Building 14 Lobby"}를 포함합니다. 이 필터 값은 DisplayName 속성이 "Building 14 Lobby"와 같은 공통 영역 전화로 반환되는 개체를 제한합니다.

    Get-CsCommonAreaPhone -Filter {DisplayName -eq "Building 14 Lobby"}

## 예제 3

예제 3에서는 Active Directory 표시 이름이 "Building 14"로 시작하는 모든 공통 영역 전화를 반환합니다. 이 작업을 수행하기 위해 **Get-CsCommonAreaPhone** cmdlet을 Filter 매개 변수 및 필터 값 {DisplayName -like "Building 14\*"}와 함께 호출합니다. 이 필터 값은 -like 연산자 및 와일드카드 문자열 "Building 14\*"를 사용하여 DisplayName 속성이 "Building 14"로 시작하는 전화에 대한 데이터만 반환하도록 제한합니다(예: "Building 14 Lobby", "Building 14 Cafeteria" 등).

    Get-CsCommonAreaPhone  -Filter {DisplayName -like "Building 14*"}

## 예제 4

예제 4에서는 LineUri 속성이 "tel:+14255551234"와 같은 단일 공통 영역 전화를 반환합니다. LineUri는 고유해야 하므로 이 명령은 둘 이상의 항목을 반환하지 않습니다.

    Get-CsCommonAreaPhone  -Filter {LineUri -eq "tel:+14255551234"}

## 예제 5

예제 5에 표시된 명령은 다이얼 플랜이 할당되지 않은 모든 공통 영역 전화에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 Filter 매개 변수와 필터 값 {DialPlan -eq $Null}을 사용합니다. 이 필터 값은 DialPlan 속성이 null 값과 같은 전화에 대한 데이터만 반환하도록 제한합니다. 공통 영역 전화에 다이얼 플랜이 명시적으로 할당되지 않은 경우에는 자동으로 전역 다이얼 플랜을 사용하거나 사이트에 할당된 다이얼 플랜(사용 가능한 경우)을 사용합니다.

    Get-CsCommonAreaPhone -Filter {DialPlan -eq $Null}

## 예제 6

예제 6에서는 Active Directory 도메인 서비스의 Telecommunications OU에 대화 상대 개체가 있는 모든 공통 영역 전화의 컬렉션을 반환합니다. 이 작업을 수행하기 위해 **Get-CsCommonAreaPhone** cmdlet을 OU 매개 변수와 함께 호출합니다. 이 매개 변수 값은 고유 이름이 ou=Telecommunications, dc=litwareinc, dc=com인 OU에 대화 상대 개체가 있는 전화로 반환되는 개체를 제한합니다.

    Get-CsCommonAreaPhone -OU "ou=Telecommunications,dc=litwareinc,dc=com"

## 자세한 정보

공통 영역 전화는 개별 사용자와 연결되지 않은 IP 전화입니다. 공통 영역 전화는 특정 사무실에 있는 것이 아니라 일반적으로 건물의 로비, 카페, 직원 라운지, 회의실 등 많은 사람이 모일 수 있는 장소에 있습니다. 따라서 관리자의 관리가 필요합니다. Lync Server를 통해 사용하는 전화는 일반적으로 개별 사용자에게 할당된 음성 정책 및 다이얼 플랜으로 유지 관리되는데, 공통 영역 전화에는 개별 사용자가 할당되지 않기 때문입니다.

이러한 문제를 해결하는 한 가지 방법은 모든 공통 영역 전화에 대해 Active Directory 연락처 개체를 만드는 방법이 있습니다. 연락처 개체는 **New-CsCommonAreaPhone** cmdlet을 사용하여 만들 수 있습니다. 이러한 연락처 개체에는 사용자 계정과 마찬가지로 정책 및 음성 계획을 할당할 수 있습니다. 따라서 공통 영역 전화가 개별 사용자와 연결되어 있지 않더라도 해당 전화에 대한 제어를 유지 관리할 수 있습니다. 예를 들어 사람들이 공통 영역 전화에서 통화를 전송하거나 대기할 수 없도록 하려면 통화 전송 및 통화 대기를 금지하는 음성 정책을 만들어 해당 정책을 공통 영역 전화에 할당하기만 하면 됩니다. 좀 더 정확하게 표현하자면 공통 영역 전화를 나타내는 연락처 개체에 할당하면 됩니다. 예를 들어 다음 명령은 음성 정책 CommonAreaPhoneVoicePolicy를 모든 공통 영역 전화에 할당합니다.

Get-CsCommonAreaPhone | Grant-CsVoicePolicy –PolicyName "CommonAreaPhoneVoicePolicy"

**Get-CsCommonAreaPhone** cmdlet을 사용하면 조직에서 사용하도록 구성된 공통 영역 전화에 대한 정보를 검색할 수 있습니다. **Get-CsCommonAreaPhone** cmdlet을 매개 변수 없이 호출한 경우 이 cmdlet은 모든 공통 영역 전화에 대한 정보를 반환합니다. 하지만 선택적 매개 변수를 사용하여 정보를 필터링할 수 있습니다. 예를 들어 지정된 OU(조직 구성 단위)에 대화 상대 개체가 있거나 모든 대화 상대 개체가 지정된 건물에 있는 모든 공통 영역 전화를 반환할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins, RTCUniversalServerAdmins 및 RTCUniversalReadOnlyAdmins 그룹의 구성원은 **Get-CsCommonAreaPhone** cmdlet을 로컬로 실행할 수 있습니다. 특정 사이트 또는 특정 Active Directory OU에 대해 이 cmdlet을 실행할 권한은 **Grant-CsOUPermission** cmdlet을 사용하여 할당할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsCommonAreaPhone"}

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
<td><p>대체 자격 증명으로 <strong>Get-CsCommonAreaPhone</strong> cmdlet을 실행하는 데 사용됩니다. Windows에 로그온하는 데 사용한 계정에 연락처 개체를 사용하는 데 필요한 권한이 없는 경우 이 기능이 필요할 수 있습니다.</p>
<p>Credential 매개 변수를 사용하려면 먼저 <strong>Get-Credential</strong> cmdlet을 사용하여 PSCredential 개체를 만들어야 합니다. 자세한 내용은 <strong>Get-Credential</strong> cmdlet 도움말 항목을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>대화 상대 정보를 검색하기 위해 지정된 도메인 컨트롤러에 연결하는 데 사용됩니다. 특정 도메인 컨트롤러에 연결하려면 DomainController 매개 변수 뒤에 해당 컴퓨터의 FQDN(정규화된 도메인 이름)을 포함합니다(예: atl-cs-001.litwareinc.com).</p></td>
</tr>
<tr class="odd">
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>Lync Server 관련 특성을 필터링하여 반환되는 데이터를 제한할 수 있습니다. 예를 들어 특정 음성 정책이 할당된 공통 영역 전화 대화 상대 개체 또는 특정 음성 정책이 할당되지 않은 대화 상대에 대한 데이터만 반환하도록 제한할 수 있습니다.</p>
<p>Filter 매개 변수는 <strong>Where-Object</strong> cmdlet에 사용되는 구문과 동일한 Windows PowerShell 필터링 구문을 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>공통 영역 전화의 고유 식별자입니다. 공통 영역 전화는 연결된 연락처 개체의 Active Directory DN(고유 이름)을 사용하여 식별됩니다. 기본적으로 공통 영역 전화는 공용 이름으로 GUID(Globally Unique Identifier)를 사용합니다. 따라서 일반적으로 CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com과 유사한 ID가 지정됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LdapFilter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>일반 Active Directory 특성(즉, Lync Server와 관련되지 않은 특성)을 필터링하여 반환되는 데이터를 제한할 수 있습니다. 예를 들어 특정 부서에 할당되거나 특정 건물에 있는 대화 상대 개체에 대한 데이터만 반환하도록 제한할 수 있습니다.</p>
<p>필터를 만들 때 LdapFilter 매개 변수는 LDAP 쿼리 언어를 사용합니다. 예를 들어 Redmond 도시의 공통 영역 전화를 나타내는 대화 상대 개체만 반환하는 필터는</p>
<p>-LDAPFilter &quot;l=Redmond&quot;와 같습니다.</p>
<p>이 필터에서 &quot;l&quot;(소문자 L)은 Active Directory 특성(locality)을 나타내고 &quot;=&quot;는 비교 연산자(같음)를 나타내며 &quot;Redmond&quot;는 필터 값을 나타냅니다.</p></td>
</tr>
<tr class="even">
<td><p><em>OU</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.AD.OUIdParameter</p></td>
<td><p>특정 Active Directory OU(조직 구성 단위)에서 대화 상대 개체를 반환하는 데 사용됩니다. OU 매개 변수는 지정한 OU 및 모든 하위 OU의 데이터를 반환합니다. 예를 들어 Finance OU에 두 개의 하위 OU인 AccountsPayable 및 AccountsReceivable이 있는 경우 이러한 각 OU에서 공통 영역 전화 정보가 반환됩니다.</p>
<p>OU를 지정할 때 해당 컨테이너에 대한 고유 이름을 사용합니다(예: -OU &quot;OU=Finance,dc=litwareinc,dc=com&quot;).</p></td>
</tr>
<tr class="odd">
<td><p><em>ResultSize</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.Unlimited</p></td>
<td><p>명령에서 반환되는 레코드 수를 제한하는 데 사용됩니다. 예를 들어 포리스트에 있는 공통 영역 전화 수에 상관없이 7개의 공통 영역 전화만 반환하려면 -ResultSize 매개 변수를 포함하고 매개 변수 값을 7로 설정합니다. 반환될 7개의 전화를 지정하는 방법은 없습니다. ResultSize를 7로 설정했지만 포리스트에 공통 영역 전화가 3개만 있는 경우 3개의 전화가 반환된 다음, 오류 없이 완료됩니다.</p>
<p>결과 크기는 0-2147483647(포함) 사이의 임의 정수로 설정할 수 있습니다. 0으로 설정할 경우 명령이 실행되지만 데이터가 반환되지 않습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

문자열. **Get-CsCommonAreaPhone** cmdlet은 공통 영역 전화의 ID를 나타내는 파이프라인된 문자열 값을 허용합니다.

## 반환 형식

**Get-CsCommonAreaPhone** cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.OCSADCommonAreaPhoneContact 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Move-CsCommonAreaPhone](move-cscommonareaphone.md)  
[New-CsCommonAreaPhone](new-cscommonareaphone.md)  
[Remove-CsCommonAreaPhone](remove-cscommonareaphone.md)  
[Set-CsCommonAreaPhone](set-cscommonareaphone.md)

