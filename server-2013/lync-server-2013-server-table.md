---
title: 'Lync Server 2013: Server 테이블'
TOCTitle: Server 테이블
ms:assetid: 9af89d08-d35a-48e8-b56d-6df292f973cc
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398801(v=OCS.15)
ms:contentKeyID: 49304498
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 Server 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

Server 테이블은 지원 테이블입니다. 각 레코드는 하나의 서버를 나타냅니다.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>열</strong></th>
<th><strong>데이터 형식</strong></th>
<th><strong>키/인덱스</strong></th>
<th><strong>세부 정보</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>ServerKey</strong></p></td>
<td><p>int</p></td>
<td><p>기본</p></td>
<td><p>이 서버를 식별하는 고유 번호입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>FQDNOrIP</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>index</p></td>
<td><p>MAC 주소 문자열입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ServerType</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>1: 중재 서버</p>
<p>2: A/V 회의 서버 16394: A/V 에지 서버 32769: 게이트웨이</p></td>
</tr>
<tr class="even">
<td><p><strong>PoolName</strong></p></td>
<td><p>nvarchar(512)</p></td>
<td><p></p></td>
<td><p>서버가 속하는 풀입니다. A/V 회의 서버에만 적용할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>NextUpdateTS</strong></p></td>
<td><p>datetime</p></td>
<td><p></p></td>
<td><p>내부 용도로만 사용됩니다.</p></td>
</tr>
</tbody>
</table>

