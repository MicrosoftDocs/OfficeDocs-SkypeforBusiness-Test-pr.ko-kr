---
title: Install-CsDatabase
TOCTitle: Install-CsDatabase
ms:assetid: e91c1800-35f6-40ef-840d-7a518bddcae6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399044(v=OCS.15)
ms:contentKeyID: 49305393
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Install-CsDatabase

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 데이터베이스를 하나 이상 설치합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Install-CsDatabase -LocalDatabases <SwitchParameter> [-ForDefaultInstance <SwitchParameter>] [-ForInstance <String>] <COMMON PARAMETERS>

    Install-CsDatabase -CentralManagementDatabase <SwitchParameter> -SqlServerFqdn <Fqdn> [-Backup <SwitchParameter>] [-Collocated <SwitchParameter>] [-SqlInstanceName <String>] <COMMON PARAMETERS>

    Install-CsDatabase -ConfiguredDatabases <SwitchParameter> -SqlServerFqdn <Fqdn> [-ExcludeCollocatedStores <SwitchParameter>] [-ForDefaultInstance <SwitchParameter>] [-ForInstance <String>] <COMMON PARAMETERS>

    Install-CsDatabase -DatabaseType <Application | Archiving | Monitoring | User | Provision | CentralAdmin | Lyss | Registrar | Edge | PersistentChat | PersistentChatCompliance | CentralMgmt> [-Collocated <SwitchParameter>] [-SqlInstanceName <String>] [-SqlServerFqdn <Fqdn>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Clean <SwitchParameter>] [-Confirm [<SwitchParameter>]] [-DatabasePathMap <Hashtable>] [-DatabasePaths <String[]>] [-Force <SwitchParameter>] [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-NoReindex <SwitchParameter>] [-Report <String>] [-SkipPrepareCheck <SwitchParameter>] [-Update <SwitchParameter>] [-UseDefaultSqlPaths <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 **Install-CsDatabase** cmdlet이 Lync Server 토폴로지에서 읽고 atl-sql-001.litwareinc.com 풀에 필요한 데이터베이스를 설치합니다.

    Install-CsDatabase -ConfiguredDatabases -SqlServerFqdn atl-sql-001.litwareinc.com -DatabasePaths "E:\CSLog","F:\CSLog","G:\CSDB"

## 예제 2

예제 2에 표시된 명령은 atl-sql-001.litwareinc.com 풀에 중앙 관리 저장소를 설치합니다. 이 데이터베이스는 rtc 인스턴스에 설치되며 G:\\CSDB 폴더를 사용합니다.

    Install-CsDatabase -CentralManagementDatabase -SqlServerFqdn atl-sql-001.litwareinc.com -SqlInstanceName rtc -DatabasePaths "G:\CSDB"

## 자세한 정보

Lync Server는 중앙 관리 저장소에서 보관 데이터베이스까지 SQL Server 데이터베이스를 광범위하게 사용합니다. 일반적으로 이러한 데이터베이스는 Lync Server를 설치하거나 데이터베이스 백 엔드가 필요한 Lync Server 역할(예: 모니터링 서버)을 설치함과 동시에 설치됩니다. 설치 후에는 일반적으로 이러한 데이터베이스를 다시 설치하거나 새 위치로 이동할 필요가 없습니다.

그러나 데이터베이스를 다른 서버로 이동해야 하거나, 설치 관련 문제로 인해 데이터베이스를 설치하지 못한 경우 등 Lync Server 데이터베이스를 수동으로 설치해야 하는 경우가 간혹 있을 수 있습니다. **Install-CsDatabase** cmdlet을 사용하면 Lync Server에서 사용하는 모든 SQL Server 데이터베이스를 설치할 수 있습니다.

**Install-CsDatabase** cmdlet을 실행할 때는 일반적으로 설치할 데이터베이스의 구성을 세 가지 방법으로 처리할 수 있습니다.

옵션 1 -- 데이터베이스 경로를 지정하는 매개 변수를 포함하지 않고 cmdlet을 실행합니다. **Install-CsDatabase** cmdlet이 DatabasePath 또는 UseDefaultSqlPath 매개 변수 없이 실행되면 기본 제공 알고리즘을 사용하여 데이터베이스 로그 및 데이터 파일의 저장 위치를 선택합니다. 이 기본 제공 알고리즘은 독립 실행형 SQL Server와 작동하며 SQL Server 클러스터에서는 작동하지 않습니다. SQL Server 클러스터에 데이터베이스를 설치하려면 명령에 DatabasePath 또는 UseDefaultSqlPath 매개 변수를 포함해야 합니다.

옵션 2 -- DatabasePath 매개 변수와 함께 cmdlet을 실행합니다. **Install-CsDatabase** cmdlet이 DatabasePath와 함께 실행되면 기본 제공 알고리즘을 사용하여 데이터베이스 로그 및 데이터 파일의 저장 위치를 선택하지 않습니다. 대신에 관리자가 이러한 로그 및 데이터 파일의 위치를 선택할 수 있습니다. 데이터 파일과 SQL Server 로그를 모두 동일한 위치에 설치하려면 이 데이터를 저장할 폴더의 경로를 지정하면 됩니다. 예를 들면 다음과 같습니다.

\-DatabasePath C:\\SqlData

데이터 파일과 로그 파일을 서로 다른 위치에 저장하려면 각 폴더의 경로를 지정합니다. 두 위치는 쉼표를 사용하여 구분하며 쉼표 앞뒤에는 공백을 넣지 않습니다.

\-DatabasePath C:\\SqlLogs,D:\\SqlData

로그 파일은 항상 지정된 첫 번째 위치에 저장되며, 데이터 파일은 두 번째 위치에 저장됩니다.

풀 백 엔드에서는 특정 로그 파일이 자동으로 드라이브에 저장될 수 있습니다. 단일 드라이브와 풀 백 엔드가 있는 경우 파일은 다음과 같이 배포됩니다.

드라이브 1 – Rtcdyn 로그, Rtc 로그, 기타 로그, 기타 데이터

드라이브가 2개 있는 경우 파일은 다음과 같이 배포됩니다.

드라이브 1 – Rtcdyn 로그, Rtc 로그

드라이브 2 – 기타 로그, 기타 데이터

드라이브가 3개 있는 경우:

드라이브 1 – Rtcdyn 로그

드라이브 2 – Rtc 로그

드라이브 3 – 기타 로그, 기타 데이터

드라이브가 4개 있는 경우:

드라이브 1 – Rtcdyn 로그

드라이브 2 – Rtc 로그

드라이브 3 – 기타 로그

드라이브 4 – 기타 데이터

옵션 3 -- UseDefaultSqlPaths 매개 변수와 함께 cmdlet을 실행합니다. **Install-CsDatabase** cmdlet이 UseDefaultSqlPaths를 사용하여 실행되면 기본 제공 알고리즘을 사용하여 데이터베이스 로그 및 데이터 파일의 저장 위치를 선택하지 않습니다. 대신에 SQL Server 기본 경로에 의해 지정된 위치에 로그 및 데이터 파일이 저장됩니다. 이러한 경로는 SQL Server 관리자가 미리 구성해야 합니다. 데이터 파일은 기본 SQL Server 데이터 파일 위치에 저장되고, 로그 파일은 기본 SQL Server 로그 파일 위치에 저장됩니다.

**Install-CsDatabase** cmdlet을 실행하기 전에 RTCUniversalServerAdmins 그룹이 데이터베이스 소유자로 할당되지 않았는지 확인해야 합니다. 해당 그룹이 소유자로 나열된 경우 **Install-CsDatabase** cmdlet을 호출하면 이 그룹이 삭제될 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: **Install-CsDatabase** cmdlet을 로컬로 실행하려면 도메인 구성원, RTCUniversalReadOnlyAdmins 그룹 구성원, SQL Server 관리자 및 SQL Server가 설치된 컴퓨터의 로컬 관리자여야 합니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Install-CsDatabase"}

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
<td><p><em>CentralManagementDatabase</em></p></td>
<td><p>필수</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 포함하면 <strong>Install-CsDatabase</strong> cmdlet이 SqlServerFqdn 매개 변수를 사용하여 지정한 컴퓨터에 중앙 관리 저장소를 설치합니다. 이 매개 변수는 일반적으로 토폴로지 작성기에서만 사용되며 초기 설치 과정에서만 한 번 호출됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ConfiguredDatabases</em></p></td>
<td><p>필수</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Lync Server 토폴로지에서 정보를 읽고 지정된 SQL Server 컴퓨터 또는 SQL Server 클러스터에 필요한 데이터베이스를 설치합니다. <strong>Install-CsDatabase</strong> cmdlet을 호출해야 하는 관리자는 설치할 데이터베이스를 지정할 때 거의 항상 이 매개 변수를 사용합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DatabaseType</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.DatabaseNameType</p></td>
<td><p>특정 SQL Server 컴퓨터 또는 SQL Server 클러스터에 특정 데이터베이스를 설치하는 데 사용됩니다. 일반적으로 관리자는 Microsoft 지원 담당자가 별도로 지시하지 않는 한 DatabaseType 매개 변수와 함께 <strong>Install-CsDatabase</strong> cmdlet을 실행해서는 안 됩니다. 대신에 ConfiguredDatabases 매개 변수를 사용해야 합니다. DatabaseType 매개 변수를 사용하려면 토폴로지에서 사용되는 모든 데이터베이스에 대한 정확한 유형과 위치를 알아야 합니다. 이 매개 변수는 ConfiguredDatabases 매개 변수를 사용하여 <strong>Install-CsDatabase</strong> cmdlet 명령을 실행할 수 없는 경우에만 필요합니다.</p>
<p>DatabaseType의 유효한 값은 다음과 같습니다.</p>
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
<td><p><em>LocalDatabases</em></p></td>
<td><p>필수</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 포함하면 <strong>Install-CsDatabase</strong> cmdlet이 Lync Server 토폴로지에서 읽고 로컬 컴퓨터에 필요한 데이터베이스 및 저장소를 설치합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SqlServerFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>데이터베이스를 설치할 컴퓨터의 FQDN(정규화된 도메인 이름)입니다(예: -SqlServerFqdn atl-sql-001.litwareinc.com).</p></td>
</tr>
<tr class="even">
<td><p><em>Backup</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 사용하는 경우 기존 중앙 관리 서버 데이터베이스를 지정한 SQL Server 인스턴스로 백업합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Clean</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 포함하면 <strong>Install-CsDatabase</strong> cmdlet에서 필요에 따라 데이터베이스를 삭제하고 다시 설치하며, 이 매개 변수를 포함하지 않으면 <strong>Install-CsDatabase</strong> cmdlet에서 기존 데이터베이스를 덮어쓰지 않습니다. Clean과 Update를 같은 명령에 함께 사용할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Collocated</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 추가 데이터베이스 역할이 중앙 관리 저장소와 함께 배치됩니다.</p></td>
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
<td><p><em>DatabasePaths</em></p></td>
<td><p>선택</p></td>
<td><p>System.String[]</p></td>
<td><p>데이터 및 로그 파일을 저장할 수 있는 드라이브와 폴더를 지정합니다(예: -DatabasePaths &quot;D:\Logs&quot;, &quot;E:\Data&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>ExcludeCollocatedStores</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수는 함께 배치된 데이터베이스 저장소를 로컬 컴퓨터에 설치해야 함을 알리는 경고 메시지를 숨깁니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 해당 유형의 기존 데이터베이스를 현재 사용 중인 경우에도 새 데이터베이스가 강제로 설치됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ForDefaultInstance</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 지정하면 기본 SQL Server 인스턴스에 대해서만 작동하도록 <strong>Install-CsDatabase</strong> cmdlet에 지시합니다. 같은 명령에서 ForDefaultInstance 및 ForInstance를 모두 사용할 수는 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ForInstance</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 매개 변수를 지정하면 지정한 SQL Server 인스턴스에 대해서만 작동하도록 <strong>Install-CsDatabase</strong> cmdlet에 지시합니다. 같은 명령에서 ForInstance 및 ForDefaultInstance를 모두 사용할 수는 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>GlobalCatalog</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>도메인에 있는 전역 카탈로그 서버의 FQDN(정규화된 도메인 이름)입니다. 사용자 도메인의 계정을 가진 컴퓨터에서 <strong>Install-CsDatabase</strong> cmdlet을 실행하는 경우 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>GlobalSettingsDomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>전역 설정이 저장되는 도메인 컨트롤러의 FQDN(정규화된 도메인 이름)입니다. 전역 설정이 Active Directory 도메인 서비스의 시스템 컨테이너에 저장되는 경우 이 매개 변수는 루트 도메인 컨트롤러를 가리켜야 합니다. 전역 설정이 구성 컨테이너에 저장된 경우 아무 도메인 컨트롤러나 사용할 수 있으며 이 매개 변수는 생략해도 됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>NoReindex</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>데이터베이스를 업데이트할 때 인덱스 파일이 다시 작성되지 않도록 합니다. 이 매개 변수는 Update 매개 변수와 함께 사용해야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet이 실행될 때 만들어지는 로그 파일의 파일 경로를 지정하는 데 사용됩니다(예: -Report &quot;C:\Logs\InstallDatabases.html&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>SkipPrepareCheck</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 <strong>Install-CsDatabase</strong> cmdlet에서 초기 준비 검사를 건너뜁니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SqlInstanceName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>데이터베이스를 설치할 데이터베이스 인스턴스의 이름입니다. 데이터베이스 인스턴스는 데이터베이스 파일에 대한 액세스를 제공하는 실행 중인 프로세스의 집합입니다. 이 매개 변수를 생략하면 <strong>Install-CsDatabase</strong> cmdlet에서 기본 SQL Server 인스턴스를 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Update</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수는 기존 데이터베이스를 업데이트합니다. Update와 Clean을 같은 명령에 함께 사용할 수 없습니다.</p>
<p>미러된 데이터베이스에는 Update 매개 변수를 사용할 수 없습니다. 미러 데이터베이스는 삭제한 후 다시 만들 수 없으므로 명령이 실패합니다. 미러 데이터베이스에 Update 매개 변수를 사용하려면 먼저 <a href="uninstall-csmirrordatabase.md">Uninstall-CsMirrorDatabase</a> cmdlet을 사용하여 미러 데이터베이스의 연결을 해제해야 합니다. 그리고 나면 Install-CsDatabase 및 Update 매개 변수를 실행할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>UseDefaultSqlPaths</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 지정하면 데이터 및 로그 파일을 저장할 드라이브와 경로를 선택하도록 SQL Server에 지시합니다.</p></td>
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

없음. **Install-CsDatabase** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Install-CsDatabase** cmdlet은 값이나 개체를 반환하지 않습니다.

## 참고 항목

#### 기타 리소스

[Uninstall-CsDatabase](uninstall-csdatabase.md)

