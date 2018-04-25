---
title: Set-CsLisPort
TOCTitle: Set-CsLisPort
ms:assetid: 8a8a8f95-9366-4d87-bf2a-9767e5eb9996
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398700(v=OCS.15)
ms:contentKeyID: 49304309
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsLisPort

 

_**마지막으로 수정된 항목:** 2015-03-09_

LIS(위치 정보 서버) 포트를 생성하거나, 포트와 위치 사이 연결을 생성하거나(해당 위치가 없는 경우 새 위치 생성), 기존 포트 및 연결된 위치를 수정합니다. 포트와 위치 간의 연결은 E9-1-1(Enhanced 9-1-1) Enterprise Voice 구현에서 응급 서비스 운영자에게 발신자의 위치를 알리는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsLisPort -ChassisID <String> -PortID <String> [-City <String>] [-CompanyName <String>] [-Country <String>] [-Description <String>] [-HouseNumber <String>] [-HouseNumberSuffix <String>] [-Location <String>] [-PortIDSubType <InterfaceAlias | InterfaceName | LocallyAssigned>] [-PostalCode <String>] [-PostDirectional <String>] [-PreDirectional <String>] [-State <String>] [-StreetName <String>] [-StreetSuffix <String>] <COMMON PARAMETERS>

    Set-CsLisPort -ChassisID <String> -PortID <String> [-Description <String>] [-PortIDSubType <InterfaceAlias | InterfaceName | LocallyAssigned>] <COMMON PARAMETERS>

    Set-CsLisPort -City <String> -CompanyName <String> -Country <String> -HouseNumber <String> -HouseNumberSuffix <String> -Location <String> -PostalCode <String> -PostDirectional <String> -PreDirectional <String> -State <String> -StreetName <String> -StreetSuffix <String> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 LIS 포트 위치 항목을 생성하거나 업데이트합니다. 이 예제의 명령에는 세 개의 매개 변수 ChassisID, PortID 및 PortIDSubtype이 포함됩니다. ChassisID 값은 MAC 주소 99-99-99-99-99-99이고, PortID 값은 4200이고, PortIDSubType 값은 1입니다. PortIDSubType의 값 1은 InterfaceAlias 값으로 변환됩니다. 이 매개 변수 및 값을 -PortIDSubType InterfaceAlias와 같이 입력할 수도 있습니다. 포트 위치의 고유한 인스턴스를 생성하려면 이러한 세 개의 매개 변수가 필요합니다.

이 예제는 아무 주소 정보도 포함하지 않습니다. 주소와 연결하지 않고 위치 정보 서버에서 포트 항목을 생성할 수 있습니다. 그러나 이 포트를 통해 경로가 지정된 응급 통화에는 응급 운영자가 위치를 식별할 수 있는 충분한 정보가 포함되지 않을 수 있습니다(정의된 서브넷 또는 스위치 위치에 따라).

중요: 이 키 조합의 LIS 포트 위치가 이미 존재하는 경우 이 명령의 값으로 바뀝니다. 즉, 이 포트가 주소(실제 위치)와 연결된 경우 이 명령에 위치 정보를 포함하지 않았으므로 해당 연결은 더 이상 존재하지 않습니다. 위치는 위치 데이터베이스에 있지만 이 포트와 연결되지 않습니다.

    Set-CsLisPort -ChassisID 99-99-99-99-99-99 -PortID 4200 -PortIDSubType 1

## 예제 2

예제 2에서는 주소 정보를 추가하여 예제 1에서 생성된 포트를 업데이트합니다. 위치 데이터베이스에 주소가 존재하지 않는 경우 이 cmdlet이 해당 위치를 만듭니다.

    Set-CsLisPort -ChassisID 99-99-99-99-99-99 -PortID 4200 -PortIdSubType 1 -Location "30/1000" -HouseNumber 1234 -PreDirectional NE -StreetName First -StreetSuffix Avenue -City Redmond -State WA -Country US -PostalCode 99999

## 예제 3

이 예제에서는 MAC 주소(ChassisID) 99-99-99-99-99-88이 포함된 포트에 대해 정의된 모든 위치를 업데이트합니다. 이 예제의 첫 번째 줄은 먼저 **Get-CsLisPort** cmdlet을 호출하여 LIS 서비스에 정의된 모든 포트를 검색합니다. 이 포트 컬렉션은 컬렉션에서 ChassisID가 99-99-99-99-99-88과 같은(-eq) 모든 항목을 찾는 **Where-Object** cmdlet에 파이프됩니다. ChassisID 99-99-99-99-99-88이 포함된 이 포트 컬렉션은 변수 $a에 할당됩니다.

이 예제의 두 번째 줄에서는 변수 $a의 내용(ChassisID 99-99-99-99-99-88이 포함된 LIS 포트 컬렉션)을 **Set-CsLisPort** cmdlet에 파이프합니다. 이 cmdlet은 해당 컬렉션의 각 항목을 가져오고 지정된 매개 변수(Location, HouseNumber, StreetName, StreetSuffix, City, State, Country 및 PostalCode)의 값을 사용하여 업데이트합니다.

    $a = Get-CsLisPort | Where-Object {$_.ChassisID -eq "99-99-99-99-99-88"}
    $a | Set-CsLisPort -Location "30/1000" -HouseNumber 1234 -StreetName First -StreetSuffix Avenue -City Redmond -State WA -Country US -PostalCode 99999

## 자세한 정보

Enhanced 9-1-1을 통해 응급 운영자는 발신자에게 위치를 묻지 않고도 발신자 위치를 확인할 수 있습니다. 발신자가 VoIP(Voice over Internet Protocol) 연결을 통해 전화를 건 경우에는 여러 가지 연결 요소를 기반으로 정보를 추출해야 합니다. VoIP 관리자는 발신자의 위치를 확인하는 위치 맵(와이어맵(wiremap)이라고 함)을 구성해야 합니다. 관리자는 이 cmdlet을 사용하여 실제 위치를 클라이언트가 연결된 포트에 매핑합니다.

