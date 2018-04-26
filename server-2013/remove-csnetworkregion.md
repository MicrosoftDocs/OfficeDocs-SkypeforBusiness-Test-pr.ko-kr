---
title: Remove-CsNetworkRegion
TOCTitle: Remove-CsNetworkRegion
ms:assetid: 661dce40-f601-4181-b8f1-3277a76d5df4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398466(v=OCS.15)
ms:contentKeyID: 49303871
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsNetworkRegion

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 네트워크 지역을 제거합니다. 네트워크 지역은 엔터프라이즈 네트워크에서 네트워크 허브 또는 백본을 나타냅니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsNetworkRegion -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 Identity가 NorthAmerica인 네트워크 지역을 제거합니다. Identity는 고유하므로 이 명령은 하나의 네트워크 지역만 제거합니다.

    Remove-CsNetworkRegion -Identity NorthAmerica

## 예제 2

이 예제에서는 중앙 사이트 Redmond와 연결된 모든 네트워크 지역을 제거합니다. 명령은 먼저 매개 변수 없이 **Get-CsNetworkRegion** cmdlet을 호출하여 Lync Server 배포에 대해 정의된 모든 네트워크 지역의 컬렉션을 검색합니다. 이 컬렉션은 **Where-Object** cmdlet에 파이프됩니다. **Where-Object** cmdlet은 이 컬렉션을 필터링하여 CentralSite 값이 site:Redmond와 같은(-eq) 항목(네트워크 지역)만 반환합니다. 컬렉션의 범위가 이러한 항목으로 좁혀진 후 새 컬렉션은 컬렉션 내의 모든 항목을 제거하는 **Remove-CsNetworkRegion** cmdlet에 파이프됩니다.

    Get-CsNetworkRegion | Where-Object {$_.CentralSite -eq "site:Redmond"} | Remove-CsNetworkRegion

## 예제 3

이 예제에서는 Identity가 NorthAmerica인 네트워크 지역을 제거합니다. 그러나 사이트와 연결된 지역은 제거할 수 없습니다. 따라서 이 예제에서는 먼저 NorthAmerica 지역과 사이트 간의 연결을 제거합니다.

먼저 **Get-CsNetworkSite** cmdlet을 매개 변수 없이 호출하여 Lync Server 배포에 대해 정의된 모든 네트워크 사이트의 컬렉션을 검색합니다. 이 컬렉션은 **Where-Object** cmdlet에 파이프됩니다. **Where-Object** cmdlet은 이 컬렉션을 필터링하여 NetworkRegionID 값이 NorthAmerica와 같은(-eq) 항목(네트워크 사이트)만 반환합니다. 컬렉션의 범위가 이러한 항목으로 좁혀진 후 이 새 컬렉션은 **Set-CsNetworkSite** cmdlet에 파이프됩니다. NetworkRegionID가 NorthAmerica인 각 사이트에 대해 NetworkRegionID를 Null($null)로 설정합니다. 이렇게 하면 해당 사이트에서 영역에 대한 참조가 제거됩니다. 단, 사이트는 사이트와 연결되지 않은 경우 BypassID를 가질 수 없습니다. 따라서 NetworkRegionID를 Null로 설정하여 지역에 대한 참조를 제거하는 것 외에, BypassID를 Null로 설정하여 우회 연결도 제거해야 합니다.

첫째 줄이 완료되고 나면 NorthAmerica 지역과 연결되었던 모든 사이트는 더 이상 지역 또는 우회 설정에 연결되지 않습니다. 이제 네트워크 지역을 제거하는 둘째 줄을 호출할 수 있습니다.

    Get-CsNetworkSite | Where-Object {$_.NetworkRegionID -eq "NorthAmerica"} | Set-CsNetworkSite -NetworkRegionID $null -BypassID $null
    Remove-CsNetworkRegion -Identity "NorthAmerica"

## 자세한 정보

네트워크 지역은 여러 지역의 많은 네트워크 부분을 교차합니다. 모든 네트워크 지역은 중앙 사이트와 연결되어 있어야 합니다. 중앙 사이트는 대역폭 정책 서비스가 실행되는 데이터 센터 사이트입니다. 이 cmdlet을 사용하여 네트워크 지역을 제거할 수 있습니다.

네트워크 지역이 네트워크 사이트와 연결된 경우(즉, 사이트의 NetworkRegionID가 해당 영역의 Identity와 동일한 경우) 네트워크 지역을 제거할 수 없습니다. 사이트와 연결된 지역을 제거하려고 시도하면 오류 메시지가 표시됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsNetworkRegion** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsNetworkRegion"}

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
<td><p>제거할 네트워크 지역의 고유 식별자입니다. ID는 해당 지역을 고유하게 식별하는 문자열 형식입니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionType 개체입니다. 네트워크 지역 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다. Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionType 유형의 개체를 제거합니다.

## 참고 항목

#### 기타 리소스

[New-CsNetworkRegion](new-csnetworkregion.md)  
[Set-CsNetworkRegion](set-csnetworkregion.md)  
[Get-CsNetworkRegion](get-csnetworkregion.md)

