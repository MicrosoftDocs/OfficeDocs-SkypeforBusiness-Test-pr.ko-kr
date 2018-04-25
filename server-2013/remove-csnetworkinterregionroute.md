---
title: Remove-CsNetworkInterRegionRoute
TOCTitle: Remove-CsNetworkInterRegionRoute
ms:assetid: 91948c03-2bcb-4e25-b0b6-23827e85bbb3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398743(v=OCS.15)
ms:contentKeyID: 49304387
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsNetworkInterRegionRoute

 

_**마지막으로 수정된 항목:** 2015-03-09_

CAC(통화 허용 제어) 구성 내의 네트워크 지역을 연결하는 경로를 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsNetworkInterRegionRoute -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 Identity가 NA\_APAC\_Route인 경로를 제거합니다.

    Remove-CsNetworkInterRegionRoute -Identity NA_APAC_Route

## 예제 2

예제 2에서는 NorthAmerica 지역이 포함된 모든 지역 경로를 제거합니다. 명령의 처음 부분은 **Get-CsNetworkInterRegionRoute** cmdlet을 호출합니다. 이 cmdlet은 매개 변수 없이 호출되어 모든 지역 경로를 검색합니다. 그런 다음 이 경로 컬렉션이 **Where-Object** cmdlet에 파이프됩니다. **Where-Object** cmdlet은 경로의 지역 중 하나로 NorthAmerica가 정의되어 있는 경로로 컬렉션의 범위를 좁힙니다. 이를 위해 경로에 NorthAmerica와 같은(-eq) NetworkRegionID1 값, 또는(-or) NorthAmerica와 같은 NetworkRegionID2 값이 있는지 확인합니다. 컬렉션에 NorthAmerica 지역을 포함하는 경로만 남으면 이 컬렉션을 각 경로를 제거하는 **Remove-CsNetworkInterRegionRoute** cmdlet에 파이프합니다.

    Get-CsNetworkInterRegionRoute | Where-Object {$_.NetworkRegionID1 -eq "NorthAmerica" -or $_.NetworkRegionID2 -eq "NorthAmerica"} | Remove-CsNetworkInterRegionRoute

## 자세한 정보

CAC 구성 내의 모든 지역에는 다른 모든 지역에 액세스할 수 있는 방법이 있어야 합니다. 영역 링크는 영역 간 연결에 대한 대역폭 제한을 설정하고 실제 링크를 나타내며, 경로는 한 영역에서 다른 영역으로 연결이 통과하게 되는 링크된 경로를 결정합니다. 이 cmdlet은 이러한 경로 연결 중 하나를 제거합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsNetworkInterRegionRoute** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsNetworkInterRegionRoute"}

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
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>제거할 네트워크 지역 경로의 고유 식별자입니다. 네트워크 지역 경로는 전역 범위에서만 만들어지므로 이 식별자에서는 범위를 지정할 필요가 없습니다. 대신 여기에는 경로를 식별하는 고유한 이름인 문자열이 포함됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkRegionRouteType 개체입니다. 네트워크 영역 간 경로 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다. Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkRegionRouteType 유형의 개체를 제거합니다.

## 참고 항목

#### 기타 리소스

[New-CsNetworkInterRegionRoute](new-csnetworkinterregionroute.md)  
[Set-CsNetworkInterRegionRoute](set-csnetworkinterregionroute.md)  
[Get-CsNetworkInterRegionRoute](get-csnetworkinterregionroute.md)

