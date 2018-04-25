---
title: 'Lync Server 2013: Devices 테이블'
TOCTitle: Devices 테이블
ms:assetid: 532e2280-4bbc-4a6c-93da-45d9f80a30a0
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398351(v=OCS.15)
ms:contentKeyID: 49303643
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 Devices 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

Devices 테이블은 지원 테이블입니다. 각 레코드에는 하나의 장치(일반 전화)에 대한 정보가 저장됩니다.


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
<td><p><strong>DeviceId</strong></p></td>
<td><p>int</p></td>
<td><p>기본</p></td>
<td><p>이 하드웨어 버전을 식별하는 고유 번호입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>ManufacturerId</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>이 장치의 제조업체입니다. 자세한 내용은 <a href="lync-server-2013-manufacturers-table.md">Lync Server 2013의 Manufacturers 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>HardwareVersionId</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>이 장치의 하드웨어 버전입니다. 자세한 내용은 <a href="lync-server-2013-hardwareversions-table.md">Lync Server 2013의 HardwareVersions 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>MacAddress</strong></p></td>
<td><p>bigint</p></td>
<td><p></p></td>
<td><p>MAC 주소</p></td>
</tr>
</tbody>
</table>

