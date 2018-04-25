---
title: Remove-CsNetworkConfiguration
TOCTitle: Remove-CsNetworkConfiguration
ms:assetid: d6945015-67f7-4f04-87ae-7cb977650d96
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398938(v=OCS.15)
ms:contentKeyID: 49305174
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsNetworkConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 배포의 모든 네트워크 구성 설정을 기본값으로 다시 설정합니다. 그러면 전체 CAC(통화 허용 제어) 배포 및 관련 E9-1-1 구성이 삭제됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsNetworkConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 모든 CAC, 위치, E9-1-1 네트워크 및 미디어 바이패스 설정을 제거합니다. 여기서 Confirm 매개 변수는 모든 항목을 삭제하기 전에 이 작업을 수행할지 확인하는 메시지를 표시하는 데 사용됩니다.

    Remove-CsNetworkConfiguration -Identity Global -Confirm

## 자세한 정보

경고: 이 cmdlet을 실행하면 CAC, E9-1-1 지역 및 사이트, 미디어 바이패스 등을 포함하여 전체 네트워크 구성이 삭제됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsNetworkConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsNetworkConfiguration"}

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
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>ID는 항상 Global입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다. 이 cmdlet에는 항상 이 매개 변수를 사용하는 것이 좋습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경 내용을 적용하기 전에 표시될 수 있는 확인 메시지를 숨깁니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkConfigurationSettings 개체입니다. 네트워크 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 개체를 반환하지 않습니다. Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkConfigurationSettings 개체와 같은 유형의 개체를 제거합니다.

## 참고 항목

#### 기타 리소스

[Set-CsNetworkConfiguration](set-csnetworkconfiguration.md)  
[Get-CsNetworkConfiguration](get-csnetworkconfiguration.md)  
[Get-CsNetworkSite](get-csnetworksite.md)  
[Get-CsNetworkRegionLink](get-csnetworkregionlink.md)  
[Get-CsNetworkInterSitePolicy](get-csnetworkintersitepolicy.md)  
[Get-CsNetworkInterRegionRoute](get-csnetworkinterregionroute.md)  
[Get-CsNetworkRegion](get-csnetworkregion.md)  
[Get-CsNetworkSubnet](get-csnetworksubnet.md)  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)

