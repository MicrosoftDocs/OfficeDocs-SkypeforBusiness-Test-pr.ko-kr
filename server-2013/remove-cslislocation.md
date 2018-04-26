---
title: Remove-CsLisLocation
TOCTitle: Remove-CsLisLocation
ms:assetid: 24e49a83-01a9-48ce-b940-fb0503f52077
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425722(v=OCS.15)
ms:contentKeyID: 49303072
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsLisLocation

 

_**마지막으로 수정된 항목:** 2015-03-09_

E9-1-1(Enhanced 9-1-1)에 대한 위치 구성 데이터베이스에서 위치를 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsLisLocation [-City <String>] [-CompanyName <String>] [-Country <String>] [-HouseNumber <String>] [-HouseNumberSuffix <String>] [-Location <String>] [-PostalCode <String>] [-PostDirectional <String>] [-PreDirectional <String>] [-State <String>] [-StreetName <String>] [-StreetSuffix <String>] <COMMON PARAMETERS>

    Remove-CsLisLocation -City <String> -CompanyName <String> -Country <String> -HouseNumber <String> -HouseNumberSuffix <String> -Location <String> -PostalCode <String> -PostDirectional <String> -PreDirectional <String> -State <String> -StreetName <String> -StreetSuffix <String> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 Bldg30NEWing이라는 위치를 제거합니다. 이 명령은 Location, HouseNumber, StreetName, City, State 및 Country 매개 변수의 값을 지정합니다. 즉, 이러한 매개 변수는 삭제할 위치의 속성 중 null이 아닌 값을 포함하는 유일한 속성입니다. null이 아닌 모든 속성에 대해 매개 변수 값을 제공하지 않으면 위치가 삭제되지 않습니다. 명령에서 지정하지 않은 매개 변수에 대한 메시지가 표시되지만 해당 매개 변수가 null 값을 포함하는 경우 각 프롬프트에서 Enter 키만 누르면 됩니다.

    Remove-CsLisLocation -Location Bldg30NEWing -HouseNumber 1000 -StreetName Main -City Redmond -State WA -Country US

## 예제 2

이 예제에서는 LIS 포트, 서브넷, 스위치 또는 무선 액세스 지점에서 참조되지 않는 모든 위치를 제거합니다. 먼저 Unreferenced 매개 변수를 지정하여 **Get-CsLisLocation** cmdlet을 호출합니다. 이렇게 하면 LIS 포트, 서브넷, 스위치 또는 무선 액세스 지점에서 참조되지 않는 모든 위치 컬렉션이 반환됩니다. 그런 다음 이 컬렉션은 컬렉션의 각 위치를 제거하는 **Remove-CsLisLocation** cmdlet에 파이프됩니다.

    Get-CsLisLocation -Unreferenced | Remove-CsLisLocation

## 자세한 정보

E9-1-1은 긴급 통화를 받는 사람이 발신자에게 묻지 않고도 발신자의 지리적 위치를 확인할 수 있도록 지원합니다. Lync Server에서는 발신자의 포트, 서브넷, 스위치 또는 무선 액세스 지점을 특정 위치에 매핑하여 위치를 확인합니다. 이 cmdlet은 위치 구성 데이터베이스에서 위치를 제거합니다. 위치의 모든 속성이 결합되어 위치를 고유하게 하므로 위치를 제거하려면 해당 위치의 null이 아닌 속성을 모두 입력해야 합니다. 제거할 위치의 null이 아닌 속성을 모두 입력하지 않으면 지정한 속성만 포함된 다른 위치가 없는 경우 위치가 제거되지 않습니다. 이 경우 오류가 표시되지는 않지만 작업이 수행되지 않습니다.

이 cmdlet은 LIS(Location Information Server) 포트, 서브넷, 스위치 또는 무선 액세스 지점에 연결된 위치를 제거하지 않습니다. 이러한 장치에서 참조되는 위치를 제거하려고 하면 오류가 표시됩니다. 위치를 제거하기 전에 모든 참조를 제거해야 합니다. **Remove-CsLisPort** cmdlet, **Remove-CsLisSubnet** cmdlet, **Remove-CsLisSwitch** cmdlet 및 **Remove-CsLisWirelessAccessPoint** cmdlet을 사용하여 이러한 참조를 제거할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsLisLocation** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsLisLocation"}

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
<td><p>위치의 구/군/시입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>CompanyName</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>이 위치에 있는 회사의 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Country</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>이 위치가 있는 국가/지역입니다. 이 값에는 2자 이하가 포함됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>HouseNumber</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>위치의 번지입니다. 회사의 경우 회사가 위치한 거리의 번지를 의미합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>HouseNumberSuffix</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>1/2 또는 A와 같은 집 번지 수에 대한 추가 정보입니다(예: 1234 1/2 Oak Street 또는 1234 A Elm Street).</p></td>
</tr>
<tr class="even">
<td><p><em>Location</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>이 위치의 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PostalCode</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>이 위치와 연결된 우편 번호입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PostDirectional</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>거리 이름의 방향 표시입니다(예: Main Street NE 또는 7th Avenue NW의 NE 또는 NW).</p></td>
</tr>
<tr class="odd">
<td><p><em>PreDirectional</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>거리 이름 앞에 오는 거리 이름의 방향 표시입니다(예: NE Main Street 또는 NW 7th Avenue의 NE 또는 NW).</p></td>
</tr>
<tr class="even">
<td><p><em>State</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>이 위치와 연결된 시 또는 도입니다. 이 값은 2자 이하입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>StreetName</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>이 위치가 속한 거리 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>StreetSuffix</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>거리 이름에 지정된 거리 유형입니다(예: Street, Avenue 또는 Court).</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
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

LIS 위치 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값이나 개체를 반환하지 않고 System.Management.Automation.PSCustomObject 유형의 개체를 제거합니다.

## 참고 항목

#### 기타 리소스

[Set-CsLisLocation](set-cslislocation.md)  
[Get-CsLisLocation](get-cslislocation.md)  
[Remove-CsLisPort](remove-cslisport.md)  
[Remove-CsLisSubnet](remove-cslissubnet.md)  
[Remove-CsLisSwitch](remove-cslisswitch.md)  
[Remove-CsLisWirelessAccessPoint](remove-csliswirelessaccesspoint.md)  
[Get-CsLisCivicAddress](get-csliscivicaddress.md)

