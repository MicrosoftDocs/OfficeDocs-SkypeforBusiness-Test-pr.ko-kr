---
title: Remove-CsNetworkBandwidthPolicyProfile
TOCTitle: Remove-CsNetworkBandwidthPolicyProfile
ms:assetid: 7b1f3c8d-486c-4a7e-aa40-57893f249f66
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398609(v=OCS.15)
ms:contentKeyID: 49304134
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsNetworkBandwidthPolicyProfile

 

_**마지막으로 수정된 항목:** 2015-03-09_

네트워크 대역폭 정책 프로필을 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsNetworkBandwidthPolicyProfile -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 ID LowBWProfile이 포함된 대역폭 정책 프로필을 제거합니다. ID가 고유해야 하기 때문에 하나의 프로필만 제거됩니다.

    Remove-CsNetworkBandwidthPolicyProfile -Identity LowBWProfile

## 예제 2

예제 2에서는 프로필이 할당된 모든 사이트에서 ID가 LowBWProfile인 대역폭 정책 프로필에 대한 모든 참조를 제거한 다음 해당 프로필을 제거합니다. 이 예제의 첫 번째 줄은 먼저 **Get-CsNetworkSite** cmdlet을 호출하여 CAC(통화 허용 제어)에 대해 구성된 모든 사이트를 검색합니다. 이 사이트 컬렉션은 BWPolicyProfileID가 LowBWProfile과 같은(-eq) 사이트만 검색하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 LowBWProfile의 BWPolicyProfileID 값이 있는 사이트만 포함하도록 범위가 좁혀진 이 컬렉션은 이러한 각 사이트를 수정하여 BWPolicyProfileID를 Null($null)로 변경하는 **Set-CSNetworkSite** cmdlet에 파이프됩니다. 지금까지 LowBWProfile의 BWPolicyProfileID가 포함된 모든 사이트를 찾고 해당 값을 Null로 설정했습니다. 현재 LowBWProfile 프로필을 사용하는 사이트는 없습니다. 이제 LowBWProfile 프로필에 대해 **Remove-CsNetworkBandwidthPolicyProfile** cmdlet을 호출하여 현재 아무 사이트에서도 사용하고 있지 않는 프로필을 제거합니다.

네트워크 구성의 어디에서도 프로필이 사용되고 있지 않음을 확인하려면 사이트 간 정책 및 네트워크 지역 링크에 대해 첫 번째 줄의 단계를 수행하십시오.

    Get-CsNetworkSite | Where-Object {$_.BWPolicyProfileID -eq "LowBWProfile"} | Set-CsNetworkSite -BWPolicyProfileID $null
    Remove-CsNetworkBandwidthPolicyProfile -Identity LowBWProfile

## 자세한 정보

대역폭 정책은 CAC(통화 허용 제어)의 일부로 특정 형식에 대한 대역폭 제한을 정의하는 데 사용됩니다. Lync Server에서는 오디오 및 비디오 형식에만 대역폭 제한이 할당될 수 있습니다. 이 cmdlet은 이러한 정책에 대한 컨테이너 프로필을 제거합니다.

중요: 사이트(**New-CsNetworkSite** cmdlet 또는 **Set-CsNetworkSite** cmdlet 사용), 사이트 간 정책(**New-CsNetworkInterSitePolicy** cmdlet 또는 **Set-CsNetworkInterSitePolicy** cmdlet 사용) 또는 네트워크 지역 링크(**New-CsNetworkRegionLink** cmdlet 또는 **Set-CsNetworkRegionLink** cmdlet 사용)에 할당된 프로필은 제거할 수 없습니다. **Remove-CsNetworkBandwidthPolicyProfile** cmdlet을 호출하여 프로필을 제거하려고 하면 오류가 발생합니다. 먼저 모든 사이트, 사이트 간 정책 및 네트워크 지역 링크에서 프로필을 제거해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsNetworkBandwidthPolicyProfile** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsNetworkBandwidthPolicyProfile"}

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
<td><p>제거할 대역폭 정책 프로필을 고유하게 식별하는 문자열 값입니다. Identity를 지정하면 하나의 프로필이 제거됩니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyProfileType 개체입니다. 네트워크 대역폭 정책 프로필 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다. Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyProfileType 유형의 개체를 제거합니다.

## 참고 항목

#### 기타 리소스

[New-CsNetworkBandwidthPolicyProfile](new-csnetworkbandwidthpolicyprofile.md)  
[Set-CsNetworkBandwidthPolicyProfile](set-csnetworkbandwidthpolicyprofile.md)  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)

