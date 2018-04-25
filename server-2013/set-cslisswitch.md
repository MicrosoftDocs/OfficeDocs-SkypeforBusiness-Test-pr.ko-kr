---
title: Set-CsLisSwitch
TOCTitle: Set-CsLisSwitch
ms:assetid: ad2a1890-724a-4f9f-bd50-de0c9de86f8e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412823(v=OCS.15)
ms:contentKeyID: 49304711
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsLisSwitch

 

_**마지막으로 수정된 항목:** 2015-03-09_

LIS(위치 정보 서버) 스위치를 만들거나, 스위치와 위치(해당 위치가 없는 경우 새 위치 생성) 간의 연결을 만들거나, 기존 스위치 및 연결된 해당 위치를 수정합니다. 스위치와 위치 간의 연결은 E9-1-1(Enhanced 9-1-1) Enterprise Voice 구현에서 응급 서비스 운영자에게 발신자의 위치를 알리는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsLisSwitch -ChassisID <String> [-City <String>] [-CompanyName <String>] [-Country <String>] [-Description <String>] [-HouseNumber <String>] [-HouseNumberSuffix <String>] [-Location <String>] [-PostalCode <String>] [-PostDirectional <String>] [-PreDirectional <String>] [-State <String>] [-StreetName <String>] [-StreetSuffix <String>] <COMMON PARAMETERS>

    Set-CsLisSwitch -ChassisID <String> [-Description <String>] <COMMON PARAMETERS>

    Set-CsLisSwitch -City <String> -CompanyName <String> -Country <String> -HouseNumber <String> -HouseNumberSuffix <String> -Location <String> -PostalCode <String> -PostDirectional <String> -PreDirectional <String> -State <String> -StreetName <String> -StreetSuffix <String> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 LIS 스위치 위치 항목을 만들거나 업데이트합니다. 이 예제의 명령은 유일한 필수 매개 변수인 ChassisID만 포함합니다. ChassisID의 값은 스위치의 MAC 주소입니다(이 경우 99-99-99-99-99-99).

이 예제는 아무런 주소 정보도 포함하지 않습니다. 위치 정보 서버에서 주소와 연결되지 않은 스위치 항목을 만들 수 있습니다. 그러나 이 스위치를 통해 경로 지정된 응급 통화는 정의된 서브넷 또는 포트 위치에 따라 응급 운영자가 위치를 식별할 수 있을 만큼 충분한 정보를 포함하지 않을 수 있습니다.

중요: 이 ChassisID를 가진 LIS 스위치 위치가 이미 존재하는 경우 이 명령의 값으로 대체됩니다. 즉, 이 스위치가 주소(실제 위치)와 연결된 경우 이 명령에 아무 위치 정보도 포함되지 않았으므로 해당 연결이 더 이상 존재하지 않습니다. 위치는 위치 데이터베이스에 여전히 존재하지만 이 스위치와 연결되지는 않습니다.

    Set-CsLisSwitch -ChassisID 99-99-99-99-99-99

## 예제 2

예제 2에서는 주소 정보를 추가하여 예제 1에서 만든 스위치를 업데이트합니다. 실제로는 기존 항목을 삭제하고 새로운 이 항목으로 대체하는 것입니다. 위치 데이터베이스에 주소가 존재하지 않는 경우 이 cmdlet이 해당 위치를 만듭니다.

    Set-CsLisSwitch -ChassisID 99-99-99-99-99-99 -Location "30/1000" -HouseNumber 1234 -PreDirectional NE -StreetName First -StreetSuffix Avenue -City Redmond -State WA -Country US -PostalCode 99999

## 자세한 정보

Enhanced 9-1-1을 통해 응급 운영자는 발신자에게 위치를 묻지 않고도 발신자 위치를 확인할 수 있습니다. 발신자가 VoIP(Voice over Internet Protocol) 연결을 통해 전화를 건 경우에는 여러 가지 연결 요소를 기반으로 정보를 추출해야 합니다. VoIP 관리자는 발신자의 위치를 확인하는 위치 맵(와이어맵(wiremap)이라고 함)을 구성해야 합니다. 이 cmdlet을 통해 관리자는 클라이언트가 연결된 네트워크 스위치에 실제 위치를 매핑할 수 있습니다.

