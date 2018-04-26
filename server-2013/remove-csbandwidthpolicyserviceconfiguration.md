---
title: Remove-CsBandwidthPolicyServiceConfiguration
TOCTitle: Remove-CsBandwidthPolicyServiceConfiguration
ms:assetid: cf920168-3f65-4747-86cd-d3e287c84349
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398877(v=OCS.15)
ms:contentKeyID: 49305088
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsBandwidthPolicyServiceConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 대역폭 정책 서비스 구성을 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsBandwidthPolicyServiceConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 Redmond 사이트(-Identity site:Redmond)에 대해 정의된 대역폭 정책 서비스 구성을 제거합니다.

    Remove-CsBandwidthPolicyServiceConfiguration -Identity site:Redmond

## 예제 2

예제 2에서는 로깅을 사용하지 않는 모든 대역폭 정책 서비스 구성을 제거합니다. 이 작업을 수행하기 위해 이 예제에서는 먼저 **Get-CsBandwidthPolicyServiceConfiguration** cmdlet을 호출합니다. 그러면 Lync Server 배포의 모든 대역폭 정책 서비스 구성 컬렉션이 반환됩니다. 이 컬렉션은 EnableLogging 속성이 False($False)와 같은(-eq) 구성으로 컬렉션 범위를 좁히는 **Where-Object** cmdlet에 파이프됩니다. 이렇게 하면 로깅을 사용하지 않는 구성 컬렉션만 남게 됩니다. 그런 다음 이 컬렉션은 컬렉션의 모든 항목을 제거하는 **Remove-CsBandwidthPolicyServiceConfiguration** cmdlet에 파이프됩니다.

    Get-CsBandwidthPolicyServiceConfiguration | Where-Object {$_.EnableLogging -eq $False} | Remove-CsBandwidthPolicyServiceConfiguration

## 자세한 정보

CAC(통화 허용 제어)는 음성 또는 비디오 통화와 같은 실시간 통신 세션을 대역폭 제약 조건에 따라 설정하도록 허용할지 여부를 결정하는 방법입니다. Lync Server의 CAC 구현에는 지역 사이트 및 서브넷 간의 대역폭을 제한하기 위해 이러한 엔터티 간의 관계 및 링크와 함께 각 엔터티가 네트워크 내에 정의됩니다. 대역폭 정책 서비스는 Lync Server 배포 내에서 CAC 기능을 수행하여 통화를 설정하기에 대역폭이 충분한지 여부를 결정하는 구성 요소입니다. 이 cmdlet은 사이트 수준에 정의된 대역폭 정책 서비스 구성을 제거합니다. 또한 이 cmdlet을 사용하여 전역 대역폭 정책 서비스를 "제거"할 수 있습니다. 그러나 전역 서비스는 실제로 제거되는 것이 아니라 기본값으로 다시 설정됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsBandwidthPolicyServiceConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsBandwidthPolicyServiceConfiguration"}

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
<td><p>제거할 구성의 고유 식별자입니다. 이 식별자는 범위(전역 구성의 경우) 또는 범위와 이름(site:Redmond와 같은 사이트 수준 구성의 경우)으로 구성됩니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.BandwidthPolicyServiceConfiguration.BandwidthPolicyServiceConfiguration 개체입니다. 대역폭 정책 서비스 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다. Microsoft.Rtc.Management.WritableConfig.Settings.BandwidthPolicyServiceConfiguration.BandwidthPolicyServiceConfiguration 유형의 개체를 제거합니다.

## 참고 항목

#### 기타 리소스

[New-CsBandwidthPolicyServiceConfiguration](new-csbandwidthpolicyserviceconfiguration.md)  
[Set-CsBandwidthPolicyServiceConfiguration](set-csbandwidthpolicyserviceconfiguration.md)  
[Get-CsBandwidthPolicyServiceConfiguration](get-csbandwidthpolicyserviceconfiguration.md)

