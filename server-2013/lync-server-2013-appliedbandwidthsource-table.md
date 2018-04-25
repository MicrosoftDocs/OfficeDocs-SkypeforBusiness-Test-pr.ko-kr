---
title: 'Lync Server 2013: AppliedBandwidthSource 테이블'
TOCTitle: AppliedBandwidthSource 테이블
ms:assetid: 24fb3caf-19b3-4c0a-90d7-ca5d53de32ad
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425725(v=OCS.15)
ms:contentKeyID: 49303078
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 AppliedBandwidthSource 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

AppliedBandwidthSource 테이블은 지원 테이블입니다. 각 레코드는 하나의 소스를 나타냅니다.


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
<td><p><strong>AppliedBandwidthSourceKey</strong></p></td>
<td><p>int</p></td>
<td><p>기본</p></td>
<td><p>원본을 식별하는 고유 번호입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>AppliedBandwidthSource</strong></p></td>
<td><p>varchar(256)</p></td>
<td><p>Unique</p></td>
<td><p>적용 중인 대역폭 용량의 원본입니다. 이 원본은 대역폭 제한이 시작되는 위치(예: &quot;정책 서버&quot;, &quot;TURN 서버&quot; 또는 &quot;형식&quot;)를 설명합니다.</p></td>
</tr>
</tbody>
</table>

