---
title: Remove-CsNetworkRegionLink
TOCTitle: Remove-CsNetworkRegionLink
ms:assetid: f26cde90-e789-44a7-a304-695c85e64403
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413012(v=OCS.15)
ms:contentKeyID: 49305504
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsNetworkRegionLink

 

_**마지막으로 수정된 항목:** 2015-03-09_

CAC(통화 허용 제어)에 대해 구성된 두 지역 간의 링크를 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsNetworkRegionLink -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 첫 번째 예제에서는 ID가 NA\_EMEA인 네트워크 지역 링크를 제거합니다.

    Remove-CsNetworkRegionLink -Identity NA_EMEA

## 예제 2

예제 2에서는 HighBWLimits라는 대역폭 정책 프로필을 사용하는 모든 네트워크 지역 링크를 제거합니다. 이 예제에서 첫 번째로 호출된 cmdlet은 모든 지역 링크를 검색하는 **Get-CsNetworkRegionLink** cmdlet(매개 변수 없음)입니다. 이 링크 컬렉션은 **Where-Object** cmdlet에 파이프됩니다. **Where-Object** cmdlet은 컬렉션의 각 구성원을 하나씩 살펴보고 BWPolicyProfileID 속성 값을 확인합니다. 이 속성이 HighBWLimits와 같은(-eq) 경우 링크를 제거하는 **Remove-CsNetworkRegionLink** cmdlet에 해당 구성원을 파이프합니다.

    Get-CsNetworkRegionLink | Where-Object {$_.BWPolicyProfileID -eq "HighBWLimits"} | Remove-CsNetworkRegionLink

## 자세한 정보

네트워크 내의 지역은 실제 WAN 연결을 통해 연결됩니다. 이 cmdlet은 실제 연결에 영향을 주지 않지만 CAC 구성에서 링크를 제거합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsNetworkRegionLink** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsNetworkRegionLink"}

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
<td><p>제거할 네트워크 지역 링크의 고유 식별자입니다. 네트워크 지역 링크는 전역 범위에서만 만들어지므로 이 식별자는 범위를 지정할 필요가 없습니다. 대신 이 식별자는 해당 링크를 식별하는 고유 이름 문자열을 포함합니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionLinkType 개체입니다. 네트워크 지역 링크 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다. Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionLinkType 개체 유형을 제거합니다.

## 참고 항목

#### 기타 리소스

[New-CsNetworkRegionLink](new-csnetworkregionlink.md)  
[Set-CsNetworkRegionLink](set-csnetworkregionlink.md)  
[Get-CsNetworkRegionLink](get-csnetworkregionlink.md)

