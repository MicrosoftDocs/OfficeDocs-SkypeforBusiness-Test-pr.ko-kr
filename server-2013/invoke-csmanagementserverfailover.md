---
title: Invoke-CsManagementServerFailover
TOCTitle: Invoke-CsManagementServerFailover
ms:assetid: 060ab02a-1267-4b35-bc2b-6a4a35616be0
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204647(v=OCS.15)
ms:contentKeyID: 49302687
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Invoke-CsManagementServerFailover

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 2013 중앙 관리 저장소를 장애 조치(failover)하는 프로세스를 호출합니다. 중앙 관리 저장소가 장애 조치(failover)되면 주 데이터베이스는 미리 할당된 미러 데이터베이스 또는 지정된 백업 데이터베이스로 바뀝니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Invoke-CsManagementServerFailover -BackupSqlServerFqdn <Fqdn> -Force <SwitchParameter> [-BackupMirrorSqlInstanceName <String>] [-BackupMirrorSqlServerFqdn <Fqdn>] [-BackupSqlInstanceName <String>] <COMMON PARAMETERS>

    Invoke-CsManagementServerFailover [-Restore <SwitchParameter>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Report <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Lync Server 2013에 대해 중앙 관리 저장소를 장애 조치(failover)합니다. 이 경우 기존 관리 저장소가 redmond-cs-001.litwareinc.com 컴퓨터에 있는 RTC 데이터베이스 인스턴스로 바뀝니다.

    Invoke-CsManagementServerFailover -BackupSqlServerFqdn "redmond-cs-001.litwareinc.com" - BackupSqlInstanceName "RTC" -Force

## 자세한 정보

관리자는 **Invoke-CsManagementServerFailover** cmdlet을 사용하여 CMS(중앙 관리 서버)를 "장애 조치(failover)"할 수 있습니다. **Invoke-CsManagementServerFailover** cmdlet은 CMS를 장애 조치(failover)하는 두 가지 방법을 제공합니다. 그 중 하나는 SQL Server의 지정한 백업 인스턴스로 장애 조치(failover)하는 것이고, 다른 하나는 미리 할당된 미러 데이터베이스로 장애 조치(failover)하는 것입니다. 지정된 백업 인스턴스로 장애 조치(failover)하려면 BackupSqlServerFqdn 및 BackupSqlInstanceName 매개 변수를 사용합니다. 미러 데이터베이스로 장애 조치(failover)하려면 BackupMirrorSqlServerFqdn 및 BackupMirrorSqlInstanceName 매개 변수를 사용합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Invoke-CsManagementServerFailover"}

**Lync Server 제어판:** **Invoke-CsManagementServerFailover** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>BackupSqlServerFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>SQL Server 백업 데이터베이스를 호스트하는 컴퓨터의 정규화된 도메인 이름입니다. <strong>Invoke-CsManagementServerFailover</strong> cmdlet을 재해 복구 모드에서 실행 중인 경우 이 매개 변수가 필요합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다. <strong>Invoke-CsManagementServerFailover</strong> cmdlet을 재해 복구 모드에서 실행 중인 경우 이 매개 변수가 필요합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>BackupMirrorSqlInstanceName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>미러 데이터베이스에 대한 SQL Server 인스턴스입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>BackupMirrorSqlServerFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>SQL Server 미러 데이터베이스를 호스트하는 컴퓨터의 정규화된 도메인 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>BackupSqlInstanceName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>백업 데이터베이스에 대한 SQL Server 인스턴스입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet이 실행될 때 만들어지는 로그 파일의 파일 경로를 지정할 수 있습니다(예: -Report &quot;C:\Logs\CMSFailover.html&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>Restore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>지정하는 경우 기존 중앙 관리 서버 데이터베이스를 복원합니다.</p></td>
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

없음. **Invoke-CsManagementServerFailover** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음

## 참고 항목

#### 기타 리소스

[Invoke-CsDatabaseFailover](invoke-csdatabasefailover.md)

