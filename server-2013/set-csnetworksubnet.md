---
title: Set-CsNetworkSubnet
TOCTitle: Set-CsNetworkSubnet
ms:assetid: 9e85cdbb-b5fb-48d6-8f95-6e7cba9d9597
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412739(v=OCS.15)
ms:contentKeyID: 49304544
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsNetworkSubnet

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 네트워크 서브넷을 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsNetworkSubnet [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Set-CsNetworkSubnet [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Description <String>] [-Force <SwitchParameter>] [-MaskBits <Int32>] [-NetworkSiteID <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 ID(서브넷 ID)가 172.11.15.0인 서브넷을 수정합니다. 새 MaskBits 값(25) 및 새 NetworkSiteID(Chicago)를 사용하여 서브넷을 수정합니다.

    Set-CsNetworkSubnet -Identity 172.11.15.0 -MaskBits 25 -NetworkSiteID Chicago

## 예제 2

예제 2에서는 Vancouver 사이트의 모든 서브넷을 Chicago 사이트로 이동합니다. 이 작업을 수행하기 위해 먼저 **Get-CsNetworkSubnet** cmdlet을 호출합니다. 그러면 Lync Server 배포 내에 정의된 모든 서브넷의 컬렉션을 검색합니다. 그런 다음 이 서브넷 컬렉션은 **Where-Object** cmdlet에 파이프됩니다. **Where-Object** cmdlet은 NetworkSiteID가 Vancouver와 같은(-eq) 서브넷만 검색되도록 컬렉션의 검색 범위를 좁힙니다. 이제 컬렉션은 Vancouver 사이트와 연결된 서브넷만으로 구성되므로 이 컬렉션을 **Set-CsNetworkSubnet** cmdlet에 파이프합니다. **Set-CsNetworkSubnet** cmdlet: NetworkSiteID에 하나의 매개 변수를 제공합니다. 매개 변수에 Chicago 값을 전달하여, 컬렉션에 있는 모든 구성원의 네트워크 사이트 ID를 Chicago로 변경하도록 **Set-CsNetworkSubnet** cmdlet에 지시합니다.

    Get-CsNetworkSubnet | Where-Object {$_.NetworkSiteID -eq "Vancouver"} | Set-CsNetworkSubnet -NetworkSiteID Chicago

## 자세한 정보

각 서브넷은 해당 서브넷에 속한 호스트의 지리적 위치를 확인할 수 있도록 네트워크 사이트에 연결되어야 합니다. 연결된 네트워크 사이트를 수정하거나 서브넷 설명을 변경하거나 서브넷의 마스크 비트를 수정하려면 이 cmdlet을 사용합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsNetworkSubnet** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsNetworkSubnet"}

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
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>수정되는 서브넷의 설명입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Xds 글로벌 상대 ID</p></td>
<td><p>수정할 서브넷의 고유한 서브넷 ID입니다. 이 값은 http: 또는 https:으로 시작하는 IP 주소(예: 174.11.12.0) 또는 URL입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>SubnetType</p></td>
<td><p>수정할 네트워크 서브넷 개체에 대한 참조입니다. 이 개체의 유형은 <strong>Get-CsNetworkSubnet</strong> cmdlet을 호출하여 검색할 수 있는 Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.SubnetType이어야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MaskBits</em></p></td>
<td><p>선택</p></td>
<td><p>Int32</p></td>
<td><p>서브넷에 적용할 비트마스크입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>NetworkSiteID</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>서브넷이 적용되는 네트워크 사이트의 사이트 ID입니다. <strong>Get-CsNetworkSite</strong> cmdlet을 호출하여 배포에 사용할 사이트 ID를 검색할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.SubnetType 개체입니다. 네트워크 서브넷 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다. Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.SubnetType 유형의 개체를 수정합니다.

## 참고 항목

#### 기타 리소스

[New-CsNetworkSubnet](new-csnetworksubnet.md)  
[Remove-CsNetworkSubnet](remove-csnetworksubnet.md)  
[Get-CsNetworkSubnet](get-csnetworksubnet.md)

