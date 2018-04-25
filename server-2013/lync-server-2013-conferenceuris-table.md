---
title: 'Lync Server 2013: ConferenceUris 테이블'
TOCTitle: ConferenceUris 테이블
ms:assetid: b1721d52-3c65-45ea-8997-06af8fef93fc
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412854(v=OCS.15)
ms:contentKeyID: 49304757
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 ConferenceUris 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

ConfereneUris 테이블은 데이터베이스에 기록되는 회의 세션에 참여한 다양한 회의 URI 목록이 저장되는 지원 테이블입니다. 테이블의 각 레코드는 하나의 회의 URI를 나타냅니다.


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
<td><p><strong>NextUpdateTS</strong></p></td>
<td><p>datetime</p></td>
<td><p>기본</p></td>
<td><p>타임스탬프입니다. 내부적으로 사용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>ConferenceUriId</strong></p></td>
<td><p>int</p></td>
<td><p>기본</p></td>
<td><p>이 회의 URI를 식별하는 고유 번호입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ConferenceUri</strong></p></td>
<td><p>nvarchar(450)</p></td>
<td><p></p></td>
<td><p>회의 URI입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>Checksum</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>ConferenceUri의 체크섬입니다. 데이터베이스 검색 속도를 늘리기 위해 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UriTypeId</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>IM 회의의 conf:chat 또는 오디오/비디오 회의의 conf:audio-video와 같은 URI 유형입니다. 자세한 내용은 <a href="lync-server-2013-uritypes-table.md">Lync Server 2013의 UriTypes 테이블</a>을 참조하십시오.</p></td>
</tr>
</tbody>
</table>

