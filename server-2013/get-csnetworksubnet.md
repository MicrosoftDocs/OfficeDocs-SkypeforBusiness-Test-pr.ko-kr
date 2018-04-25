---
title: Get-CsNetworkSubnet
TOCTitle: Get-CsNetworkSubnet
ms:assetid: ad74155a-8d83-42f6-bb1e-8bfc7d57d5b0
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412825(v=OCS.15)
ms:contentKeyID: 49304706
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsNetworkSubnet

 

_**마지막으로 수정된 항목:** 2015-03-09_

하나 이상의 네트워크 서브넷에 대한 정보를 검색합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsNetworkSubnet [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsNetworkSubnet [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

이 예제에서는 Lync Server 배포 내 모든 서브넷을 검색합니다.

    Get-CsNetworkSubnet

## 예제 2

이 예제에서는 ID(서브넷 ID)가 172.11.15.0인 서브넷에 대한 모든 정보를 검색합니다.

    Get-CsNetworkSubnet -Identity 172.11.15.0

## 예제 3

이 예제에서는 ID가 172.11.로 시작하는 모든 서브넷을 검색합니다.

    Get-CsNetworkSubnet -Filter 172.11.*

## 예제 4

예제 4에서는 Vancouver 사이트와 연결된 모든 서브넷을 검색합니다. 먼저 매개 변수 없이 **Get-CsNetworkSubnet** cmdlet을 호출합니다. 예제 2에서와 같이 이 명령은 정의된 모든 서브넷을 검색합니다. 그런 다음 이 서브넷 컬렉션을 **Where-Object** cmdlet에 파이프합니다. **Where-Object** cmdlet은 NetworkSiteID가 Vancouver와 같은(-eq) 서브넷만 검색되도록 컬렉션의 검색 범위를 좁힙니다.

    Get-CsNetworkSubnet | Where-Object {$_.NetworkSiteID -eq "Vancouver"}

## 자세한 정보

각 서브넷은 해당 서브넷에 속한 호스트의 지리적 위치를 확인할 수 있도록 네트워크 사이트에 연결되어야 합니다. 이 cmdlet을 사용하여 ID(서브넷 ID), 마스크 비트 수, 연결된 네트워크 사이트 및 서브넷 설명 등 서브넷에 대한 정보를 검색할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsNetworkSubnet** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsNetworkSubnet"}

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
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 매개 변수를 사용하면 ID에 기초하여 모든 서브넷의 와일드카드 검색을 수행할 수 있습니다. 예를 들어 Filter 값 172.11.*는 ID가 172.11.로 시작하는 모든 서브넷을 검색합니다(예: 172.11.10.0, 172.11.25.0 등).</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>검색할 서브넷의 고유한 서브넷 ID입니다. 이 값은 IP 주소입니다(예: 174.11.12.0).</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 네트워크 서브넷 정보를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.SubnetType 유형의 개체를 하나 이상 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsNetworkSubnet](new-csnetworksubnet.md)  
[Remove-CsNetworkSubnet](remove-csnetworksubnet.md)  
[Set-CsNetworkSubnet](set-csnetworksubnet.md)

