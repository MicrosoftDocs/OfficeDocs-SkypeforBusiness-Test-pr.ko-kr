---
title: 위치 데이터베이스 채우기
TOCTitle: 위치 데이터베이스 채우기
ms:assetid: fb84f5b6-c991-4893-bdbf-f195b4b7d28e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413069(v=OCS.15)
ms:contentKeyID: 49305609
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 위치 데이터베이스 채우기

 

_**마지막으로 수정된 항목:** 2015-03-09_

네트워크에서 클라이언트를 자동으로 찾으려면 먼저 네트워크 요소를 구/군/시 주소로 매핑하는 네트워크 *와이어맵(wiremap)*으로 위치 데이터베이스를 채워야 합니다. 서브넷, 무선 액세스 지점, 스위치 및 포트를 사용하여 와이어맵(wiremap)을 정의할 수 있습니다.

위치 데이터베이스에는 주소를 개별적으로 추가하거나 다음 표에 설명된 열 형식이 포함된 CSV 파일을 사용하여 일괄적으로 추가할 수 있습니다.

ELIN(Emergency Location Identification Number) 게이트웨이를 사용하는 경우 각 위치의 **CompanyName** 필드에 ELIN을 포함합니다. 각 위치마다 세미콜론으로 구분하여 여러 ELIN을 포함할 수 있습니다.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>네트워크 요소</th>
<th>필수 열</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>무선 액세스 지점</strong></p></td>
<td><p>&lt;BSSID&gt;,&lt;Description&gt;,&lt;Location&gt;,&lt;CompanyName&gt;,&lt;HouseNumber&gt;,&lt;HouseNumberSuffix&gt;,&lt;PreDirectional&gt;,…</p>
<p>…&lt;StreetName&gt;,&lt;StreetSuffix&gt;,&lt;PostDirectional&gt;,&lt;City&gt;,&lt;State&gt;,&lt;PostalCode&gt;,&lt;Country&gt;</p></td>
</tr>
<tr class="even">
<td><p><strong>서브넷</strong></p></td>
<td><p>&lt;Subnet&gt;,&lt;Description&gt;,&lt;Location&gt;,&lt;CompanyName&gt;,&lt;HouseNumber&gt;,&lt;HouseNumberSuffix&gt;,&lt;PreDirectional&gt;,…</p>
<p>…&lt;StreetName&gt;,&lt;StreetSuffix&gt;,&lt;PostDirectional&gt;,&lt;City&gt;,&lt;State&gt;,&lt;PostalCode&gt;,&lt;Country&gt;</p></td>
</tr>
<tr class="odd">
<td><p><strong>포트</strong></p></td>
<td><p>&lt;ChassisID&gt;,&lt;PortIDSubType&gt;,&lt;PortID&gt;,&lt;Description&gt;,&lt;Location&gt;,&lt;CompanyName&gt;,&lt;HouseNumber&gt;,&lt;HouseNumberSuffix&gt;,…</p>
<p>…&lt;PreDirectional&gt;,&lt;StreetName&gt;,&lt;StreetSuffix&gt;,&lt;PostDirectional&gt;,&lt;City&gt;,&lt;State&gt;,&lt;PostalCode&gt;,&lt;Country&gt;</p></td>
</tr>
<tr class="even">
<td><p><strong>스위치</strong></p></td>
<td><p>&lt;ChassisID&gt;,&lt;Description&gt;,&lt;Location&gt;,&lt;CompanyName&gt;,&lt;HouseNumber&gt;,&lt;HouseNumberSuffix&gt;,&lt;PreDirectional&gt;,…</p>
<p>…&lt;StreetName&gt;,&lt;StreetSuffix&gt;,&lt;PostDirectional&gt;,&lt;City&gt;,&lt;State&gt;,&lt;PostalCode&gt;,&lt;Country&gt;</p></td>
</tr>
</tbody>
</table>


위치 정책에서 **위치 필요**가 **예**나 **고지 사항**으로 설정되었을 때 위치 데이터베이스를 채우지 않으면 위치를 수동으로 입력하라는 메시지가 클라이언트에 표시됩니다.

