---
title: Set-CsNetworkInterSitePolicy
TOCTitle: Set-CsNetworkInterSitePolicy
ms:assetid: 973979bc-db2c-47a6-909e-5949a927f51c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398772(v=OCS.15)
ms:contentKeyID: 49304453
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsNetworkInterSitePolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

CAC(통화 허용 제어) 구성 내에서 직접 연결된 사이트 간의 대역폭 제한을 정의하는 기존 네트워크 사이트 간 정책을 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsNetworkInterSitePolicy [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Set-CsNetworkInterSitePolicy [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-BWPolicyProfileID <String>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-NetworkSiteID1 <String>] [-NetworkSiteID2 <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 Identity가 Reno\_Portland인 네트워크 사이트 정책을 수정합니다. BWPolicyProfileID 매개 변수를 사용하여 이 네트워크 사이트 정책과 연결된 대역폭 정책 프로필을 HighBWLimits로 변경합니다.

    Set-CsNetworkInterSitePolicy -Identity Reno_Portland -BWPolicyProfileID HighBWLimits

## 자세한 정보

두 네트워크 사이트가 직접 링크를 공유하는 경우 이러한 두 사이트 간에 오디오 및 비디오 연결에 대한 대역폭 제한이 정의될 수 있습니다. 이 cmdlet은 직접 연결된 두 사이트에 대역폭 제한을 두는 네트워크 사이트 간 정책을 수정합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsNetworkInterSitePolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsNetworkInterSitePolicy"}

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
<td><p>이 사이트 정책에 대한 제한을 정의하는 대역폭 정책 프로필의 ID입니다. <strong>Get-CsNetworkBandwidthPolicyProfile</strong> cmdlet을 호출하여 사용 가능한 프로필 목록을 검색할 수 있습니다.</p></td>
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
<td><p>수정할 네트워크 사이트 정책의 고유 식별자입니다. 네트워크 사이트 정책은 전역 범위에서만 만들어지므로 이 식별자에서는 범위를 지정할 필요가 없습니다. 대신 여기에는 사이트 정책을 식별하는 고유한 이름인 문자열이 포함됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>네트워크 사이트 간 정책 유형</p></td>
<td><p>메모리에서 수정된 사이트 정책에 대한 개체 참조입니다. 이 개체는 Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkSitePolicyType 유형이어야 하며 <strong>Get-CsNetworkInterSitePolicy</strong> cmdlet을 호출하여 검색할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>NetworkSiteID1</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>이 정책과 연결된 두 사이트 중 하나의 Identity(NetworkSiteID)입니다. NetworkSiteID1과 NetworkSiteID2의 조합은 고유해야 합니다. 예를 들어 Reno와 Portland를 연결하는 두 사이트 정책을 정의할 수 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>NetworkSiteID2</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>이 정책과 연결된 두 사이트 중 하나의 Identity(NetworkSiteID)입니다. NetworkSiteID1과 NetworkSiteID2의 조합은 고유해야 합니다. 예를 들어 Reno와 Portland를 연결하는 두 사이트 정책을 정의할 수 없습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkSitePolicyType 개체입니다. 네트워크 사이트 간 정책 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다. Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkSitePolicyType 유형의 개체를 수정합니다.

## 참고 항목

#### 기타 리소스

[New-CsNetworkInterSitePolicy](new-csnetworkintersitepolicy.md)  
[Remove-CsNetworkInterSitePolicy](remove-csnetworkintersitepolicy.md)  
[Get-CsNetworkInterSitePolicy](get-csnetworkintersitepolicy.md)

