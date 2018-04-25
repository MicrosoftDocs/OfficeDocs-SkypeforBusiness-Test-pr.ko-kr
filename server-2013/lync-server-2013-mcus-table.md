---
title: 'Lync Server 2013: Mcus 테이블'
TOCTitle: Mcus 테이블
ms:assetid: 271b7963-8fd8-4d92-a701-1a62aaf895ee
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425742(v=OCS.15)
ms:contentKeyID: 49303106
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 Mcus 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

Mcus 테이블은 지원 테이블입니다. 각 레코드는 하나의 회의 서비스에 대한 정보를 저장합니다. 여기에는 IM 회의 서비스 및 전화 회의 서비스(프런트 엔드 서버에 대한 프로세스로 실행), 웹 회의 서비스 및 A/V 회의 서비스가 포함될 수 있습니다.


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
<td><p><strong>McuId</strong></p></td>
<td><p>int</p></td>
<td><p>기본</p></td>
<td><p>이 회의 서버를 식별하는 고유 번호입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>McuUri</strong></p></td>
<td><p>nvarchar(450)</p></td>
<td><p> </p></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p><strong>McuTypeId</strong></p></td>
<td><p>inyint</p></td>
<td><p>외래</p></td>
<td><p>conf:chat(IM용) 또는 conf:audio-video와 같은 회의 서버 유형입니다. 자세한 내용은 <a href="lync-server-2013-uritypes-table.md">Lync Server 2013의 UriTypes 테이블</a>을 참조하십시오.</p></td>
</tr>
</tbody>
</table>

