---
title: New-CsNetworkRegionLink
TOCTitle: New-CsNetworkRegionLink
ms:assetid: 61a6a7be-8078-4d59-a78a-2f241f6bf800
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398437(v=OCS.15)
ms:contentKeyID: 49303817
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsNetworkRegionLink

 

_**마지막으로 수정된 항목:** 2015-03-09_

CAC(통화 허용 제어)에 대해 구성된 두 영역 사이에 링크를 생성합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsNetworkRegionLink -NetworkRegionLinkID <String> <COMMON PARAMETERS>

    New-CsNetworkRegionLink -Identity <XdsGlobalRelativeIdentity> <COMMON PARAMETERS>

    COMMON PARAMETERS: -NetworkRegionID1 <String> -NetworkRegionID2 <String> [-BWPolicyProfileID <String>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 NA\_EMEA라는 새 네트워크 지역 링크를 생성하여 영역 NorthAmerica 및 EMEA를 연결합니다. 지역 링크 이름은 Identity 매개 변수 값으로 지정됩니다. 이 값은 NetworkRegionLinkID 값으로 자동으로 할당됩니다. 연결되는 두 개의 네트워크 지역은 링크 생성을 위한 필수 매개 변수입니다(이 경우 NorthAmerica 및 EMEA 지역). 이 예제에서는 BWPolicyProfile 매개 변수에도 값을 할당했습니다. 이 매개 변수는 해당 대역폭 정책 프로필(LowBWLimits)에 정의된 대역폭 제한을 이러한 지역 간 연결에 할당합니다. BWPolicyProfileID를 제공하지 않는 경우 이 두 지역 간 연결에 대해 대역폭 제한이 적용되지 않습니다. 사이트 간에는 여전히 제한이 있을 수 있습니다. 자세한 내용은 **New-CsNetworkSite** cmdlet 도움말 항목을 참조하십시오.

    New-CsNetworkRegionLink -Identity NA_EMEA -NetworkRegionID1 NorthAmerica -NetworkRegionID2 EMEA -BWPolicyProfileID LowBWLimits

## 자세한 정보

네트워크 내의 지역은 실제 WAN 연결을 통해 연결됩니다. 이 cmdlet은 두 영역 사이에 링크를 정의하고 이러한 영역 간 오디오 및 비디오 연결에 대한 대역폭 제한을 설정합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsNetworkRegionLink** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsNetworkRegionLink"}

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
<td><p>새로 생성된 네트워크 지역 링크의 고유 식별자입니다. 네트워크 지역 링크는 전역 범위에서만 만들어지므로 이 식별자는 범위를 지정할 필요가 없습니다. 대신 이 식별자는 해당 링크를 식별하는 고유 이름 문자열을 포함합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>NetworkRegionID1</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>NetworkRegionID2 매개 변수로 식별되는 영역에 연결된 영역의 ID(NetworkRegionID)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>NetworkRegionID2</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>NetworkRegionID1 매개 변수로 식별되는 영역에 연결된 영역의 ID(NetworkRegionID)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>NetworkRegionLinkID</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>이 값은 Identity와 같습니다. Identity와 NetworkRegionLinkID를 모두 지정할 수는 없습니다. 한 항목에 대해 입력한 값이 자동으로 두 항목에 모두 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>BWPolicyProfileID</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 링크에 대한 대역폭 제한을 정의하는 대역폭 정책 프로필의 ID입니다. <strong>Get-CsNetworkBandwidthPolicyProfile</strong> cmdlet을 호출하여 사용 가능한 프로필 목록을 검색할 수 있습니다.</p></td>
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
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
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

이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.NetworkRegionLinkType 유형의 개체를 생성합니다.

## 참고 항목

#### 기타 리소스

[Remove-CsNetworkRegionLink](remove-csnetworkregionlink.md)  
[Set-CsNetworkRegionLink](set-csnetworkregionlink.md)  
[Get-CsNetworkRegionLink](get-csnetworkregionlink.md)  
[Get-CsNetworkBandwidthPolicyProfile](get-csnetworkbandwidthpolicyprofile.md)  
[New-CsNetworkSite](new-csnetworksite.md)

