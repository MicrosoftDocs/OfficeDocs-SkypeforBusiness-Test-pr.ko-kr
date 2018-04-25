---
title: New-CsNetworkInterSitePolicy
TOCTitle: New-CsNetworkInterSitePolicy
ms:assetid: e127153f-a1c3-4a31-8dd3-f08d45eca800
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398994(v=OCS.15)
ms:contentKeyID: 49305298
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsNetworkInterSitePolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

CAC(통화 허용 제어) 구성 내에 직접 연결된 사이트 간 대역폭 제한을 정의하는 새 네트워크 사이트 간 정책을 만듭니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsNetworkInterSitePolicy -InterNetworkSitePolicyID <String> <COMMON PARAMETERS>

    New-CsNetworkInterSitePolicy -Identity <XdsGlobalRelativeIdentity> <COMMON PARAMETERS>

    COMMON PARAMETERS: -NetworkSiteID1 <String> -NetworkSiteID2 <String> [-BWPolicyProfileID <String>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 연결된 사이트 Reno와 Portland 간의 대역폭을 제한하는 새 네트워크 사이트 간 정책을 만듭니다. 이 사이트 간의 오디오 및 비디오 연결에 대한 대역폭 제한은 대역폭 정책 프로필 LowBWLimits에 대해 구성된 설정에 따라 제한됩니다.

    New-CsNetworkInterSitePolicy -Identity Reno_Portland -NetworkSiteID1 Reno -NetworkSiteID2 Portland -BWPolicyProfileID LowBWLimits

## 자세한 정보

네트워크 사이트에서 직접 연결을 공유하는 경우 이 두 사이트 간에 오디오 및 비디오 연결에 대한 대역폭 제한이 정의될 수 있습니다. 이 cmdlet은 직접 연결된 두 사이트에 대역폭 제한 정책을 적용하는 네트워크 사이트 정책을 만듭니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsNetworkInterSitePolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsNetworkInterSitePolicy"}

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
<td><p>새로 만든 네트워크 사이트 간 정책의 고유 식별자입니다. 네트워크 사이트 간 정책은 전역 범위에서만 만들어지므로 이 식별자는 범위를 지정할 필요가 없습니다. 대신 해당 사이트 정책을 식별하는 고유 이름인 문자열을 포함합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>InterNetworkSitePolicyID</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>이 값은 Identity와 같습니다. 따라서 Identity와 InterNetworkSitePolicyID를 둘 다 지정할 수 없습니다. 둘 중 하나의 값을 입력하면 두 매개 변수 모두에 자동으로 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>NetworkSiteID1</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>이 정책과 연결된 두 사이트 중 하나의 ID(NetworkSiteID)입니다. NetworkSiteID1과 NetworkSiteID2의 조합은 고유해야 합니다. 예를 들어 Reno와 Portland를 연결하는 두 개의 사이트 정책을 정의할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>NetworkSiteID2</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>이 정책과 연결된 두 사이트 중 하나의 ID(NetworkSiteID)입니다. NetworkSiteID1과 NetworkSiteID2의 조합은 고유해야 합니다. 예를 들어 Reno와 Portland를 연결하는 두 개의 사이트 정책을 정의할 수 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>BWPolicyProfileID</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 사이트 정책에 대한 제한을 정의하는 대역폭 정책 프로필 ID입니다. <strong>Get-CsNetworkBandwidthPolicyProfile</strong> cmdlet을 호출하여 사용 가능한 프로필 목록을 검색할 수 있습니다.</p></td>
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
<td><p>변경 내용을 적용하기 전에 표시될 수 있는 확인 메시지를 숨깁니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkSitePolicyType 유형의 개체를 만듭니다.

## 참고 항목

#### 기타 리소스

[Remove-CsNetworkInterSitePolicy](remove-csnetworkintersitepolicy.md)  
[Set-CsNetworkInterSitePolicy](set-csnetworkintersitepolicy.md)  
[Get-CsNetworkInterSitePolicy](get-csnetworkintersitepolicy.md)

