---
title: Get-CsComputer
TOCTitle: Get-CsComputer
ms:assetid: 493931a9-1670-4a76-abba-7d3c7723d2e1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425959(v=OCS.15)
ms:contentKeyID: 49303527
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsComputer

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 인프라 내에서 서비스 역할을 수행하는 컴퓨터에 대한 정보를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsComputer [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsComputer [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Local <SwitchParameter>] [-Pool <String>]

## 예제

## 예제 1

예제 1에서는 **Get-CsComputer** cmdlet을 사용하여 Lync Server 인프라 내에서 서비스 역할을 수행하는 모든 컴퓨터에 대한 정보를 반환합니다.

    Get-CsComputer

## 예제 2

예제 2에 표시된 명령은 Filter 매개 변수를 사용하여 litwareinc.com 도메인에 속하는 서비스 역할 컴퓨터만 반환합니다. 와일드카드 문자열 \*.litwareinc.com은 반환되는 정보를 FQDN이 문자열 값 ".litwareinc.com"으로 끝나는 컴퓨터로 제한합니다.

    Get-CsComputer -Filter "*.litwareinc.com"

## 예제 3

예제 3에서는 Identity 매개 변수를 사용하여 반환되는 정보를 FQDN이 atl-cs-001.litwareinc.com인 한 컴퓨터로 제한합니다.

    Get-CsComputer -Identity "atl-cs-001.litwareinc.com"

## 예제 4

예제 4에서는 Pool 매개 변수를 사용하여 atl-cs-001.litwareinc.com 풀에 있는 모든 컴퓨터에 대한 정보를 반환합니다.

    Get-CsComputer -Pool "atl-cs-001.litwareinc.com"

## 자세한 정보

**Get-CsComputer** cmdlet을 사용하면 Lync Server 서비스나 서버 역할을 실행하는 컴퓨터를 빠르게 식별할 수 있습니다. **Get-CsComputer** cmdlet을 매개 변수 없이 호출하면 Lync Server 서비스 또는 서버 역할을 실행하는 모든 컴퓨터의 컬렉션을 반환합니다. 이 컬렉션에는 각 컴퓨터의 ID, 풀 이름 및 FQDN(정규화된 도메인 이름)이 포함됩니다. 또는 Identity, Filter 또는 Pool과 같은 선택적인 매개 변수를 사용하여 반환되는 데이터를 단일 컴퓨터나 컴퓨터의 집합으로 제한할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsComputer** cmdlet을 로컬로 실행할 수 있습니다.

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
<td><p>반환된 컴퓨터의 ID를 지정할 때 와일드카드 문자를 활용하는 데 사용됩니다. 예를 들어 명령에 -Filter &quot;atl-*&quot;을 지정하면 ID가 문자열 값 &quot;atl-&quot;로 시작하는 모든 컴퓨터가 반환됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>반환할 컴퓨터의 FQDN입니다(예: -Identity &quot;atl-cs-001.litwareinc.com&quot;).</p>
<p>이 매개 변수가 지정되지 않은 경우 Lync Server를 실행하는 모든 컴퓨터가 반환됩니다.</p></td>
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
<td><p>Lync Server 풀의 FQDN입니다. 이 매개 변수를 사용하면 지정한 풀에 있는 모든 컴퓨터에 대한 정보가 반환됩니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsComputer** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsComputer** cmdlet은 Microsoft.Rtc.Management.Deploy.Internal.Machine 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Disable-CsComputer](disable-cscomputer.md)  
[Enable-CsComputer](enable-cscomputer.md)  
[Test-CsComputer](test-cscomputer.md)

