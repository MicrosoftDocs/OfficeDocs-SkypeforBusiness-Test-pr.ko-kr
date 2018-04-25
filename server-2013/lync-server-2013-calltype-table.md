---
title: 'Lync Server 2013: CallType 테이블'
TOCTitle: CallType 테이블
ms:assetid: a1d7187c-f851-4967-88ea-73922911ee7a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412752(v=OCS.15)
ms:contentKeyID: 49304576
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 CallType 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

CallType 테이블은 사용 가능한 통화 유형 목록이 저장된 정적 테이블입니다.


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
<td><p><strong>CallTypeId</strong></p></td>
<td><p>int</p></td>
<td><p>기본</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>CallType</strong></p></td>
<td><p>nvarchar</p></td>
<td><p></p></td>
<td><p>허용되는 값:</p>
<ul>
<li><p>0 – 알 수 없음</p></li>
<li><p>1 – 인스턴트 메시징</p></li>
<li><p>2 – 응용 프로그램 공유</p></li>
<li><p>3 – 오디오</p></li>
<li><p>4 – 오디오 및 비디오</p></li>
<li><p>5 – 파일 전송</p></li>
</ul></td>
</tr>
</tbody>
</table>

