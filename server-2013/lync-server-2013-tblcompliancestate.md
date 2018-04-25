---
title: 'Lync Server 2013: tblComplianceState'
TOCTitle: tblComplianceState
ms:assetid: ea82e56c-3cca-4d89-b4e6-6bcaeb1f2830
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg615045(v=OCS.15)
ms:contentKeyID: 49305414
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 tblComplianceState

 

_**마지막으로 수정된 항목:** 2015-03-09_

tblComplianceState에는 풀 전체의 준수 상태 정보가 포함되어 있습니다.

### 열

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>열</th>
<th>유형</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>lastProcessedEntryID</p></td>
<td><p>bigint, null이 아님</p></td>
<td><p>마지막으로 처리된 준수 이벤트의 ID입니다.</p></td>
</tr>
<tr class="even">
<td><p>activeServerID</p></td>
<td><p>int, null이 아님</p></td>
<td><p>데이터베이스에 대해 단독 잠금을 유지하는 준수 서버의 ID입니다. 없으면 -1입니다.</p></td>
</tr>
<tr class="odd">
<td><p>lockExpirationTime</p></td>
<td><p>datetime2, null이 아님</p></td>
<td><p>잠금 만료 시간(activeServerID가 -1이 아닌 경우)입니다.</p></td>
</tr>
</tbody>
</table>

