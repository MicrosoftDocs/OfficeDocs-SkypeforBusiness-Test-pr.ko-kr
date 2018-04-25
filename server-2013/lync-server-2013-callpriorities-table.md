---
title: 'Lync Server 2013: CallPriorities 테이블'
TOCTitle: CallPriorities 테이블
ms:assetid: 043b63ae-2d64-4f38-a0df-18aa08d6caf5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398093(v=OCS.15)
ms:contentKeyID: 49302655
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 CallPriorities 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

CallPriorities 테이블은 '응급', '긴급' 또는 '보통'과 같은 가능한 통화 우선 순위 목록을 저장하는 정적 테이블입니다.


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
<td><p><strong>PriorityId</strong></p></td>
<td><p>tinyint</p></td>
<td><p>기본</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Priority</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p></p></td>
<td><p>허용되는 값:</p>
<ul>
<li><p>0 - 알 수 없음</p></li>
<li><p>1 - 일반</p></li>
<li><p>2 - 보통</p></li>
<li><p>3 - 긴급</p></li>
<li><p>4 - 응급</p></li>
</ul></td>
</tr>
</tbody>
</table>

