---
title: Set-CsBandwidthPolicyServiceConfiguration
TOCTitle: Set-CsBandwidthPolicyServiceConfiguration
ms:assetid: b39af1ca-465d-4598-96a3-e19283ddf731
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412863(v=OCS.15)
ms:contentKeyID: 49304774
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsBandwidthPolicyServiceConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 대역폭 정책 서비스 구성을 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsBandwidthPolicyServiceConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsBandwidthPolicyServiceConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-EnableLogging <$true | $false>] [-Force <SwitchParameter>] [-LogCleanUpInterval <TimeSpan>] [-MaxLogFileSizeMb <UInt32>] [-MaxTokenLifetime <TimeSpan>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 Redmond라는 사이트(-Identity site:Redmond)에 대한 대역폭 정책 서비스를 수정합니다. 로깅을 사용하도록 설정하고, 토큰의 최대 수명을 3시간으로 변경하며, 로그 정리 기간을 5일로 변경하도록 구성을 수정합니다. 이 모든 작업이 하나의 명령으로 수행됩니다. 먼저, 로깅을 사용하도록 설정하기 위해 EnableLogging 매개 변수를 True($true)로 설정합니다. 그런 다음 MaxTokenLifetime 매개 변수에서 3시간을 나타내는 값인 3:00:00을 받습니다. 마지막으로 LogCleanUpInterval 매개 변수에서 5일을 나타내는 값인 5.00:00:00을 받습니다.

    Set-CsBandwidthPolicyServiceConfiguration -Identity site:Redmond -EnableLogging $true -MaxTokenLifetime 3:00:00 -LogCleanUpInterval 5.00:00:00

## 자세한 정보

CAC(통화 허용 제어)는 음성 또는 비디오 통화와 같은 실시간 통신 세션을 대역폭 제약 조건에 따라 설정하도록 허용할지 여부를 결정하는 방법입니다. Lync Server의 CAC 구현에는 지역 사이트 및 서브넷 간의 대역폭을 제한하기 위해 이러한 엔터티 간의 관계 및 링크와 함께 각 엔터티가 네트워크 내에 정의됩니다. 대역폭 정책 서비스는 Lync Server 배포 내에서 CAC 기능을 수행하여 통화를 설정하기에 대역폭이 충분한지 여부를 결정하는 구성 요소입니다. 이 cmdlet은 기존 대역폭 정책 서비스 구성을 수정합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsBandwidthPolicyServiceConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsBandwidthPolicyServiceConfiguration"}

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
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableLogging</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>이 매개 변수를 True로 설정하면 대역폭 정책 서비스와 관련된 CAC 실패 및 링크 상태 로그가 생성됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>변경할 구성의 고유 식별자입니다. 이 식별자는 범위(전역 구성의 경우) 또는 범위와 이름(site:Redmond와 같은 사이트 수준 구성의 경우)으로 구성됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>대역폭 정책 서비스 구성</p></td>
<td><p>대역폭 정책 서비스 구성 개체에 대한 참조입니다. 이 개체의 유형은 BandwidthPolicyServiceConfiguration이어야 하며, <strong>Get-CsBandwidthPolicyServiceConfiguration</strong> cmdlet을 호출하여 검색할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>LogCleanUpInterval</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>이 시간이 경과하면 CAC 실패 및 링크 상태 로그가 제거됩니다.</p>
<p>이 값은 1일에서 60일 사이의 범위에 속해야 하며, dd.hh:mm:ss 형식으로 입력해야 합니다. 여기서 d는 일 수, h는 시간, m은 분, s는 초입니다. 예를 들어 20일은 20.00:00:00입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaxLogFileSizeMb</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>로그 파일에 허용되는 최대 크기입니다. 이 매개 변수 값은 양수여야 하며 파일 크기를 메가바이트로 지정합니다. 예를 들어 허용되는 로그 파일의 최대 크기를 10메가바이트로 지정하려면 값을 10으로 입력합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MaxTokenLifetime</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>대역폭 정책 인증 서비스에서 발급한 토큰이 존재하는 최대 시간입니다.</p>
<p>이 값은 1시간에서 24시간 사이의 범위에 속해야 하며, dd.hh:mm:ss 형식으로 입력해야 합니다. 여기서 d는 일 수, h는 시간, m은 분, s는 초입니다. 예를 들어 12시간에 해당하는 값은 12:00:00입니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.BandwidthPolicyServiceConfiguration.BandwidthPolicyServiceConfiguration 개체입니다. 대역폭 정책 서비스 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다. Microsoft.Rtc.Management.WritableConfig.Settings.BandwidthPolicyServiceConfiguration.BandwidthPolicyServiceConfiguration 유형의 개체를 수정합니다.

## 참고 항목

#### 기타 리소스

[New-CsBandwidthPolicyServiceConfiguration](new-csbandwidthpolicyserviceconfiguration.md)  
[Remove-CsBandwidthPolicyServiceConfiguration](remove-csbandwidthpolicyserviceconfiguration.md)  
[Get-CsBandwidthPolicyServiceConfiguration](get-csbandwidthpolicyserviceconfiguration.md)

