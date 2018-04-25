---
title: Lync Server 2013의 UserStatistics 테이블
TOCTitle: Lync Server 2013의 UserStatistics 테이블
ms:assetid: cfaf803b-1679-4169-92d3-533fad3e56ed
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721893(v=OCS.15)
ms:contentKeyID: 49885993
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 UserStatistics 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

UserStatistics 테이블은 지원 테이블입니다. 테이블의 각 레코드에는 개별 사용자의 시스템 사용 정보가 저장되어 있습니다. 이 테이블은 Microsoft Lync Server 2013에서 도입되었습니다.


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
<td><p><strong>UserId</strong></p></td>
<td><p>int</p></td>
<td><p>Primary</p></td>
<td><p>이 사용자를 식별하는 고유 번호입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>LastLogInTime</strong></p></td>
<td><p>datetime</p></td>
<td><p></p></td>
<td><p>사용자가 로그인한 마지막 시간입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>LastConfOrganizedTime</strong></p></td>
<td><p>datetime</p></td>
<td><p></p></td>
<td><p>사용자가 회의를 조직한 마지막 시간입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>LastCallOrganizerCallFailureTime</strong></p></td>
<td><p>datetime</p></td>
<td><p></p></td>
<td><p>사용자에게 통화 오류가 발생한 마지막 시간입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>LastConfOrganizerCallFailureTime</strong></p></td>
<td><p>datetime</p></td>
<td><p></p></td>
<td><p>회의 이끌이인 사용자에게 통화 오류가 발생한 마지막 시간입니다.</p></td>
</tr>
</tbody>
</table>

