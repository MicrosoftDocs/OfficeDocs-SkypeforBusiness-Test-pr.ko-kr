---
title: 'Lync Server 2013: Conferences 테이블'
TOCTitle: Conferences 테이블
ms:assetid: c3da6271-b3c6-4898-894f-10456ec794d0
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412964(v=OCS.15)
ms:contentKeyID: 49304947
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 Conferences 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

이 테이블의 각 레코드에는 하나의 회의에 대한 통화 정보가 포함됩니다.


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
<td><p><strong>SessionIdTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>기본</p></td>
<td><p>회의 요청이 CDR 에이전트에서 캡처된 시간입니다. 회의 인스턴스를 고유하게 식별하기 위해 기본 키로만 사용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>기본</p></td>
<td><p>세션을 식별하기 위한 ID 번호입니다. <strong>SessionIdTime</strong> 과 함께 회의 인스턴스를 고유하게 식별하기 위해 사용됩니다. *</p></td>
</tr>
<tr class="odd">
<td><p><strong>ConferenceUriId</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>회의 URI입니다. 자세한 내용은 <a href="lync-server-2013-conferenceuris-table.md">Lync Server 2013의 ConferenceUris 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>ConfInstance</strong></p></td>
<td><p>uniqueidentifier</p></td>
<td><p> </p></td>
<td><p>되풀이 회의에 유용합니다. 되풀이 회의의 각 인스턴스에는 동일한 <strong>ConferenceUri</strong> 가 포함되지만 <strong>ConfInstance</strong> 가 서로 다릅니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ConferenceStartTime</strong></p></td>
<td><p>datetime</p></td>
<td><p> </p></td>
<td><p>회의 종료 시간입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>ConferenceEndTime</strong></p></td>
<td><p>datetime</p></td>
<td><p> </p></td>
<td><p>회의 종료 시간입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>PoolId</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>회의가 캡처된 풀을 식별하는 ID 번호입니다. 자세한 내용은 <a href="lync-server-2013-pools-table.md">Lync Server 2013의 Pools 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>OrganizerId</strong></p></td>
<td><p>Int</p></td>
<td><p>외래</p></td>
<td><p>이 회의의 이끌이 URI를 식별하기 위한 ID 번호입니다. 자세한 내용은 <a href="lync-server-2013-users-table.md">Lync Server 2013의 Users 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Flag</strong></p></td>
<td><p>smallint</p></td>
<td><p></p></td>
<td><p>회의 특성을 포함하는 비트 마스크입니다. 사용할 수 있는 값은 다음과 같습니다.</p>
<ul>
<li><p>0X01</p></li>
<li><p>가상</p></li>
<li><p>트랜잭션</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Processed</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>모니터링 서비스에서 사용하는 내부 필드입니다.</p>
<p>이 필드는 Microsoft Lync Server 2013에 새로 도입되었습니다.</p></td>
</tr>
</tbody>
</table>


\* 대부분의 경우 SessionIdSeq는 1을 해당 값으로 사용합니다. 두 개의 세션이 정확히 동시에 시작될 경우 한 세션에 대한 SessionIdSeq가 1이 되고 다른 세션에 대해서는 2가 지정됩니다.

