---
title: Set-CsHealthMonitoringConfiguration
TOCTitle: Set-CsHealthMonitoringConfiguration
ms:assetid: 375af06c-70c8-4775-8c7b-3b3f8fd9afcc
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425847(v=OCS.15)
ms:contentKeyID: 49303300
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsHealthMonitoringConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

상태 모니터링 구성 설정의 기존 컬렉션을 수정합니다. 관리자는 이러한 설정을 사용하여 필수 테스트 계정에 대해 사용자 이름과 암호를 제공하지 않고도 품질 보증 테스트를 실행할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsHealthMonitoringConfiguration [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Set-CsHealthMonitoringConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-FirstTestSamAccountName <String>] [-FirstTestUserSipUri <String>] [-Force <SwitchParameter>] [-SecondTestSamAccountName <String>] [-SecondTestUserSipUri <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 atl-cs-001.litwareinc.com 풀에 대한 상태 모니터링 구성 설정에 할당된 첫 번째 테스트 사용자를 구성합니다. 이 예에서는 새 테스트 사용자의 SIP 주소를 sip:kenmyer@litwareinc.com으로 설정하며 이 테스트 사용자의 SamAccountName은 kenmyer로 설정합니다.

    Set-CsHealthMonitoringConfiguration -Identity atl-cs-001.litwareinc.com -FirstTestUserSipUri "sip:kenmyer@litwareinc.com" -FirstTestSamAccountName "litwareinc\kenmyer"

## 예제 2

예제 2는 예제 1에 표시된 명령의 변형입니다. 이 경우에는 조직에서 사용 중인 상태 모니터링 구성 설정의 각 컬렉션에 동일한 테스트 사용자를 할당합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsHealthMonitoringConfiguration** cmdlet을 사용하여 모든 상태 모니터링 구성 설정의 컬렉션을 반환합니다. 이 컬렉션은 동일한 첫 번째 테스트 사용자 SIP 주소와 SamAccountName을 컬렉션의 각 항목에 할당하는 **Set-CsHealthMonitoringConfiguration** cmdlet에 파이프됩니다.

    Get-CsHealthMonitoringConfiguration | Set-CsHealthMonitoringConfiguration -FirstTestUserSipUri "sip:kenmyer@litwareinc.com" -FirstTestSamAccountName "litwareinc\kenmyer"

## 예제 3

예제 3에서는 상태 구성 설정의 컬렉션에 할당된 첫 번째 테스트 사용자를 검색하고 바꾸는 방법을 보여 줍니다. 이 예에서는 SIP 주소가 sip:pilar@litwareinc.com인 사용자가 컬렉션의 첫 번째 테스트 사용자로 나타날 때마다 대체됩니다.

이 작업을 수행하기 위해 먼저 **Get-CsHealthMonitoringConfiguration** cmdlet을 추가 매개 변수 없이 호출하여 현재 조직에서 사용 중인 모든 상태 모니터링 구성 설정의 컬렉션을 반환합니다. 이 컬렉션은 FirstTestUserSipUri 속성이 sip:pilar@litwareinc.com과 같은(-eq) 항목만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목에 대해 FirstTestUserSipUri 속성 값을 sip:kenmyer@litwareinc.com으로 설정하고 FirstTestSamAccountName 속성 값을 kenmyer로 설정하는 **Set-CsHealthMonitoringConfiguration** cmdlet에 파이프됩니다.

    Get-CsHealthMonitoringConfiguration | Where-Object {$_.FirstTestUserSipUri -eq "sip:pilar@litwareinc.com"} | Set-CsHealthMonitoringConfiguration -FirstTestUserSipUri "sip:kenmyer@litwareinc.com" -FirstTestSamAccountName "litwareinc\kenmyer"

## 자세한 정보

가상 트랜잭션은 Lync Server에서 사용자가 시스템 로그온, 메신저 대화 교환 또는 PSTN(공중 전화망)의 전화로 전화 걸기와 같은 일반적인 작업을 성공적으로 수행할 수 있는지 확인하는 데 사용됩니다. 이러한 테스트는 관리자가 "수동으로" 수행하거나 Microsoft System Center Operations Manager(이전 Microsoft Operations Manager)와 같은 응용 프로그램에 의해 자동으로 실행될 수 있습니다.

가상 트랜잭션은 두 가지 방식으로 수행할 수 있습니다. 많은 관리자들이 **CsHealthMonitoringConfiguration** cmdlet을 사용하여 각 등록자 풀의 테스트 계정을 설정합니다. 이러한 테스트 계정은 가상 트랜잭션에 사용하도록 미리 구성된 사용자 계정 쌍입니다. 일반적으로 이는 테스트 계정이며 실제 사용자에게 속한 계정이 아닙니다. 풀에 테스트 계정이 구성되면 관리자는 테스트에 참여한 사용자 계정의 ID 및 자격 증명을 지정하지 않고도 해당 풀에 대해 가상 트랜잭션을 실행할 수 있습니다. 대신 가상 트랜잭션은 확인할 때 미리 구성된 테스트 계정을 자동으로 사용합니다.

또는 실제 사용자 계정을 사용하여 가상 트랜잭션을 실행할 수 있습니다. 예를 들어 두 사용자가 메신저 대화를 교환할 수 없는 경우 관리자는 테스트 계정 쌍 대신 해당하는 두 사용자 계정을 사용하여 가상 트랜잭션을 실행할 수 있습니다. 실제 사용자 계정을 사용하여 가상 트랜잭션을 수행하도록 결정한 경우 각 사용자에 대한 자격 증명을 제공해야 합니다.

상태 모니터링 구성 설정을 구성한 후에는 **Set-CsHealthMonitoringConfiguration** cmdlet을 사용하여 언제든지 이러한 설정을 수정할 수 있습니다. 이 cmdlet을 사용하면 풀에 사용하도록 구성된 한 가지(또는 두 가지 모두) 테스트 계정을 변경할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsHealthMonitoringConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsHealthMonitoringConfiguration"}

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
<td><p><em>FirstTestSamAccountName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>첫 번째 테스트 사용자의 SamAccountName입니다. FirstTestSamAccountName은 도메인\사용자 이름 형식으로 입력해야 합니다. 예를 들면 다음과 같습니다.</p>
<p>-FirstTestSamAccountName litwareinc\kenmyer</p></td>
</tr>
<tr class="odd">
<td><p><em>FirstTestUserSipUri</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 상태 모니터링 설정의 컬렉션에서 사용하도록 구성된 첫 번째 테스트 사용자의 SIP 사용자입니다. SIP 주소는 &quot;sip:&quot; 접두사를 포함해야 합니다(예: -FirstTestUserSipUri &quot;sip:kenmyer@litwareinc.com&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>수정할 상태 모니터링 구성 설정이 할당된 풀의 FQDN(정규화된 도메인 이름)입니다 (예: -Identity atl-cs-001.litwareinc.com).</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>상태 모니터링 설정 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SecondTestSamAccountName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>두 번째 테스트 사용자의 SamAccountName입니다. SecondTestSamAccountName은 도메인\사용자 이름 형식으로 입력해야 합니다. 예를 들면 다음과 같습니다.</p>
<p>-SecondTestSamAccountName litwareinc\pilar</p></td>
</tr>
<tr class="even">
<td><p><em>SecondTestUserSipUri</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 상태 모니터링 설정의 컬렉션에서 사용하도록 구성된 두 번째 테스트 사용자의 SIP 사용자입니다. SIP 주소는 &quot;sip:&quot; 접두사를 포함해야 합니다(예: -FirstTestUserSipUri &quot;sip:pilar@litwareinc.com&quot;).</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.HealthMonitoring.HealthMonitoringSettings 개체입니다. **Set-CsHealthMonitoringConfiguration** cmdlet은 상태 모니터링 구성 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Set-CsHealthMonitoringConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.HealthMonitoring.HealthMonitoringSettings 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsHealthMonitoringConfiguration](get-cshealthmonitoringconfiguration.md)  
[New-CsHealthMonitoringConfiguration](new-cshealthmonitoringconfiguration.md)  
[Remove-CsHealthMonitoringConfiguration](remove-cshealthmonitoringconfiguration.md)

