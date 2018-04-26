---
title: 네트워크 지역, 사이트, 서브넷 배포
TOCTitle: 네트워크 지역, 사이트, 서브넷 배포
ms:assetid: c4b75601-3538-4d07-8d23-1ad90459ae48
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994067(v=OCS.15)
ms:contentKeyID: 52056937
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 네트워크 지역, 사이트, 서브넷 배포

 

_**마지막으로 수정된 항목:** 2015-03-09_

Enterprise Voice를 배포한 후에는 다음을 구성해야 합니다.

  - 네트워크 지역

  - 네트워크 사이트

  - 네트워크 서브넷

## 네트워크 지역 정의

Lync ServerWindows PowerShell 명령(New-CsNetworkRegion) 또는 Lync Server 제어판을 사용하여 네트워크 지역을 정의합니다.

    New-CsNetworkRegion -NetworkRegionID <region ID> -CentralSite <site ID>

자세한 내용은 [New-CsNetworkRegion](new-csnetworkregion.md)을 참고하세요.

이 예제에서 다음 Windows PowerShell 명령은 이 시나리오에서 정의한 네트워크 지역인 지역 1(인도)을 나타냅니다.

    New-CsNetworkRegion -NetworkRegionID "India" -CentralSite "India Central Site"


## 네트워크 사이트 정의

Lync ServerWindows PowerShell 명령(New-CsNetworkSite) 또는 Lync Server 제어판을 사용하여 네트워크 사이트를 정의합니다.

    New-CsNetworkSite -NetworkSiteID <site ID> -NetworkRegionID <region ID>

자세한 내용은 [New-CsNetworkSite](new-csnetworksite.md)를 참고하세요.

이 예제에서 다음 표 및 Lync ServerWindows PowerShell 명령은 이 시나리오에서 정의한 사이트를 나타냅니다. 위치 기반 라우팅에 대한 설정은 이해를 돕기 위해 표에 포함되었습니다.

    New-CsNetworkSite -NetworkSiteID "Delhi" -NetworkRegionID "India"
    New-CsNetworkSite -NetworkSiteID "Hyderabad" -NetworkRegionID "India"


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>사이트 1(델리)</th>
<th>사이트 2(히드라바드)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>사이트 ID</p></td>
<td><p>사이트 1(델리)</p></td>
<td><p>사이트 2(히드라바드)</p></td>
</tr>
<tr class="even">
<td><p>지역 ID</p></td>
<td><p>지역 1(인도)</p></td>
<td><p>지역 1(인도)</p></td>
</tr>
</tbody>
</table>



## 네트워크 서브넷 정의

Lync ServerWindows PowerShell 명령(New-CsNetworkSubnet) 또는 Lync Server 제어판을 사용하여 네트워크 서브넷을 정의하고 네트워크 사이트에 할당합니다.

    New-CsNetworkSubnet -SubnetID <Subnet IP address> -MaskBits <Subnet bitmask> -NetworkSiteID <site ID>

자세한 내용은 [New-CsNetworkSubnet](new-csnetworksubnet.md)을 참고하세요.

이 예제에서 다음 표 및 Windows PowerShell 명령은 이 시나리오에서 정의한 네트워크 사이트(Delhi 및 Hyderabad)에 대한 네트워크 서브넷의 할당을 나타냅니다. 위치 기반 라우팅에 대한 설정은 이해를 돕기 위해 표에 포함되었습니다.

    New-CsNetworkSubnet -SubnetID "192.168.0.0" -MaskBits "24" -NetworkSiteID "Delhi"
    New-CsNetworkSubnet -SubnetID "192.168.1.0" -MaskBits "24" -NetworkSiteID "Hyderabad"


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>사이트 1(델리)</th>
<th>사이트 2(히드라바드)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>서브넷 ID</p></td>
<td><p>192.168.0.0</p></td>
<td><p>192.168.1.0</p></td>
</tr>
<tr class="even">
<td><p>마스크</p></td>
<td><p>24</p></td>
<td><p>24</p></td>
</tr>
<tr class="odd">
<td><p>사이트 ID</p></td>
<td><p>사이트 1(델리)</p></td>
<td><p>사이트 2(히드라바드)</p></td>
</tr>
</tbody>
</table>



## 참고 항목

#### 기타 리소스

[Lync Server 2013에서 위치 기반 라우팅 구성](lync-server-2013-configuring-location-based-routing.md)

