---
title: Set-CsLisSubnet
TOCTitle: Set-CsLisSubnet
ms:assetid: e51ef9ec-c307-4046-b64b-f23b354713fc
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399016(v=OCS.15)
ms:contentKeyID: 49305343
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsLisSubnet

 

_**마지막으로 수정된 항목:** 2015-03-09_

LIS(위치 정보 서버) 서브넷을 만들거나 서브넷과 위치(해당 위치가 없는 경우 새 위치 생성) 간의 연결을 만들거나 기존 서브넷 및 연결된 해당 위치를 수정합니다. 서브넷과 위치 간 연결은 E9-1-1(Enhanced 9-1-1) Enterprise Voice 구현에서 발신자의 위치를 응급 서비스 운영자에게 알리는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsLisSubnet -Subnet <String> [-Description <String>] <COMMON PARAMETERS>

    Set-CsLisSubnet -Subnet <String> [-City <String>] [-CompanyName <String>] [-Country <String>] [-Description <String>] [-HouseNumber <String>] [-HouseNumberSuffix <String>] [-Location <String>] [-PostalCode <String>] [-PostDirectional <String>] [-PreDirectional <String>] [-State <String>] [-StreetName <String>] [-StreetSuffix <String>] <COMMON PARAMETERS>

    Set-CsLisSubnet -City <String> -CompanyName <String> -Country <String> -HouseNumber <String> -HouseNumberSuffix <String> -Location <String> -PostalCode <String> -PostDirectional <String> -PreDirectional <String> -State <String> -StreetName <String> -StreetSuffix <String> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 LIS 서브넷 위치 항목을 만들거나 업데이트합니다. 이 예제의 명령은 유일한 필수 매개 변수인 Subnet만 포함합니다. 이 예제의 Subnet 값은 IPv4 주소 192.10.10.0입니다.

이 예제는 아무런 주소 정보도 포함하지 않습니다. 위치 정보 서버에서 주소와 연결되지 않은 서브넷 항목을 만들 수 있습니다. 그러나 이 서브넷을 통해 경로 지정된 응급 통화는 정의된 포트 또는 스위치 위치에 따라 응급 운영자가 위치를 식별할 수 있을 만큼 충분한 정보를 포함하지 않을 수 있습니다.

중요: 이 Subnet 값을 가진 LIS 서브넷 위치가 이미 존재하는 경우 이 명령의 값으로 대체됩니다. 즉, 이 서브넷이 주소(실제 위치)와 연결된 경우 이 명령에 아무 위치 정보도 포함되지 않았으므로 해당 연결이 더 이상 존재하지 않습니다. 위치는 위치 데이터베이스에 여전히 존재하지만 이 서브넷과 연결되지는 않습니다.

    Set-CsLisSubnet -Subnet 192.10.10.0

## 자세한 정보

Enhanced 9-1-1을 통해 응급 운영자는 발신자에게 위치를 묻지 않고도 발신자 위치를 확인할 수 있습니다. 발신자가 VoIP(Voice over Internet Protocol) 연결을 통해 전화를 건 경우에는 여러 가지 연결 요소를 기반으로 정보를 추출해야 합니다. VoIP 관리자는 발신자의 위치를 확인하는 위치 맵(와이어맵(wiremap)이라고 함)을 구성해야 합니다. 이 cmdlet을 통해 관리자는 클라이언트가 연결된 서브넷에 실제 위치를 매핑할 수 있습니다.

Subnet 매개 변수는 이 cmdlet의 유일한 필수 매개 변수입니다. 이미 존재하는 서브넷 값을 입력하면 이 cmdlet에서 제공된 위치 매개 변수에 따라 해당 서브넷의 위치를 업데이트합니다. 서브넷이 없는 경우에는 새 서브넷 위치가 만들어집니다.

