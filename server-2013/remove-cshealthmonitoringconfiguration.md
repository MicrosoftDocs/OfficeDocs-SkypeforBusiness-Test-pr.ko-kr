---
title: Remove-CsHealthMonitoringConfiguration
TOCTitle: Remove-CsHealthMonitoringConfiguration
ms:assetid: 2e401908-2366-4e67-ba5b-68ba7ece166e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425794(v=OCS.15)
ms:contentKeyID: 49303180
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsHealthMonitoringConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 상태 모니터링 구성 설정 컬렉션을 제거합니다. 관리자는 이러한 설정을 사용하여 필수 테스트 계정에 대해 사용자 이름과 암호를 제공하지 않고도 품질 보증 테스트를 실행할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsHealthMonitoringConfiguration -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Identity가 atl-cs-001.litwareinc.com인 상태 모니터링 구성 설정 컬렉션을 삭제합니다. Identity가 고유해야 하므로 이 명령은 최대 한 개의 설정 컬렉션을 삭제합니다.

    Remove-CsHealthMonitoringConfiguration -Identity atl-cs-001.litwareinc.com

## 예제 2

예제 2에서는 현재 사용 중인 상태 모니터링 구성 설정을 모두 삭제합니다. 이 작업을 수행하기 위해 이 명령은 먼저 매개 변수 없이 **Get-CsHealthMonitoringConfiguration** cmdlet을 호출합니다. 그러면 조직의 모든 상태 모니터링 구성 설정 컬렉션이 반환됩니다. 이 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CsHealthMonitoringConfiguration** cmdlet에 파이프됩니다.

    Get-CsHealthMonitoringConfiguration | Remove-CsHealthMonitoringConfiguration 

## 예제 3

예제 3에서는 litwareinc.com 도메인에 대해 만들어진 모든 상태 모니터링 구성 설정을 반환합니다. 이 작업을 수행하기 위해 Filter 매개 변수와 함께 **Get-CsHealthMonitoringConfiguration** cmdlet을 호출합니다. 필터 값 "\*.litwareinc.com"은 ID가 문자열 값 ".litwareinc.com"으로 끝나는 설정만 반환되도록 합니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CsHealthMonitoringConfiguration** cmdlet에 파이프됩니다.

    Get-CsHealthMonitoringConfiguration -Filter *.litwareinc.com  | Remove-CsHealthMonitoringConfiguration 

## 예제 4

예제 4에 표시된 명령은 SIP 주소가 sip:kenmyer@litwareinc.com인 사용자를 테스트 사용자 중 하나로 포함하는 모든 상태 모니터링 구성 설정을 삭제합니다. 이 작업을 수행하기 위해 이 명령은 먼저 추가 매개 변수 없이 **Get-CsHealthMonitoringConfiguration** cmdlet을 호출합니다. 그러면 조직에서 현재 사용 중인 모든 상태 모니터링 구성 설정 컬렉션이 반환됩니다. 이 컬렉션은 FirstTestUserSipUri 속성이 "sip:kenmyer@litwareinc.com"과 같거나 SecondTestUserSipUri 속성이 "sip:kenmyer@litwareinc.com"과 같은 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 이러한 설정은 **Remove-CsHealthMonitoringConfiguration** cmdlet에 파이프되어 제거됩니다.

    (Get-CsHealthMonitoringConfiguration | Where-Object {$_.FirstTestUserSipUri -eq "sip:kenmyer@litwareinc.com" -or $_.SecondTestUserSipUri -eq " sip:kenmyer@litwareinc.com"}) | Remove-CsHealthMonitoringConfiguration

## 자세한 정보

가상 트랜잭션은 Lync Server에서 사용자가 시스템 로그온, 메신저 대화 교환 또는 PSTN(공중 전화망)의 전화로 전화 걸기와 같은 일반적인 작업을 성공적으로 수행할 수 있는지 확인하는 데 사용됩니다. 이러한 테스트는 관리자가 "수동으로" 수행하거나 Microsoft System Center Operations Manager(이전 Microsoft Operations Manager)와 같은 응용 프로그램에 의해 자동으로 실행될 수 있습니다.

가상 트랜잭션은 두 가지 방식으로 수행할 수 있습니다. 많은 관리자들이 **CsHealthMonitoringConfiguration** cmdlet을 사용하여 각 등록자 풀의 테스트 계정을 설정합니다. 이러한 테스트 계정은 가상 트랜잭션에 사용하도록 미리 구성된 사용자 계정 쌍입니다. 일반적으로 이는 테스트 계정이며 실제 사용자에게 속한 계정이 아닙니다. 풀에 이러한 테스트 계정이 구성되면 관리자는 테스트에 참여한 사용자 계정의 ID 및 자격 증명을 지정하지 않고도 해당 풀에 대해 가상 트랜잭션을 실행할 수 있습니다. 대신 가상 트랜잭션은 확인할 때 미리 구성된 테스트 계정을 자동으로 사용합니다.

또는 실제 사용자 계정을 사용하여 가상 트랜잭션을 실행할 수도 있습니다. 예를 들어 두 사용자가 메신저 대화를 교환할 수 없는 경우 관리자는 테스트 계정 쌍 대신 해당하는 두 사용자 계정을 사용하여 가상 트랜잭션을 실행할 수 있습니다. 실제 사용자 계정을 사용하여 가상 트랜잭션을 수행하도록 결정한 경우 각 사용자에 대한 자격 증명을 제공해야 합니다.

**Remove-CsHealthMonitoringConfiguration** cmdlet을 사용하면 조직에서 사용하도록 구성된 모든 상태 모니터링 구성 설정을 제거할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsHealthMonitoringConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsHealthMonitoringConfiguration"}

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
<td><p>삭제할 상태 모니터링 구성 설정을 호스트하는 풀의 FQDN(정규화된 도메인 이름)입니다. 예: -Identity atl-cs-001.litwareinc.com.</p></td>
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
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.HealthMonitoring.HealthMonitoringSettings 개체입니다. **Remove-CsHealthMonitoringConfiguration** cmdlet은 상태 모니터링 구성 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Remove-CsHealthMonitoringConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.HealthMonitoring.HealthMonitoringSettings 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsHealthMonitoringConfiguration](get-cshealthmonitoringconfiguration.md)  
[New-CsHealthMonitoringConfiguration](new-cshealthmonitoringconfiguration.md)  
[Set-CsHealthMonitoringConfiguration](set-cshealthmonitoringconfiguration.md)

