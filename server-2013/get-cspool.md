---
title: Get-CsPool
TOCTitle: Get-CsPool
ms:assetid: e0911c68-9a0a-461a-88d6-c610c6cd996c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398992(v=OCS.15)
ms:contentKeyID: 49305291
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsPool

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 배포에서 사용되는 풀에 대한 정보를 반환합니다. 풀은 사이트에서 모두 동일한 Lync Server 서비스 집합을 실행하는 컴퓨터 컬렉션입니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsPool [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsPool [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Site <String>]

## 예제

## 예제 1

예제 1에서는 Lync Server 배포에서 찾은 모든 풀을 반환합니다.

    Get-CsPool

## 예제 2

예제 2에서는 각 풀에서 찾은 컴퓨터에 대한 자세한 정보를 표시합니다. 이 작업을 수행하기 위해 **Get-CsPool** cmdlet을 호출한 다음 반환된 데이터를 **Select-Object** cmdlet에 파이프합니다. ExpandProperty 매개 변수는 Computers 속성 값을 "확장"하는 데 사용됩니다. Computers 속성은 풀의 각 컴퓨터를 나타내는 개체 배열입니다. Computers 속성을 확장하면 이러한 각 컴퓨터에 대한 자세한 정보가 반환됩니다.

    Get-CsPool | Select-Object -ExpandProperty Computers

## 예제 3

예제 3에서는 Identity 매개 변수를 사용하여 반환되는 데이터를 ID가 atl-cs-001.litwareinc.com인 풀로 제한합니다.

    Get-CsPool -Identity atl-cs-001.litwareinc.com

## 예제 4

예제 4에서는 Redmond 사이트에서 찾은 모든 풀을 반환합니다. 이 작업을 수행하기 위해 명령은 Site 매개 변수를 사용합니다. 매개 변수 값 "Redmond"는 Site 속성이 Redmond와 같은 풀에 대한 데이터만 반환하도록 제한합니다.

    Get-CsPool -Site "Redmond"

## 예제 5

예제 5에 표시된 명령은 Lync Server 서비스가 설치되지 않은 모든 풀 컬렉션을 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsPool** cmdlet을 호출합니다. 그러면 조직에서 현재 사용 중인 모든 풀 컬렉션이 반환됩니다. 이 컬렉션은 Services.Count 속성이 0과 같은 모든 풀을 선택하는 **Where-Object** cmdlet에 파이프됩니다. Count가 0인 경우 해당 풀에 대해 구성된 Lync Server 서비스가 없다는 의미입니다.

    Get-CsPool | Where-Object {$_.Services.Count -eq 0}

## 자세한 정보

Lync Server에서 풀은 동일한 서비스 집합을 실행하는 동일한 사이트에 있는 하나 이상의 컴퓨터입니다. 예를 들어 Redmond 사이트에서 중재 서버 서비스를 실행하는 서버가 하나 있는 경우 중재 서버 풀은 컴퓨터 한 대로 구성되고, Redmond 사이트에서 중재 서버를 실행하는 서버가 두 대 있는 경우 중재 서버 풀은 컴퓨터 두 대로 구성됩니다. 조직에서 사용되는 풀의 수는 보유한 서버 수 및 이러한 서버에서 실행하는 여러 서비스에 따라 다릅니다.

**Get-CsPool** cmdlet을 사용하면 각 풀에서 실행 중인 서비스에 대한 정보를 포함하여 조직에서 사용 중인 각 풀에 대한 정보를 검색할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins, RTCUniversalServerAdmins, RTCUniversalReadOnlyAdmins 그룹의 구성원은 **Get-CsPool** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsPool"}

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
<td><p>와일드카드를 사용하여 반환할 풀의 ID를 지정하는 데 사용됩니다. 예를 들어 -Filter &quot;*.fabrikam.com&quot; 구문은 ID가 문자열 값 &quot;.fabrikam.com&quot;으로 끝나는 모든 풀을 반환합니다.</p>
<p>Filter 매개 변수와 Identity 매개 변수를 같은 명령에 함께 사용할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>반환할 풀의 FQDN(정규화된 도메인 이름)입니다(예: -Identity atl-cs-001.litwareinc.com).</p>
<p>이 매개 변수가 없으면 조직에서 사용하는 모든 풀이 반환됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Site</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>지정된 사이트에서 찾은 모든 풀을 반환합니다. 해당 사이트는 사이트 ID(예: site:Redmond) 대신 사이트의 표시 이름(예: Redmond)을 사용하여 참조해야 합니다(예: -Site &quot;Redmond&quot;). 다음 명령을 실행하여 사이트의 표시 이름을 검색할 수 있습니다.</p>
<p>Get-CsSite | Select-Object Identity, DisplayName</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsPool** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsPool** cmdlet은 Microsoft.Rtc.Management.Deploy.Internal.Cluster 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsSite](get-cssite.md)  
[Get-CsTopology](get-cstopology.md)

