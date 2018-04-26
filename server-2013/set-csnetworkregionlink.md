---
title: Set-CsNetworkRegionLink
TOCTitle: Set-CsNetworkRegionLink
ms:assetid: b3d5d203-2aa7-4a54-93d4-30bcda391d68
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412867(v=OCS.15)
ms:contentKeyID: 49304771
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsNetworkRegionLink

 

_**마지막으로 수정된 항목:** 2015-03-09_

CAC(통화 허용 제어)를 위해 구성된 두 네트워크 지역 간의 링크를 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsNetworkRegionLink [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Set-CsNetworkRegionLink [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-BWPolicyProfileID <String>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-NetworkRegionID1 <String>] [-NetworkRegionID2 <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 NA\_EMEA라는 네트워크 지역 링크의 대역폭 정책 프로필을 HighBWLimits 프로필로 변경합니다. 수정할 네트워크 지역 링크 이름을 Identity 매개 변수 값으로 지정한 다음 HighBWLimits 값을 BWPolicyProfile 매개 변수에 할당합니다. 그러면 해당 대역폭 정책 프로필(HighBWLimits)에 정의된 대역폭 제한이 이러한 지역 간의 연결에 할당됩니다.

    Set-CsNetworkRegionLink -Identity NA_EMEA -BWPolicyProfileID HighBWLimits

## 자세한 정보

네트워크 내의 지역은 실제 WAN 연결을 통해 연결됩니다. 이 cmdlet은 연결된 지역 간의 오디오 및 비디오 연결 대역폭 제한 및 이러한 지역 중 하나를 변경할 수 있게 지원하여 두 지역 간의 링크를 수정합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsNetworkRegionLink** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsNetworkRegionLink"}

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
<td><p><em>BWPolicyProfileID</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>이 링크에 대한 제한을 정의하는 대역폭 정책 프로필 ID입니다. <strong>Get-CsNetworkBandwidthPolicyProfile</strong> cmdlet을 호출하여 사용 가능한 프로필 목록을 검색할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
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
<td><p>수정할 네트워크 지역 링크의 고유 식별자입니다. 네트워크 지역 링크는 전역 범위에서만 만들어지므로 이 식별자는 범위를 지정할 필요가 없습니다. 대신 이 식별자는 해당 링크를 식별하는 고유 이름 문자열을 포함합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>네트워크 지역 링크 유형</p></td>
<td><p>네트워크 지역 링크에 대한 개체 참조입니다. 이 개체의 유형은 Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionLinkType이어야 하며, <strong>Get-CsNetworkRegionLink</strong> cmdlet을 호출하여 검색할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>NetworkRegionID1</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>NetworkRegionID2 속성으로 식별되는 지역에 연결된 지역의 ID(NetworkRegionID)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>NetworkRegionID2</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>NetworkRegionID1 속성으로 식별되는 지역에 연결된 지역의 ID(NetworkRegionID)입니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionLinkType 개체입니다. 네트워크 지역 링크 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다. Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionLinkType 유형의 개체를 수정합니다.

## 참고 항목

#### 기타 리소스

[New-CsNetworkRegionLink](new-csnetworkregionlink.md)  
[Remove-CsNetworkRegionLink](remove-csnetworkregionlink.md)  
[Get-CsNetworkRegionLink](get-csnetworkregionlink.md)  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)

