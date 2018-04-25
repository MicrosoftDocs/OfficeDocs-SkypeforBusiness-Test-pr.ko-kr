---
title: 'Lync Server 2013: McuJoinsAndLeaves 테이블'
TOCTitle: McuJoinsAndLeaves 테이블
ms:assetid: 4e073366-0b5d-45b4-a3f6-d63dd5fd9f25
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398316(v=OCS.15)
ms:contentKeyID: 49303596
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 McuJoinsAndLeaves 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

이 테이블의 각 레코드에는 사용자의 회의 입장 또는 퇴장과 회의 서버를 하나로 조합한 결과에 대한 통화 세부 정보가 포함됩니다. 예를 들어 사용자가 웹 회의 및 오디오/비디오 요소가 포함된 회의에 참여하면 해당 사용자의 웹 회의 입장에 대한 레코드가 하나 만들어지고 사용자의 오디오/비디오 회의 입장에 대한 다른 레코드가 만들어집니다.


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
<td><p>기본, 외래</p></td>
<td><p>이 사용자를 식별하는 고유 번호입니다. 자세한 내용은 <a href="lync-server-2013-users-table.md">Lync Server 2013의 Users 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>McuUserInstance</strong></p></td>
<td><p>int</p></td>
<td><p>기본</p></td>
<td><p>사용자가 한 번에 여러 컴퓨터 또는 장치에 로그온된 경우 McuUserInstance는 사용자/장치 조합을 고유하게 식별합니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>IsFromPstn</strong></p></td>
<td><p>bit</p></td>
<td><p> </p></td>
<td><p>사용자가 PSTN으로부터 참가 중인지 여부입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>McuId</strong></p></td>
<td><p>int</p></td>
<td><p>기본, 외래</p></td>
<td><p>이 회의 서버를 식별하는 고유 번호입니다. 자세한 내용은 <a href="lync-server-2013-mcus-table.md">Lync Server 2013의 Mcus 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DialogSessionIdTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>외래</p></td>
<td><p>세션 요청 시간입니다. <strong>SessionIdSeq</strong> 와 함께 세션을 고유하게 식별하기 위해 사용됩니다. 자세한 내용은 <a href="lync-server-2013-dialogs-table.md">Lync Server 2013의 Dialogs 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>DialogSessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>세션을 식별하기 위한 ID 번호입니다. <strong>SessionIdTime</strong> 과 함께 세션을 고유하게 식별하기 위해 사용됩니다. 자세한 내용은 <a href="lync-server-2013-dialogs-table.md">Lync Server 2013의 Dialogs 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserJoinTime</strong></p></td>
<td><p>datetime</p></td>
<td><p> </p></td>
<td><p>이 사용자가 이 회의 서버에 참가하는 시간입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserLeaveTime</strong></p></td>
<td><p>datetime</p></td>
<td><p> </p></td>
<td><p>이 사용자가 이 회의 서버를 나가는 시간입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ClientVerId</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>회의에 사용된 클라이언트 소프트웨어의 버전 번호를 지정하는 식별자입니다. 자세한 내용은 <a href="lync-server-2013-clientversions-table.md">Lync Server 2013의 ClientVersions 테이블</a>을 참조하십시오.</p>
<p>이 필드는 Microsoft Lync Server 2013에 새로 도입되었습니다.</p></td>
</tr>
</tbody>
</table>

