---
title: 'Lync Server 2013: EndpointSubnet 테이블'
TOCTitle: EndpointSubnet 테이블
ms:assetid: d62e51d6-2117-4c41-adce-08f8d9d75ce0
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398933(v=OCS.15)
ms:contentKeyID: 49305167
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 EndpointSubnet 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

EndpointSubnet 테이블은 지원 테이블입니다. 각 레코드는 끝점에서 캡처된 하나의 서브넷을 나타냅니다.


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
<td><p><strong>SubnetIP</strong></p></td>
<td><p>int</p></td>
<td><p>기본, 외래</p></td>
<td><p>정수로 표시된 서브넷입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>NextUpdateTS</strong></p></td>
<td><p>datetime</p></td>
<td><p></p></td>
<td><p>내부 용도로만 사용됩니다.</p></td>
</tr>
</tbody>
</table>