여기에 입력한 주소 매개 변수(Null 값 포함)와 정확히 일치하는 주소를 가진 위치가 위치 데이터베이스에 없는 경우 이 cmdlet과 함께 입력한 매개 변수에 따라 새 주소가 만들어집니다. **Get-CsLisLocation** cmdlet을 호출하여 위치 목록을 검색할 수 있습니다. **Set-CsLisSubnet** cmdlet은 위치 매개 변수를 요구하거나 묻지 않으므로 위치와 연결하지 않고 서브넷 항목을 만들 수 있습니다. 또한 이 cmdlet을 사용하여 유효하지 않은 위치를 만들 수도 있습니다. 유효한 위치는 최소한 Location, HouseNumber, StreetName, City, State 및 Country로 구성됩니다. 이러한 매개 변수 중 하나라도 지정하지 않으면 서브넷 설정 대신 사용할 수 있는 스위치, 포트 또는 무선 액세스 지점에 유효한 설정을 사용할 수 있는지 여부에 따라 지정된 서브넷에서 발신한 통화에 응급 운영자에게 필요한 정보가 포함되지 않을 수도 있습니다. 위치 매개 변수는 가능한 구체적이고 자세하게 입력하는 것이 좋습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsLisSubnet** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsLisSubnet"}

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
<td><p><em>Subnet</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>서브넷의 IP 주소입니다. 이 값은 IPv4 주소(192.0.2.0과 같은 마침표로 구분된 숫자)로 입력해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>City</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>위치의 구/군/시입니다.</p>
<p>최대 길이: 64자</p></td>
</tr>
<tr class="odd">
<td><p><em>CompanyName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 위치에 있는 회사의 이름입니다.</p>
<p>최대 길이: 60자</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Country</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 위치가 속한 국가/지역입니다.</p>
<p>최대 길이: 2자</p></td>
</tr>
<tr class="even">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 서브넷 위치에 대한 자세한 설명입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>HouseNumber</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>위치의 번지입니다. 회사의 경우 회사가 위치한 거리의 번지를 의미합니다.</p>
<p>최대 길이: 10자</p></td>
</tr>
<tr class="even">
<td><p><em>HouseNumberSuffix</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>1/2 또는 A와 같은 집 번지 수에 대한 추가 정보입니다(예: 1234 1/2 Oak Street 또는 1234 A Elm Street).</p>
<p>참고: 아파트 호 수 또는 사무실 호 수를 지정하려면 Location 매개 변수를 사용해야 합니다(예: -Location &quot;Suite 100/Office 150&quot;).</p>
<p>최대 길이: 5자</p></td>
</tr>
<tr class="odd">
<td><p><em>Location</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 위치의 이름입니다. 일반적으로 이 값은 구/군/시 주소(예: 사무실 호 수)보다 구체적인 위치의 이름이며 아무 문자열 값이나 지정할 수 있습니다.</p>
<p>최대 길이: 20자</p></td>
</tr>
<tr class="even">
<td><p><em>PostalCode</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 위치와 연결된 우편 번호입니다.</p>
<p>최대 길이: 10자</p></td>
</tr>
<tr class="odd">
<td><p><em>PostDirectional</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>거리 이름의 방향 표시입니다(예: Main Street NE 또는 7th Avenue NW의 NE 또는 NW).</p>
<p>최대 길이: 2자</p></td>
</tr>
<tr class="even">
<td><p><em>PreDirectional</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>거리 이름 앞에 오는 거리 이름의 방향 표시입니다(예: NE Main Street 또는 NW 7th Avenue의 NE 또는 NW).</p>
<p>최대 길이: 2자</p></td>
</tr>
<tr class="odd">
<td><p><em>State</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 위치와 연결된 시 또는 도입니다.</p>
<p>최대 길이: 2자</p></td>
</tr>
<tr class="even">
<td><p><em>StreetName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 위치가 속한 거리 이름입니다.</p>
<p>최대 길이: 60자</p></td>
</tr>
<tr class="odd">
<td><p><em>StreetSuffix</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>거리 이름에 지정된 거리 유형입니다(예: Street, Avenue 또는 Court).</p>
<p>최대 길이: 10자</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

LIS 서브넷 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 System.Management.Automation.PSCustomObject 유형의 개체를 만들거나 수정합니다.

## 참고 항목

#### 기타 리소스

[Remove-CsLisSubnet](remove-cslissubnet.md)  
[Get-CsLisSubnet](get-cslissubnet.md)  
[Get-CsLisLocation](get-cslislocation.md)

