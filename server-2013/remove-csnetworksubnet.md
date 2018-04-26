---
title: Remove-CsNetworkSubnet
TOCTitle: Remove-CsNetworkSubnet
ms:assetid: 251ddb5c-4837-4810-b46f-d276f9535653
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425726(v=OCS.15)
ms:contentKeyID: 49303077
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsNetworkSubnet

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 네트워크 서브넷을 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsNetworkSubnet -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 ID(서브넷 ID)가 172.11.15.0인 서브넷을 제거합니다.

    Remove-CsNetworkSubnet -Identity 172.11.15.0

## 예제 2

예제 2에서는 Vancouver 사이트와 연결된 모든 서브넷을 제거합니다. 이를 위해 먼저 **Get-CsNetworkSubnet** cmdlet을 호출합니다. 그러면 Lync Server 배포 내에 정의된 모든 서브넷의 컬렉션을 검색합니다. 그런 다음 이 서브넷 컬렉션은 **Where-Object** cmdlet에 파이프됩니다. **Where-Object** cmdlet은 NetworkSiteID가 Vancouver와 같은(-eq) 서브넷만 검색되도록 컬렉션의 검색 범위를 좁힙니다. 이제 컬렉션은 Vancouver 사이트와 연결된 서브넷으로만 구성되므로 컬렉션을 **Remove-CsNetworkSubnet** cmdlet에 파이프하여 컬렉션의 모든 항목을 제거합니다.

    Get-CsNetworkSubnet | Where-Object {$_.NetworkSiteID -eq "Vancouver"} | Remove-CsNetworkSubnet

## 자세한 정보

각 서브넷은 해당 서브넷에 속한 호스트의 지리적 위치를 확인할 수 있도록 네트워크 사이트에 연결되어야 합니다. 이 cmdlet은 네트워크 서브넷을 제거하는 데 사용됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsNetworkSubnet** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsNetworkSubnet"}

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
<td><p>제거할 서브넷의 고유한 서브넷 ID입니다. 이 값은 IP 주소입니다(예: 174.11.12.0).</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.SubnetType 개체입니다. 네트워크 서브넷 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다. Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.SubnetType 유형의 개체를 제거합니다.

## 참고 항목

#### 기타 리소스

[New-CsNetworkSubnet](new-csnetworksubnet.md)  
[Set-CsNetworkSubnet](set-csnetworksubnet.md)  
[Get-CsNetworkSubnet](get-csnetworksubnet.md)

