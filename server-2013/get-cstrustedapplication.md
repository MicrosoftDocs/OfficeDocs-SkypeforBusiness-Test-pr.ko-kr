---
title: Get-CsTrustedApplication
TOCTitle: Get-CsTrustedApplication
ms:assetid: e6623931-3bac-4146-92a9-4465396e9fe6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399025(v=OCS.15)
ms:contentKeyID: 49305360
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsTrustedApplication

 

_**마지막으로 수정된 항목:** 2015-03-09_

신뢰할 수 있는 응용 프로그램에 대한 설정을 검색합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsTrustedApplication [-ApplicationId <String>] [-TrustedApplicationPoolFqdn <String>] <COMMON PARAMETERS>

    Get-CsTrustedApplication [-Identity <ExternalApplicationIdentity>] <COMMON PARAMETERS>

    Get-CsTrustedApplication [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS:

## 예제

## 예제 1

이 예제에서는 Lync Server 배포 내에 정의된 모든 신뢰할 수 있는 응용 프로그램에 대한 정보를 검색합니다.

    Get-CsTrustedApplication

## 예제 2

예제 2에서는 ID가 TrustPool.litwareinc.com/urn:application:tapp2인 신뢰할 수 있는 응용 프로그램을 검색합니다. **Get-CsTrustedApplication** cmdlet은 자동으로 접두사를 추가하고 올바른 응용 프로그램을 검색하므로 접두사 urn:application:은 생략할 수 있습니다.

    Get-CsTrustedApplication -Identity TrustPool.litwareinc.com/tapp2

## 예제 3

예제 3에서는 Filter 값으로 지정된 와일드카드 문자열과 일치하는 ID를 가진 모든 신뢰할 수 있는 응용 프로그램을 검색합니다. 이 예제에서는 Filter 값 \*trust\*를 사용하여 ID에 문자열 “trust”가 포함된 모든 신뢰할 수 있는 응용 프로그램을 검색합니다. 이 문자열은 ID의 일부, 즉 풀 FQDN 또는 응용 프로그램 ID에 포함될 수 있습니다. 따라서 이 명령은 TrustedPool.litwareinc.com/urn:application:application1, Pool1.litwareinc.com/urn:application:trustedapp 및 Pool1.litwareinc.com/urn:application:trust와 같은 ID를 가진 신뢰할 수 있는 응용 프로그램을 검색합니다.

    Get-CsTrustedApplication -Filter *trust*

## 예제 4

예제 4에서는 Identity 매개 변수만 지정한 예제 2와 동일한 결과를 반환합니다. 다만, 예제 2에서는 신뢰할 수 있는 풀 FQDN 뒤에 응용 프로그램 ID가 오는 Identity를 기반으로 신뢰할 수 있는 응용 프로그램을 검색한 반면, 이 예제에서는 응용 프로그램 ID와 신뢰할 수 있는 풀 FQDN을 두 가지 별도의 매개 변수(ApplicationId 및 TrustedApplicationPoolFqdn) 값으로 입력했다는 점이 다릅니다.

    Get-CsTrustedApplication -ApplicationId tapp2 -TrustedApplicationPoolFqdn TrustPool.litwareinc.com

## 예제 5

예제 5에서는 TrustPool.litwareinc.com 풀에 있는 모든 신뢰할 수 있는 응용 프로그램을 검색합니다. 이 작업을 수행하기 위해 먼저 **Get-CsTrustedApplication** cmdlet을 호출합니다. 그러면 Lync Server 배포 내에 정의된 모든 신뢰할 수 있는 응용 프로그램 컬렉션이 반환됩니다. 이 컬렉션은 컬렉션의 각 항목을 하나씩 확인하여 TrustedApplicationPoolFqdn 속성 값이 TrustPool.litwareinc.com과 같은(-eq) 항목을 찾는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsTrustedApplication | Where-Object {$_.TrustedApplicationPoolFqdn -eq "TrustPool.litwareinc.com"}

## 자세한 정보

신뢰할 수 있는 응용 프로그램은 Lync Server의 일부로 포함되어 기본 제공되지는 않지만 이 제품의 일부로 실행하도록 신뢰할 수 있는 상태가 지정된 타사에서 개발한 응용 프로그램입니다. 이 cmdlet을 사용하면 하나 이상의 신뢰할 수 있는 응용 프로그램에 대한 포트 및 GRUU(전역적으로 경로 지정 가능한 사용자 에이전트 URI) 설정을 검색할 수 있습니다.

이 cmdlet을 사용하여 신뢰할 수 있는 단일 응용 프로그램을 검색하려면 Identity 매개 변수 값을 제공해야 합니다. Identity는 응용 프로그램이 속해 있는 풀의 FQDN(정규화된 도메인 이름) 뒤에 슬래시(/)와 응용 프로그램 ID가 오는 형식으로 구성됩니다. 예를 들어 TrustPool.litwareinc.com/tapp2의 경우 TrustPool.litwareinc.com은 풀 FQDN이고, tapp2는 응용 프로그램 ID입니다. 이 cmdlet을 사용하여 응용 프로그램을 검색하면 TrustPool.litwareinc.com/urn:application:tapp2와 유사한 ID가 표시됩니다. 여기서 접두사 urn:application:이 응용 프로그램 이름(tapp2) 앞에 오는 것에 주의해야 합니다. 이 접두사는 Identity의 일부이므로 Identity 매개 변수 값을 지정할 때 별도로 입력하지 않아도 됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins, RTCUniversalServerAdmins, RTCUniversalReadOnlyAdmins 그룹의 구성원은 **Get-CsTrustedApplication** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsTrustedApplication\\b"}

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
<td><p>응용 프로그램의 이름입니다. 여기에는 응용 프로그램 ID 접두사를 포함할 수 있지만 필수는 아닙니다. 예를 들어 ApplicationId 값 urn:application:tapp1 및 tapp1은 모두 동일한 응용 프로그램을 반환합니다. ApplicationId 값을 제공한 경우 Identity 값은 제공할 수 없지만 TrustedApplicationPoolFqdn 매개 변수 값을 제공해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>와일드카드가 포함된 문자열로서, 이 문자열과 일치하는 ID 값을 기반으로 신뢰할 수 있는 응용 프로그램을 검색할 수 있습니다. ID는 신뢰할 수 있는 응용 프로그램 풀 FQDN 뒤에 슬래시(/)와 신뢰할 수 있는 응용 프로그램 ID가 차례로 오는 형식으로 구성됩니다. Filter 값은 FQDN 또는 응용 프로그램 ID에 적용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.ExternalApplicationIdentity</p></td>
<td><p>검색할 신뢰할 수 있는 응용 프로그램의 고유 식별자입니다. Identity 값은 &lt;풀 FQDN&gt;/&lt;응용 프로그램 ID&gt; 형식으로 입력해야 합니다. 여기서 풀 FQDN은 응용 프로그램이 있는 풀의 FQDN이고, 응용 프로그램 ID는 응용 프로그램 이름입니다. Identity를 지정한 경우에는 ApplicationID 또는 TrustedApplicationPoolFqdn을 지정할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>TrustedApplicationPoolFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>응용 프로그램이 있는 신뢰할 수 있는 응용 프로그램 풀의 FQDN입니다. TrustedApplicationPoolFqdn 값을 제공한 경우 Identity 값은 제공할 수 없지만 ApplicationID 매개 변수 값을 제공해야 합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

Microsoft.Rtc.Management.Xds.DisplayTrustedApplication 유형의 개체를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsTrustedApplication](new-cstrustedapplication.md)  
[Remove-CsTrustedApplication](remove-cstrustedapplication.md)  
[Set-CsTrustedApplication](set-cstrustedapplication.md)

