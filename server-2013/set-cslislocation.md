---
title: Set-CsLisLocation
TOCTitle: Set-CsLisLocation
ms:assetid: 955cdce0-250d-48b7-8891-5355d801911f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398757(v=OCS.15)
ms:contentKeyID: 49304426
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsLisLocation

 

_**마지막으로 수정된 항목:** 2015-03-09_

E9-1-1(Enhanced 9-1-1)에 대한 위치 구성 데이터베이스의 기존 위치를 수정하거나 새 위치를 만듭니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsLisLocation -Instance <PSObject> [-City <String>] [-CompanyName <String>] [-Country <String>] [-HouseNumber <String>] [-HouseNumberSuffix <String>] [-Location <String>] [-PostalCode <String>] [-PostDirectional <String>] [-PreDirectional <String>] [-State <String>] [-StreetName <String>] [-StreetSuffix <String>] <COMMON PARAMETERS>

    Set-CsLisLocation -City <String> -CompanyName <String> -Country <String> -HouseNumber <String> -HouseNumberSuffix <String> -Location <String> -PostalCode <String> -PostDirectional <String> -PreDirectional <String> -State <String> -StreetName <String> -StreetSuffix <String> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 Bldg30NEWing이라는 새 위치를 만듭니다. 이 명령은 위치를 만들기 위해 값을 가져야 하는 모든 매개 변수를 채웁니다. 이 예제에서 위치의 주소는 1000 Main, Redmond, WA, US입니다. 이 주소는 HouseNumber 매개 변수 값으로 1000, StreetName 매개 변수 값으로 Main, City 매개 변수 값으로 Redmond, 그리고 Country 매개 변수 값으로 US를 지정하여 입력됩니다.

여기 나온 매개 변수만 사용하여 명령을 실행할 경우 추가 매개 변수를 입력하라는 메시지가 표시됩니다. 그러나 각 메시지에서 값을 지정하지 않고 Enter 키를 누르기만 하면 위치가 만들어집니다.

    Set-CsLisLocation -Location Bldg30NEWing -HouseNumber 1000 -StreetName Main -City Redmond -State WA -Country US

## 예제 2

이 예제는 새 위치를 만든다는 측면에서 예제 1과 비슷합니다. 그러나 이 예제에서는 cmdlet에 대한 모든 매개 변수를 지정합니다. 이 예제에서는 비워 두려는 모든 값을 빈 문자열로 설정하므로 예제 1의 명령을 실행할 경우 표시되는 메시지가 표시되지 않습니다.

    Set-CsLisLocation -Location "Suite 100/Office 20" -CompanyName "Litware, Inc." -HouseNumber 1234 -HouseNumberSuffix "" -PreDirectional "" -StreetName Main -StreetSuffix St -PostDirectional "" -City Redmond -State WA -PostalCode 99999 -Country US

## 예제 3

이 예제에서는 예제 1에서 만든 위치를 수정합니다. 이 예제의 첫 번째 줄에서는 먼저 **Get-CsLisLocation** cmdlet을 호출합니다. 이렇게 하면 Lync Server 배포 내에 정의된 모든 위치가 반환됩니다. 이 컬렉션은 **Where-Object** cmdlet에 파이프됩니다. **Where-Object** cmdlet은 컬렉션에서 Location 속성이 Bldg30NEWing과 같은(-ceq, 대/소문자를 구별하여 동일함) 모든 항목을 검색합니다. 이 조건을 대조하는 개체는 변수 $a에 할당됩니다.

두 번째 줄에서는 **Set-CsLisLocation** cmdlet을 호출합니다. 첫 번째 매개 변수는 Instance 매개 변수입니다. 이 매개 변수에 첫 번째 줄에서 검색한 개체가 포함된 변수($a)를 전달합니다. 여기서는 이 개체를 수정하려고 합니다. 그런 다음 StreetSuffix 매개 변수를 지정하고 Street를 값으로 전달합니다. 이렇게 하면 변수 $a에 있는 위치의 StreetSuffix 속성 값이 Street로 변경됩니다.

