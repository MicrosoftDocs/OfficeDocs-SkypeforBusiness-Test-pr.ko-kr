---
title: Set-CsNetworkInterRegionRoute
TOCTitle: Set-CsNetworkInterRegionRoute
ms:assetid: 5d9da3c0-56fc-401d-baf3-ed6c0f50f53d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398410(v=OCS.15)
ms:contentKeyID: 49303773
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsNetworkInterRegionRoute

 

_**마지막으로 수정된 항목:** 2015-03-09_

CAC(통화 허용 제어) 구성 내에서 네트워크 지역을 연결하는 기존 경로를 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsNetworkInterRegionRoute [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Set-CsNetworkInterRegionRoute [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-NetworkRegionID1 <String>] [-NetworkRegionID2 <String>] [-NetworkRegionLinkIDs <String>] [-NetworkRegionLinks <PSListModifier>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 경로를 따라 통과하는 영역 링크를 변경하여 경로 NA\_APAC\_Route를 수정합니다. NetworkRegionLinkIDs 매개 변수는 기존 링크를 해당 문자열에 지정된 두 개 링크로 바꾸는 "NA\_SA,SA\_APAC" 값과 함께 사용됩니다.

    Set-CsNetworkInterRegionRoute -Identity NA_APAC_Route -NetworkRegionLinkIDs "NA_SA,SA_APAC"

## 예제 2

예제 1과 마찬가지로 예제 2에서도 NA\_APAC\_Route 경로 내의 링크를 수정합니다. 그러나 이 예제에서는 NetworkRegionLinkIDs 매개 변수를 사용하여 해당 경로의 모든 링크를 바꾸는 대신 NetworkRegionLinks 매개 변수를 사용하여 이미 해당 경로에 있는 링크 목록에 링크를 추가합니다. 이 경우 링크 SA\_EMEA가 경로에 추가됩니다. @{add=\<link\>} 구문은 링크 목록에 요소를 추가합니다. @{replace=\<link\>} 구문을 사용하여 모든 기존 링크를 \<link\>(본질적으로 NetworkRegionLinkIDs를 사용하는 것과 동일하게 동작)에 의해 지정된 링크로 바꾸거나 @{remove=\<link\>} 구문을 사용하여 목록에서 링크를 제거할 수도 있습니다.

    Set-CsNetworkInterRegionRoute -Identity NA_APAC_Route -NetworkRegionLinks @{add="SA_EMEA"}

## 예제 3

예제 3에서는 NA\_Route5 경로를 수정합니다. 이 예제에서는 이 경로를 구성하는 영역 중 하나를 변경합니다. NetworkRegionID2 매개 변수를 사용하여 새 영역을 지정한 다음 NetworkRegionLinkIDs 매개 변수를 사용하여 이 경로의 영역을 연결할 새 링크 목록을 만듭니다.

    Set-CsNetworkInterRegionRoute -Identity NA_Route5 -NetworkRegionID2 SouthAmerica -NetworkRegionLinkIDs "NA_SA,SA_APAC"

## 자세한 정보

CAC 구성 내의 모든 영역에는 다른 모든 영역에 액세스할 수 있는 방법이 있어야 합니다. 영역 링크는 영역 간 연결에 대한 대역폭 제한을 설정하고 실제 링크를 나타내며, 경로는 한 영역에서 다른 영역으로 연결이 통과하게 되는 링크된 경로를 결정합니다. 이 cmdlet은 해당 경로 연결을 수정합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsNetworkInterRegionRoute** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsNetworkInterRegionRoute"}

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
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Xds 글로벌 상대 ID</p></td>
<td><p>수정할 네트워크 지역 경로의 고유한 식별자입니다. 네트워크 지역 경로는 전역 범위에서만 만들어지므로 이 식별자에서는 범위를 지정할 필요가 없습니다. 대신 여기에는 경로를 식별하는 고유한 이름인 문자열이 포함됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>InterNetworkRegionRouteType</p></td>
<td><p>기존 영역 경로에 대한 개체 참조입니다. 이 개체의 유형은 <strong>Get-CsNetworkInterRegionRoute</strong> cmdlet을 호출하여 검색할 수 있는 Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkRegionRouteType이어야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>NetworkRegionID1</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>경로를 통해 연결된 두 영역 중 하나의 Identity(NetworkRegionID)입니다. 이 매개 변수에 전달되는 값은 NetworkRegionID2 매개 변수의 값과 다른 영역이어야 합니다. 다시 말해 영역의 경로를 영역 자체로 지정할 수 없습니다. 또한 NetworkRegionID1 및 NetworkRegionID2 조합은 고유해야 합니다. 예를 들어, NorthAmerica 및 EMEA를 연결하는 두 개의 경로를 정의할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>NetworkRegionID2</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>경로를 통해 연결된 두 영역 중 하나의 Identity(NetworkRegionID)입니다. 이 매개 변수에 전달되는 값은 NetworkRegionID1 매개 변수의 값과 다른 영역이어야 합니다. 다시 말해 영역의 경로를 영역 자체로 지정할 수 없습니다. 또한 NetworkRegionID1 및 NetworkRegionID2 조합은 고유해야 합니다. 예를 들어, NorthAmerica 및 EMEA를 연결하는 두 개의 경로를 정의할 수 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>NetworkRegionLinkIDs</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>이 경로에 대한 모든 링크를 쉼표로 구분된 값의 문자열로 지정할 수 있도록 합니다. 값은 영역 링크의 ID(NetworkRegionLinkIDs)입니다. NetworkRegionLinkIDs와 NetworkRegionLinks에 대한 값을 둘 다 입력한 경우 NetworkRegionLinkIDs는 무시됩니다. 이 매개 변수를 사용하여 수정된 모든 링크가 경로의 모든 기존 링크를 대체합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>NetworkRegionLinks</em></p></td>
<td><p>선택</p></td>
<td><p>PS 목록 한정자</p></td>
<td><p>이 경로에 적용되는 영역 링크의 ID(NetworkRegionLinkIDs)가 포함된 목록 개체입니다. 이 cmdlet의 경우 이 매개 변수는 이 경로의 모든 기존 링크를 바꾸는 데 사용될 뿐만 아니라 개별 링크를 추가하거나 제거할 수 있다는 점에서 NetworkRegionLinkIDs와 다릅니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkRegionRouteType 개체입니다. 네트워크 지역 간 경로 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다. Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkRegionRouteType 유형의 개체를 수정합니다.

## 참고 항목

#### 기타 리소스

[New-CsNetworkInterRegionRoute](new-csnetworkinterregionroute.md)  
[Remove-CsNetworkInterRegionRoute](remove-csnetworkinterregionroute.md)  
[Get-CsNetworkInterRegionRoute](get-csnetworkinterregionroute.md)

