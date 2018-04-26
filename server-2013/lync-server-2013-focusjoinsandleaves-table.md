---
title: 'Lync Server 2013: FocusJoinsAndLeaves 테이블'
TOCTitle: FocusJoinsAndLeaves 테이블
ms:assetid: e6f0212c-67e9-4061-8720-d0296e855991
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399026(v=OCS.15)
ms:contentKeyID: 49305355
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 FocusJoinsAndLeaves 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

이 테이블의 각 레코드에는 한 회의에 대한 사용자의 입장 및 퇴장 정보에 대한 CDR 정보가 포함됩니다. 각 회의는 이 테이블에서 사용자가 회의에 입장하고 퇴장할 때마다 하나의 레코드로 표시됩니다.


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
<td><p><strong>DialogSessionIdTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>기본, 외래</p></td>
<td><p>세션 요청 시간입니다. <strong>SessionIdSeq</strong> 와 함께 세션을 고유하게 식별하기 위해 사용됩니다. 자세한 내용은 <a href="lync-server-2013-dialogs-table.md">Lync Server 2013의 Dialogs 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>DialogSessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>기본, 외래</p></td>
<td><p>세션을 식별하기 위한 ID 번호입니다. <strong>SessionIdTime</strong> 과 함께 세션을 고유하게 식별하기 위해 사용됩니다. 자세한 내용은 <a href="lync-server-2013-dialogs-table.md">Lync Server 2013의 Dialogs 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserId</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>이 사용자를 식별하는 고유 번호입니다. <a href="lync-server-2013-users-table.md">Lync Server 2013의 Users 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>FocusUserInstance</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>사용자가 동시에 여러 컴퓨터 또는 장치에 로그온되어 있으면 <strong>UserInstance</strong> 를 사용하여 사용자/장치 조합을 고유하게 식별합니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>IsUserInternal</strong></p></td>
<td><p>bit</p></td>
<td><p> </p></td>
<td><p>사용자가 내부로부터 로그온되었는지 여부입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserRole</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>회의에서 발표자 또는 참석자와 같은 이 사용자의 역할입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserJoinTime</strong></p></td>
<td><p>datetime</p></td>
<td><p> </p></td>
<td><p>이 사용자가 회의에 참가하는 시간입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserLeaveTime</strong></p></td>
<td><p>datetime</p></td>
<td><p> </p></td>
<td><p>이 사용자가 회의에서 나가는 시간입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ClientVerId</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>사용자의 클라이언트 소프트웨어 버전입니다. <a href="lync-server-2013-clientversions-table.md">Lync Server 2013의 ClientVersions 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserEndpointId</strong></p></td>
<td><p>uniqueIdentifier</p></td>
<td><p></p></td>
<td><p>전화 회의에 사용된 끝점의 GUID(Globally Unique Identification)입니다.</p>
<p>이 필드는 Microsoft Lync Server 2013에 새로 도입되었습니다.</p></td>
</tr>
</tbody>
</table>