Location은 고유한 속성이 아니므로 **Where-Object** cmdlet은 두 개 이상의 위치를 반환할 수 있습니다. 이 경우 이 예제는 작동하지 않습니다. 한 번에 여러 위치를 수정하려면 예제 4를 참조하십시오.

    $a = Get-CsLisLocation | Where-Object {$_.Location -ceq "Bldg30NEWing"}
    Set-CsLisLocation -Instance $a -StreetSuffix Street

## 예제 4

예제 4에서는 하나 이상의 위치 개체에서 StreetSuffix 속성을 수정합니다. 시작 부분은 예제 3과 거의 비슷합니다. 먼저 **Get-CsLisLocation** cmdlet을 호출하여 모든 위치를 검색합니다. Location 속성이 NorthCampus와 같은 위치만 포함하는 컬렉션으로 범위를 좁히는 **Where-Object** cmdlet으로 이 위치 컬렉션을 파이프합니다. 이 새 컬렉션은 변수 $a에 저장됩니다. 두 번째 줄에서 $a의 내용을 **Set-CsLisLocation** cmdlet에 파이프합니다. 이 cmdlet은 $a에 저장된 각 개체(각 위치)를 거치면서 해당 개체를 수정합니다. 이 경우 수정은 각 개체의 StreetSuffix 속성을 Avenue로 변경하는 것입니다.

이 예제의 명령은 변수를 사용하지 않고도 수행할 수 있습니다. 다음과 같이 **Where-Object** cmdlet 명령의 결과를 **Set-CsLisLocation** cmdlet에 파이프하기만 하면 됩니다.

Get-CsLisLocation | Where-Object {$\_.Location -ceq "NorthCampus"} | Set-CsLisLocation -StreetSuffix Avenue

    $a = Get-CsLisLocation | Where-Object {$_.Location -ceq "NorthCampus"}
    $a | Set-CsLisLocation -StreetSuffix Avenue

## 자세한 정보

E9-1-1은 긴급 통화를 받는 사람이 호출자에게 위치 정보를 묻지 않고도 호출자의 지리적 위치를 확인할 수 있도록 합니다. Lync Server에서 위치는 특정 위치에 대한 호출자의 포트, 서브넷, 스위치 또는 무선 액세스 지점 매핑을 기반으로 확인됩니다. 이 맵을 와이어맵(wiremap)이라고 합니다. 이 cmdlet은 LIS(위치 정보 서버)의 위치 구성 데이터베이스에 저장된 위치 목록에 있는 기존 주소를 수정하거나 새 주소를 추가합니다. 이후 이 위치는 회사와 연결된 응급 서비스 공급자가 제공하는 유효한 주소 목록과 대조됩니다.

이 cmdlet에 대한 모든 필수 매개 변수의 조합(Instance 제외)은 고유한 항목을 구성합니다. 이러한 매개 변수 중 하나라도 변경되면 기존 위치가 수정되지 않고 새 위치가 만들어집니다. 이러한 매개 변수는 모두 필수 항목이지만 일부는 null 값을 포함할 수 있습니다. null이 아닌 값을 포함해야 하는 매개 변수는 Location, HouseNumber, StreetName, City, State 및 Country입니다. 기존 값을 수정하려면 Instance 매개 변수를 사용하거나 인스턴스를 cmdlet에 파이프해야 합니다.

