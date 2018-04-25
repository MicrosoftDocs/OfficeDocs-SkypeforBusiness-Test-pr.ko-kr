---
title: 'Lync Server 2013: UriTypes 테이블'
TOCTitle: UriTypes 테이블
ms:assetid: 77c4dfae-1b29-4e81-ba05-609e61643998
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398587(v=OCS.15)
ms:contentKeyID: 49304092
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 UriTypes 테이블

 

_**마지막으로 수정된 항목:** 2015-06-16_

UriTypes 테이블에는 Microsoft Lync Server 2013에서 모니터링되는 다른 URI(Uniform resource identifier) 유형이 포함됩니다.


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
<td><p><strong>UriTypeId</strong></p></td>
<td><p>tinyint</p></td>
<td><p>기본</p></td>
<td><p>URI 유형에 지정된 고유 식별자입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>UriType</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p></p></td>
<td><p>다른 URI 유형에 대한 설명입니다. 허용되는 값은 다음과 같습니다.</p>
<ul>
<li><p>0 – Phone Uri</p></li>
<li><p>1 – User Uri</p></li>
</ul></td>
</tr>
</tbody>
</table>

