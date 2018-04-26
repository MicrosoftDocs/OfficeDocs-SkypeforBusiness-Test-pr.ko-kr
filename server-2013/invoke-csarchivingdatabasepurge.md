---
title: Invoke-CsArchivingDatabasePurge
TOCTitle: Invoke-CsArchivingDatabasePurge
ms:assetid: 02310b08-736d-4ce9-91d8-5a6c8f323d7c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204627(v=OCS.15)
ms:contentKeyID: 49302623
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Invoke-CsArchivingDatabasePurge

 

_**마지막으로 수정된 항목:** 2015-03-09_

보관 데이터베이스에서 레코드를 수동으로 제거합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Invoke-CsArchivingDatabasePurge -Identity <XdsIdentity> <COMMON PARAMETERS>

    Invoke-CsArchivingDatabasePurge -SqlServerFqdn <String> [-SqlInstanceName <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: -PurgeArchivingDataOlderThanHours <Int32> -PurgeExportedArchivesOnly <$true | $false> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-MaxArchivingRecordsToDelete <Int32>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 atl-sql-001.litwareinc.com의 보관 데이터베이스에서 24시간보다 오래된 모든 레코드를 제거합니다. 내보내지 않은 레코드를 포함하여 모든 레코드가 삭제되도록 하기 위해 PurgeExportedArchivesOnly 매개 변수는 False($False)로 설정됩니다.

    Invoke-CsArchivingDatabasePurge -Identity "service:ArchivingDatabase:atl-sql-001.litwareinc.com" -PurgeArchivingDataOlderThanHours 24 -PurgeExportedArchivesOnly $False

## 예제 2

예제 2에 표시된 명령은 예제 1에 표시된 명령의 변형으로, 이 경우에는 다음 구문을 사용하여 Confirm 매개 변수가 추가됩니다.

\-Confirm:$False

해당 구문은 보관 레코드 제거 시 일반적으로는 표시되는 확인 메시지를 표시하지 않습니다.

    Invoke-CsArchivingDatabasePurge -Identity "service:ArchivingDatabase:atl-sql-001.litwareinc.com" -PurgeArchivingDataOlderThanHours 24 -PurgeExportedArchivesOnly $False -Confirm:$False

## 예제 3

예제 3에서는 조직에서 사용 중인 모든 보관 데이터베이스에서 24시간보다 오래된 레코드를 모두 제거합니다. 이를 위해 예제의 첫 번째 명령은 **Get-CsService** cmdlet 및 ArchivingDatabase 매개 변수를 사용하여 모든 보관 데이터베이스의 컬렉션을 반환하며, 이 컬렉션은 **ForEach-Object** cmdlet에 파이프됩니다. ForEach-Object cmdlet은 컬렉션의 각 데이터베이스를 가져온 다음 해당 데이터베이스에 대해 **Invoke-CsArchivingDatabasePurge** cmdlet을 실행하여 24시간보다 오래된 모든 레코드를 제거합니다.

    Get-CsService -ArchivingDatabase | ForEach-Object {Invoke-CsArchivingDatabasePurge -Identity $_.Identity -PurgeArchivingDataOlderThanHours 24 -PurgeExportedArchivesOnly $False -Confirm:$False}

## 자세한 정보

대부분의 조직에서는 조직의 사용자 또는 선택된 사용자의 하위 집합이 수행하는 모든 메신저 세션의 대화 내용을 보관하여 유용하게 활용하고 있습니다. 그러한 대화 내용을 의무적으로 보관해야 하는 조직도 있습니다. 예를 들어 법에 따라 모든 전자 통신의 복사본을 보관해야 하는 금융 분야의 조직 대부분이 이에 해당합니다.

조직에서 보관을 사용하도록 설정했으며 보관 백 엔드로 Lync Server를 사용하도록 선택한 경우에는 보관 레코드가 SQL Server 데이터베이스 LcsLog에 저장됩니다. 대신 Microsoft Exchange를 사용하여 보관 레코드를 저장할 수도 있습니다. 자세한 내용은 **New-CsArchivingConfiguration** cmdlet 도움말 항목을 참조하십시오. 시간이 지남에 따라 보관 데이터베이스는 매우 커질 수 있으므로, Lync Server에서는 관리자가 오래된 레코드를 데이터베이스에서 제거하는 두 가지 방법을 제공합니다. 그 중 하나는 매일 오래된 보관 레코드를 자동으로 삭제하도록 Lync Server를 구성하는 것이고, 다른 하나는 언제든지 **Invoke-CsArchivingDatabasePurge** cmdlet을 사용하여 LcsLog 데이터베이스에서 보관 레코드를 삭제하는 것입니다. **Invoke-CsArchivingDatabasePurge** cmdlet은 SQL Server 저장 프로시저 RtcCleanupTempConference 및 RtcCleanupDB를 호출하고 저장된 모임 콘텐츠를 삭제하는 방법으로 이 작업을 수행합니다.

**Invoke-CsArchivingDatabasePurge** cmdlet을 호출할 때는 보관 레코드가 저장된 보관 데이터베이스의 서비스 위치를 지정해야 합니다(예: ArchivingDatabase:atl-sql-001.litwareinc.com). 또한 삭제할 보관 레코드의 최소 기간을 시간 단위로 지정해야 합니다. 예를 들어 최소 기간을 24시간으로 지정하면 24시간보다 오래된 모든 보관 레코드가 데이터베이스에서 삭제됩니다.

이러한 레코드는 지정한 데이터베이스에 대해 제거를 사용하지 않도록 설정한 경우(보관 구성 설정에서 EnablePurging 속성이 False로 설정된 경우)에도 삭제됩니다. EnablePurging 속성은 자동화된 보관 레코드 제거만 제어하며, **Invoke-CsArchivingDatabasePurge** cmdlet에는 아무런 영향을 주지 않습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Invoke-CsArchivingDatabasePurge"}

**Lync Server 제어판:** **Invoke-CsArchivingDatabasePurge** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>제거할 보관 데이터베이스의 서비스 ID입니다. 다음 명령을 실행하면 보관 데이터베이스의 ID를 검색할 수 있습니다.</p>
<p>Get-CsService –ArchivingDatabase</p>
<p>Identity 매개 변수와 SqlServerFqdn 매개 변수를 같은 명령에 사용할 수는 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PurgeArchivingDataOlderThanHours</em></p></td>
<td><p>필수</p></td>
<td><p>System.Int32</p></td>
<td><p>데이터베이스에서 제거할 보관 레코드의 보관 기간을 시간 단위로 지정합니다. 이 값보다 오래된 레코드는 삭제됩니다. PurgeArchivingDataOlderThanHours는 1에서 2147483647(포함) 사이의 정수 값으로 설정할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PurgeExportedArchivesOnly</em></p></td>
<td><p>필수</p></td>
<td><p>System.Boolean</p></td>
<td><p>이 매개 변수가 있으면 이전에 내보냈으며 삭제하도록 표시된 레코드만 보관 데이터베이스에 대해 제거됩니다. 내보내지 않은 레코드는 PurgeArchivingDataOlderThanHours 속성으로 지정된 값보다 오래되었더라도 데이터베이스에 유지됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SqlServerFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>보관 데이터베이스가 있는 컴퓨터의 정규화된 도메인 이름입니다. 예를 들면 다음과 같습니다.</p>
<p>-SqlServerFqdn &quot;atl-sql-001.litwareinc.com&quot;</p>
<p>Identity 매개 변수와 SqlServerFqdn 매개 변수를 같은 명령에 사용할 수는 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaxArchivingRecordsToDelete</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>데이터베이스에서 제거할 보관 레코드의 최대 수를 지정합니다. 이 값을 99로 설정했는데 데이터베이스에 PurgeArchivingDataOlderThanHours 조건을 충족하는 레코드는 100개가 있다면 가장 오래된 99개 레코드만 삭제됩니다.</p>
<p>MaxArchivingRecordsToDelete는 1에서 2147483647(포함) 사이의 정수 값으로 설정할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SqlInstanceName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>보관 데이터베이스의 SQL Server 인스턴스 이름입니다. 예를 들면 다음과 같습니다.</p>
<p>-SqlInstanceName &quot;archinst&quot;</p></td>
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

**Invoke-CsArchivingDatabasePurge** cmdlet은 Microsoft.Rtc.Management.Xds.DisplayArchivingDatabase\#Decorated 클래스의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

Invoke-CsArchivingDatabasePurge cmdlet은 Microsoft.Rtc.Management.Purge.ArchDataPurgeStatistics 클래스의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsArchivingConfiguration](new-csarchivingconfiguration.md)  
[Set-CsArchivingConfiguration](set-csarchivingconfiguration.md)