위치 데이터베이스를 채우는 방법에 대한 자세한 내용은 다음 cmdlet에 대한 Lync Server 관리 셸 설명서를 참조하십시오.

  - **Get-CsLisSubnet**

  - **Set-CsLisSubnet**

  - Remove-CsLisSubnet

  - **Get-CsLisWirelessAccessPoint**

  - **Set-CsLisWirelessAccessPoint**

  - **Remove-CsLisWirelessAccessPoint**

  - **Get-CsLisSwitch**

  - **Set-CsLisSwitch**

  - **Remove-CsLisSwitch**

  - **Get-CsLisPort**

  - **Set-CsLisPort**

  - **Remove-CsLisPort**

## 위치 데이터베이스에 네트워크 요소를 추가하려면

1.  다음 cmdlet를 실행하여 위치 데이터베이스에 서브넷 위치를 추가합니다.
    
        Set-CsLisSubnet -Subnet 157.56.66.0 -Description "Subnet 1" -Location Location1 -CompanyName "Litware" -HouseNumber 1234 -HouseNumberSuffix "" -PreDirectional "" -StreetName 163rd -StreetSuffix Ave -PostDirectional NE -City Redmond -State WA -PostalCode 99123 -Country US
    
    ELIN 게이트웨이의 경우, CompanyName 필드에 ELIN을 추가합니다. 두 개 이상의 ELIN을 포함할 수 있습니다. 예를 들면 다음과 같습니다.
    
        Set-CsLisSubnet -Subnet 157.56.66.0 -Description "Subnet 1" -Location Location1 -CompanyName 425-555-0100; 425-555-0200; 425-555-0300 -HouseNumber 1234 -HouseNumberSuffix "" -PreDirectional "" -StreetName 163rd -StreetSuffix Ave -PostDirectional NE -City Redmond -State WA -PostalCode 99123 -Country US
    
    또는 다음 cmdlet를 실행하고 'subnets.csv' 파일을 사용하여 서브넷 위치를 일괄적으로 업데이트할 수도 있습니다.
    
        $g = Import-Csv subnets.csv
        $g | Set-CsLisSubnet

2.  다음 cmdlet를 실행하여 위치 데이터베이스에 무선 위치를 추가합니다.
    
        Set-CsLisWirelessAccessPoint -BSSID 0A-23-CD-16-AA-2E -Description "Wireless1" -Location Location2 -CompanyName "Litware" -HouseNumber 2345 -HouseNumberSuffix "" -PreDirectional "" -StreetName 163rd -StreetSuffix Ave -PostDirectional NE -City Bellevue -State WA -PostalCode 99234 -Country US
    
    또는 다음 cmdlet를 실행하고 csv 파일 ‘waps.csv’를 사용하여 무선 위치를 일괄적으로 업데이트할 수 있습니다.
    
        $g = Import-Csv waps.csv
        $g | Set-CsLisWirelessAccessPoint

3.  다음 cmdlet를 실행하여 위치 데이터베이스에 스위치 위치를 추가합니다.
    
        Set-CsLisSwitch-ChassisID 0B-23-CD-16-AA-BB -Description "Switch1" -Location Location1 -CompanyName "Litware" -HouseNumber 1234 -HouseNumberSuffix "" -PreDirectional "" -StreetName 163rd -StreetSuffix Ave -PostDirectional NE -City Redmond -State WA -PostalCode 99123 -Country US
    
    또는 다음 cmdlet를 실행하고 csv 파일 ‘switches.csv’를 사용하여 스위치 위치를 일괄적으로 업데이트할 수 있습니다.
    
        $g = Import-Csv switches.csv
        $g | Set-CsLisSwitch

4.  다음 cmdlet를 실행하여 위치 데이터베이스에 포트 위치를 추가합니다.
    
        Set-CsLisPort -ChassisID 0C-23-CD-16-AA-CC -PortID 0A-abcd -Description "Port1" -Location Location2 -CompanyName "Litware" -HouseNumber 2345 -HouseNumberSuffix "" -PreDirectional "" -StreetName 163rd -StreetSuffix Ave -PostDirectional NE -City Bellevue -State WA -PostalCode 99234 -Country US
    
    PortIDSubType의 기본값은 LocallyAssigned이며, 이 값을 InterfaceAlias 또는 InterfaceName으로 설정할 수도 있습니다.
    
    또는 다음 cmdlet를 실행하고 'ports.csv' 파일을 사용하여 포트 위치를 일괄적으로 업데이트할 수도 있습니다.
    
        $g = Import-Csv ports.csv
        $g | Set-CsLisPort

