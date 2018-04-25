---
title: Install-CsMirrorDatabase
TOCTitle: Install-CsMirrorDatabase
ms:assetid: 6e3acdfb-39da-4aa4-b125-1ea542971da3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204986(v=OCS.15)
ms:contentKeyID: 49303971
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Install-CsMirrorDatabase

 

_**마지막으로 수정된 항목:** 2015-03-09_

미러 데이터베이스를 Lync Server 2013 데이터베이스와 연결합니다. 데이터베이스 미러를 통해 서로 다른 서버에 있는 두 데이터베이스 복사본을 동시에 유지 관리할 수 있습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Install-CsMirrorDatabase -ConfiguredDatabases <SwitchParameter> -SqlServerFqdn <Fqdn> [-ForDefaultInstance <SwitchParameter>] [-ForInstance <String>] <COMMON PARAMETERS>

    Install-CsMirrorDatabase -DatabaseType <Application | Archiving | Monitoring | User | Provision | CentralAdmin | Lyss | Registrar | Edge | PersistentChat | PersistentChatCompliance | CentralMgmt> -SqlServerFqdn <Fqdn> [-SqlInstanceName <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: -FileShare <String> [-Confirm [<SwitchParameter>]] [-DatabasePathMap <Hashtable>] [-DropExistingDatabasesOnMirror <SwitchParameter>] [-ExcludeDatabaseList <String[]>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 미리 정의된 데이터베이스를 설치합니다. ConfiguredDatabases 매개 변수는 **Install-CsMirrorDatabase** cmdlet이 현재 토폴로지를 사용하여 데이터베이스를 결정하도록 합니다.

    Install-CsMirrorDatabase -ConfiguredDatabases -FileShare "\\atl-fs-001\DbBackup" -SqlServerFqdn "atl-primary-001.litwareinc.com" -DropExisitingDatabasesOnMirror

## 자세한 정보

미러 데이터베이스를 사용하면 두 데이터베이스 복사본을 동시에 유지 관리할 수 있습니다. 데이터를 데이터베이스 A에 쓰면 해당 데이터의 복사본이 미러 데이터베이스에도 기록됩니다. 따라서 데이터베이스 A를 사용할 수 없을 때 즉시 교체할 수 있습니다. 사용자의 작업 중단과 데이터 손실을 최소화하면서 미러 데이터베이스로 "장애 조치(failover)"할 수 있기 때문입니다. 기본 데이터베이스를 설치한 후에 **Install-CsMirrorDatabase** cmdlet을 사용하여 미러 데이터베이스를 설치 및 구성할 수 있습니다.

기본적으로 **Install-CsMirrorDatabase** cmdlet은 지정된 서버에 저장되어 있는 모든 Lync Server 데이터베이스에 대해 미러 데이터베이스를 설치 및 구성합니다. 그러나 DatabaseType 또는 ExcludeDatabaseList 매개 변수를 사용하여 설치하거나 설치하지 않을 미러 데이터베이스를 정확하게 지정할 수 있습니다. DatabaseType으로는 설치할 데이터베이스만 지정할 수 있고 ExcludeDatabaseList로는 설치하지 않을 데이터베이스를 지정할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Install-CsMirrorDatabase"}

Lync Server 제어판: **Install-CsMirrorDatabase** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>ConfiguredDatabases</em></p></td>
<td><p>필수</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Lync Server 토폴로지에서 정보를 읽고 지정된 SQL Server 컴퓨터 또는 SQL Server 클러스터에 필요한 미러 데이터베이스를 설치합니다.</p></td>
</tr>
<tr class="even">
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
<tr class="odd">
<td><p><em>FileShare</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>데이터베이스 공유 폴더의 UNC 경로입니다. 파일 공유는 주 SQL Server에서 데이터베이스를 내보내고 해당 데이터베이스를 미러로 가져오는 데 사용됩니다.</p>
<p>공유 폴더 및 해당 콘텐츠는 미러링이 설정된 후에 삭제될 수 있습니다. 미러링을 사용하지 않도록 결정한 경우에는 폴더도 삭제해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SqlServerFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>주 SQL Server 컴퓨터의 FQDN(정규화된 도메인 이름)입니다. 예를 들면 다음과 같습니다.</p>
<p>-SqlServerFqdn atl-sql-001.litwareinc.com</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DatabasePathMap</em></p></td>
<td><p>선택</p></td>
<td><p>System.Collections.Hashtable</p></td>
<td><p>데이터 파일 및 로그 파일에 대해 사용자 지정 폴더 경로를 지정할 수 있습니다. 경로가 여러 개이면 세미콜론(;)을 사용하여 구분해야 합니다. 예를 들면 다음과 같습니다.</p>
<p>-DatabasePathMap @{&quot;Archiving:DbPath&quot;=&quot;\\atl-sql-001.litwareinc.com\db&quot;;&quot;Archiving:LogPath&quot;=&quot;\\atl-sql-002.litwareinc.com\logs&quot;}</p></td>
</tr>
<tr class="odd">
<td><p><em>DropExistingDatabasesOnMirror</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 미러로 작동하는 서버로 새 데이터를 복사하기 전에 해당 서버에서 미러링된 데이터베이스의 기존 복사본을 모두 삭제합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ExcludeDatabaseList</em></p></td>
<td><p>선택</p></td>
<td><p>System.String[]</p></td>
<td><p>미러 데이터베이스에 포함되면 안 되는 데이터베이스의 목록입니다. 데이터베이스가 여러 개이면 쉼표를 사용하여 구분할 수 있습니다. 예를 들면 다음과 같습니다.</p>
<p>-ExcludeDatabaseList &quot;RTCCAB&quot;,&quot;RTCPROV&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>ForDefaultInstance</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 지정하면 기본 SQL Server 인스턴스에 대해서만 작동하도록 <strong>Install-CsMirrorDatabase</strong> cmdlet에 지시합니다. 같은 명령에서 ForDefaultInstance 및 ForInstance를 모두 사용할 수는 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ForInstance</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 매개 변수를 지정하면 지정한 SQL Server 인스턴스에 대해서만 작동하도록 <strong>Install-CsMirrorDatabase</strong> cmdlet에 지시합니다. 같은 명령에서 ForInstance 및 ForDefaultInstance를 모두 사용할 수는 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet이 실행될 때 만들어진 로그 파일에 대한 파일 경로를 지정할 수 있도록 합니다. 예를 들면 다음과 같습니다.</p>
<p>Report &quot;C:\Logs\InstallDatabaseMirror.html&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>SqlInstanceName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>데이터베이스를 설치할 데이터베이스 인스턴스의 이름입니다. 데이터베이스 인스턴스는 데이터베이스 파일에 대한 액세스를 제공하는 실행 중인 프로세스의 집합입니다. 이 매개 변수를 생략하면 <strong>Install-CsMirrorDatabase</strong> cmdlet에서 기본 SQL Server 인스턴스를 사용합니다.</p></td>
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

없음. **Install-CsMirrorDatabase** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음.

## 참고 항목

#### 기타 리소스

[Get-CsDatabaseMirrorState](get-csdatabasemirrorstate.md)  
[Uninstall-CsMirrorDatabase](uninstall-csmirrordatabase.md)

