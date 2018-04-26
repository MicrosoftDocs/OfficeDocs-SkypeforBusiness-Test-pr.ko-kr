---
title: Get-CsTrustedApplicationPool
TOCTitle: Get-CsTrustedApplicationPool
ms:assetid: f8dc4ad7-fc32-482b-a1cb-5ba106df3344
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413055(v=OCS.15)
ms:contentKeyID: 49305607
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsTrustedApplicationPool

 

_**마지막으로 수정된 항목:** 2015-03-09_

신뢰할 수 있는 응용 프로그램을 호스트하는 컴퓨터를 포함하는 하나 이상의 풀에 대한 설정을 검색합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsTrustedApplicationPool [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsTrustedApplicationPool [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-PoolFqdn <String>]

## 예제

## 예제 1

예제 1에서는 Lync Server 배포 내에 신뢰할 수 있는 응용 프로그램 풀로 정의된 모든 풀을 검색합니다.

    Get-CsTrustedApplicationPool

## 예제 2

이 예제에서는 Identity 매개 변수를 사용하여 신뢰할 수 있는 응용 프로그램 풀을 하나만 검색합니다(이 경우 FQDN이 TrustPool.litwareinc.com인 풀).

    Get-CsTrustedApplicationPool -Identity TrustPool.litwareinc.com

## 예제 3

이 예제에서는 풀 FQDN에 TrustPool 사이트가 포함된 신뢰할 수 있는 응용 프로그램 풀을 모두 검색합니다. Filter 매개 변수에는 \*:TrustPool.\* 값을 사용합니다. 이 필터 문자열은 “:TrustPool.” 문자열이 포함된 모든 신뢰할 수 있는 응용 프로그램 풀의 Identity 값을 검색합니다. 예를 들어 이 명령은 Identity 값이 TrustedApplicationPool:TrustPool.litwareinc.com인 풀을 검색합니다.

    Get-CsTrustedApplicationPool -Filter *:TrustPool.*

## 예제 4

Filter 매개 변수는 Identity만을 기준으로 검색하는데, 신뢰할 수 있는 응용 프로그램 풀의 경우 이는 TrustedApplicationPool:\<FQDN\> 형식의 서비스 ID입니다. 이 예제에서는 \<사이트\>-ExternalServer-\<id\> 형식의 서비스 ID를 기준으로 풀을 검색합니다(예: Redmond1-ExternalServer-1). 이를 통해 특정 사이트에 있는 신뢰할 수 있는 풀을 찾을 수 있습니다. 이 예제에서는 먼저 모든 신뢰할 수 있는 응용 프로그램 풀의 컬렉션을 검색하는 **Get-CsTrustedApplicationPool** cmdlet을 매개 변수 없이 호출합니다. 이 컬렉션은 서비스 ID($\_.ServiceId)가 와일드카드 문자열 Redmond1\*와 일치하는(-like) 풀만 남도록 컬렉션 범위를 좁히는 **Where-Object** cmdlet에 파이프됩니다. 그러면 Redmond1-ExternalServer-1, Redmond1-ExternalServer-2 및 Redmond1-ExternalServer-3과 같이 Redmond1 문자열로 시작하는 FQDN을 가진 모든 신뢰할 수 있는 응용 프로그램 풀 컬렉션이 반환됩니다.

    Get-CsTrustedApplicationPool | Where-Object {$_.ServiceId -like "Redmond1*"}

## 자세한 정보

Lync Server 배포 내에서 신뢰할 수 있는 응용 프로그램을 실행하는 컴퓨터는 신뢰할 수 있는 응용 프로그램 전용으로 사용되는 별도의 풀에 추가하는 것이 좋습니다. 그러나 다용도로 사용되는 기존 풀에 신뢰할 수 있는 응용 프로그램 컴퓨터를 추가할 수도 있습니다. 이 cmdlet은 신뢰할 수 있는 응용 프로그램 풀로 정의된 하나 이상의 풀을 검색합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsTrustedApplicationPool** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 RBAC 역할의 목록을 가져오려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsTrustedApplicationPool"}

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
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>와일드카드 문자열과 일치하는 ID를 가진 풀을 검색하는 데 사용된 하나 이상의 와일드카드 문자를 포함하는 문자열입니다. 예를 들어 *Redmond* 문자열을 지정하면 Redmond 문자열이 포함된 ID를 가진 TrustedApplicationPool:Redmond.litwareinc.com과 같은 신뢰할 수 있는 응용 프로그램 풀이 모두 검색됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>설정을 검색할 풀의 FQDN(정규화된 도메인 이름) 또는 서비스 ID입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PoolFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>검색할 풀의 FQDN입니다. 이는 Identity 매개 변수와 동일하게 동작합니다. 단, Identity는 서비스 ID도 받는다는 점이 다릅니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

Microsoft.Rtc.Management.Xds.DisplayExternalServer 개체 유형을 한 개 이상 검색합니다.

## 참고 항목

#### 기타 리소스

[New-CsTrustedApplicationPool](new-cstrustedapplicationpool.md)  
[Remove-CsTrustedApplicationPool](remove-cstrustedapplicationpool.md)  
[Set-CsTrustedApplicationPool](set-cstrustedapplicationpool.md)

