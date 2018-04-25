---
title: Invoke-CsDatabaseFailover
TOCTitle: Invoke-CsDatabaseFailover
ms:assetid: 24b73e8e-948c-4e9c-bf4e-04ec0a229ffa
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204744(v=OCS.15)
ms:contentKeyID: 49303070
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Invoke-CsDatabaseFailover

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 2013 데이터베이스가 해당 미러 데이터베이스로 장애 조치(failover)되는 프로세스를 호출합니다. 장애 조치(failover)가 완료되고 나면 미러 데이터베이스가 주 데이터베이스가 되어 모든 새 데이터베이스 요청을 처리합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Invoke-CsDatabaseFailover -DatabaseType <Application | Archiving | Monitoring | User | Provision | CentralAdmin | Lyss | Registrar | Edge | PersistentChat | PersistentChatCompliance | CentralMgmt> -NewPrincipal <Primary | Mirror> -PoolFqdn <Fqdn> [-Confirm [<SwitchParameter>]] [-ExcludeDatabaseList <String[]>] [-Force <SwitchParameter>] [-LocalStore <SwitchParameter>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 atl-cs-001.litwareinc.com 풀에 있는 User 데이터베이스에 대해 장애 조치(failover)를 호출합니다. 이 명령을 실행하면 User 데이터베이스가 이전에 할당된 미러 데이터베이스로 장애 조치(failover)됩니다.

    Invoke-CsDatabaseFailover -PoolFqdn atl-cs-001.litwareinc.com -DatabaseType "User" -NewPrincipal "Mirror"

## 예제 2

예제 2에서는 LcsCDR 및 LcsLog 데이터베이스를 제외한 atl-cs-001.litwareinc.com 풀의 모든 데이터베이스가 장애 조치(failover)됩니다. ExcludeDatabaseList 매개 변수를 사용하여 이 두 데이터베이스를 장애 조치(failover)에서 제외합니다.

    Invoke-CsDatabaseFailover -PoolFqdn atl-cs-001.litwareinc.com -ExcludeDatabase -NewPrincipal "Mirror" -ExcludeDatabaseList "LcsCDR", "LcsLog"

## 자세한 정보

**Invoke-CsDatabaseFailover** cmdlet을 통해 관리자는 하나 이상의 Lync Server 2013 데이터베이스를 "장애 조치(failover)"할 수 있습니다. 예를 들어 하드웨어 업그레이드를 수행하기 위해 기본 데이터베이스의 가동을 일시적으로 중지해야 한다고 가정하겠습니다. 이 경우 **Invoke-CsDatabaseFailover** cmdlet을 사용하여 기본 데이터베이스에서 미러 데이터베이스로 장애 조치(failover)할 수 있습니다. 그러면 해당 데이터베이스에 대한 모든 요청이 미러 데이터베이스로 라우팅됩니다. 나중에 하드웨어 업그레이드가 완료되면 같은 cmdlet을 사용하여 기본 데이터베이스로 장애 복구(failback)할 수 있습니다.

원하는 데이터베이스에 대해 기본 데이터베이스와 미러 데이터베이스를 모두 구성하지 않은 경우 **Invoke-CsDatabaseFailover** cmdlet을 사용하는 모든 명령은 실패합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Invoke-CsDatabaseFailover"}

**Lync Server 제어판:** **Invoke-CsDatabaseFailover** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>장애 조치(failover)되는 데이터베이스의 유형입니다. 사용할 수 있는 값은 다음과 같습니다.</p>
<p>Application</p>
<p>Archiving</p>
<p>CentralAdmin</p>
<p>CentralMgmt</p>
<p>Cls</p>
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
<td><p><em>NewPrincipal</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.MirrorRole</p></td>
<td><p>장애 조치(failover) 대상을 기본 데이터베이스 또는 미러 데이터베이스 중 하나로 지정합니다. 사용할 수 있는 값은 다음과 같습니다.</p>
<p>Mirror</p>
<p>Primary</p></td>
</tr>
<tr class="odd">
<td><p><em>PoolFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>장애 조치(failover)할 데이터베이스가 포함된 풀의 정규화된 도메인 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ExcludeDatabaseList</em></p></td>
<td><p>선택</p></td>
<td><p>System.String[]</p></td>
<td><p>장애 조치(failover)하지 않을 데이터베이스의 목록입니다. 예를 들면 다음과 같습니다.</p>
<p>-ExcludeDatabaseList &quot;LcsCDR&quot;</p>
<p>여러 데이터베이스에 대해 장애 조치(failover)를 수행하지 않으려면 데이터베이스 이름을 쉼표로 구분합니다.</p>
<p>-ExcludeDatabaseList &quot;LcsCDR&quot;, &quot;LcsLog&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다. 현재 데이터베이스에 액세스할 수 없으면 Force 매개 변수도 사용됩니다.</p></td>
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
<td><p>cmdlet이 실행될 때 만들어지는 로그 파일의 파일 경로를 지정하는 데 사용됩니다(예: -Report &quot;C:\Logs\DatabaseFailover.html&quot;).</p></td>
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

없음. **Invoke-CsDatabaseFailover** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음.

## 참고 항목

#### 기타 리소스

[Get-CsDatabaseMirrorState](get-csdatabasemirrorstate.md)  
[Install-CsMirrorDatabase](install-csmirrordatabase.md)

