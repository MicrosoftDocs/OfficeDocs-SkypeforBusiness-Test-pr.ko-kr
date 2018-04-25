---
title: Test-CsDatabase
TOCTitle: Test-CsDatabase
ms:assetid: 4165f1e1-fe64-45e7-a13f-f23c0205f386
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204839(v=OCS.15)
ms:contentKeyID: 49303437
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsDatabase

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 2013 데이터베이스의 구성을 테스트합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Test-CsDatabase -LocalService <SwitchParameter> <COMMON PARAMETERS>

    Test-CsDatabase -CentralManagementDatabase <SwitchParameter> [-SqlInstanceName <String>] [-SqlServerFqdn <Fqdn>] <COMMON PARAMETERS>

    Test-CsDatabase -ConfiguredDatabases <SwitchParameter> -SqlServerFqdn <Fqdn> <COMMON PARAMETERS>

    Test-CsDatabase -DatabaseType <Application | Archiving | Monitoring | User | Provision | CentralAdmin | Lyss | Registrar | Edge | PersistentChat | PersistentChatCompliance | CentralMgmt> -SqlServerFqdn <Fqdn> [-SqlInstanceName <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Report <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 중앙 관리 데이터베이스의 구성을 확인합니다.

    Test-CsDatabase -CentralManagementDatabase

## 예제 2

예제 2에서는 atl-sql-001.litwareinc.com 컴퓨터에 설치된 모든 Lync Server 데이터베이스를 확인합니다.

    Test-CsDatabase -ConfiguredDatabases -SqlServerFqdn "atl-sql-001.litwareinc.com"

## 예제 3

예제 3에서는 atl-sql-001.litwareinc.com 컴퓨터에 설치된 보관 데이터베이스에 대해서만 확인을 수행합니다. 보관 데이터베이스가 있는 SQL Server 인스턴스(Archinst)를 지정하기 위해 SqlInstanceName 매개 변수가 포함되었습니다.

    Test-CsDatabase -DatabaseType "Archiving" -SqlServerFqdn "atl-sql-001.litwareinc.com" -SqlInstanceName "archinst"

## 예제 4

예제 4에 표시된 명령은 로컬 컴퓨터에 설치된 데이터베이스를 확인합니다.

    Test-CsDatabase -LocalService

## 자세한 정보

**Test-CsDatabase** cmdlet은 하나 이상의 Lync Server 2013 데이터베이스에 대한 연결을 확인합니다. **Test-CsDatabase** cmdlet을 실행하면 Lync Server 토폴로지를 읽고 각 관련 데이터베이스에 연결을 시도한 다음 각 시도의 성공 또는 실패를 보고합니다. 연결이 가능한 경우 이 cmdlet은 데이터베이스 이름, SQL Server 버전 정보 및 설치된 미러 데이터베이스의 위치와 같은 정보도 보고합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsDatabase"}

**Lync Server 제어판:** **Test-CsDatabase** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>중앙 관리 데이터베이스의 구성을 테스트합니다. 이 매개 변수를 ConfiguredDatabases 매개 변수 또는 DatabaseType 매개 변수와 함께 사용할 수는 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ConfiguredDatabases</em></p></td>
<td><p>필수</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>지정한 컴퓨터에 설치된 모든 Lync Server 데이터베이스의 구성을 테스트합니다. ConfiguredDatabases 매개 변수를 사용할 때는 SqlServerFqdn 매개 변수를 포함해야 합니다. 또한 이 매개 변수는 CentralManagementDatabase 또는 DatabaseType 매개 변수와 같은 명령에서 사용할 수 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DatabaseType</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.DatabaseNameType</p></td>
<td><p>유효성을 검사할 데이터베이스의 유형입니다. 사용 가능한 값은 다음과 같습니다.</p>
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
<td><p><em>LocalService</em></p></td>
<td><p>필수</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>로컬 컴퓨터에 설치된 Lync Server 서비스에서 사용하는 모든 데이터베이스의 유효성을 검사합니다. 하나 이상의 로컬 서비스에서 사용하는 로컬로 설치된 데이터베이스뿐만 아니라 원격 컴퓨터에 설치된 데이터베이스도 여기에 포함됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SqlServerFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>유효성을 검사할 데이터베이스가 설치된 컴퓨터의 정규화된 도메인 이름입니다.</p></td>
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
<td><p>cmdlet이 실행될 때 만들어진 로그 파일에 대한 파일 경로를 지정할 수 있도록 합니다. 예를 들면 다음과 같습니다.</p>
<p>-Report &quot;C:\Logs\TestDatabases.html&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>SqlInstanceName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>유효성을 검사할 데이터베이스가 설치된 SQL Server 인스턴스입니다. 예를 들면 다음과 같습니다.</p>
<p>-SqlInstanceName &quot;rtc&quot;</p></td>
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

없음. **Test-CsDatabase** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Test-CsDatabase** cmdlet은 Microsoft.Rtc.SyntheticTransactions.TaskOutput 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsDatabaseMirrorState](get-csdatabasemirrorstate.md)  
[Get-CsService](get-csservice.md)  
[Get-CsUserDatabaseState](get-csuserdatabasestate.md)

