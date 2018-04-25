---
title: 'Lync Server 2013: MacAddress 테이블'
TOCTitle: MacAddress 테이블
ms:assetid: a32e68c5-3f95-4217-aff4-cb3d1cc70505
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412761(v=OCS.15)
ms:contentKeyID: 49304588
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 MacAddress 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

MacAddress 테이블은 지원 테이블입니다. 각 레코드는 하나의 소스를 나타냅니다.


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
<td><p><strong>MacAddressKey</strong></p></td>
<td><p>int</p></td>
<td><p>기본</p></td>
<td><p>Mac 주소를 식별하는 고유 번호입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>MacAddress</strong></p></td>
<td><p>varchar(256)</p></td>
<td><p>Unique</p></td>
<td><p>Mac 주소 문자열입니다.</p></td>
</tr>
</tbody>
</table>

