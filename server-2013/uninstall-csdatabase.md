---
title: Uninstall-CsDatabase
TOCTitle: Uninstall-CsDatabase
ms:assetid: bd08ac1c-cfcd-4cf8-b082-7d2e83a2837e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412922(v=OCS.15)
ms:contentKeyID: 49304862
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Uninstall-CsDatabase

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정된 Lync Server 데이터베이스를 삭제합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Uninstall-CsDatabase -DatabaseType <Application | Archiving | Monitoring | User | Provision | CentralAdmin | Lyss | Registrar | Edge | PersistentChat | PersistentChatCompliance | CentralMgmt> [-SqlInstanceName <String>] [-SqlServerFqdn <Fqdn>] <COMMON PARAMETERS>

    Uninstall-CsDatabase -CentralManagementDatabase <SwitchParameter> -SqlServerFqdn <Fqdn> [-SqlInstanceName <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Detach <SwitchParameter>] [-Force <SwitchParameter>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 atl-sql-001.litwareinc.com 컴퓨터에서 중앙 관리 저장소를 삭제합니다.

    Uninstall-CsDatabase -CentralManagementDatabase -SqlServerFqdn atl-sql-001.litwareinc.com 

## 예제 2

예제 2에서는 User 데이터베이스가 atl-sql-001.litwareinc.com 컴퓨터에서 삭제됩니다. DatabaseType 매개 변수를 사용하면 지정된 데이터베이스와 관련된 모든 저장소가 삭제됩니다.

    Uninstall-CsDatabase -DatabaseType User -SqlServerFqdn atl-sql-001.litwareinc.com 

## 자세한 정보

Lync Server는 중앙 관리 저장소 및 보관 데이터베이스와 같은 SQL Server 데이터베이스를 광범위하게 사용합니다. 이러한 데이터베이스는 Lync Server를 설치하거나 데이터베이스 백 엔드가 필요한 Lync Server 역할을 설치함과 동시에 설치됩니다. 데이터베이스가 설치되면 제거할 필요가 거의 없습니다.

그러나 나중에 Lync Server를 제거해야 하는 경우가 있을 수 있습니다. 예를 들어 하드웨어 오류 또는 네트워크 연결 문제로 인해 기존 데이터베이스를 사용할 수 없게 되는 경우가 있습니다. 어떤 이유든지 **Uninstall-CsDatabase** cmdlet을 사용하여 Lync Server에서 사용하는 SQL Server 데이터베이스를 제거하거나 분리할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: **Uninstall-CsDatabase** cmdlet을 로컬로 실행하려면 도메인 구성원, SQL Server 관리자 및 SQL Server가 설치된 컴퓨터의 로컬 관리자여야 합니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Uninstall-CsDatabase"}

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
<td><p>이 매개 변수가 있으면 중앙 관리 저장소가 제거됩니다. CentralManagementDatabase와 DatabaseType을 같은 명령에 함께 사용할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DatabaseType</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.DatabaseNameType</p></td>
<td><p>삭제할 데이터베이스입니다. 사용할 수 있는 값은 다음과 같습니다.</p>
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
<p>User</p>
<p>중앙 관리 저장소를 삭제하려면 CentralManagementDatabase 매개 변수를 사용합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SqlServerFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>데이터베이스가 있는 컴퓨터 또는 SQL Server 클러스터의 FQDN(정규화된 도메인 이름)입니다(예: -SqlServer atl-sql-001.litwareinc.com).</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Detach</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 지정된 데이터베이스가 분리됩니다. 데이터베이스가 분리되면 SQL Server에 의해 적용된 모든 파일 잠금이 제거됩니다. 따라서 데이터베이스 파일에 직접 액세스하여 이러한 파일을 다른 컴퓨터에 복사하는 등의 작업을 수행할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>있을 경우 데이터베이스가 현재 사용 중이더라도 강제로 제거됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet이 실행될 때 만들어지는 로그 파일의 파일 경로를 지정하는 데 사용됩니다(예: -Report &quot;C:\Logs\UninstallDatabase.html&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>SqlInstanceName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>제거할 데이터베이스가 포함된 데이터베이스 인스턴스의 이름입니다. 데이터베이스 인스턴스는 데이터베이스 파일에 대한 액세스를 제공하는 실행 중인 프로세스의 집합입니다.</p></td>
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

없음. **Uninstall-CsDatabase** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Uninstall-CsDatabase** cmdlet은 값이나 개체를 반환하지 않습니다.

## 참고 항목

#### 기타 리소스

[Install-CsDatabase](install-csdatabase.md)

