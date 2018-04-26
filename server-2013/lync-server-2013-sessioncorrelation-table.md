---
title: 'Lync Server 2013: SessionCorrelation 테이블'
TOCTitle: SessionCorrelation 테이블
ms:assetid: 041705e1-7290-464f-95f8-96256cfa2e3e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398091(v=OCS.15)
ms:contentKeyID: 49302652
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 SessionCorrelation 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

SessionCorrelation 테이블은 지원 테이블입니다. 각 레코드는 여러 세션의 관계를 지정하는 데 사용되는 하나의 CorrelationID를 나타냅니다.


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
<td><p><strong>Checksum</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>CorrelationKey</strong></p></td>
<td><p>int</p></td>
<td><p>기본</p></td>
<td><p>이 A/V 회의 서버를 식별하는 고유 번호입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CorrelationID</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>Unique</p></td>
<td><p>상호 연관된 세션은 상관 ID가 동일합니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>NextUpdateTS</strong></p></td>
<td><p>datetime</p></td>
<td><p> </p></td>
<td><p>내부 용도로만 사용됩니다.</p></td>
</tr>
</tbody>
</table>

