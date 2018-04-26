---
title: SessionDetails 보기
TOCTitle: SessionDetails 보기
ms:assetid: ea328c6f-cf22-48dd-8f7f-f1666c9148c8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721924(v=OCS.15)
ms:contentKeyID: 49886033
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# SessionDetails 보기

 

_**마지막으로 수정된 항목:** 2015-03-09_

SessionDetails 보기는 피어 투 피어 세션(VoIP-VoIP 전화 통화, 두 사용자 간 IM 세션 또는 기타 세션 유형)에 대한 정보를 저장합니다. 이 보기는 Microsoft Lync Server 2013에 새로 도입되었습니다.


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
<td><p>세션 요청 시간입니다. SessionIdSeq와 함께 세션을 고유하게 식별하기 위해 사용됩니다. 자세한 내용은 <a href="lync-server-2013-dialogs-table.md">Lync Server 2013의 Dialogs 테이블</a> 테이블을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>세션을 식별하기 위한 ID 번호입니다. SessionIdTime과 함께 세션을 고유하게 식별하기 위해 사용됩니다. 자세한 내용은 <a href="lync-server-2013-dialogs-table.md">Lync Server 2013의 Dialogs 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>InviteTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>첫 번째 INVITE 요청의 시간입니다. 이 필드는 일반적으로 세션의 초기 INVITE 메시지에서 생성된 데이터로 채워집니다. INVITE 메시지가 없으면 이 필드는 첫 번째 관련 SIP 메시지(BYE, CANCEL, MESSAGE 또는 INFO)의 날짜 및 시간으로 채워집니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>FromUri</strong></p></td>
<td><p>nvarchar(450)</p></td>
<td><p>세션을 시작한 사용자의 URI입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ToUri</strong></p></td>
<td><p>nvarchar(450)</p></td>
<td><p>세션에 참가한 사용자의 URI입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>FromUriType</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>세션을 시작한 사용자의 URI 형식입니다. 자세한 내용은 <a href="lync-server-2013-uritypes-table.md">Lync Server 2013의 UriTypes 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ToUriType</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>세션에 참가한 사용자의 URI 형식입니다. 자세한 내용은 <a href="lync-server-2013-uritypes-table.md">Lync Server 2013의 UriTypes 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>FromTenant</strong></p></td>
<td><p>nvarchar(450)</p></td>
<td><p>세션을 시작한 사용자의 테넌트입니다. 자세한 내용은 <a href="lync-server-2013-tenants-table.md">Lync Server 2013의 Tenants 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ToTenant</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>세션에 참가한 사용자의 테넌트입니다. 자세한 내용은 <a href="lync-server-2013-tenants-table.md">Lync Server 2013의 Tenants 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>FromEndpointId</strong></p></td>
<td><p>uniqueidentifier</p></td>
<td><p>세션을 시작한 사용자의 고유한 끝점 식별자입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ToEndpointId</strong></p></td>
<td><p>uniqueidentifier</p></td>
<td><p>세션에 참가한 사용자의 고유한 끝점 식별자입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>EndTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>세션 종료 시간입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>FromMessageCount</strong></p></td>
<td><p>int</p></td>
<td><p>세션을 시작한 사용자가 보낸 메시지 수입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>ToMessageCount</strong></p></td>
<td><p>int</p></td>
<td><p>세션에 참가한 사용자가 보낸 메시지 수입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>FromClientVersion</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>세션을 시작한 사용자가 사용하는 클라이언트 버전입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>FromClientType</strong></p></td>
<td><p>int</p></td>
<td><p>세션을 시작한 사용자가 사용하는 클라이언트입니다. 자세한 내용은 <a href="lync-server-2013-useragentdef-table.md">Lync Server 2013의 UserAgentDef 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>FromClientCategory</strong></p></td>
<td><p>nvarchar(64)</p></td>
<td><p>세션을 시작한 사용자가 사용하는 클라이언트의 범주 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>ToClientVersion</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>세션에 참가한 사용자가 사용하는 클라이언트 버전입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ToClientType</strong></p></td>
<td><p>int</p></td>
<td><p>세션에 참가한 사용자가 사용하는 클라이언트입니다. 자세한 내용은 <a href="lync-server-2013-useragentdef-table.md">Lync Server 2013의 UserAgentDef 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>ToClientCategory</strong></p></td>
<td><p>nvarchar(64)</p></td>
<td><p>세션에 참가한 사용자가 사용하는 클라이언트의 범주 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>TargetUri</strong></p></td>
<td><p>nvarchar(450)</p></td>
<td><p>세션 대상 사용자의 URI입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>TargetUriType</strong></p></td>
<td><p>nvarchar(450)</p></td>
<td><p>세션 대상 사용자의 URI 형식입니다. 자세한 내용은 <a href="lync-server-2013-uritypes-table.md">Lync Server 2013의 UriTypes 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>OnBehalfOfUri</strong></p></td>
<td><p>nvarchar(450)</p></td>
<td><p>세션이 대신 시작된 사용자의 URI입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>OnnnBehalfOfUriType</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>세션이 대신 시작된 사용자의 URI 형식입니다. 자세한 내용은 <a href="lync-server-2013-uritypes-table.md">Lync Server 2013의 UriTypes 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>OnBehalfOfTenant</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>세션이 대신 시작된 사용자의 테넌트입니다. 자세한 내용은 <a href="lync-server-2013-tenants-table.md">Lync Server 2013의 Tenants 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>ReferredByUri</strong></p></td>
<td><p>nvarchar(450)</p></td>
<td><p>세션을 참조한 사용자의 URI입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ReferredByUriType</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>세션을 참조한 사용자의 URI 형식입니다. 자세한 내용은 <a href="lync-server-2013-uritypes-table.md">Lync Server 2013의 UriTypes 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>ReferredByTenant</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>세션을 참조한 사용자의 테넌트입니다. 자세한 내용은 <a href="lync-server-2013-tenants-table.md">Lync Server 2013의 Tenants 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DialogId</strong></p></td>
<td><p>varchar(775)</p></td>
<td><p>SIP 대화 ID입니다. 형식은 다음과 같습니다.</p>
<p>dialog;from-tag;to-tag</p></td>
</tr>
<tr class="even">
<td><p><strong>CorrelationId</strong></p></td>
<td><p>uniqueidentifier</p></td>
<td><p>여러 세션의 관계를 지정하는 데 사용된 GUID입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ReplaceDialogIdTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>해당 새션으로 대체된 대화의 시간입니다 ReplaceDialogIdSeq와 함께 해당 세션으로 대체되는 대화를 고유하게 식별하는 데 사용됩니다. 자세한 내용은 <a href="lync-server-2013-dialogs-table.md">Lync Server 2013의 Dialogs 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>ReplaceDialogIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>세션을 식별하기 위한 ID 번호입니다. ReplaceDialogIdTime과 함께 해당 세션으로 대체되는 대화를 고유하게 식별하는 데 사용됩니다. 자세한 내용은 <a href="lync-server-2013-dialogs-table.md">Lync Server 2013의 Dialogs 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ReplacesDialogId</strong></p></td>
<td><p>varchar(775)</p></td>
<td><p>세션에서 대체하는 SIP 대화 ID입니다. 형식은 다음과 같습니다.</p>
<p>dialog;from-tag;to-tag</p></td>
</tr>
<tr class="even">
<td><p><strong>ResponseTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>첫 번째 INVITE 메시지에 대한 응답 시간입니다. 이 필드는 일반적으로 세션의 초기 INVITE 메시지로 채워집니다. INVITE 메시지가 없으면 첫 번째 관련 SIP 메시지(BYE, CANCEL, MESSAGE 또는 INFO)의 날짜 및 시간으로 채워집니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ResponseCode</strong></p></td>
<td><p>int</p></td>
<td><p>세션 초대에 대한 SIP 응답 코드입니다. 이 필드는 일반적으로 세션의 초기 INVITE 메시지로 채워집니다. INVITE 메시지가 없으면 첫 번째 관련 SIP 메시지(BYE, CANCEL, MESSAGE 또는 INFO)의 날짜 및 시간으로 채워집니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>DiagnosticId</strong></p></td>
<td><p>int</p></td>
<td><p>SIP 헤더에서 캡처된 진단 ID입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ContentType</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>세션의 콘텐츠 형식입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>FrontEnd</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>세션 데이터를 캡처한 프런트 엔드 서버의 FQDN입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Pool</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>세션 데이터를 캡처한 풀 FQDN입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>FromEdgeServer</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>세션을 시작한 사용자가 사용하는 에지 서버의 FQDN입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ToEdgeServer</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>세션을 시작한 사용자가 사용하는 에지 서버의 FQDN입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>IsFromInternal</strong></p></td>
<td><p>bit</p></td>
<td><p>세션을 시작한 사용자가 내부 네트워크에서 로그온했는지 여부를 나타냅니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>IsToInternal</strong></p></td>
<td><p>bit</p></td>
<td><p>세션에 참가한 사용자가 내부 네트워크에서 로그온했는지 여부를 나타냅니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallPriority</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>세션의 통화 우선 순위입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>FromUserFlag</strong></p></td>
<td><p>smallint</p></td>
<td><p>세션을 시작한 사용자의 특성을 나타냅니다. 다음과 같은 특성 정의가 허용됩니다.</p>
<p>0x01 - 데스크톱 전화와 통합됨</p></td>
</tr>
<tr class="even">
<td><p><strong>ToUserFlag</strong></p></td>
<td><p>smallint</p></td>
<td><p>세션을 시작한 사용자의 특성을 나타냅니다. 다음과 같은 특성 정의가 허용됩니다.</p>
<p>0x01 - 데스크톱 전화와 통합됨</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallFlag</strong></p></td>
<td><p>smallint</p></td>
<td><p>통화 특성을 나타냅니다. 다음과 같은 특성 정의가 허용됩니다.</p>
<p>0x01 - 재시도된 세션</p>
<p>0x02 - 응답 그룹을 대신하여 에이전트가 건 전화</p></td>
</tr>
<tr class="even">
<td><p><strong>Location</strong></p></td>
<td><p>varchar(max)</p></td>
<td><p>긴급 전화의 위치입니다.</p></td>
</tr>
</tbody>
</table>

