---
title: 'Lync Server 2013: Region 테이블'
TOCTitle: Region 테이블
ms:assetid: 1751a6aa-a6e8-4f16-8eb7-ae731c2e3ee3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398235(v=OCS.15)
ms:contentKeyID: 49302931
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 Region 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

Region 테이블은 지원 테이블입니다. 각 레코드는 네트워크 구성 설정에 정의된 하나의 국가/지역을 나타냅니다.


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
<td><p><strong>RegionKey</strong></p></td>
<td><p>int</p></td>
<td><p>기본</p></td>
<td><p>국가/지역을 식별하는 고유 번호입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>RegionName</strong></p></td>
<td><p>nvarchar(128)</p></td>
<td><p>Unique</p></td>
<td><p>국가/지역의 이름입니다.</p></td>
</tr>
</tbody>
</table>

