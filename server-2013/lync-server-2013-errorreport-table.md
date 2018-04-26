---
title: 'Lync Server 2013: ErrorReport 테이블'
TOCTitle: ErrorReport 테이블
ms:assetid: ae0287b4-e8ca-4f8c-84ef-502897dcaa2a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412826(v=OCS.15)
ms:contentKeyID: 49304718
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 ErrorReport 테이블

 

_**마지막으로 수정된 항목:** 2015-06-22_

ErrorReport 테이블에는 발생한 오류에 대한 정보가 저장됩니다. 각 레코드는 발생한 한 가지 오류입니다. 오류는 프런트 엔드 서버에서 실행하는 CDR 에이전트로 캡처되거나 클라이언트로 전송됩니다.


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
<td><p><strong>ErrorTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>기본</p></td>
<td><p>오류가 발생한 날짜 및 시간입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>ErrorReportSeq</strong></p></td>
<td><p>int</p></td>
<td><p>기본</p></td>
<td><p>오류 보고서를 식별하기 위한 ID 번호입니다. <strong>ErrorTime</strong> 와 함께 오류 보고서를 고유하게 식별하기 위해 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ErrorId</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>오류 유형의 고유한 ID입니다. 자세한 내용은 <a href="lync-server-2013-errordef-table.md">Lync Server 2013의 ErrorDef 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>FromUserId</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>오류를 일으킨 요청을 시작한 사용자입니다. 자세한 내용은 <a href="lync-server-2013-users-table.md">Lync Server 2013의 Users 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ToUserId</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>오류를 일으킨 요청의 대상 사용자입니다. 자세한 내용은 <a href="lync-server-2013-users-table.md">Lync Server 2013의 Users 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>ConferenceUriId</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>이 오류와 관련된 회의 URI입니다. 자세한 내용은 <a href="lync-server-2013-conferenceuris-table.md">Lync Server 2013의 ConferenceUris 테이블</a>을 참조하십시오. 일반적으로 ConferenceUriId가 Null이 아니면 FromUserId 또는 ToUserId가 Null이 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SessionIdTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>외래</p></td>
<td><p><strong>SessionIdSeq</strong> 와 함께 세션을 고유하게 식별하기 위해 사용됩니다. 자세한 내용은 <a href="lync-server-2013-dialogs-table.md">Lync Server 2013의 Dialogs 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>세션을 식별하기 위한 ID 번호입니다. <strong>SessionIdTime</strong> 과 함께 세션을 고유하게 식별하기 위해 사용됩니다. 자세한 내용은 <a href="lync-server-2013-dialogs-table.md">Lync Server 2013의 Dialogs 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SourceId</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>오류 보고서를 전송한 서버입니다(보고서가 서버 구성 요소에서 전송되는 경우). 자세한 내용은 <a href="lync-server-2013-servers-table.md">Lync Server 2013의 Servers 테이블</a>을 참조하십시오.</p>
<p>이 필드는 Microsoft Lync Server 2013에 새로 도입되었습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>ApplicationId</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>오류 보고서를 전송한 서버입니다(보고서가 서버 구성 요소에서 전송되는 경우). 자세한 내용은 <a href="lync-server-2013-application-table.md">Lync Server 2013의 Application 테이블</a>을 참조하십시오.</p>
<p>이 필드는 Microsoft Lync Server 2013에 새로 도입되었습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MsDiagHeader</strong></p></td>
<td><p>이미지</p></td>
<td><p> </p></td>
<td><p>오류에 대한 추가 정보입니다.</p>
<p>이 데이터는 다음 구문을 사용하여 텍스트 형식으로 변환할 수 있습니다.</p>
<p><code>cast(cast(Detail as varbinary(max)) as varchar(max)) </code></p></td>
</tr>
<tr class="even">
<td><p><strong>ClientVersionId</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>오류 보고서를 전송한 끝점의 클라이언트 버전입니다. 자세한 내용은 <a href="lync-server-2013-clientversions-table.md">Lync Server 2013의 ClientVersions 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>IsCapturedByServer</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>프런트 엔드 서버에서 실행하는 CDR 에이전트에 의해 캡처되었거나 클라이언트에 의해 전송된 오류 보고서입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>Flag</strong></p></td>
<td><p>smallint</p></td>
<td><p></p></td>
<td><p>나중에 사용하도록 예약됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>TelemetryId</strong></p></td>
<td><p>uniqueIdentifier</p></td>
<td><p></p></td>
<td><p>회의에 포함된 서로 다른 구성 요소의 참가 시간 정보와 연결된 고유 ID입니다.</p>
<p>이 필드는 Microsoft Lync Server 2013에 새로 도입되었습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionSetupTime</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>회의에 참가하는 특정 구성 요소에 필요한 시간(밀리초)입니다.</p>
<p>이 필드는 Microsoft Lync Server 2013에 새로 도입되었습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ServerId</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>오류 보고서를 생성한 서버의 FQDN(정규화된 도메인 이름)을 나타냅니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>PoolId</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>오류 보고서가 생성된 서버의 풀의 FQDN(정규화된 도메인 이름)을 나타냅니다.</p></td>
</tr>
</tbody>
</table>