ChassisID, PortID 및 PortIDSubType의 조합으로 고유한 포트 위치가 생성됩니다. 이미 존재하는 ChassisID/PortID/PortIDSubType 키 조합을 입력할 경우 이 cmdlet은 제공되는 위치 매개 변수에 따라 해당 포트의 위치를 업데이트합니다. 키 조합이 존재하지 않는 경우 새 포트 위치가 생성됩니다.

여기에 입력한 주소 매개 변수(Null 값 포함)와 정확히 일치하는 주소를 가진 위치가 위치 데이터베이스에 없는 경우 이 cmdlet과 함께 입력한 매개 변수에 따라 새 주소가 만들어집니다. **Get-CsLisLocation** cmdlet을 호출하여 위치 목록을 검색할 수 있습니다. **Set-CsLisPort** cmdlet은 위치 매개 변수를 요구하거나 묻지 않으므로 위치와 연결하지 않고 포트 항목을 만들 수 있습니다. 이 cmdlet으로 잘못된 위치를 생성할 수도 있습니다. 유효한 위치는 최소한 Location, HouseNumber, StreetName, City, State 및 Country로 구성됩니다. 이러한 매개 변수를 모두 제공하지 않으면, 참조되는 포트에서 수신한 통화에 응급 운영자에게 필요한 정보가 포함되지 않을 수 있습니다(포트 설정 대신 사용할 수 있는 스위치, 서브넷 또는 무선 액세스 지점에 대한 올바른 설정을 사용할 수 있는지 여부에 따라). 위치 매개 변수는 가능한 구체적이고 자세하게 입력하는 것이 좋습니다.

이 cmdlet의 필수 매개 변수 중 하나는 ChassisID입니다. ChassisID는 포트 네트워크 스위치의 MAC(미디어 액세스 제어) 주소입니다. 위치 데이터베이스에 이 스위치가 없는 경우 이 cmdlet은 해당 스위치를 생성합니다. **Get-CsLisSwitch** cmdlet을 호출하여 기존 스위치를 검색할 수 있습니다. 새 스위치 항목이 생성되지만 해당 스위치는 **Set-CsLisPort** cmdlet을 사용하여 입력된 위치 정보와 자동으로 연결되지 않습니다. **Set-CsLisSwitch** cmdlet을 사용하여 스위치 위치를 설정해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsLisPort** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsLisPort"}

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
<td><p>포트 스위치의 MAC 주소입니다. 이 값은 nn-nn-nn-nn-nn-nn 형식(예: 12-34-56-78-90-ab)이거나 IP 주소여야 합니다. ChassisID, PortID 및 PortIDSubType의 조합이 고유한 경우 새 포트 위치가 생성됩니다. 이 조합이 고유하지 않은 경우 해당 키 조합이 포함된 포트 위치는 명령으로 제공된 매개 변수 값을 사용하여 업데이트됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PortID</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>이 위치와 연결된 포트의 ID입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>City</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 포트의 위치 구/군/시입니다.</p>
<p>최대 길이: 64자</p></td>
</tr>
<tr class="even">
<td><p><em>CompanyName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 위치에 있는 회사의 이름입니다.</p>
<p>최대 길이: 60자</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Country</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 포트가 있는 국가/지역입니다.</p>
<p>최대 길이: 2자</p></td>
</tr>
<tr class="odd">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 포트 위치의 세부 설명입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>HouseNumber</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>포트 위치의 번지입니다. 회사의 경우 회사가 위치한 거리의 번지를 의미합니다.</p>
<p>최대 길이: 10자</p></td>
</tr>
<tr class="odd">
<td><p><em>HouseNumberSuffix</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>1/2 또는 A와 같은 집 번지 수에 대한 추가 정보입니다(예: 1234 1/2 Oak Street 또는 1234 A Elm Street).</p>
<p>참고: 아파트 호 수 또는 사무실 호 수를 지정하려면 Location 매개 변수를 사용해야 합니다(예: -Location &quot;Suite 100/Office 150&quot;).</p>
<p>최대 길이: 5자</p></td>
</tr>
<tr class="even">
<td><p><em>Location</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 위치의 이름입니다. 일반적으로 이 값은 구/군/시 주소(예: 사무실 호 수)보다 구체적인 위치의 이름이며 아무 문자열 값이나 지정할 수 있습니다.</p>
<p>최대 길이: 20자</p></td>
</tr>
<tr class="odd">
<td><p><em>PortIDSubType</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Lis.PortIDSubType</p></td>
<td><p>포트의 하위 유형입니다. 이 값은 숫자 값 또는 문자열로 입력할 수 있지만 유효한 하위 유형이어야 합니다. 사용할 수 있는 하위 유형은 다음과 같습니다.</p>
<p>1: InterfaceAlias</p>
<p>5: InterfaceName</p>
<p>7: LocallyAssigned</p>
<p>기본값: 7(LocallyAssigned)</p></td>
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
<td><p>거리 이름 앞에 오는 거리 이름의 방향 표시입니다 (예: NE Main Street 또는 NW 7th Avenue의 NE 또는 NW).</p>
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

LIS 포트 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 System.Management.Automation.PSCustomObject 유형의 개체를 만들거나 수정합니다.

## 참고 항목

#### 기타 리소스

[Remove-CsLisPort](remove-cslisport.md)  
[Get-CsLisPort](get-cslisport.md)  
[Get-CsLisLocation](get-cslislocation.md)  
[Get-CsLisSwitch](get-cslisswitch.md)

