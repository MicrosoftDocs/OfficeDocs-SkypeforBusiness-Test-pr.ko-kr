---
title: 'Lync Server 2013: Roles 테이블'
TOCTitle: Roles 테이블
ms:assetid: e8eb8a10-26b5-488b-bc8c-f9ef93f98bdb
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399043(v=OCS.15)
ms:contentKeyID: 49305390
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 Roles 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

Roles 테이블은 참가자 및 발표자와 같은 가능한 회의 역할 목록을 저장하는 정적 테이블입니다.


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
<td><p><strong>RoleId</strong></p></td>
<td><p>tinyint</p></td>
<td><p>기본</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Role</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p></p></td>
<td><p>허용되는 값:</p>
<ul>
<li><p>0 - 알 수 없음</p></li>
<li><p>1 - 발표자</p></li>
<li><p>2 - 참석자</p></li>
</ul></td>
</tr>
</tbody>
</table>

