---
title: 'Lync Server 2013: Device 테이블'
TOCTitle: Device 테이블
ms:assetid: d5a4f777-bc12-4ce8-bc0d-867d5e22b436
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398930(v=OCS.15)
ms:contentKeyID: 49305164
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 Device 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

Device 테이블은 여러 캡처 또는 렌더링 장치에 대한 정보를 저장하는 지원 테이블입니다. 테이블의 각 레코드는 하나의 장치를 나타냅니다.


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
<td><p><strong>DeviceKey</strong></p></td>
<td><p>int</p></td>
<td><p>기본</p></td>
<td><p>이 장치를 식별하는 고유 번호입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>DeviceName</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>DeviceName + DeviceType은 고유합니다.</p></td>
<td><p>장치 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DeviceType</strong></p></td>
<td><p>bit</p></td>
<td><p>DeviceName + DeviceType은 고유합니다.</p></td>
<td><p>장치 유형입니다. 1은 캡처 장치이고 0은 렌더링 장치입니다.</p></td>
</tr>
</tbody>
</table>

