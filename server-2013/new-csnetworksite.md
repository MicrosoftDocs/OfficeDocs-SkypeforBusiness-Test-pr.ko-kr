---
title: New-CsNetworkSite
TOCTitle: New-CsNetworkSite
ms:assetid: 55134dd4-eb2b-483b-8b3d-e9e42ac1acc2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398365(v=OCS.15)
ms:contentKeyID: 49303671
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsNetworkSite

 

_**마지막으로 수정된 항목:** 2015-03-09_

CAC(통화 허용 제어) 또는 E9-1-1(Enhanced 9-1-1)에 사용할 새 네트워크 사이트를 만듭니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsNetworkSite -Identity <XdsGlobalRelativeIdentity> <COMMON PARAMETERS>

    New-CsNetworkSite -NetworkSiteID <String> <COMMON PARAMETERS>

    COMMON PARAMETERS: -NetworkRegionID <String> [-BWPolicyProfileID <String>] [-BypassID <String>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-EnableLocationBasedRouting <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-LocationPolicy <String>] [-VoiceRoutingPolicy <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 Vancouver라는 새 네트워크 사이트를 만듭니다. 사이트 이름은 Identity 매개 변수의 값으로 지정합니다. NetworkRegionID 매개 변수에도 값을 지정했는데 이 매개 변수는 사이트를 지역(이 예에서는 NorthAmerica)과 연결합니다. BypassID 값이 자동으로 생성됩니다. BypassID 값을 수동으로 설정하는 방법은 권장되지 않습니다.

이 예제의 명령은 BWPolicyProfileID 매개 변수를 포함하지 않습니다. 나중에 **Set-CsNetworkSite** cmdlet을 사용하여 값을 추가하지 않으면(또는 추가하기 전까지) 이 사이트에는 미디어 연결에 대한 대역폭 제한이 없게 됩니다.

    New-CsNetworkSite -Identity Vancouver -NetworkRegionID NorthAmerica

## 예제 2

예제 2에서는 Paris라는 새 네트워크 사이트를 만듭니다. 사이트 이름은 Identity 매개 변수의 값으로 지정합니다. 예제 1에 나오는 것처럼 NetworkRegionID에도 값을 지정하며 이번에는 EMEA 지역을 지정합니다. 이번에도 cmdlet이 BypassID를 생성하도록 허용하는 권장되는 방법을 따릅니다. 예제 1과는 다르게 이 예제에서는 BWPolicyProfileID 매개 변수의 값을 LowBWLimits로 지정합니다. 이 프로필과 연결된 정책이 이 사이트에 사용됩니다.

    New-CsNetworkSite -Identity Paris -NetworkRegionID EMEA -BWPolicyProfileID LowBWLimits

## 자세한 정보

네트워크 사이트는 각 CAC 또는 E9-1-1 배포 영역 내에 구성된 사무실 또는 위치입니다. 이 cmdlet은 새 사이트를 만들고 선택적으로 이를 지역과 연결합니다. 예를 들어 북미 지역의 네트워크 영역은 Chicago, Redmond 및 Vancouver와 같은 네트워크 사이트와 연결할 수 있습니다. 조직 내의 모든 사이트에는 해당 사이트에 대역폭 제한이 없더라도 CAC 네트워크 사이트를 만들어야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsNetworkSite** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsNetworkSite"}

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
<td><p>새로 만든 네트워크 사이트에 대한 고유한 식별자입니다. 사이트는 전역 범위에서만 만들어지므로 이 매개 변수로 범위를 지정할 필요는 없으며 대신 Lync Server 배포 내의 모든 네트워크 사이트에서 고유한 문자열을 포함하면 됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>NetworkRegionID</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>이 사이트가 연결되어 있는 네트워크 지역의 ID입니다. BypassID(자동으로 생성하거나 수동으로 지정)를 제공하려고 하거나 네트워크 구성의 EnableBandwidthPolicyCheck 속성이 True인 경우 이 매개 변수에는 값이 포함되어야 합니다. <strong>Get-CsNetworkConfiguration</strong> cmdlet을 호출하여 네트워크 구성 설정을 검색할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>NetworkSiteID</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>이 값은 Identity와 동일합니다. Identity와 NetworkSiteID에 값을 모두 지정할 수 없습니다. 둘 중 하나에 입력한 값이 자동으로 둘 모두에 사용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>BWPolicyProfileID</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 사이트의 대역폭 제한을 정의하는 대역폭 정책 프로필의 ID입니다. <strong>Get-CsNetworkBandwidthPolicyProfile</strong> cmdlet을 호출하여 사용 가능한 프로필 목록을 검색할 수 있습니다.</p>
<p>이 매개 변수의 값을 지정하면 NetworkRegionID 매개 변수의 값도 지정해야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>BypassID</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>GUID(Globally Unique Identifier)입니다. 이 GUID는 네트워크 사이트를 CAC 또는 E9-1-1 네트워크 구성 내의 미디어 바이패스 설정으로 매핑하는 데 사용됩니다. <strong>New-CsNetworkMediaBypassConfiguration</strong> cmdlet을 호출할 때 이 BypassID 값을 사용합니다.</p>
<p>이 매개 변수에 값을 지정하지 않으면 값이 자동으로 생성되지만 NetworkRegionID 매개 변수에 값을 제공했을 경우에만 해당됩니다. NetworkRegionID 매개 변수를 제공하지 않으면 BypassID가 생성되지 않습니다. NetworkRegionID 매개 변수에 값을 제공하지 않으면 BypassID 매개 변수에 명시적으로 값을 제공할 수 없습니다.</p>
<p>명시적으로 값을 지정하는 경우 값 형식은 GUID 형식(예: 3b24a047-dce6-48b2-9f20-9fbff17ed62a)이어야 합니다. 자동 생성하는 것이 좋습니다. 값을 수동으로 입력하면 값을 자동으로 생성하지 않을지를 확인하는 메시지가 표시됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>사이트를 설명하는 문자열입니다. 이 매개 변수를 사용하면 사이트가 어떤 용도로 사용되고 어디에 있는지에 대해 ID만 사용할 때보다 더 자세한 설명을 제공할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableLocationBasedRouting</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 전화를 거는 사용자와 받는 사용자의 위치를 모두 고려하여 음성 라우팅을 관리합니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocationPolicy</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 사이트와 연결된 위치 정책의 이름입니다. 위치 정책은 특정 E9-1-1 설정을 사이트에 할당합니다. <strong>Get-CsLocationPolicy</strong> cmdlet을 호출하여 위치 정책의 목록을 검색할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>VoiceRoutingPolicy</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>사이트에 할당할 사용자별 음성 라우팅 정책입니다. 예를 들면 다음과 같습니다.</p>
<p>-VoiceRoutingPolicy &quot;RedmondVoiceRouting”</p>
<p>사용자별 정책을 지정해야 합니다. 전역 및/또는 사이트 정책은 VoiceRoutingPolicy 매개 변수를 사용하여 할당할 수 없습니다.</p>
<p>이 매개 변수는 Lync Server 2013의 2013년 2월 릴리스에서 도입되었습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.DisplayNetworkSiteType 유형의 개체를 만듭니다.

## 참고 항목

#### 기타 리소스

[Remove-CsNetworkSite](remove-csnetworksite.md)  
[Set-CsNetworkSite](set-csnetworksite.md)  
[Get-CsNetworkSite](get-csnetworksite.md)  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)  
[New-CsNetworkMediaBypassConfiguration](new-csnetworkmediabypassconfiguration.md)  
[Get-CsLocationPolicy](get-cslocationpolicy.md)  
[Get-CsNetworkConfiguration](get-csnetworkconfiguration.md)

