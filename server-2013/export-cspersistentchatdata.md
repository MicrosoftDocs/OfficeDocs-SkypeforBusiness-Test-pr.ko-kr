---
title: Export-CsPersistentChatData
TOCTitle: Export-CsPersistentChatData
ms:assetid: f4855109-26e0-41b8-8a9f-890f8d892645
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205378(v=OCS.15)
ms:contentKeyID: 49305531
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Export-CsPersistentChatData

 

_**마지막으로 수정된 항목:** 2015-03-09_

영구 채팅 데이터베이스에서 데이터를 내보냅니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Export-CsPersistentChatData [-FileName <String>] <COMMON PARAMETERS>

    Export-CsPersistentChatData [-AsBytes <SwitchParameter>] <COMMON PARAMETERS>

    COMMON PARAMETERS: -DBInstance <String> [-DBName <String>] [-DisableExportedNodes <SwitchParameter>] [-Level <User | Category | RoomDirectory | Content | All>] [-Report <String>] [-Scope <List>] [-StartDate <DateTime>]

## 예제

## 예제 1

예제 1에 표시된 명령은 atl-sql-001.litwareinc.com 서버에 있는 영구 채팅 데이터베이스에서 영구 채팅 데이터를 내보냅니다. 내보낸 데이터는 C:\\Logs\\PersistentChatData.zip 파일에 저장됩니다. Level 매개 변수가 지정되지 않았으므로 **Export-CsPersistentChatData** cmdlet은 전체 영구 채팅 정보를 내보냅니다.

    Export-CsPersistentChatData -DBInstance "atl-sql-001.litwareinc.com\rtc" -FileName "C:\Logs\PersistentChatData.zip"

## 자세한 정보

Microsoft Lync Server 2010에서 사용되었던 그룹 채팅 서비스 대신 제공되는 영구 채팅 서비스를 사용하는 조직에서는 인터넷 토론 포럼과 비슷한 메시징 및 공동 작업 기능을 사용할 수 있습니다. 사용자는 실시간으로 메시지를 교환하는 동시에 언제든지 대화를 다시 방문하여 다시 시작할 수 있습니다. 특정 주제에 대해 대화를 할 수 있으며, 해당 대화를 모든 사용자가 확인할 수 있도록 하거나 선택한 사용자 집합만 확인하도록 할 수 있습니다. 마찬가지로 개별 채팅방도 누구나 메시지를 게시할 수 있도록 구성하거나 지정된 발표자만 메시지를 게시하도록 구성할 수 있습니다.

현재 Lync Server 2010을 실행 중인 경우 **Export-CsPersistentChatData** cmdlet을 사용하여 기존 그룹 채팅 구성 설정을 내보낸 다음 **Import-CsPersistentChatData** cmdlet을 사용하여 해당 정보를 Lync Server 2013 및 영구 채팅 서비스로 마이그레이션함으로써 현재 그룹 채팅 구현을 마이그레이션할 수 있습니다. **Export-CsPersistentChatData** cmdlet을 사용하면 모든 그룹 채팅 설정과 데이터를 가져오거나 그룹 채팅 설정 및 데이터 중 일부분만 가져올 수 있습니다. 예를 들어 그룹 채팅 범주 및 채팅방과 연결된 모든 콘텐츠를 내보내지 않고 해당 범주 및 채팅방만 내보낸 다음 가져올 수 있습니다.

**CsPersistentChatData** cmdlet은 기본적으로 마이그레이션에 사용되지만 Lync Server 2013에서 영구 채팅 데이터를 관리하는 데 사용할 수도 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Export-CsPersistentChatData"}

Lync Server 제어판: **Export-CsPersistentChatData** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>DBInstance</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>Lync Server 2013 영구 채팅 데이터베이스가 있는 SQL Server 인스턴스의 정규화된 도메인 이름 및 이름입니다. 예를 들어 다음 구문은 atl-sql-001.litwareinc.com 서버의 RTC 데이터베이스 인스턴스에 있는 데이터베이스를 지정합니다.</p>
<p>-DBInstance &quot;atl-sql-001.litwareinc.com\rtc&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>AsBytes</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>영구 채팅 정보를 바이트 배열로 반환합니다. 나중에 <strong>Import-CsPersistentChatData</strong> cmdlet에서 사용하려면 반환된 데이터를 변수에 저장해야 합니다. 같은 명령에 AsBytes와 FileName을 함께 사용할 수는 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DBName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>영구 채팅 데이터베이스의 SQL 인스턴스 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DisableExportedNodes</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 내보내기 완료 시 내보낸 범주 및 채팅방이 모두 사용하지 않도록 설정됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>FileName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p><strong>Export-CsPersistentChatData</strong> cmdlet이 만드는 .ZIP 파일(내보내는 사용자 데이터가 포함됨)의 전체 경로입니다. 예를 들면 다음과 같습니다.</p>
<p>-FileName &quot;C:\Logs\PersistentChatData.zip&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Level</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Chat.Cmdlets.ExportLevel</p></td>
<td><p>내보낼 영구 채팅 정보를 지정할 수 있습니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>* All</p>
<p>* User</p>
<p>* Category</p>
<p>* RoomDirectory</p>
<p>* Content</p>
<p>기본값은 All(모든 영구 채팅 정보를 내보냄)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>cmdlet이 실행될 때 만들어진 로그 파일에 대한 전체 경로입니다. 예를 들면 다음과 같습니다.</p>
<p>-Report &quot;C:\Logs\ExportPersistentChat.html&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Scope</em></p></td>
<td><p>선택</p></td>
<td><p>System.Collections.Generic.List</p></td>
<td><p>지정된 범주 집합 및 해당 채팅방에 대해 데이터를 내보낼 수 있습니다. 기본적으로는 모든 범주를 내보냅니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>StartDate</em></p></td>
<td><p>선택</p></td>
<td><p>System.DateTime</p></td>
<td><p>영구 채팅방 콘텐츠를 내보낼 기간의 시작 날짜입니다. 예를 들면 다음과 같습니다.</p>
<p>-StartDate &quot;1/1/2012&quot;</p>
<p>이 매개 변수는 Level이 RoomDirectory로 설정된 경우에만 유효합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Export-CsPersistentChatData** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Export-CsPersistentChatData** cmdlet은 .ZIP 파일을 만듭니다.

