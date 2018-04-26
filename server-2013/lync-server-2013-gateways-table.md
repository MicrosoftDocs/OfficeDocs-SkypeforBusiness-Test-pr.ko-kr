---
title: 'Lync Server 2013: Gateways 테이블'
TOCTitle: Gateways 테이블
ms:assetid: a909daad-d137-45e0-b149-1de9f8e1e029
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412795(v=OCS.15)
ms:contentKeyID: 49304660
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 Gateways 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

Gateways 테이블은 지원 테이블입니다. 각 레코드에는 데이터베이스에 레코드가 있는 PSTN(공중 전화망) 통화와 관련된 하나의 게이트웨이에 대한 정보가 저장됩니다.


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
<td><p><strong>GatewayId</strong></p></td>
<td><p>int</p></td>
<td><p>기본</p></td>
<td><p>이 게이트웨이를 식별하는 고유 번호입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>Gateway</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p> </p></td>
<td><p>게이트웨이 이름입니다.</p></td>
</tr>
</tbody>
</table>

