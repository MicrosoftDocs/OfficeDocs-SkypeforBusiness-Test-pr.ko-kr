---
title: New-CsNetworkInterRegionRoute
TOCTitle: New-CsNetworkInterRegionRoute
ms:assetid: 97deeba5-b49f-4078-9843-fee7b2d1e72e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398779(v=OCS.15)
ms:contentKeyID: 49304467
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsNetworkInterRegionRoute

 

_**마지막으로 수정된 항목:** 2015-03-09_

CAC(통화 허용 제어) 구성 내의 네트워크 지역을 연결하는 새 경로를 만듭니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsNetworkInterRegionRoute -InterNetworkRegionRouteID <String> <COMMON PARAMETERS>

    New-CsNetworkInterRegionRoute -Identity <XdsGlobalRelativeIdentity> <COMMON PARAMETERS>

    COMMON PARAMETERS: -NetworkRegionID1 <String> -NetworkRegionID2 <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-NetworkRegionLinkIDs <String>] [-NetworkRegionLinks <PSListModifier>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 NorthAmerica 지역과 APAC 지역 사이에 새 네트워크 지역 경로를 만듭니다. 새 경로의 Identity는 NA\_APAC\_Route로 지정합니다. 이는 InterNetworkRegionRouteID로 자동으로 할당됩니다. 연결되는 지역은 NorthAmerica(NetworkRegionID1 매개 변수에 대한 값으로 전달됨), 그리고 APAC(NetworkRegionID2 매개 변수에 대한 값으로 전달됨)입니다. 이 예제에서는 NorthAmerica를 APAC에 직접 연결하도록 구성된 지역 링크가 없다고 가정합니다. 그러나 NorthAmerica에서 EMEA로의 링크(NA\_EMEA), 그리고 EMEA에서 APAC으로의 링크(EMEA\_APAC)는 있습니다. 이러한 링크를 쉼표로 구분하여 NetworkRegionLinkIDs 매개 변수에 대한 값으로 사용합니다. 이렇게 하면 EMEA를 통해 NorthAmerica에서 APAC으로 연결이 경로 지정되며 이러한 링크에 연결된 오디오 및 비디오 연결에 대역폭 제한이 적용됩니다.

    New-CsNetworkInterRegionRoute -Identity NA_APAC_Route -NetworkRegionID1 NorthAmerica -NetworkRegionID2 APAC -NetworkRegionLinkIDs "NA_EMEA,EMEA_APAC"

## 자세한 정보

CAC 구성 내의 모든 영역에는 다른 모든 영역에 액세스할 수 있는 방법이 있어야 합니다. 영역 링크는 영역 간 연결에 대한 대역폭 제한을 설정하고 실제 링크를 나타내며, 경로는 한 영역에서 다른 영역으로 연결이 통과하게 되는 링크된 경로를 결정합니다. 이 cmdlet은 이러한 경로 연결을 만듭니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsNetworkInterRegionRoute** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsNetworkInterRegionRoute"}

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
<td><p>새로 만들어진 네트워크 지역 경로에 대한 고유 식별자입니다. 네트워크 지역 경로는 전역 범위에서만 만들어지므로 이 식별자에서는 범위를 지정할 필요가 없습니다. 대신 여기에는 경로를 식별하는 고유한 이름인 문자열이 포함됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>InterNetworkRegionRouteID</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>이 값은 Identity와 같습니다. Identity와 InterNetworkRegionRouteID를 모두 지정할 수는 없습니다. 둘 중 하나에 입력한 값이 자동으로 두 가지 모두에 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>NetworkRegionID1</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>경로를 통해 연결된 두 영역 중 하나의 Identity(NetworkRegionID)입니다. 이 매개 변수에 전달되는 값은 NetworkRegionID2 매개 변수의 값과 다른 영역이어야 합니다. 다시 말해 영역의 경로를 영역 자체로 지정할 수 없습니다. 또한 NetworkRegionID1 및 NetworkRegionID2 조합은 고유해야 합니다. 예를 들어, NorthAmerica 및 EMEA를 연결하는 두 개의 경로를 정의할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>NetworkRegionID2</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>경로를 통해 연결된 두 영역 중 하나의 Identity(NetworkRegionID)입니다. 이 매개 변수에 전달되는 값은 NetworkRegionID1 매개 변수의 값과 다른 영역이어야 합니다. 다시 말해 영역의 경로를 영역 자체로 지정할 수 없습니다. 또한 NetworkRegionID1 및 NetworkRegionID2 조합은 고유해야 합니다. 예를 들어, NorthAmerica 및 EMEA를 연결하는 두 개의 경로를 정의할 수 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>NetworkRegionLinkIDs</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 경로에 대한 모든 링크를 쉼표로 구분된 값의 문자열로 지정할 수 있도록 합니다. 값은 영역 링크의 ID(NetworkRegionLinkIDs)입니다. NetworkRegionLinkIDs와 NetworkRegionLinks에 대한 값을 둘 다 입력한 경우 NetworkRegionLinkIDs는 무시됩니다. 이 매개 변수를 사용하면 목록 개체를 만들어서 이를 NetworkRegionLinks 매개 변수에 전달할 필요 없이 편리하게 링크 목록을 지정할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>NetworkRegionLinks</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>이 경로에 적용되는 영역 링크의 ID(NetworkRegionLinkIDs)가 포함된 목록 개체입니다. 이 cmdlet에서 두 개 이상의 링크를 입력하는 경우 이 매개 변수는 NetworkRegionLinkIDs 매개 변수와 형식만 다릅니다. 이 cmdlet의 초기 목록을 정의하는 경우 NetworkRegionLinkIDs 매개 변수를 사용하는 것이 좋습니다.</p></td>
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

없음.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkRegionRouteType 유형의 개체를 만듭니다.

## 참고 항목

#### 기타 리소스

[Remove-CsNetworkInterRegionRoute](remove-csnetworkinterregionroute.md)  
[Set-CsNetworkInterRegionRoute](set-csnetworkinterregionroute.md)  
[Get-CsNetworkInterRegionRoute](get-csnetworkinterregionroute.md)

