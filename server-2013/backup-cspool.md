---
title: Backup-CsPool
TOCTitle: Backup-CsPool
ms:assetid: 66ec46de-e1e7-4e33-961d-7ef785059c48
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204955(v=OCS.15)
ms:contentKeyID: 49303884
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Backup-CsPool

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정한 Lync Server 2013 풀의 백업 복사본을 만듭니다. 이 cmdlet은 Lync Server 2013에 도입되었습니다.

## 구문

    Backup-CsPool -PoolFqdn <Fqdn> [-Category <UserData | CMS>] [-Confirm [<SwitchParameter>]] [-FailedOverPoolOnly <SwitchParameter>] [-Force <SwitchParameter>] [-FullBackup <SwitchParameter>] [-LocalStore <SwitchParameter>] [-Report <String>] [-RetryCount <Int32>] [-SteadyState <SwitchParameter>] [-WaitTime <TimeSpan>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 atl-cs-001.litwareinc.com 풀을 백업합니다.

    Backup-CsPool -PoolFqdn "atl-cs-001.litwareinc.com"

## 예제 2

예제 2에서는 atl-cs-001.litwareinc.com 풀에 대해 "안정 상태" 백업을 수행합니다.

    Backup-CsPool -PoolFqdn "atl-cs-001.litwareinc.com" -SteadyState

## 자세한 정보

관리자는 **Backup-CsPool** cmdlet을 사용하여 지정한 백업 풀에 사용자 데이터 및 전화 회의 데이터를 복사할 수 있습니다. 기본 풀에 장애가 발생하거나 사용할 수 없는 상태가 되면 해당 기본 풀에 있는 사용자를 백업 풀로 "장애 조치"할 수 있습니다. 이러한 사용자는 백업 풀을 통해 Lync Server에 로그온할 수 있으며 홈 풀이 복원될 때까지 해당 풀을 계속 사용할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Backup-CsPool"} 명령을 실행합니다.

**Lync Server 제어판**: **Backup-CsPool** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>PoolFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>백업할 풀의 정규화된 도메인 이름입니다. 예를 들면 다음과 같습니다.</p>
<p>-SourcePoolFqdn &quot;atl-cs-001.litwareinc.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Category</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Hadr.BackupService.BackupCategory</p></td>
<td><p>백업할 Lync Server 모듈을 선택할 수 있습니다. 이 매개 변수가 없으면 모든 모듈이 백업됩니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>* CMS</p>
<p>* UserData</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>FailedOverPoolOnly</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 지정하면 풀이 장애 조치(failover)된 상태일 때만 백업을 수행합니다. 이 매개 변수를 사용하는 경우에는 FullBackup 매개 변수도 사용해야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>FullBackup</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 백업 서비스가 최종 상태에 도달할 때까지 백업을 시작하지 않습니다. 같은 명령에서 FullBackup 매개 변수와 SteadyState 매개 변수를 모두 사용할 수는 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 토폴로지 정보를 검색합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet이 실행될 때 만들어진 로그 파일에 대한 파일 경로입니다. 예를 들면 다음과 같습니다.</p>
<p>-Report &quot;C:\Logs\BackupPool.html&quot;</p>
<p>이 파일이 이미 있는 경우 cmdlet을 실행할 때 덮어쓰게 됩니다.</p>
<p>기본적으로 보고서는 사용자 프로필의 AppData\Local\Temp 폴더에 기록됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>RetryCount</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>오류가 발생할 때까지 Backup-CsPool이 백업 서비스 호출을 시도하는 최대 횟수입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SteadyState</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 백업 서비스가 안정 상태에 도달할 때까지 백업을 시작하지 않습니다. &quot;안정 상태&quot;는 풀이 읽기 전용 또는 장애 조치(failover)/장애 복구(failback) 모드로 전환되어 백업해야 하는 새 데이터를 더 이상 생성하지 않는 상태입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WaitTime</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>백업 서비스가 전체 상태인지 안정 상태인지를 확인할 때까지 cmdlet이 대기하는 시간(초)입니다.</p></td>
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

없음. **Backup-CsPool** cmdlet은 파이프라인된 데이터를 허용하지 않습니다.

## 반환 형식

없음.

## 참고 항목

#### 기타 리소스

[Get-CsBackupServiceConfiguration](get-csbackupserviceconfiguration.md)  
[Get-CsBackupServiceStatus](get-csbackupservicestatus.md)  
[Get-CsPoolBackupRelationship](get-cspoolbackuprelationship.md)

