---
title: Get-CsTrustedApplicationComputer
TOCTitle: Get-CsTrustedApplicationComputer
ms:assetid: 360796d8-48c7-4ce2-9bb4-1f8967562f24
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425843(v=OCS.15)
ms:contentKeyID: 49303279
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsTrustedApplicationComputer

 

_**마지막으로 수정된 항목:** 2015-03-09_

신뢰할 수 있는 응용 프로그램을 호스트하는 하나 이상의 컴퓨터에 대한 정보를 검색합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsTrustedApplicationComputer [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsTrustedApplicationComputer [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Local <SwitchParameter>] [-Pool <String>]

## 예제

## 예제 1

예제 1에서는 Lync Server 배포 내의 모든 신뢰할 수 있는 응용 프로그램 풀에 할당된 모든 컴퓨터를 검색합니다.

    Get-CsTrustedApplicationComputer

## 예제 2

예제 2에서는 FQDN이 Trust1.litwareinc.com인 컴퓨터에 대한 정보를 검색합니다.

    Get-CsTrustedApplicationComputer -Identity Trust1.litwareinc.com

## 예제 3

이 예제에서는 Filter 매개 변수를 사용하여 신뢰할 수 있는 응용 프로그램 풀에 할당되고 FQDN이 문자열 Trust로 시작하는 모든 컴퓨터에 대해 와일드카드 검색을 수행합니다. Filter 매개 변수는 모든 신뢰할 수 있는 응용 프로그램 컴퓨터의 Identity 속성을 검색합니다. 문자열 끝의 와일드카드 문자(\*)는 필터가 문자열 Trust로 시작하고 뒤에 아무 문자가 나오는 ID를 검색하도록 지정합니다.

    Get-CsTrustedApplicationComputer -Filter Trust*

## 예제 4

예제 4에서는 신뢰할 수 있는 응용 프로그램 풀 TrustPool.litwareinc.com에 할당된 모든 컴퓨터의 목록을 검색합니다.

    Get-CsTrustedApplicationComputer -Pool TrustPool.litwareinc.com

## 예제 5

예제 3에서는 Filter 매개 변수를 사용하여 ID(컴퓨터의 FQDN)에 대한 와일드카드 검색을 수행합니다. 이 예제에서도 와일드카드 검색을 수행하지만 이번에는 ID가 아닌 풀에 대한 검색을 수행합니다. 먼저 **Get-CsTrustedApplicationComputer** cmdlet을 호출하여 모든 신뢰할 수 있는 응용 프로그램 컴퓨터의 컬렉션을 검색합니다. 그런 다음 해당 컬렉션을 **Where-Object** cmdlet에 파이프합니다. **Where-Object** cmdlet은 파이프한 컬렉션의 범위를 좁히는 데 사용됩니다. 이 경우에는 litwareinc.com 도메인의 모든 풀에 있는 신뢰할 수 있는 응용 프로그램 컴퓨터만 남기려고 합니다. 이 작업을 수행하기 위해 컬렉션($\_.Pool)의 각 항목에서 Pool 속성이 와일드카드 문자열 \*.litwareinc.com과 일치(-like)하는지 확인합니다. 이 경우 임의의 문자로 시작하고 .litwareinc.com 문자열로 끝나는 값이 일치하게 됩니다.

    Get-CsTrustedApplicationComputer | Where-Object {$_.Pool -like "*.litwareinc.com"}

## 자세한 정보

Lync Server 배포 내에서 신뢰할 수 있는 응용 프로그램을 실행하는 컴퓨터는 신뢰할 수 있는 응용 프로그램 전용으로 사용되는 별도의 풀에 추가하는 것이 좋습니다. 그러나 다용도로 사용되는 기존 풀에 신뢰할 수 있는 응용 프로그램 컴퓨터를 추가할 수도 있습니다. 이 cmdlet을 사용하여 ID(FQDN)와 신뢰할 수 있는 응용 프로그램이 포함된 컴퓨터가 하나 이상 위치한 풀을 검색할 수 있습니다.

이 cmdlet을 사용하여 FQDN을 기준으로 컴퓨터를 검색하거나 지정한 풀에 속한 모든 컴퓨터를 검색할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsTrustedApplicationComputer** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsTrustedApplicationComputer"}

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
<td><p>와일드카드가 포함된 문자열로서, 이 문자열과 일치하는 ID 값을 기반으로 신뢰할 수 있는 컴퓨터를 검색할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>검색할 컴퓨터의 FQDN(정규화된 도메인 이름)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Local</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 로컬 컴퓨터에 대한 정보만 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Pool</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>컴퓨터 정보를 검색할 신뢰할 수 있는 응용 프로그램 풀의 FQDN입니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

Microsoft.Rtc.Management.Xds.DisplayComputer 유형의 개체를 한 개 이상 검색합니다.

## 참고 항목

#### 기타 리소스

[New-CsTrustedApplicationComputer](new-cstrustedapplicationcomputer.md)  
[Remove-CsTrustedApplicationComputer](remove-cstrustedapplicationcomputer.md)

