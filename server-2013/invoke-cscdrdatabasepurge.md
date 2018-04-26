---
title: Invoke-CsCdrDatabasePurge
TOCTitle: Invoke-CsCdrDatabasePurge
ms:assetid: 95eb0faf-49dc-4afb-b98c-15735a4cab13
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205113(v=OCS.15)
ms:contentKeyID: 49304441
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Invoke-CsCdrDatabasePurge

 

_**마지막으로 수정된 항목:** 2015-03-09_

CDR(통화 정보 기록) 데이터베이스에서 레코드를 수동으로 제거합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Invoke-CsCdrDatabasePurge -Identity <XdsIdentity> <COMMON PARAMETERS>

    Invoke-CsCdrDatabasePurge -SqlServerFqdn <String> [-SqlInstanceName <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: -PurgeCallDetailDataOlderThanDays <Int32> -PurgeDiagnosticDataOlderThanDays <Int32> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 모니터링 데이터베이스 atl-sql-001.litwareinc.com에서 10일보다 오래된 모든 레코드(통화 정보 기록과 진단 기록 모두)를 삭제합니다.

    Invoke-CsCdrDatabasePurge -Identity "service:MonitoringDatabase:atl-sql-001.litwareinc.com" -PurgeCallDetailDataOlderThanDays 10 -PurgeDiagnosticDataOlderThanDays 10

## 예제 2

예제 2에 표시된 명령은 예제 1에 표시된 명령의 변형으로, 이 경우에는 다음 구문을 사용하여 Confirm 매개 변수가 추가됩니다.

\-Confirm:$False

해당 구문은 CDR 레코드 제거 시 일반적으로는 표시되는 확인 메시지를 표시하지 않습니다.

    Invoke-CsCdrDatabasePurge -Identity "service:MonitoringDatabase:atl-sql-001.litwareinc.com" -PurgeCallDetailDataOlderThanDays 10 -PurgeDiagnosticDataOlderThanDays 10 -Confirm:$False

## 예제 3

예제 3에서는 조직에서 사용 중인 모든 CDR 데이터베이스에서 10일보다 오래된 레코드를 모두 제거합니다. 이를 위해 예제의 첫 번째 명령은 **Get-CsService** cmdlet 및 MonitoringDatabase 매개 변수를 사용하여 모든 모니터링 데이터베이스의 컬렉션을 반환하며, 이 컬렉션은 **ForEach-Object** cmdlet에 파이프됩니다. **ForEach-Object** cmdlet은 컬렉션의 각 데이터베이스를 가져온 다음 해당 데이터베이스에 대해 **Invoke-CsCdrDatabasePurge** cmdlet을 실행하여 10일보다 오래된 모든 통화 정보 기록을 제거합니다.

    Get-CsService -MonitoringDatabase | ForEach-Object {Invoke-CsCdrDatabasePurge -Identity $_.Identity -PurgeCallDetailDataOlderThanDays 10 -PurgeDiagnosticDataOlderThanDays 10 -Confirm:$False}

## 자세한 정보

CDR(통화 정보 기록)을 사용하면 VoIP(Voice over IP) 전화 통화, 메신저 대화, 파일 전송, A/V(오디오/비디오) 회의 및 응용 프로그램 공유 세션과 같은 Lync Server 기능의 사용 내역을 추적할 수 있습니다. CDR은 통화에 참여한 사람, 통화 시간, 파일 전송 여부 등에 대한 정보를 기록합니다. 그러나 통화 자체를 녹음하지는 않습니다.

또한 CDR은 통화 오류 정보를 추적하며 피어-투-피어 세션과 전화 회의 통화에 대한 자세한 진단 데이터를 제공합니다.

통화 정보 기록은 SQL Server 데이터베이스 LcsCDR에 저장됩니다. 시간이 지남에 따라 이 데이터베이스는 매우 커질 수 있으므로, Lync Server에서는 관리자가 오래된 레코드를 데이터베이스에서 제거하는 두 가지 방법을 제공합니다. 그중 하나는 매일 오래된 CDR 레코드를 자동으로 삭제하도록 Lync Server를 구성하는 것이고, 다른 하나는 언제든지 **Invoke-CsCdrDatabasePurge** cmdlet을 사용하여 LcsCDR 데이터베이스에서 CDR 레코드를 삭제하는 것입니다. **Invoke-CsCdrDatabasePurge** cmdlet은 SQL Server 저장 프로시저 RtcCleanupDB를 호출하여 이 작업을 수행합니다.

**Invoke-CsCdrDatabasePurge** cmdlet을 호출할 때는 CDR 레코드가 저장된 모니터링 데이터베이스의 서비스 위치를 지정해야 합니다(예: MonitoringDatabase:atl-sql-001.litwareinc.com). 또한 삭제할 통화 정보 기록 및 진단 데이터 레코드의 최소 기간을 일 단위로 지정해야 합니다. 예를 들어 통화 정보 기록에 대해 최소 기간을 10일로 지정하면 10일보다 오래된 모든 통화 정보 기록이 데이터베이스에서 삭제됩니다.

이러한 레코드는 지정한 데이터베이스에 대해 제거를 사용하지 않도록 설정한 경우(CDR 구성 설정에서 EnablePurging 속성이 False로 설정된 경우)에도 삭제됩니다. EnablePurging 속성은 자동화된 CDR 레코드 제거만 제어하며, **Invoke-CsCdrDatabasePurge** cmdlet에는 아무런 영향을 주지 않습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Invoke-CsCdrDatabasePurge"}

**Lync Server 제어판:** **Invoke-CsCdrDatabasePurge** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<th>형식</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>제거할 모니터링 데이터베이스의 서비스 ID입니다. 다음 명령을 실행하면 모니터링 데이터베이스의 ID를 검색할 수 있습니다.</p>
<p>Get-CsService –MonitoringDatabase</p>
<p>Identity 매개 변수와 SqlServerFqdn 매개 변수를 같은 명령에 사용할 수는 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PurgeCallDetailDataOlderThanDays</em></p></td>
<td><p>필수</p></td>
<td><p>System.Int32</p></td>
<td><p>데이터베이스에서 제거할 통화 정보 기록의 시간을 일 단위로 지정합니다. 이 값보다 오래된 레코드는 삭제됩니다. 통화 정보 기록은 사용자/세션 보고서를 나타내며, Lync 2013 등의 클라이언트 응용 프로그램에서 업로드하는 진단 로그인 진단 데이터 보고서와는 다릅니다.</p>
<p>PurgeCallDetailDataOlderThanDays는 1에서 2147483647(포함) 사이의 정수 값으로 설정할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PurgeDiagnosticDataOlderThanDays</em></p></td>
<td><p>필수</p></td>
<td><p>System.Int32</p></td>
<td><p>데이터베이스에서 제거할 진단 데이터의 시간을 일 단위로 지정합니다. 이 값보다 오래된 레코드는 삭제됩니다. 진단 데이터 보고서는 Lync 2013 등의 클라이언트 응용 프로그램에서 업로드하는 진단 로그입니다.</p>
<p>PurgeDiagnosticDataOlderThanHours는 1에서 2147483647(포함) 사이의 정수 값으로 설정할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SqlServerFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>CDR 데이터베이스가 있는 컴퓨터의 정규화된 도메인 이름입니다. 예를 들면 다음과 같습니다.</p>
<p>-SqlServerFqdn &quot;atl-sql-001.litwareinc.com&quot;</p>
<p>Identity 매개 변수와 SqlServerFqdn 매개 변수를 같은 명령에 사용할 수는 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SqlInstanceName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>CDR 데이터베이스의 SQL Server 인스턴스 이름입니다. 예를 들면 다음과 같습니다.</p>
<p>-SqlInstanceName &quot;archinst&quot;</p></td>
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

**Invoke-CsCdrDatabasePurge** cmdlet은 Microsoft.Rtc.Management.Xds.DisplayMonitoringDatabase\#Decorated 클래스의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Invoke-CsCdrDatabasePurge** cmdlet은 Microsoft.Rtc.Management.Purge.CdrDataPurgeStatistics 클래스의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsCdrConfiguration](new-cscdrconfiguration.md)  
[Set-CsCdrConfiguration](set-cscdrconfiguration.md)

