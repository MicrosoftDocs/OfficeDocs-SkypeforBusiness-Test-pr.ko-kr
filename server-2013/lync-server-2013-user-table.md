---
title: 'Lync Server 2013: User 테이블'
TOCTitle: User 테이블
ms:assetid: 6b52047e-286d-47ab-b7bc-a9b266f62d82
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398505(v=OCS.15)
ms:contentKeyID: 49303948
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 User 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

User 테이블은 데이터베이스에 기록되는 세션에 참여한 다양한 사용자 목록이 저장되는 지원 테이블입니다. 테이블의 각 레코드는 한 명의 사용자를 나타냅니다.


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
<td><p><strong>UserKey</strong></p></td>
<td><p>int</p></td>
<td><p>기본</p></td>
<td><p>이 사용자를 식별하는 고유 번호입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>URI</strong></p></td>
<td><p>nvarchar(450)</p></td>
<td><p>Unique</p></td>
<td><p>URI 문자열입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>URIType</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>1은 알 수 없는 URI 유형입니다.</p>
<p>2는 사용자 URI입니다.</p>
<p>4는 회의 URI입니다.</p>
<p>8은 전화 URI입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>TenantKey</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>사용자의 테넌트입니다. 테넌트 테이블을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>LastPoorCallTime</strong></p></td>
<td><p>datetime</p></td>
<td><p></p></td>
<td><p>사용자의 오디오 통화 품질이 낮은 최근 타임스탬프입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>NextUpdateTS</strong></p></td>
<td><p>datetime</p></td>
<td><p></p></td>
<td><p>내부 용도로만 사용됩니다.</p></td>
</tr>
</tbody>
</table>

