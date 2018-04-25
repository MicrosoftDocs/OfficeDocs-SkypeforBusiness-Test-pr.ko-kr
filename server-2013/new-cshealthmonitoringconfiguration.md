---
title: New-CsHealthMonitoringConfiguration
TOCTitle: New-CsHealthMonitoringConfiguration
ms:assetid: 8ed1da01-f7db-482d-b99a-777f239908e7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398718(v=OCS.15)
ms:contentKeyID: 49304351
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsHealthMonitoringConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용할 상태 모니터링 구성 설정의 새 컬렉션을 생성합니다. 관리자는 이러한 설정을 사용하여 필수 테스트 계정에 대해 사용자 이름과 암호를 제공하지 않고도 품질 보증 테스트를 실행할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsHealthMonitoringConfiguration -TargetFqdn <String> <COMMON PARAMETERS>

    New-CsHealthMonitoringConfiguration -Identity <XdsGlobalRelativeIdentity> <COMMON PARAMETERS>

    COMMON PARAMETERS: -FirstTestUserSipUri <String> -SecondTestUserSipUri <String> [-Confirm [<SwitchParameter>]] [-FirstTestSamAccountName <String>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-SecondTestSamAccountName <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 풀 atl-cs-001.litwareinc.com에 대한 상태 모니터링 구성 설정의 새 컬렉션을 만듭니다. 이러한 새 설정은 sip:kenmyer@litwareinc.com 및 sip:pilar@litwareinc.com을 미리 구성된 테스트 계정으로 사용합니다.

    New-CsHealthMonitoringConfiguration -Identity atl-cs-001.litwareinc.com -FirstTestUserSipUri "sip:kenmyer@litwareinc.com" -SecondTestUserSipUri "sip:pilar@litwareinc.com"

## 예제 2

예제 2에서는 조직의 모든 등록자 풀에 대한 상태 모니터링 구성 설정의 새 컬렉션을 만듭니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 **Get-Service** cmdlet과 Registrar 매개 변수를 사용하여 모든 등록자 풀의 컬렉션을 반환합니다. 이 컬렉션은 PoolFqdn 속성만 선택하는 **Select-Object** cmdlet에 파이프됩니다. 이 속성은 등록자 풀의 FQDN을 반환하며, 이러한 FQDN은 $x라는 변수에 저장됩니다.

두 번째 명령은 각 등록자 풀 FQDN을 통해 반복할 foreach 루프를 만듭니다. 각 FQDN에 대해 **New-CsHealthMonitoringConfiguration** cmdlet을 호출하여 $x에 저장된 FQDN을 ID로 사용하는 새 구성 설정 컬렉션을 만듭니다. 각 컬렉션에는 동일한 두 개의 테스트 계정인 sip:kenmyer@litwareinc.com과 sip:pilar@litwareinc.com이 할당됩니다.

    $x = Get-CsService -Registrar | Select-Object PoolFqdn
    foreach ($i in $x)
       {New-CsHealthMonitoringConfiguration -Identity $i.PoolFqdn -FirstTestUserSipUri "sip:kenmyer@litwareinc.com" -SecondTestUserSipUri "sip:pilar@litwareinc.com"}

## 자세한 정보

가상 트랜잭션은 Lync Server에서 사용자가 시스템 로그온, 메신저 대화 교환 또는 PSTN(공중 전화망)의 전화로 전화 걸기와 같은 일반적인 작업을 성공적으로 수행할 수 있는지 확인하는 데 사용됩니다. 이러한 테스트는 관리자가 "수동으로" 수행하거나 Microsoft System Center Operations Manager(이전 Microsoft Operations Manager)와 같은 응용 프로그램에 의해 자동으로 실행될 수 있습니다.

가상 트랜잭션은 두 가지 방식으로 수행할 수 있습니다. 많은 관리자들이 **CsHealthMonitoringConfiguration** cmdlet을 사용하여 각 등록자 풀의 테스트 계정을 설정합니다. 이러한 테스트 계정은 가상 트랜잭션에 사용하도록 미리 구성된 사용자 계정 쌍입니다. 일반적으로 이러한 계정은 테스트 계정이며 실제 사용자가 소유한 계정은 아닙니다. 풀에 이러한 테스트 계정이 구성되면 관리자는 테스트에 참여한 사용자 계정의 ID 및 자격 증명을 지정하지 않고도 해당 풀에 대해 가상 트랜잭션을 실행할 수 있습니다. 대신 가상 트랜잭션은 확인할 때 미리 구성된 테스트 계정을 자동으로 사용합니다.

또는 실제 사용자 계정을 사용하여 가상 트랜잭션을 실행할 수도 있습니다. 예를 들어 두 사용자가 메신저 대화를 교환할 수 없는 경우 관리자는 테스트 계정 쌍 대신 해당하는 두 사용자 계정을 사용하여 가상 트랜잭션을 실행할 수 있습니다. 실제 사용자 계정을 사용하여 가상 트랜잭션을 수행하도록 결정한 경우 각 사용자에 대한 자격 증명을 제공해야 합니다.

**New-CsHealthMonitoringConfiguration** cmdlet을 사용하면 등록자 풀 또는 디렉터 풀에 대한 새 상태 모니터링 구성 설정을 만들 수 있습니다. 상태 모니터링 구성 설정의 새 컬렉션을 생성할 때 풀의 FQDN(정규화된 도메인 이름)뿐만 아니라 풀 테스트 계정으로 사용할 두 계정의 SIP 주소도 지정해야 합니다. 그러나 해당 테스트 계정의 암호를 제공할 필요는 없습니다. 각 풀은 상태 모니터링 구성 설정의 단일 컬렉션만 호스트할 수 있습니다. atl-cs-001.litwareinc.com 풀에 등록자가 이미 할당된 상태에서 이 풀에 대한 새 컬렉션을 만들려고 하면 명령이 실패합니다.

테스트 사용자가 할당되지 않은 풀(디렉터 풀 및 Office Communications Server 풀 포함)이 있는 경우 **New-CsHealthMonitoringConfiguration** cmdlet을 실행하면 경고가 표시될 수 있습니다. 이러한 경고는 무시해도 됩니다. 원하는 경우 다른 풀에 속한 테스트 사용자를 디렉터 풀에 할당하여 디렉터에 대해 **Test-CsRegistration** cmdlet을 실행할 수도 있습니다. 그러나 Office Communications Server 풀에는 테스트 사용자를 할당할 수 없습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsHealthMonitoringConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsHealthMonitoringConfiguration"}

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
<td><p><em>FirstTestUserSipUri</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>이 상태 모니터링 설정 컬렉션에서 사용하도록 구성할 첫 번째 테스트 사용자의 SIP 주소입니다. SIP 주소는 &quot;sip:&quot; 접두사를 포함해야 합니다(예: -FirstTestUserSipUri &quot;sip:kenmyer@litwareinc.com&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>상태 모니터링 구성 설정을 할당할 풀의 FQDN입니다(예: -Identity atl-cs-001.litwareinc.com). 지정된 풀이 이미 상태 모니터링 구성 설정의 컬렉션을 호스트하는 경우 명령이 실패합니다.</p>
<p>Identity는 TargetFqdn 매개 변수와 같습니다. 새 설정 컬렉션을 생성할 때 두 매개 변수 중 하나를 사용할 수 있습니다. 두 매개 변수를 모두 생략하면 <strong>New-CsHealthMonitoringConfiguration</strong> cmdlet에서 Identity 입력을 요청하는 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SecondTestUserSipUri</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>이 상태 모니터링 설정 컬렉션에서 사용하도록 구성할 두 번째 테스트 사용자의 SIP 주소입니다. SIP 주소는 &quot;sip:&quot; 접두사를 포함해야 합니다(예: -SecondTestUserSipUri &quot;sip:pilar@litwareinc.com&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>TargetFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>상태 모니터링 구성 설정을 할당할 풀의 FQDN입니다(예: -TargetFqdn atl-cs-001.litwareinc.com). 지정된 풀이 이미 상태 모니터링 구성 설정의 컬렉션을 호스트하는 경우 명령이 실패합니다.</p>
<p>TargetFqdn은 Identity 매개 변수와 같습니다. 새 설정 컬렉션을 생성할 때 두 매개 변수 중 하나를 사용할 수 있습니다. 두 매개 변수를 모두 생략하면 <strong>New-CsHealthMonitoringConfiguration</strong> cmdlet에서 Identity 입력을 요청하는 메시지를 표시합니다.</p></td>
</tr>
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
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SecondTestSamAccountName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>두 번째 테스트 사용자의 SamAccountName입니다. SecondTestSamAccountName은 도메인\사용자 이름 형식으로 입력해야 합니다. 예를 들면 다음과 같습니다.</p>
<p>-SecondTestSamAccountName litwareinc\pilar</p></td>
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

없음. **New-CsHealthMonitoringConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsHealthMonitoringConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.HealthMonitoring.HealthMonitoringSettings 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsHealthMonitoringConfiguration](get-cshealthmonitoringconfiguration.md)  
[Remove-CsHealthMonitoringConfiguration](remove-cshealthmonitoringconfiguration.md)  
[Set-CsHealthMonitoringConfiguration](set-cshealthmonitoringconfiguration.md)

