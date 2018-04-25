---
title: Lync Server 2013의 ErrorCategory 테이블
TOCTitle: Lync Server 2013의 ErrorCategory 테이블
ms:assetid: 0fde3b73-9a2f-44dd-b8dc-6df512303ff1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204675(v=OCS.15)
ms:contentKeyID: 49302828
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 ErrorCategory 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

ErrorCategory 테이블에는 각 Microsoft Lync Server 2013 진단 분류의 이름이 포함되어 있습니다. 기본적으로 Lync Server 2013에서는 다음 분류를 사용합니다.

  - 0 -- 성공

  - 1 -- 예상 오류

  - 2 -- 예기치 않은 오류

이 테이블은 Microsoft Lync Server 2013에서 도입되었습니다.


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
<td><p><strong>CategoryId</strong></p></td>
<td><p>tinyint</p></td>
<td><p>Primary</p></td>
<td><p>분류의 고유한 식별자입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>Name</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p></p></td>
<td><p>분류에 할당된 값과 이름입니다. 허용되는 값은 다음과 같습니다.</p>
<ul>
<li><p>0 -- 성공</p></li>
<li><p>1 -- 예상 오류</p></li>
<li><p>2 -- 예기치 않은 오류</p></li>
</ul></td>
</tr>
</tbody>
</table>

