---
title: 'Lync Server 2013: Pool 테이블'
TOCTitle: Pool 테이블
ms:assetid: 92ded8fd-d0ad-4f8a-9e6f-2e8a690fda3a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398746(v=OCS.15)
ms:contentKeyID: 49304399
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 Pool 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

Pool 테이블은 여러 프런트 엔드 풀에 대한 정보를 저장하는 지원 테이블입니다. 테이블의 각 레코드는 하나의 풀을 나타냅니다.


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
<td><p><strong>PoolKey</strong></p></td>
<td><p>int</p></td>
<td><p>기본</p></td>
<td><p>이 풀을 식별하는 고유 번호입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>PoolName</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>고유</p></td>
<td><p>풀 FQDN입니다.</p></td>
</tr>
</tbody>
</table>

