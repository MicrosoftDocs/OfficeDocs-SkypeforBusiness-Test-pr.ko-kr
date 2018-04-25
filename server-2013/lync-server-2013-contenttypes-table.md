---
title: 'Lync Server 2013: ContentTypes 테이블'
TOCTitle: ContentTypes 테이블
ms:assetid: e3e38035-457c-4173-bdb9-d53a7420eba2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399007(v=OCS.15)
ms:contentKeyID: 49305331
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 ContentTypes 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

ContentTypes 테이블은 피어-투-피어 세션 및 회의 세션에 사용되는 콘텐츠 유형 목록을 저장하는 지원 테이블입니다. 테이블의 각 레코드는 하나의 콘텐츠 유형을 나타냅니다.


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
<td><p><strong>ContentTypeId</strong></p></td>
<td><p>int</p></td>
<td><p>기본</p></td>
<td><p>콘텐츠 유형을 식별하는 고유 번호입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>ContentType</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td> </td>
<td><p>콘텐츠 유형 이름입니다.</p></td>
</tr>
</tbody>
</table>

