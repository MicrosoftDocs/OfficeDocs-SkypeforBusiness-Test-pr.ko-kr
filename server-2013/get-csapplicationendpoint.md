---
title: Get-CsApplicationEndpoint
TOCTitle: Get-CsApplicationEndpoint
ms:assetid: 820d3bbd-0348-4272-bdb3-c3d612d0836a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398655(v=OCS.15)
ms:contentKeyID: 49304221
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsApplicationEndpoint

 

_**마지막으로 수정된 항목:** 2015-03-09_

응용 프로그램 서비스의 끝점을 검색합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsApplicationEndpoint [-Identity <UserIdParameter>] [-ApplicationId <String>] [-Credential <PSCredential>] [-DomainController <Fqdn>] [-Filter <String>] [-OU <OUIdParameter>] [-PoolFqdn <Fqdn>] [-ResultSize <Unlimited>]

## 예제

## 예제 1

이 예제에서는 Lync Server 배포 내에 정의된 모든 응용 프로그램 끝점에 대한 정보를 검색합니다.

    Get-CsApplicationEndpoint

## 예제 2

예제 2에서는 표시 이름 내의 위치에 관계없이 문자열 “endpoint”가 포함된 모든 응용 프로그램 끝점을 검색합니다. 이를 위해 Filter 매개 변수를 사용합니다. 이 매개 변수 값은 필터링을 통해 문자열 endpoint(\*endpoint\* - 와일드카드 문자는 endpoint라는 문자열 앞 또는 뒤에 어떤 문자라도 올 수 있음을 나타내며, 이는 endpoint가 표시 이름 내의 아무 데나 있어도 됨을 의미함)가 포함된(-like) 표시 이름(DisplayName)을 가진 끝점 개체를 찾습니다.

    Get-CsApplicationEndpoint -Filter {DisplayName -like "*endpoint*"}

## 예제 3

예제 3에서는 응용 프로그램 urn:application:tapp2와 연결된 모든 응용 프로그램 끝점을 반환합니다. 이 작업을 수행하기 위해 ID tapp2를 ApplicationId 매개 변수에 전달합니다. 풀 FQDN은 지정하지 않았습니다. 이는 ID가 tapp2인 응용 프로그램이 두 개 이상의 풀에 존재하는 경우 이러한 응용 프로그램 모두에 대한 끝점이 검색됨을 의미합니다. 이 명령의 다음 부분에서는 반환된 개체를 해당 개체의 Identity, SipAddress, DisplayName 및 OwnerUrn 속성만 표시하는 **Select-Object** cmdlet에 파이프합니다.

    Get-CsApplicationEndpoint -ApplicationId tapp2 | Select-Object Identity, SipAddress, DisplayName, OwnerUrn

## 자세한 정보

이 cmdlet은 Active Directory 도메인 서비스에서 하나 이상의 응용 프로그램 대화 상대를 검색합니다. 이러한 개체는 Active Directory에서 RTC 서비스의 응용 프로그램 대화 상대 컨테이너에 저장됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins, RTCUniversalServerAdmins 및 RTCUniversalReadOnlyAdmins 그룹의 구성원은 **Get-CsApplicationEndpoint** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsApplicationEndpoint"}

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
<td><p><em>ApplicationId</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>검색할 응용 프로그램 끝점의 응용 프로그램 ID입니다. 응용 프로그램 ID는 끝점의 OwnerUrn 속성 값입니다. 예를 들어 OwnerUrn 속성의 값이 urn:application:Caa인 경우 응용 프로그램 ID는 urn:application:Caa입니다. 그러나 접미사(이 경우 Caa)만 입력하여 끝점을 검색할 수 있습니다(예: -ApplicationId Caa).</p></td>
</tr>
<tr class="even">
<td><p><em>Credential</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSCredential</p></td>
<td><p>Get 작업이 진행되는 대체 자격 증명입니다. Windows PowerShell cmdlet <strong>Get-Credential</strong>을 호출하여 PSCredential 개체를 검색할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>도메인 컨트롤러를 지정하도록 합니다. 도메인 컨트롤러를 지정하지 않으면 사용 가능한 첫 번째 도메인 컨트롤러가 사용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>Lync Server 관련 특성을 필터링하여 반환된 데이터를 제한할 수 있도록 합니다. 예를 들어 반환되는 데이터를 표시 이름 또는 SIP 주소가 특정 와일드카드 패턴과 일치하는 연락처로 제한할 수 있습니다.</p>
<p>Filter 매개 변수는 <strong>Where-Object</strong> cmdlet에 사용되는 구문과 동일한 Windows PowerShell 필터링 구문을 사용합니다. 예를 들어 Enterprise Voice를 사용하도록 설정된 대화 상대만 반환하는 필터는 {EnterpriseVoiceEnabled -eq $True}와 유사합니다. 여기서 EnterpriseVoiceEnabled는 Active Directory 특성을 나타내고 -eq는 비교 연산자(같음)를 나타내며 $True(기본 제공 Windows PowerShell 변수)는 필터 값을 나타냅니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>검색할 응용 프로그램 끝점의 ID, SIP 주소 또는 표시 이름입니다. ID는 끝점의 고유 이름으로 구성됩니다. 일반적으로 CN의 일부로 GUID(Globally Unique Identifier)를 포함합니다(예: CN={8811fefe-e0bb-4fab-ae39-7aaeddd423dc},CN=Application Contacts,CN=RTC Service,CN=Services,CN=Configuration,DC=Vdomain,DC=com).</p></td>
</tr>
<tr class="even">
<td><p><em>OU</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.AD.OUIdParameter</p></td>
<td><p>끝점이 있는 OU(조직 구성 단위)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PoolFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>응용 프로그램 끝점이 위치하는 풀의 FQDN(정규화된 도메인 이름)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ResultSize</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.Unlimited</p></td>
<td><p>검색할 끝점 레코드의 최대 수입니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

문자열. 응용 프로그램 끝점의 ID를 나타내는 파이프라인된 문자열 값을 허용합니다.

## 반환 형식

Microsoft.Rtc.Management.ADConnect.Schema.OCSADApplicationContact 유형의 개체를 검색합니다.

## 참고 항목

#### 기타 리소스

[Move-CsApplicationEndpoint](move-csapplicationendpoint.md)

