---
title: FocusJoinsAndLeaves 보기
TOCTitle: FocusJoinsAndLeaves 보기
ms:assetid: 226460ef-766f-4d61-80cb-f332b65a210d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ687992(v=OCS.15)
ms:contentKeyID: 49885680
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# FocusJoinsAndLeaves 보기

 

_**마지막으로 수정된 항목:** 2015-03-09_

FocusJoinsAndLeaves 보기에는 단일 전화 회의에 대한 참가 및 나가기 정보가 저장됩니다. 각 전화 회의는 이 보기에서 사용자가 전화 회의에 참가하고 전화 회의에서 나갈 때마다 기록되는 하나의 레코드로 표시됩니다. 이 보기는 Microsoft Lync Server 2013에서 도입되었습니다.


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
<td><p>전화 회의 인스턴스 시간입니다. SessionIdSeq와 함께 전화 회의 인스턴스를 고유하게 식별하기 위해 사용됩니다. 자세한 내용은 <a href="lync-server-2013-conferences-table.md">Lync Server 2013의 Conferences 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>전화 회의 인스턴스를 식별하기 위한 ID 번호입니다. SessionIdTime과 함께 전화 회의 인스턴스를 고유하게 식별하기 위해 사용됩니다. 자세한 내용은 <a href="lync-server-2013-conferences-table.md">Lync Server 2013의 Conferences 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserUri</strong></p></td>
<td><p>nvarchar(450)</p></td>
<td><p>전화 회의 참가/나가기 정보가 캡처된 사용자의 URL입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserUriType</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>전화 회의 참가/나가기 정보가 캡처된 사용자의 URL 유형입니다. 자세한 내용은 <a href="lync-server-2013-uritypes-table.md">Lync Server 2013의 UriTypes 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserTenant</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>전화 회의 참가/나가기 정보가 캡처된 사용자의 테넌트입니다. 자세한 내용은 <a href="lync-server-2013-tenants-table.md">Lync Server 2013의 Tenants 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserEndpointId</strong></p></td>
<td><p>uniqueidentifier</p></td>
<td><p>전화 회의 참가/나가기 정보가 캡처된 사용자의 고유 식별자입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserClientVersion</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>전화 회의 참가/나가기 정보가 캡처된 사용자가 사용하는 클라이언트의 버전입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserClientType</strong></p></td>
<td><p>int</p></td>
<td><p>전화 회의 참가/나가기 정보가 캡처된 사용자가 사용하는 클라이언트입니다. 자세한 내용은 <a href="lync-server-2013-useragentdef-table.md">Lync Server 2013의 UserAgentDef 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserClientCategory</strong></p></td>
<td><p>nvarchar(64)</p></td>
<td><p>전화 회의 참가/나가기 정보가 캡처된 사용자가 사용하는 클라이언트의 범주 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>FocusUserInstance</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p><strong>IsuserInternal</strong></p></td>
<td><p>bit</p></td>
<td><p>사용자가 내부 사용자인지 여부를 나타내는 비트입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>DialogSessionIdTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>세션 요청 시간입니다. SessionIdSeq와 함께 세션을 고유하게 식별하기 위해 사용됩니다. 자세한 내용은 <a href="lync-server-2013-dialogs-table.md">Lync Server 2013의 Dialogs 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DialogSessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>사용자가 동시에 여러 컴퓨터 또는 장치에 로그온되어 있으면 UserInstance를 사용하여 사용자/장치 조합을 고유하게 식별합니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>DialogId</strong></p></td>
<td><p>varchar(775)</p></td>
<td><p>세션의 SIP 대화 상자 ID입니다. dialog;from-tag;to-tag 형식입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserJoinTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>사용자가 전화 회의에 참가한 시간입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserLeaveTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>사용자가 전화 회의에서 나간 시간입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserRole</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>전화 회의에서 발표자 또는 참석자와 같은 사용자의 역할입니다.</p></td>
</tr>
</tbody>
</table>

