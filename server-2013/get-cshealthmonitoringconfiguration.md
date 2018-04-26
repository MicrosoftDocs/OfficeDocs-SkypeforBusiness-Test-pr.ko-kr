---
title: Get-CsHealthMonitoringConfiguration
TOCTitle: Get-CsHealthMonitoringConfiguration
ms:assetid: 843876f1-8aa6-4324-a981-8eded4d3b16d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398667(v=OCS.15)
ms:contentKeyID: 49304246
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsHealthMonitoringConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 현재 사용 중인 상태 모니터링 구성 설정에 대한 정보를 반환합니다. 관리자는 이러한 설정을 사용하여 필수 테스트 계정에 대해 사용자 이름과 암호를 제공하지 않고도 품질 보증 테스트를 실행할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsHealthMonitoringConfiguration [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsHealthMonitoringConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에서는 조직에서 현재 사용 중인 모든 상태 모니터링 구성 설정을 반환합니다.

    Get-CsHealthMonitoringConfiguration

## 예제 2

예제 2의 명령은 상태 모니터링 구성 설정 컬렉션 하나를 반환합니다. Identity가 atl-cs-001.litwareinc.com인 설정입니다.

    Get-CsHealthMonitoringConfiguration -Identity atl-cs-001.litwareinc.com

## 예제 3

예제 3에서는 litwareinc.com 도메인에 대해 만들어진 모든 상태 모니터링 구성 설정을 반환합니다. 이 작업을 수행하기 위해 Filter 매개 변수를 포함하여 **Get-CsHealthMonitoringConfiguration** cmdlet을 호출합니다. 필터 값 "\*.litwareinc.com"은 ID가 문자열 값 ".litwareinc.com"으로 끝나는 설정만 반환되도록 합니다.

    Get-CsHealthMonitoringConfiguration -Filter *.litwareinc.com

## 예제 4

예제 4의 명령은 SIP 주소가 sip:kenmyer@litwareinc.com인 사용자가 테스트 사용자로 포함된 모든 상태 모니터링 구성 설정을 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsHealthMonitoringConfiguration** cmdlet을 추가 매개 변수 없이 호출합니다. 이렇게 하면 현재 조직에서 사용 중인 모든 상태 모니터링 구성 설정의 컬렉션이 반환됩니다. 이 컬렉션은 FirstTestUserSipUri 속성이 "sip:kenmyer@litwareinc.com"과 같거나 SecondTestUserSipUri 속성이 "sip:kenmyer@litwareinc.com"과 같은 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 따라서 Ken Myer의 SIP 주소가 첫 번째 또는 두 번째 테스트 사용자로 사용되는 설정 컬렉션이 모두 반환됩니다.

    Get-CsHealthMonitoringConfiguration | Where-Object {$_.FirstTestUserSipUri -eq "sip:kenmyer@litwareinc.com" -or $_.SecondTestUserSipUri -eq " sip:kenmyer@litwareinc.com"}

## 자세한 정보

가상 트랜잭션은 Lync Server에서 사용자가 시스템 로그온, 메신저 대화 교환 또는 PSTN(공중 전화망)의 전화로 전화 걸기와 같은 일반적인 작업을 성공적으로 수행할 수 있는지 확인하는 데 사용됩니다. 이러한 테스트는 관리자가 "수동으로" 수행하거나 Microsoft System Center Operations Manager(이전 Microsoft Operations Manager)와 같은 응용 프로그램에 의해 자동으로 실행될 수 있습니다.

가상 트랜잭션은 두 가지 방법으로 수행할 수 있습니다. 많은 관리자들이 **CsHealthMonitoringConfiguration** cmdlet을 사용하여 각 등록자 또는 디렉터 풀의 테스트 계정을 설정합니다. 이러한 테스트 계정은 가상 트랜잭션에 사용하도록 미리 구성된 사용자 계정 쌍입니다. 일반적으로 이러한 계정은 테스트 계정이며 실제 사용자가 소유한 계정은 아닙니다. 풀에 테스트 계정이 구성되면 관리자는 테스트에 참여한 사용자 계정의 ID 및 자격 증명을 지정하지 않고도 해당 풀에 대해 가상 트랜잭션을 실행할 수 있습니다. 사실 가상 트랜잭션은 검사를 수행할 때 미리 구성된 테스트 계정을 자동으로 사용합니다.

또는 실제 사용자 계정을 사용하여 가상 트랜잭션을 실행할 수도 있습니다. 예를 들어 두 사용자가 메신저 대화를 교환할 수 없는 경우 관리자는 테스트 계정 쌍 대신 해당하는 두 사용자 계정을 사용하여 가상 트랜잭션을 실행할 수 있습니다. 실제 사용자 계정을 사용하여 가상 트랜잭션을 수행하도록 결정한 경우 각 사용자에 대한 자격 증명을 제공해야 합니다.

**Get-CsHealthMonitoringConfiguration** cmdlet은 현재 조직에서 사용되는 상태 모니터링 구성 설정에 대한 정보를 검색할 수 있는 방법을 제공합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsHealthMonitoringConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsHealthMonitoringConfiguration"}

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
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>검색할 상태 모니터링 구성 설정을 지정할 때 와일드카드 문자를 사용할 수 있도록 합니다. 예를 들어 -Filter *.litwareinc.com 구문은 litwareinc.com 도메인에 대해 구성된 모든 설정을 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>상태 모니터링 구성 설정이 할당된 풀의 FQDN(정규화된 도메인 이름)입니다(예: -Identity atl-cs-001.litwareinc.com).</p>
<p>이 매개 변수를 포함하지 않으면 <strong>Get-CsHealthMonitoringConfiguration</strong> cmdlet은 현재 사용 중인 모든 상태 모니터링 구성 설정에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 상태 모니터링 구성 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsHealthMonitoringConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsHealthMonitoringConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.HealthMonitoring.HealthMonitoringSettings 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsHealthMonitoringConfiguration](new-cshealthmonitoringconfiguration.md)  
[Remove-CsHealthMonitoringConfiguration](remove-cshealthmonitoringconfiguration.md)  
[Set-CsHealthMonitoringConfiguration](set-cshealthmonitoringconfiguration.md)

