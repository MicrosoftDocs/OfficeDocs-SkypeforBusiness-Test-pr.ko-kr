---
title: Set-CsNetworkConfiguration
TOCTitle: Set-CsNetworkConfiguration
ms:assetid: d54dc154-c092-4be9-8656-f7fec3fbd835
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398927(v=OCS.15)
ms:contentKeyID: 49305148
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsNetworkConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

네트워크 구성 설정을 수정합니다. CAC(통화 허용 제어) 기능을 활성화하거나 비활성화하는 데 주로 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsNetworkConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsNetworkConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-BWPolicyProfiles <PSListModifier>] [-Confirm [<SwitchParameter>]] [-EnableBandwidthPolicyCheck <$true | $false>] [-Force <SwitchParameter>] [-InterNetworkRegionRoutes <PSListModifier>] [-InterNetworkSitePolicies <PSListModifier>] [-MediaBypassSettings <MediaBypassSettingsType>] [-NetworkRegionLinks <PSListModifier>] [-NetworkRegions <PSListModifier>] [-NetworkSites <PSListModifier>] [-Subnets <PSListModifier>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제의 명령은 전체 CAC 구성에 대해 유효성 검사를 실행한 다음 반환되는 경고 메시지에 대한 응답에 따라 CAC를 활성화합니다. CAC가 이미 활성화되어 있는 경우(즉, EnableBandwidthPolicyCheck 속성이 True인 경우) 이 명령을 실행하면 유효성 검사만 실행됩니다.

    Set-CsNetworkConfiguration -EnableBandwidthPolicyCheck $True

## 자세한 정보

네트워크 구성 개체는 Lync Server 배포 내의 전체 CAC 구성에 대한 모든 설정과 미디어 바이패스 설정을 포함합니다. 이 cmdlet을 사용하여 CAC 구성의 일부를 수정할 수 있으며, 미디어 바이패스 설정을 변경해야 하는 경우 이 cmdlet을 사용해야 합니다. 그러나 대부분의 CAC 구성 설정을 수정할 때는 개체 유형에 맞는 cmdlet을 사용하는 것이 좋습니다. 예를 들어 네트워크 지역을 사용하려면 이 cmdlet의 NetworkRegions 매개 변수를 조작하는 대신 명사 CsNetworkRegion으로 끝나는 cmdlet을 사용하십시오.

이 cmdlet의 기본적인 사용 방법은 CAC를 활성화 및 비활성화하고 미디어 바이패스 설정을 적용하는 것입니다. 구성(예: 지역, 사이트, 서브넷 등)에 필요한 다양한 구성 요소를 설정한 후에는 구성을 적용하기 전에 활성화해야 합니다. 이렇게 하려면 EnableBandwidthPolicyCheck 매개 변수를 True로 설정하면 됩니다. EnableBandwidthPolicyCheck를 True로 설정한 상태에서 이 cmdlet을 실행하면 CAC가 즉시 활성화되지 않습니다. 활성화하기 전에 여러 유효성 검사를 수행해야 설정이 제대로 구성됩니다. 설정에 오류나 불일치 항목이 있으면 경고와 함께 문제가 있어도 CAC를 계속 활성화할지 묻는 메시지가 표시됩니다. Enter 키나 Y 키를 눌러 계속하겠다고 선택하면 유효성 검사가 계속되고 다른 문제가 발견되는지 다시 묻는 메시지가 표시됩니다.

전체 유효성 검사를 실행하는 경우 각 경고가 나타날 때마다 계속하도록 선택하면 EnableBandwidthPolicyCheck가 True로 설정되고 CAC가 활성화되지만 대부분의 경우 문제를 해결할 때까지 예상대로 작동하지 않습니다. 유효성 검사 중 언제든지 경고 메시지에서 N을 입력하여 유효성 검사를 중지하도록 선택하면 유효성 검사가 종료되고 EnableBandwidthPolicyCheck가 계속 False(기본값)로 설정되어 있습니다.

EnableBandwidthPolicyCheck가 이미 True로 설정되어 있으면 **Set-CsNetworkConfiguration** cmdlet을 호출하고 True 값을 EnableBandwidthPolicyCheck 매개 변수로 전달하므로 설정을 수정하지 않고도 유효성 검사를 실행할 수 있습니다. 그뿐만 아니라 EnableBandwidthPolicyCheck가 True이면 **Set-CsNetworkConfiguration** cmdlet을 호출하여 변경하려고 하는 모든 내용에 대해 다시 유효성 검사가 실행됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsNetworkConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsNetworkConfiguration"}

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
<td><p><em>BWPolicyProfiles</em></p></td>
<td><p>선택</p></td>
<td><p>PS 목록 한정자</p></td>
<td><p>사이트 정책, 사이트 간 정책 및 네트워크 지역 링크에 할당할 수 있는 모든 대역폭 정책 프로필의 컬렉션입니다. 각 대역폭 정책 프로필에는 오디오 및/또는 비디오 연결에 대한 대역폭 제한(전체 제한 및 세션 제한)이 포함됩니다. 대역폭 정책 프로필의 전체 목록은 <strong>Get-CsNetworkBandwidthPolicyProfile</strong> cmdlet을 호출하여 검색할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableBandwidthPolicyCheck</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>이 매개 변수를 True로 설정하면 전체 CAC 구성에 대해 유효성 검사가 실행됩니다. 모든 유효성 검사를 통과하거나 모든 경고를 무시하도록 선택하면 CAC가 활성화됩니다. 유효성 검사를 통과하지 못한 경우에는 유효성 검사를 중지하도록 선택하면 EnableBandwidthPolicyCheck의 값이 변경되지 않습니다. 유효성 검사를 실행하기 전에 각 네트워크 지역 쌍 간에 지역 경로를 정의해야 합니다.</p>
<p>이 값을 False로 설정하면 CAC가 비활성화됩니다.</p>
<p>기본값: False</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>이 매개 변수는 값을 사용하지 않습니다. 이 매개 변수를 포함하면 구성을 활성화하는 등의 모든 구성 변경 작업이 경고 또는 유효성 검사 없이 수행됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Xds ID</p></td>
<td><p>이 값은 항상 Global입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>네트워크 구성 설정</p></td>
<td><p>네트워크 구성 개체에 대한 참조입니다. 이 개체는 <strong>Get-CsNetworkConfiguration</strong> cmdlet을 호출하여 검색할 수 있는 Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkConfigurationSettings 유형이어야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InterNetworkRegionRoutes</em></p></td>
<td><p>선택</p></td>
<td><p>PS 목록 한정자</p></td>
<td><p>CAC 구성 내에 정의된 모든 네트워크 지역 경로의 컬렉션입니다. 이 컬렉션의 모든 구성원은 <strong>Get-CsNetworkInterRegionRoute</strong> cmdlet을 호출하여 검색할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>InterNetworkSitePolicies</em></p></td>
<td><p>선택</p></td>
<td><p>PS 목록 한정자</p></td>
<td><p>CAC 구성 내에 정의된 네트워크 사이트 간 정책의 컬렉션입니다. 이 컬렉션의 모든 구성원은 <strong>Get-CsNetworkInterSitePolicy</strong> cmdlet을 호출하여 검색할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MediaBypassSettings</em></p></td>
<td><p>선택</p></td>
<td><p>미디어 바이패스 설정 유형</p></td>
<td><p>CAC 구성의 전역 미디어 바이패스 설정을 정의하는 개체에 대한 참조입니다. 이 값을 설정하면 기존 미디어 바이패스 설정을 모두 덮어쓰게 됩니다. 이 개체 참조는 <strong>New-CsNetworkMediaBypassConfiguration</strong> cmdlet을 호출하고 새 구성 설정을 변수에 할당하여 가져옵니다. 이 변수를 MediaBypassSettings 매개 변수로 전달하여 전역 미디어 바이패스 설정을 변경합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>NetworkRegionLinks</em></p></td>
<td><p>선택</p></td>
<td><p>PS 목록 한정자</p></td>
<td><p>CAC 구성 내에 정의된 네트워크 지역 링크의 컬렉션입니다. 각 네트워크 지역 링크는 두 영역 사이에 존재하는 연결 및 두 지역 간의 연결에 적용할 대역폭 제한을 정의합니다. 이 컬렉션의 모든 구성원은 <strong>Get-CsNetworkRegionLink</strong> cmdlet을 호출하여 검색할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>NetworkRegions</em></p></td>
<td><p>선택</p></td>
<td><p>PS 목록 한정자</p></td>
<td><p>CAC 구성 내에 정의된 네트워크 지역의 컬렉션입니다. 컬렉션의 각 지역은 네트워크 내의 허브 또는 백본을 나타냅니다. 이 컬렉션의 모든 구성원은 <strong>Get-CsNetworkRegion</strong> cmdlet을 호출하여 검색할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>NetworkSites</em></p></td>
<td><p>선택</p></td>
<td><p>PS 목록 한정자</p></td>
<td><p>CAC 구성 내에 정의된 네트워크 사이트의 컬렉션입니다. 컬렉션의 각 사이트는 영역 내의 사무실 또는 위치를 나타냅니다. 이 컬렉션의 모든 구성원은 <strong>Get-CsNetworkSite</strong> cmdlet을 호출하여 검색할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Subnets</em></p></td>
<td><p>선택</p></td>
<td><p>PS 목록 한정자</p></td>
<td><p>CAC 구성 내에 정의된 네트워크 서브넷의 컬렉션입니다. 컬렉션의 각 서브넷은 끝점이 사이트와 연결되어 있습니다. 이 컬렉션의 모든 구성원은 <strong>Get-CsNetworkSubnet</strong> cmdlet을 호출하여 검색할 수 있습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkConfigurationSettings 개체입니다. 네트워크 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

**Set-CsNetworkConfiguration** cmdlet은 값이나 개체를 반환하지 않습니다. 대신에 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkConfigurationSettings 개체의 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Remove-CsNetworkConfiguration](remove-csnetworkconfiguration.md)  
[Get-CsNetworkConfiguration](get-csnetworkconfiguration.md)  
[Get-CsNetworkSite](get-csnetworksite.md)  
[Get-CsNetworkRegionLink](get-csnetworkregionlink.md)  
[Get-CsNetworkInterSitePolicy](get-csnetworkintersitepolicy.md)  
[Get-CsNetworkInterRegionRoute](get-csnetworkinterregionroute.md)  
[Get-CsNetworkRegion](get-csnetworkregion.md)  
[Get-CsNetworkSubnet](get-csnetworksubnet.md)  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)  
[New-CsNetworkMediaBypassConfiguration](new-csnetworkmediabypassconfiguration.md)

