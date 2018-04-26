---
title: Lync Server 2013의 IMReportSummary 테이블
TOCTitle: Lync Server 2013의 IMReportSummary 테이블
ms:assetid: 27ff9453-53f2-4fae-b637-70a086c9df96
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204753(v=OCS.15)
ms:contentKeyID: 49303116
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 IMReportSummary 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

IMReportSummaryTable은 조직에서 진행하는 인스턴트 메시징 세션에 대한 전체 보고서를 제공합니다. 이 테이블은 Microsoft Lync Server 2013에서 도입되었습니다.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>열</th>
<th>데이터 형식</th>
<th>키/인덱스</th>
<th>세부 정보</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>StartTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>Primary</p></td>
<td><p>인스턴트 메시징 세션이 시작된 날짜 및 시간입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>TimePeriod</strong></p></td>
<td><p>char(1)</p></td>
<td><p>Primary</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>PoolFQDN</strong></p></td>
<td><p>nvarchar(257)</p></td>
<td><p>Primary</p></td>
<td><p>세션을 호스팅하는 풀의 정규화된 도메인 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>AuthType</strong></p></td>
<td><p>int</p></td>
<td><p>Primary</p></td>
<td><p>통화의 우선 순위(예: 긴급, 일반)입니다. 우선 순위 정보는 <a href="lync-server-2013-callpriorities-table.md">Lync Server 2013의 CallPriorities 테이블</a>에 저장됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SessionCount</strong></p></td>
<td><p>bigint</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>MsgCount</strong></p></td>
<td><p>bigint</p></td>
<td><p></p></td>
<td><p>세션 중 교환된 총 인스턴트 메시지 수입니다.</p></td>
</tr>
</tbody>
</table>

