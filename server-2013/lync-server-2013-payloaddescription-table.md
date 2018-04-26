---
title: 'Lync Server 2013: PayloadDescription 테이블'
TOCTitle: PayloadDescription 테이블
ms:assetid: c49d61c0-305a-4770-a5d2-5d9f05decc6d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412971(v=OCS.15)
ms:contentKeyID: 49304958
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 PayloadDescription 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

PayloadDescription 테이블은 지원 테이블입니다. 각 레코드는 오디오 및 비디오 세션에 사용되는 하나의 코덱을 나타냅니다.


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
<td><p><strong>PayloadDescriptionKey</strong></p></td>
<td><p>int</p></td>
<td><p>기본</p></td>
<td><p>코덱을 식별하는 고유 번호입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>PayloadDescription</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Unique</p></td>
<td><p>코덱 이름입니다.</p></td>
</tr>
</tbody>
</table>

