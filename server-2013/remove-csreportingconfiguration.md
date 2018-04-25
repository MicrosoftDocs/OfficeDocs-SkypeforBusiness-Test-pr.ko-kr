---
title: Remove-CsReportingConfiguration
TOCTitle: Remove-CsReportingConfiguration
ms:assetid: 17cc1865-4bd9-4630-9947-2c432d1203b3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204711(v=OCS.15)
ms:contentKeyID: 49302935
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsReportingConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

보고 구성 설정의 기존 컬렉션을 제거합니다. 보고 구성 설정은 Lync Server 2013 모니터링 보고서 설치용 URL을 지정하는 데 사용됩니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Remove-CsReportingConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 ID가 service:MonitoringDatabase:atl-sql-002.litwareinc.com인 보고 구성 설정을 제거합니다.

    Remove-CsReportingConfiguration -Identity "service:MonitoringDatabase:atl-sql-002.litwareinc.com"

## 예제 2

예제 2에서는 조직에서 현재 사용 중인 모든 보고 구성 설정을 제거합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsReportingConfiguration** cmdlet을 사용하여 모든 보고 구성 설정의 컬렉션을 반환합니다. 이 컬렉션은 **Remove-CsReportingConfiguration** cmdlet에 파이프되며, 이 cmdlet은 컬렉션의 각 항목을 제거합니다.

    Get-CsReportingConfiguration | Remove-CsReportingConfiguration

## 예제 3

예제 3에 표시된 명령은 보고 URL이 https://atl-sql-002.litwareinc.com/lync\_reports로 설정된 모든 보고 구성 설정을 삭제합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsReportingConfiguration** cmdlet을 사용하여 현재 사용 중인 모든 보고 구성 설정을 반환합니다. 이 컬렉션은 **Where-Object** cmdlet에 파이프되며, 이 cmdlet은 ReportingURL 속성이 https://atl-sql-002.litwareinc.com/lync\_reports인 설정만 선택합니다. 필터링된 컬렉션은 **Remove-CsReportingConfiguration** cmdlet에 파이프되며, 이 cmdlet은 컬렉션의 각 항목을 제거합니다.

    Get-CsReportingConfiguration | Where-Object {$_.ReportingUrl -eq "https://atl-sql-002.litwareinc.com/lync_reports" | Remove-CsReportingConfiguration

## 자세한 정보

보고 구성 설정은 Lync Server 모니터링 보고서의 홈 페이지를 지정하는 데 사용됩니다. 모니터링 보고서를 사용하지 않는 경우에는 보고 구성 설정을 수정할 필요가 없습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsReportingConfiguration"}

**Lync Server 제어판:** **Remove-CsReportingConfiguration** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>해당 보고 구성 설정을 제거할 모니터링 데이터베이스의 서비스 ID입니다. 예를 들면 다음과 같습니다.</p>
<p>-Identity &quot;Service:MonitoringDatabase:atl-sql-001.litwareinc.com&quot;</p></td>
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

**Remove-CsReportingConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Reporting.ReportingConfiguration 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Remove-CsReportingConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Reporting.ReportingConfiguration 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsReportingConfiguration](get-csreportingconfiguration.md)  
[New-CsReportingConfiguration](new-csreportingconfiguration.md)  
[Set-CsReportingConfiguration](set-csreportingconfiguration.md)