ChassisID 매개 변수는 이 cmdlet의 유일한 필수 매개 변수입니다. 이미 존재하는 ChassisID 값을 입력하면 이 cmdlet에서 제공된 위치 매개 변수에 따라 해당 스위치의 위치를 업데이트합니다. ChassisID가 없는 경우에는 새 스위치 위치가 만들어집니다.

여기에 입력한 주소 매개 변수(Null 값 포함)와 정확히 일치하는 주소를 가진 위치가 위치 데이터베이스에 없는 경우 이 cmdlet과 함께 입력한 매개 변수에 따라 새 주소가 만들어집니다. **Get-CsLisLocation** cmdlet을 호출하여 위치 목록을 검색할 수 있습니다. **Set-CsLisSwitch** cmdlet은 위치 매개 변수를 요구하거나 묻지 않으므로 위치와 연결하지 않고 스위치 항목을 만들 수 있습니다. 이 cmdlet으로 잘못된 위치를 생성할 수도 있습니다. 유효한 위치는 최소한 Location, HouseNumber, StreetName, City, State 및 Country로 구성됩니다. 이러한 매개 변수 중 하나라도 지정하지 않으면 스위치 설정 대신 사용할 수 있는 서브넷 또는 무선 액세스 지점에 유효한 설정을 사용할 수 있는지 여부에 따라 참조된 스위치에서 수신한 통화에 응급 운영자에게 필요한 정보가 포함되지 않을 수도 있습니다. 위치 매개 변수는 가능한 구체적이고 자세하게 입력하는 것이 좋습니다.

**Set-CsLisPort** cmdlet을 호출하여 스위치 항목을 만들 수도 있습니다. 기존 스위치 항목이 없는 ChassisID 값과 함께 **Set-CsLisPort** cmdlet을 호출한 경우 해당 스위치가 만들어집니다.

이러한 변경 내용은 [New-CsWebServiceConfiguration](new-cswebserviceconfiguration.md) cmdlet 또는 [Set-CsWebServiceConfiguration](set-cswebserviceconfiguration.md) cmdlet을 사용하여 MACResolverUrl 속성을 구성한 경우에만 적용됩니다. MACResolverUrl 속성은 IP 주소를 사용할 수 있고 해당 IP 주소로 연결된 네트워크 카드의 MAC(미디어 액세스 제어) 주소를 확인할 수 있는 웹 서비스에 대한 URL을 지정합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsLisSwitch** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsLisSwitch"}

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
<td><p><em>ChassisID</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>네트워크 스위치의 MAC(미디어 액세스 제어) 주소입니다. 이 값은 nn-nn-nn-nn-nn-nn 형식(예: 12-34-56-78-90-ab) 또는 IP 주소 형식이어야 합니다. 지정된 ChassisID 값을 가진 항목이 없는 경우 새 스위치 위치가 만들어지고, 지정된 ChassisID를 가진 항목이 있는 경우 해당 항목이 대체됩니다.</p></td>
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
<td><p>이 네트워크 스위치 위치에 대한 자세한 설명입니다.</p></td>
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
<p>참고: 아파트 호 수 또는 사무실 호 수를 지정하려면 Location 매개 변수를 사용해야 합니다 (예: -Location &quot;Suite 100/Office 150&quot;).</p>
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

LIS 스위치 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 System.Management.Automation.PSCustomObject 유형의 개체를 만들거나 수정합니다.

## 참고 항목

#### 기타 리소스

[Remove-CsLisSwitch](remove-cslisswitch.md)  
[Get-CsLisSwitch](get-cslisswitch.md)  
[Get-CsLisLocation](get-cslislocation.md)  
[Set-CsLisPort](set-cslisport.md)  
[Get-CsLisPort](get-cslisport.md)

