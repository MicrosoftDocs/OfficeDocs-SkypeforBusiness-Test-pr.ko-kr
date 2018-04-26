---
title: 'Lync Server 2013: DeviceDriver 테이블'
TOCTitle: DeviceDriver 테이블
ms:assetid: ca91a0b4-98c0-49f6-af9d-7d0f8ac75f1a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398844(v=OCS.15)
ms:contentKeyID: 49305035
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 DeviceDriver 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

DeviceDriver 테이블은 지원 테이블입니다. 각 레코드는 캡처 장치 또는 렌더링 장치에서 사용되는 드라이버를 나타냅니다.


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
<td><p><strong>DeviceDriverKey</strong></p></td>
<td><p>int</p></td>
<td><p>기본</p></td>
<td><p>이 장치 드라이버 레코드를 식별하는 고유 번호입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>DeviceDriver</strong></p></td>
<td><p>varchar(256)</p></td>
<td><p>unique</p></td>
<td><p>장치 드라이버 이름입니다.</p></td>
</tr>
</tbody>
</table>

