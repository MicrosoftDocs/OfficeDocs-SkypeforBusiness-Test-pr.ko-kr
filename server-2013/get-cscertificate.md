---
title: Get-CsCertificate
TOCTitle: Get-CsCertificate
ms:assetid: 15b8f019-1d00-4389-9abe-18deb8cbf2ea
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398227(v=OCS.15)
ms:contentKeyID: 49302916
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsCertificate

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server에서 사용하도록 구성된 로컬 컴퓨터의 인증서에 대한 정보를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsCertificate [-Identity <XdsIdentity>] [-Report <String>] [-Type <CertType[]>]

## 예제

## 예제 1

예제 1에 표시된 명령은 Lync Server 구성 요소에 현재 할당된 모든 인증서에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 **Get-CsCertificate** cmdlet이 추가 매개 변수 없이 호출됩니다.

    Get-CsCertificate

## 예제 2

예제 2에서는 내부 웹 서비스에 사용되는 모든 Lync Server 인증서를 검색합니다. 이 작업을 수행하기 위해 Type 매개 변수가 매개 변수 값 WebServicesInternal과 함께 포함됩니다.

    Get-CsCertificate -Type WebServicesInternal

## 예제 3

예제 3에서는 2012년 9월 1일 이전에 만료되는 모든 Lync Server 인증서를 반환합니다. 먼저 현재 사용 중인 모든 Lync Server 인증서 컬렉션을 반환하기 위해 **Get-CsCertificate** cmdlet이 사용됩니다. 이 컬렉션은 2012년 9월 1일 이전에 만료되는 인증서만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 이 예제에 지정된 날짜(9/1/2012)는 날짜-시간 값에 영어(미국) 형식을 사용합니다. 날짜는 사용자의 국가 및 언어 옵션과 호환되는 형식을 사용하여 지정해야 합니다.

    Get-CsCertificate | Where-Object {$_.NotAfter -lt "9/1/2012"}

## 예제 4

예제 4에서는 MyCa CA(인증 기관)에서 발급한 모든 Lync Server 인증서에 대한 정보를 반환합니다. 먼저 현재 사용 중인 모든 인증서 컬렉션을 반환하기 위해 **Get-CsCertificate** cmdlet이 매개 변수 없이 호출됩니다. 이 컬렉션은 **Where-Object** cmdlet에 파이프되며, 여기서 Issuer 속성이 "Cn=MyCa"와 같은(-eq) 모든 인증서가 선택됩니다.

    Get-CsCertificate | Where-Object {$_.Issuer -eq "Cn=MyCa"}

## 예제 5

예제 5에 표시된 명령은 Subject 속성이 CN=atl-cs-001.litwareinc.com으로 설정된 모든 Lync Server 인증서를 반환합니다. 이 작업을 수행하기 위해 **Get-CsCertificate** cmdlet을 사용하여 모든 Lync Server 인증서 컬렉션을 반환한 다음 해당 컬렉션을 **Where-Object** cmdlet에 파이프합니다. **Where-Object** cmdlet은 Subject 속성이 "CN=atl-cs-001.litwareinc.com"과 같은 인증서만 선택합니다.

    Get-CsCertificate | Where-Object {$_.Subject -eq "CN=atl-cs-001.litwareinc.com"}

## 자세한 정보

Lync Server에서는 서버 및 서버 역할의 ID를 확인하는 방법으로 인증서를 사용합니다. 예를 들어 에지 서버는 인증서를 사용하여 현재 통신 중인 컴퓨터가 실제 프런트 엔드 서버인지 확인하며, 그 반대의 경우도 마찬가지입니다. Lync Server를 완벽하게 구현하려면 적절한 서버 역할에 적절한 인증서를 할당해야 합니다.

**Get-CsCertificate** cmdlet을 통해 Lync Server에서 사용하도록 구성된 인증서에 대한 자세한 정보를 검색할 수 있습니다. 이 cmdlet은 Lync Server 인증서에 대한 정보만 반환합니다. 인증서가 **Set-CsCertificate** cmdlet을 사용하여 Lync Server에서 사용하도록 구성된 경우에는 **Get-CsCertificate** cmdlet을 실행할 때 해당 인증서가 반환되지 않습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsCertificate** cmdlet을 로컬로 실행할 수 있습니다.

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
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>전역 범위에서 구성된 인증서를 검색할 수 있습니다. 전역 인증서는 복사되어 해당하는 컴퓨터에 배포됩니다. 전역 인증서에 대한 정보를 반환하려면 다음 구문을 사용합니다.</p>
<p>Get-CsCertificate –Identity &quot;global&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p><strong>Get-CsCertificate</strong> cmdlet에서 수행하는 절차에 대한 자세한 정보를 기록할 수 있습니다. 매개 변수 값은 생성될 HTML 파일의 전체 경로여야 합니다(예: -Report C:\Logs\Certificates.html). 지정된 파일이 이미 있는 경우에는 자동으로 새 정보로 덮어씁니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Type</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.CertType[]</p></td>
<td><p>요청되는 인증서 유형입니다. 인증서 유형의 예를 들면 다음과 같습니다.</p>
<p>AccessEdgeExternal</p>
<p>AudioVideoAuthentication</p>
<p>DataEdgeExternal</p>
<p>Default</p>
<p>External</p>
<p>Internal</p>
<p>iPhoneAPNService</p>
<p>iPadAPNService</p>
<p>MPNService</p>
<p>PICWebService(Microsoft Lync Online 2010에만 해당)</p>
<p>ProvisionService(Microsoft Lync Online 2010에만 해당)</p>
<p>WebServicesExternal</p>
<p>WebServicesInternal</p>
<p>WsFedTokenTransfer</p>
<p>예를 들어 -Type Default 구문은 Default 인증서에 대한 정보를 반환합니다.</p>
<p>다음과 같이 인증서 유형을 쉼표로 구분하여 단일 명령에 여러 유형을 지정할 수 있습니다.</p>
<p>-Type Internal,External,Default</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsCertificate** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsCertificate** cmdlet은 Microsoft.Rtc.Management.Deployment.CertificateReference 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Import-CsCertificate](import-cscertificate.md)  
[Remove-CsCertificate](remove-cscertificate.md)  
[Request-CsCertificate](request-cscertificate.md)  
[Set-CsCertificate](set-cscertificate.md)