이 cmdlet을 사용하여 위치를 만드는 것 외에 포트, 서브넷, 스위치 또는 무선 액세스 지점 정보에 대해 새 주소를 입력하는 경우에도 위치가 자동으로 만들어집니다. 이 정보는 **Set-CsLisPort** cmdlet, **Set-CsLisSubnet** cmdlet, **Set-CsLisSwitch** cmdlet 및 **Set-CsLisWirelessAccessPoint** cmdlet을 사용하여 입력할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsLisLocation** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsLisLocation"}

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
<td><p><em>City</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>위치의 구/군/시입니다.</p>
<p>최대 길이: 64자</p></td>
</tr>
<tr class="even">
<td><p><em>CompanyName</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>이 위치의 회사 이름입니다.</p>
<p>최대 길이: 60자</p></td>
</tr>
<tr class="odd">
<td><p><em>Country</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>이 위치가 속한 국가/지역입니다.</p>
<p>최대 길이: 2자</p></td>
</tr>
<tr class="even">
<td><p><em>HouseNumber</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>위치의 번지입니다. 회사의 경우 회사가 위치한 거리의 번지를 의미합니다.</p>
<p>최대 길이: 10자</p></td>
</tr>
<tr class="odd">
<td><p><em>HouseNumberSuffix</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>1/2 또는 A와 같은 번지에 대한 추가 정보입니다(예: 1234 1/2 Oak Street 또는 1234 A Elm Street).</p>
<p>참고: 아파트 번호 또는 사무실 호수를 지정하려면 Location 매개 변수를 사용해야 합니다(예: -Location &quot;Suite 100/Office 150&quot;).</p>
<p>최대 길이: 5자</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>필수</p></td>
<td><p>PS 개체</p></td>
<td><p>위치 개체에 대한 참조입니다. 이 개체에는 위치를 만드는 데 필요한 속성이 포함되어야 합니다. <strong>Get-CsLisLocation</strong> cmdlet을 호출하여 이 유형의 개체를 검색할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Location</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>이 위치의 이름입니다. 일반적으로 이 값은 구/군/시 주소보다 더 구체적인 위치 이름이지만(예: 사무실 번호) 어떠한 문자열 값이라도 될 수 있습니다.</p>
<p>최대 길이: 20자</p></td>
</tr>
<tr class="even">
<td><p><em>PostalCode</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>이 위치와 연결된 우편 번호입니다.</p>
<p>최대 길이: 10자</p></td>
</tr>
<tr class="odd">
<td><p><em>PostDirectional</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>거리 이름의 방향을 지정합니다(예: Main Street NE 또는 7th Avenue NW에서 NE 또는 NW).</p>
<p>최대 길이: 2자</p></td>
</tr>
<tr class="even">
<td><p><em>PreDirectional</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>거리 이름 앞에 오는 거리 이름의 방향을 지정합니다(예: (예: NE Main Street 또는 NW 7th Avenue의 NE 또는 NW).</p>
<p>최대 길이: 2자</p></td>
</tr>
<tr class="odd">
<td><p><em>State</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>이 위치와 연결된 시/도입니다.</p>
<p>최대 길이: 2자</p></td>
</tr>
<tr class="even">
<td><p><em>StreetName</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>이 위치의 거리 이름입니다.</p>
<p>최대 길이: 60자</p></td>
</tr>
<tr class="odd">
<td><p><em>StreetSuffix</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>거리 이름에 지정된 도로의 유형입니다(예: Street, Avenue 또는 Court).</p>
<p>최대 길이: 10자</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

LIS 위치 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값 또는 개체를 반환하지 않습니다. System.Management.Automation.PSCustomObject 유형의 개체를 만들거나 수정합니다.

## 참고 항목

#### 기타 리소스

[Remove-CsLisLocation](remove-cslislocation.md)  
[Get-CsLisLocation](get-cslislocation.md)  
[Set-CsLisPort](set-cslisport.md)  
[Set-CsLisSubnet](set-cslissubnet.md)  
[Set-CsLisSwitch](set-cslisswitch.md)  
[Set-CsLisWirelessAccessPoint](set-csliswirelessaccesspoint.md)  
[Get-CsLisCivicAddress](get-csliscivicaddress.md)

