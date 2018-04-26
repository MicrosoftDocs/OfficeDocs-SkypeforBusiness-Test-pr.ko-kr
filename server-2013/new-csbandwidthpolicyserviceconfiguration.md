---
title: New-CsBandwidthPolicyServiceConfiguration
TOCTitle: New-CsBandwidthPolicyServiceConfiguration
ms:assetid: 0cb07eda-ffbe-48e2-b6bc-995737e5ba32
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398175(v=OCS.15)
ms:contentKeyID: 49302786
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsBandwidthPolicyServiceConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 대역폭 정책 서비스 구성을 만듭니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsBandwidthPolicyServiceConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-EnableLogging <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-LogCleanUpInterval <TimeSpan>] [-MaxLogFileSizeMb <UInt32>] [-MaxTokenLifetime <TimeSpan>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 Redmond 사이트(-Identity site:Redmond)에 새 대역폭 정책 서비스 구성을 만듭니다. 다른 매개 변수를 지정하지 않았으므로 모든 구성 값에 기본값이 사용됩니다.

    New-CsBandwidthPolicyServiceConfiguration -Identity site:Redmond

## 예제 2

이 예제에서는 Dublin 사이트(-Identity site:Dublin)에 대해 다시 새 대역폭 정책 서비스 구성을 만듭니다. 이 사이트에는 기본값을 적용하는 대신 로깅을 사용하고 로그가 정리되기 전의 기간(일)을 최대 30일로 설정하려고 합니다. 이렇게 하려면 EnableLogging 매개 변수에 True 값($True)을 전달한 다음 LogCleanupInterval 매개 변수에 30.00:00:00 값을 전달합니다. LogCleanupInterval 값은 dd.hh:mm:ss 형식의 TimeSpan 개체입니다. 여기서 d는 일, h는 시간, m은 분, s는 초입니다.

    New-CsBandwidthPolicyServiceConfiguration -Identity site:Dublin -EnableLogging $True -LogCleanupInterval 30.00:00:00

## 자세한 정보

CAC(통화 허용 제어)는 음성 또는 비디오 통화와 같은 실시간 통신 세션을 대역폭 제약 조건에 따라 설정하도록 허용할지 여부를 결정하는 방법입니다. Lync Server의 CAC 구현에는 지역, 사이트 및 서브넷 간의 대역폭을 제한하기 위해 이러한 엔터티 간의 관계 및 링크와 함께 각 엔터티가 네트워크 내에 정의됩니다. 대역폭 정책 서비스는 Lync Server 배포 내에서 CAC 기능을 수행하여 통화를 설정하기에 대역폭이 충분한지 여부를 결정하는 구성 요소입니다. 이 cmdlet은 사이트 수준에서 새 대역폭 정책 서비스를 구성합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsBandwidthPolicyServiceConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsBandwidthPolicyServiceConfiguration"}

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
<td><p>구성의 범위 및 이름이 포함된 고유 식별자입니다. 이 구성은 사이트 범위에서만 만들 수 있으므로 Identity 형식이 site:&lt;사이트 이름&gt;입니다. 여기서, &lt;사이트 이름&gt;은 구성이 적용되는 사이트의 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableLogging</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>이 매개 변수를 True로 설정하면 대역폭 정책 서비스와 관련된 CAC 실패 및 링크 상태 로그가 생성됩니다.</p>
<p>기본값: False</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>LogCleanUpInterval</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>이 시간이 경과하면 CAC 실패 및 링크 상태 로그가 제거됩니다.</p>
<p>이 값은 1일에서 60일 사이의 범위에 속해야 하며, dd.hh:mm:ss 형식으로 입력해야 합니다. 여기서 d는 일 수, h는 시간, m은 분, s는 초입니다.</p>
<p>기본값: 10일(10.00:00:00)</p></td>
</tr>
<tr class="odd">
<td><p><em>MaxLogFileSizeMb</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>로그 파일에 허용되는 최대 크기입니다. 이 매개 변수 값은 양수여야 하며 파일 크기를 메가바이트로 지정합니다.</p>
<p>기본값: 3(MB)</p></td>
</tr>
<tr class="even">
<td><p><em>MaxTokenLifetime</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>대역폭 정책 인증 서비스에서 발급한 토큰이 존재하는 최대 시간입니다.</p>
<p>이 값은 1시간에서 24시간 사이의 범위에 속해야 하며, dd.hh:mm:ss 형식으로 입력해야 합니다. 여기서 d는 일 수, h는 시간, m은 분, s는 초입니다.</p>
<p>기본값: 8시간(08:00:00)</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.BandwidthPolicyServiceConfiguration.BandwidthPolicyServiceConfiguration 유형의 개체를 만듭니다.

## 참고 항목

#### 기타 리소스

[Remove-CsBandwidthPolicyServiceConfiguration](remove-csbandwidthpolicyserviceconfiguration.md)  
[Set-CsBandwidthPolicyServiceConfiguration](set-csbandwidthpolicyserviceconfiguration.md)  
[Get-CsBandwidthPolicyServiceConfiguration](get-csbandwidthpolicyserviceconfiguration.md)

