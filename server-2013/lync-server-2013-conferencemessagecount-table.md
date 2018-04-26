---
title: 'Lync Server 2013: ConferenceMessageCount 테이블'
TOCTitle: ConferenceMessageCount 테이블
ms:assetid: 78569dbf-5217-42fa-ba1a-4380f56e2a3d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398590(v=OCS.15)
ms:contentKeyID: 49304099
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 ConferenceMessageCount 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

이 테이블의 각 레코드는 하나의 IM 회의에 있는 한 명의 사용자를 나타내며 해당 사용자가 전송한 메시지 수를 포함합니다. 각 회의는 각 사용자에 대해 하나씩 이 테이블의 여러 레코드로 나타낼 수 있습니다.


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
<td><p>기본, 외래</p></td>
<td><p>회의 인스턴스의 시간입니다. <strong>SessionIdSeq</strong> 와 함께 회의 인스턴스를 고유하게 식별하기 위해 사용됩니다. 자세한 내용은 <a href="lync-server-2013-conferences-table.md">Lync Server 2013의 Conferences 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>기본, 외래</p></td>
<td><p>회의 인스턴스를 식별하기 위한 ID 번호입니다. <strong>SessionIdTime</strong> 과 함께 회의 인스턴스를 고유하게 식별하기 위해 사용됩니다. 자세한 내용은 <a href="lync-server-2013-conferences-table.md">Lync Server 2013의 Conferences 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserId</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>이 사용자를 식별하는 고유 번호입니다. <a href="lync-server-2013-users-table.md">Lync Server 2013의 Users 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>MessageCount</strong></p></td>
<td><p>smallint</p></td>
<td><p> </p></td>
<td><p>이 회의 중 이 사용자가 보낸 메시지 수입니다.</p></td>
</tr>
</tbody>
</table>

