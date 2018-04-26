---
title: 'Lync Server 2013: MediaList 테이블'
TOCTitle: MediaList 테이블
ms:assetid: 1f440590-c1bc-483e-b7bc-6cc763847768
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398279(v=OCS.15)
ms:contentKeyID: 49303010
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 MediaList 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

MediaList 테이블은 다양한 미디어 유형 목록이 저장된 정적 테이블입니다.


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
<td><p><strong>MediaId</strong></p></td>
<td><p>tinyint</p></td>
<td><p>기본</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p><strong>Media</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p></p></td>
<td><p>허용되는 값:</p>
<ul>
<li><p>1 – IM</p></li>
<li><p>2 – 파일 전송</p></li>
<li><p>3 – 원격 지원</p></li>
<li><p>4 – 응용 프로그램 공유</p></li>
<li><p>5 – 오디오</p></li>
<li><p>6 – 비디오</p></li>
<li><p>7 – 응용 프로그램 초대</p></li>
</ul></td>
</tr>
</tbody>
</table>

