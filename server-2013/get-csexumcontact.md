---
title: Get-CsExUmContact
TOCTitle: Get-CsExUmContact
ms:assetid: 9c7b2afb-4d7f-4b5a-99dd-6f8978dd5728
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412725(v=OCS.15)
ms:contentKeyID: 49304520
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsExUmContact

 

_**마지막으로 수정된 항목:** 2015-03-09_

하나 이상의 호스트된 Exchange 통합 메시징(UM) 연락처 개체를 검색합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsExUmContact [-Identity <UserIdParameter>] [-Credential <PSCredential>] [-DomainController <Fqdn>] [-Filter <String>] [-LdapFilter <String>] [-OU <OUIdParameter>] [-ResultSize <Unlimited>]

## 예제

## 예제 1

이 예제에서는 Lync Server 배포 내에 정의된 모든 Exchange UM 연락처를 검색합니다.

    Get-CsExUmContact

## 예제 2

이 예제에서는 SIP 주소가 sip:exum1@fabrikam.com인 Exchange UM 연락처를 검색합니다.

    Get-CsExUmContact -Identity sip:exum1@fabrikam.com

## 예제 3

이 예제에서는 Filter 매개 변수를 사용하여 Lync Server에 대해 활성화되지 않은 모든 Exchange UM 연락처를 검색합니다. 이를 수행하기 위해 Enabled 속성을 필터링하여 이 속성 값이 False($False)와 같은지(-eq) 확인합니다. 이 명령에서 반환된 연락처는 작동하지 않습니다.

    Get-CsExUmContact -Filter {Enabled -eq $False}

## 예제 4

이 명령은 LineURI 속성을 필터링하여 LineURI가 tel:555로 시작하는 모든 Exchange UM 연락처를 검색합니다. 즉, 전화 번호가 555로 시작하는 모든 연락처를 검색합니다.

    Get-CsExUmContact -Filter {LineURI -like "tel:555*"}

## 예제 5

이 예제의 명령은 OU 매개 변수를 사용하여 Active Directory OU OU=ExUmContacts,DC=Vdomain,DC=com에 있는 모든 Exchange UM 연락처를 검색합니다.

    Get-CsExUmContact -OU "OU=ExUmContacts,DC=Vdomain,DC=com"

## 자세한 정보

Lync Server는 Exchange UM과 함께 작동하여 자동 전화 교환 및 구독자 액세스와 같은 여러 가지 음성 관련 기능을 제공합니다. Exchange UM이 온-프레미스가 아니라 호스트된 서비스로 제공되는 경우 자동 전화 교환 및 구독자 액세스 기능을 적용하려면 Windows PowerShell을 사용하여 연락처 개체를 만들어야 합니다. 이 cmdlet은 이러한 연락처를 한 개 이상 검색합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins, RTCUniversalServerAdmins 및 RTCUniversalReadOnlyAdmins 그룹의 구성원은 **Get-CsExUmContact** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsExUmContact"}

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
<td><p>대체 자격 증명으로 cmdlet을 실행할 수 있습니다. Windows에 로그온하는 데 사용한 계정에 연락처 개체를 사용하는 데 필요한 권한이 없는 경우 이 기능이 필요할 수 있습니다.</p>
<p>Credential 매개 변수를 사용하려면 먼저 <strong>Get-Credential</strong> cmdlet을 호출하여 PSCredential 개체를 만들어야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>대화 상대 정보를 검색하기 위해 지정된 도메인 컨트롤러에 연결하는 데 사용됩니다. 특정 도메인 컨트롤러에 연결하려면 DomainController 매개 변수 뒤에 컴퓨터 이름(예: atl-mcs-001) 또는 정규화된 도메인 이름(예: atl-mcs-001.litwareinc.com)을 포함합니다.</p>
<p>전체 데이터 형식: Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
</tr>
<tr class="odd">
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>Lync Server 관련 특성을 필터링하여 반환되는 데이터를 제한할 수 있습니다. 예를 들어 &quot;tel:555&quot;로 시작하는 줄 URI를 가진 연락처를 반환하도록 데이터를 제한할 수 있습니다.</p>
<p>Filter 매개 변수는 <strong>Where-Object</strong> cmdlet에 사용되는 Windows PowerShell 필터링 구문의 하위 집합을 사용합니다. 예를 들어 Enterprise Voice를 사용하도록 설정된 대화 상대만 반환하는 필터는 {EnterpriseVoiceEnabled -eq $True}와 같이 나타납니다. 여기서 EnterpriseVoiceEnabled는 Active Directory 특성을 나타내고 -eq는 비교 연산자(같음)를 나타내며 $True(기본 제공 Windows PowerShell 변수)는 필터 값을 나타냅니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>검색할 연락처 개체의 고유한 식별자입니다. 연락처 ID는 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 연락처의 SIP 주소, 2) 연락처의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 연락처의 도메인 이름 및 로그온 이름(예: litwareinc\exum1) 및 4) 연락처의 Active Directory 표시 이름(예: Team Auto Attendant)입니다.</p>
<p>전체 데이터 형식: Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
</tr>
<tr class="odd">
<td><p><em>LdapFilter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>&quot;일반&quot; Active Directory 특성(즉, Lync Server와 관련되지 않은 특성)을 필터링하여 반환되는 데이터를 제한할 수 있습니다.</p>
<p>필터를 만들 때 LdapFilter 매개 변수는 LDAP 쿼리 언어를 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>OU</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.AD.OUIdParameter</p></td>
<td><p>검색되는 정보를 특정 Active Directory OU(조직 구성 단위)로 제한하는 데 사용됩니다. 이 경우 지정된 OU 및 모든 하위 OU에서 데이터가 반환됩니다.</p>
<p>OU를 지정할 때 해당 컨테이너에 대한 고유 이름을 사용합니다(예: OU=ExUmContacts,dc=litwareinc,dc=com).</p></td>
</tr>
<tr class="odd">
<td><p><em>ResultSize</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.Unlimited</p></td>
<td><p>명령에서 반환되는 레코드 수를 제한할 수 있게 합니다. 예를 들어, 포리스트에 있는 연락처 수에 상관없이 7개의 연락처만 반환하려면 ResultSize 매개 변수를 포함하고 매개 변수 값을 7로 설정합니다. 반환될 7개의 연락처를 지정하는 방법은 없습니다. ResultSize를 7로 설정했지만 포리스트에 연락처가 3개만 있는 경우 3개의 연락처가 반환된 다음 오류 없이 완료됩니다.</p>
<p>결과 크기는 0-2147483647(포함) 사이의 임의 정수로 설정할 수 있습니다. 0으로 설정할 경우 명령이 실행되지만 데이터가 반환되지 않습니다.</p>
<p>전체 데이터 형식: Microsoft.Rtc.Management.ADConnect.Core.Unlimited</p></td>
</tr>
</tbody>
</table>


## 입력 형식

문자열. Exchange UM 연락처 개체의 ID를 나타내는 파이프라인된 문자열 값을 허용합니다.

## 반환 형식

Microsoft.Rtc.Management.ADConnect.Schema.OCSADExUmContact 유형의 개체를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsExUmContact](new-csexumcontact.md)  
[Remove-CsExUmContact](remove-csexumcontact.md)  
[Set-CsExUmContact](set-csexumcontact.md)  
[Move-CsExUmContact](move-csexumcontact.md)

