---
title: Get-CsNetworkConfiguration
TOCTitle: Get-CsNetworkConfiguration
ms:assetid: 08bc8eca-b244-4d5e-b089-1cc95605ba14
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398140(v=OCS.15)
ms:contentKeyID: 49302729
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsNetworkConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

CAC(통화 허용 제어), E9-1-1(Enhanced 9-1-1) 및 미디어 바이패스에 대한 전역 설정을 검색합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsNetworkConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsNetworkConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

이 예제에서는 네트워크 구성 설정을 검색합니다. 이러한 설정은 전역 범위에서만 정의되므로 한 개의 항목만 반환됩니다.

    Get-CsNetworkConfiguration

## 예제 2

하나의 미디어 바이패스 설정 집합만 존재하며 전역적으로 적용됩니다. 이러한 설정은 전체 네트워크 구성의 일부로 저장됩니다. 이 명령은 먼저 **Get-CsNetworkConfiguration** cmdlet을 호출하여 해당 구성을 검색한 다음 구성의 MediaBypassSettings 속성을 검색합니다.

    (Get-CsNetworkConfiguration).MediaBypassSettings

## 자세한 정보

네트워크 구성 개체에는 해당 구성의 활성화 여부를 비롯하여 Lync Server 배포 내의 전체 CAC 구성과 미디어 바이패스에 대한 모든 전역 설정이 포함되어 있습니다. 이 cmdlet을 사용하여 이러한 구성과 설정을 검색할 수 있습니다. 그러나 EnableBandwidthPolicyCheck 및 MediaBypassSettings 이외의 CAC 구성 설정을 검색하는 경우 개체 유형과 관련된 cmdlet을 사용하는 것이 좋습니다. 예를 들어 네트워크 영역을 검색하려는 경우 일반적으로 **Get-CsNetworkRegion** cmdlet을 호출하는 것이 **Get-CsNetworkConfiguration** cmdlet을 호출한 다음 해당 구성의 NetworkRegions 속성을 검색하는 것보다 더 쉽습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsNetworkConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsNetworkConfiguration"}

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
<td><p>항상 한 개의 네트워크 구성만 있으므로 이 cmdlet에는 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>이 값은 항상 Global입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 네트워크 구성을 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

**Get-CsNetworkConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkConfigurationSettings 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Remove-CsNetworkConfiguration](remove-csnetworkconfiguration.md)  
[Set-CsNetworkConfiguration](set-csnetworkconfiguration.md)  
[Get-CsNetworkSite](get-csnetworksite.md)  
[Get-CsNetworkRegionLink](get-csnetworkregionlink.md)  
[Get-CsNetworkInterSitePolicy](get-csnetworkintersitepolicy.md)  
[Get-CsNetworkInterRegionRoute](get-csnetworkinterregionroute.md)  
[Get-CsNetworkRegion](get-csnetworkregion.md)  
[Get-CsNetworkSubnet](get-csnetworksubnet.md)  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)

