---
title: McuJoinsAndLeaves 보기
TOCTitle: McuJoinsAndLeaves 보기
ms:assetid: 6f00b8e7-b8b6-4657-ac5e-d8a571806ae2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688088(v=OCS.15)
ms:contentKeyID: 49885805
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# McuJoinsAndLeaves 보기

 

_**마지막으로 수정된 항목:** 2015-03-09_

McuJoinsAndLeaves 보기에는 하나의 회의 서버에 대한 사용자 입장 및 퇴장 정보가 저장됩니다. 이 보기의 각 레코드에는 사용자 입장 또는 퇴장과 회의 서버의 조합에 대한 통화 세부 정보가 포함됩니다. 이 보기는 Microsoft Lync Server 2013에서 도입되었습니다.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>열</th>
<th>데이터 형식</th>
<th>세부 정보</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>SessionIdTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>회의 인스턴스의 시간입니다. SessionIdSeq와 함께 회의 인스턴스를 고유하게 식별하기 위해 사용됩니다. 자세한 내용은 <a href="lync-server-2013-conferences-table.md">Lync Server 2013의 Conferences 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>회의 인스턴스를 식별하기 위한 ID 번호입니다. SessionIdTime과 함께 회의 인스턴스를 고유하게 식별하기 위해 사용됩니다. 자세한 내용은 <a href="lync-server-2013-conferences-table.md">Lync Server 2013의 Conferences 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>McuUri</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>사용자가 연결된 회의 서버의 URL입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>McuUriType</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>사용자가 연결된 회의 서버의 URL입니다. 자세한 내용은 <a href="lync-server-2013-uritypes-table.md">Lync Server 2013의 UriTypes 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserUri</strong></p></td>
<td><p>nvarchar(450)</p></td>
<td><p>회의 서버 입장/퇴장 정보가 캡처된 사용자의 URI입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserUriType</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>회의 서버 입장/퇴장 정보가 캡처된 사용자의 URI 유형입니다. 자세한 내용은 <a href="lync-server-2013-uritypes-table.md">Lync Server 2013의 UriTypes 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserTenant</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>회의 서버 입장/퇴장 정보가 캡처된 사용자의 테넌트입니다. 자세한 내용은 <a href="lync-server-2013-tenants-table.md">Lync Server 2013의 Tenants 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserClientVersion</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>회의 서버 입장/퇴장 정보가 캡처된 사용자가 사용한 클라이언트 버전입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserClientType</strong></p></td>
<td><p>int</p></td>
<td><p>회의 서버 입장/퇴장 정보가 캡처된 사용자가 사용한 클라이언트입니다. 자세한 내용은 <a href="lync-server-2013-useragentdef-table.md">Lync Server 2013의 UserAgentDef 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserClientCategory</strong></p></td>
<td><p>nvarchar(64)</p></td>
<td><p>회의 서버 입장/퇴장 정보가 캡처된 사용자가 사용한 클라이언트의 범주 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>McuUserInstance</strong></p></td>
<td><p>int</p></td>
<td><p>여러 장치에 동시에 로그인한 사용자의 사용자/장치 조합을 고유하게 식별합니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>IsUserFromPstn</strong></p></td>
<td><p>bit</p></td>
<td><p>사용자가 내부 사용자인지 여부를 나타내는 비트입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DialogSessionIdTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>세션 요청 시간입니다. SessionIdSeq와 함께 세션을 고유하게 식별하기 위해 사용됩니다. 자세한 내용은 <a href="lync-server-2013-dialogs-table.md">Lync Server 2013의 Dialogs 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>DialogSessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>세션을 식별하기 위한 ID 번호입니다. SessionIdTime과 함께 세션을 고유하게 식별하기 위해 사용됩니다. 자세한 내용은 <a href="lync-server-2013-dialogs-table.md">Lync Server 2013의 Dialogs 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DialogId</strong></p></td>
<td><p>varchar(775)</p></td>
<td><p>세션의 SIP 대화 ID입니다. 형식은 dialog;from-tag;to-tag입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserJoinTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>사용자가 회의 서버에 참가한 시간입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserLeaveTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>사용자가 회의 서버에서 나간 시간입니다.</p></td>
</tr>
</tbody>
</table>

