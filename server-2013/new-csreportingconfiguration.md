---
title: New-CsReportingConfiguration
TOCTitle: New-CsReportingConfiguration
ms:assetid: 2f033456-5c1c-4313-ab17-37038a412189
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204787(v=OCS.15)
ms:contentKeyID: 49303188
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsReportingConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

서비스 범위에서 새 보고 구성 설정 컬렉션을 만듭니다. 보고 구성 설정은 Lync Server 2013 모니터링 보고서에 액세스하는 데 사용되는 URL을 지정하는 데 사용됩니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    New-CsReportingConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-ReportingUrl <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 service:MonitoringDatabase:atl-sql-001.litwareinc.com인 모니터링 데이터베이스에 할당되는 새 보고 구성 설정 컬렉션을 만듭니다. 이 예제에서 ReportingUrl 속성의 값은 "https://atl-sql-001.litwareinc.com/lync\_reports"로 설정됩니다.

    New-CsReportingConfiguration -Identity "service:MonitoringDatabase:atl-sql-001.litwareinc.com" -ReportingUrl "https://atl-sql-001.litwareinc.com/lync_reports"

## 자세한 정보

보고 구성 설정은 Lync Server 모니터링 보고서의 홈 페이지를 지정하는 데 사용됩니다. 모니터링 보고서를 사용하지 않는 경우에는 보고 구성 설정을 수정할 필요가 없습니다.

모니터링 보고서 홈 페이지의 URL을 모르는 경우 다음을 수행하여 해당 URL을 확인할 수 있습니다.

1.  모니터링 데이터베이스가 포함된 SQL Server 인스턴스에 대해 SQL Server Reporting Services 구성 관리자를 엽니다.

2.  구성 관리자에서 **보고서 관리자 URL**을 클릭한 다음 모니터링 보고서 URL을 클릭합니다. URL이 2개 표시되면 https 프로토콜을 사용하는 URL을 클릭합니다.

3.  SQL Server Reporting Services에서 **LyncServerReports**를 클릭합니다.

4.  LyncServerReports 페이지에서 **보고서 홈 페이지**를 클릭합니다. 그러면 모니터링 보고서 홈 페이지로 이동합니다. 여기서 URL을 복사한 다음 CsReportingConfiguration cmdlet과 함께 사용할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsReportingConfiguration"}

**Lync Server 제어판:** **New-CsReportingConfiguration** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>새 보고 구성 설정과 연결할 모니터링 데이터베이스의 서비스 ID입니다. 예를 들면 다음과 같습니다.</p>
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
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 내용으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수를 사용하여 호출된 이 cmdlet의 출력을 변수에 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 내용을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ReportingUrl</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>Lync Server 2013 모니터링 보고서의 URL입니다.</p></td>
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

없음. **New-CsReportingConfiguration** cmdlet은 파이프라인된 데이터를 허용하지 않습니다.

## 반환 형식

**New-CsReportingConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Reporting.ReportingConfiguration 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsReportingConfiguration](get-csreportingconfiguration.md)  
[Remove-CsReportingConfiguration](remove-csreportingconfiguration.md)  
[Set-CsReportingConfiguration](set-csreportingconfiguration.md)

