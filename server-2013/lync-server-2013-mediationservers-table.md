---
title: 'Lync Server 2013: MediationServers 테이블'
TOCTitle: MediationServers 테이블
ms:assetid: 9f757377-ab79-4795-aaa9-1163cb9c8a59
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412743(v=OCS.15)
ms:contentKeyID: 49304556
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 MediationServers 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

MediationServers 테이블은 지원 테이블입니다. 각 레코드는 레코드가 있는 통화에 포함된 하나의 중재 서버에 대한 정보를 데이터베이스에 저장합니다.


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
<td><p><strong>MediationServerId</strong></p></td>
<td><p>int</p></td>
<td><p>기본</p></td>
<td><p>이 중재 서버를 식별하는 고유 번호입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>MediationServer</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p> </p></td>
<td><p>중재 서버 이름입니다.</p></td>
</tr>
</tbody>
</table>

