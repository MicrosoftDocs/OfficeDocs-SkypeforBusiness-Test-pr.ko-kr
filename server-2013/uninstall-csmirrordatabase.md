---
title: Uninstall-CsMirrorDatabase
TOCTitle: Uninstall-CsMirrorDatabase
ms:assetid: a5b14259-6cf6-46b5-ae8d-3b5e4428dfaf
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205159(v=OCS.15)
ms:contentKeyID: 49304622
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Uninstall-CsMirrorDatabase

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 2013 관리 셸 미러 데이터베이스를 제거합니다. 데이터베이스 미러를 통해 서로 다른 서버에 있는 두 데이터베이스 복사본을 동시에 유지 관리할 수 있습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Uninstall-CsMirrorDatabase -DatabaseType <Application | Archiving | Monitoring | User | Provision | CentralAdmin | Lyss | Registrar | Edge | PersistentChat | PersistentChatCompliance | CentralMgmt> -SqlServerFqdn <Fqdn> [-SqlInstanceName <String>] [-Confirm [<SwitchParameter>]] [-DropExistingDatabasesOnMirror <SwitchParameter>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 atl-mirror-001.litwareinc.com 컴퓨터의 SQL Server 인스턴스 RTC에서 사용자 데이터베이스를 제거합니다. DropExistingDatabaseOnMirror 매개 변수가 포함되었으므로 이 명령은 실제 사용자 데이터베이스 미러도 삭제합니다.

    Uninstall-CsMirrorDatabase -SqlServerFqdn "atl-mirror-001.litwareinc.com" -SqlInstanceName "RTC" -DatabaseType "User" -DropExistingDatabasesOnMirror

## 자세한 정보

미러 데이터베이스를 사용하면 두 데이터베이스 복사본을 동시에 유지 관리할 수 있습니다. 데이터를 데이터베이스 A에 쓰면 해당 데이터의 복사본이 미러 데이터베이스에도 기록됩니다. 따라서 데이터베이스 A를 사용할 수 없을 때 즉시 교체할 수 있습니다. 사용자의 작업 중단과 데이터 손실을 최소화하면서 미러 데이터베이스로 "장애 조치(failover)"할 수 있기 때문입니다.

미러 데이터베이스는 [Install-CsMirrorDatabase](install-csmirrordatabase.md) cmdlet을 사용하여 설치 및 구성할 수 있습니다. 미러 데이터베이스를 제거해야 하는 경우에는 **Uninstall-CsMirrorDatabase** cmdlet을 사용하면 됩니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Uninstall-CsMirrorDatabase"}

Lync Server 제어판: **Uninstall-CsMirrorDatabase** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>DatabaseType</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.DatabaseNameType</p></td>
<td><p>설치할 미러 데이터베이스의 유형입니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>Application</p>
<p>Archiving</p>
<p>CentralAdmin</p>
<p>CentralMgmt</p>
<p>Edge</p>
<p>Lyss</p>
<p>Monitoring</p>
<p>PersistentChat</p>
<p>PersistentChatCompliance</p>
<p>Provision</p>
<p>Registrar</p>
<p>User</p></td>
</tr>
<tr class="even">
<td><p><em>SqlServerFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>제거할 데이터베이스가 포함된 컴퓨터의 FQDN(정규화된 도메인 이름)입니다. 예를 들면 다음과 같습니다.</p>
<p>-SqlServerFqdn atl-sql-001.litwareinc.com</p>
<p>주 SQL Server 컴퓨터의 FQDN이어야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DropExistingDatabasesOnMirror</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 미러 서버에서 미러링된 데이터베이스의 기존 복사본을 삭제합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet이 실행될 때 만들어진 로그 파일에 대한 파일 경로를 지정할 수 있도록 합니다. 예를 들면 다음과 같습니다.</p>
<p>Report &quot;C:\Logs\UnInstallDatabaseMirror.html&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>SqlInstanceName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>데이터베이스를 설치할 데이터베이스 인스턴스의 이름입니다. 데이터베이스 인스턴스는 데이터베이스 파일에 대한 액세스를 제공하는 실행 중인 프로세스의 집합입니다. 이 매개 변수를 생략하면 <strong>Uninstall-CsMirrorDatabase</strong> cmdlet에서 기본 SQL Server 인스턴스를 사용합니다.</p></td>
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

없음. **Uninstall-CsMirrorDatabase** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음.

## 참고 항목

#### 기타 리소스

[Get-CsDatabaseMirrorState](get-csdatabasemirrorstate.md)  
[Install-CsMirrorDatabase](install-csmirrordatabase.md)

