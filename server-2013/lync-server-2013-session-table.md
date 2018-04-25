---
title: 'Lync Server 2013: Session 테이블'
TOCTitle: Session 테이블
ms:assetid: 7f05529c-794d-41ed-bca4-2e85b87b2dec
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398635(v=OCS.15)
ms:contentKeyID: 49304177
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 Session 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

각 레코드는 오디오 또는 오디오 및 비디오가 포함된 하나의 세션을 나타냅니다. 여기에는 세션에 대한 전체 정보가 포함됩니다. 세션은 두 끝점 사이의 오디오 또는 비디오 SIP(Session Initiation Protocol) 연결로 정의됩니다.


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
<td><p><strong>ConferenceDateTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>기본</p></td>
<td><p><a href="lync-server-2013-dialog-table.md">Lync Server 2013의 Dialog 테이블</a>을 참고하세요.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionSeq</strong></p></td>
<td><p>int</p></td>
<td><p>기본</p></td>
<td><p><a href="lync-server-2013-dialog-table.md">Lync Server 2013의 Dialog 테이블</a>을 참고하세요.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ConferenceKey</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>회의 키입니다. <a href="lync-server-2013-conference-table.md">Lync Server 2013의 Conference 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>CorrelationKey</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>상관 관계 키입니다. <a href="lync-server-2013-sessioncorrelation-table.md">Lync Server 2013의 SessionCorrelation 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DialogCategory</strong></p></td>
<td><p>bit</p></td>
<td><p> </p></td>
<td><p>대화 범주입니다. 0은 Lync Server - 중재 서버 레그이고 1은 중재 서버 - PSTN 게이트웨이 레그입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>MediationServerBypassFlag</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>통화가 바이패스되었는지 여부를 나타내는 플래그입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MediaBypassWarningFlag</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>이 필드는(제공된 경우) 바이패스 ID가 일치한 경우에도 통화가 바이패스되지 않은 이유를 나타냅니다. Lync Server의 경우 하나의 값만 정의되어 있습니다.</p>
<p>0x0001 - 기본 네트워크 어댑터에 대한 알 수 없는 바이패스 ID입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>StartTime</strong></p></td>
<td><p>datetime</p></td>
<td><p> </p></td>
<td><p>통화 시작 시간입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>EndTime</strong></p></td>
<td><p>datetime</p></td>
<td><p> </p></td>
<td><p>통화 종료 시간입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerPool</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>발신자의 풀입니다. <a href="lync-server-2013-pool-table.md">Lync Server 2013의 Pool 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleePool</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>통화 수신자의 풀입니다. <a href="lync-server-2013-pool-table.md">Lync Server 2013의 Pool 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleePAI</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>받는 끝점의 SIP PAI(p-asserted identity)에 있는 SIP URI입니다. <a href="lync-server-2013-user-table.md">Lync Server 2013의 User 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerURI</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>발신자의 URI입니다. <a href="lync-server-2013-user-table.md">Lync Server 2013의 User 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerEndpoint</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>발신자의 끝점입니다. <a href="lync-server-2013-endpoint-table.md">Lync Server 2013의 Endpoint 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CallerUserAgent</strong></p></td>
<td><p>bit</p></td>
<td><p>외래</p></td>
<td><p>발신자의 사용자 에이전트입니다. <a href="lync-server-2013-useragent-table.md">Lync Server 2013의 UserAgent 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallPriority</strong></p></td>
<td><p>smallint</p></td>
<td><p></p></td>
<td><p>이 통화의 우선 순위입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ClassifiedPoorCall</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>이 열은 더 이상 지원되지 않으며 Microsoft Lync Server 2013에서 사용되지 않습니다. 대신 이 정보는 미디어별 라인 기준으로 보고됩니다. 자세한 내용은 <a href="lync-server-2013-medialine-table.md">Lync Server 2013의 MediaLine 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallerPAI</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>호출을 수행한 사용자의 P-Asserted-Identity입니다. PAI(P-Asserted-Identity)는 호출을 수행한 사용자의 실제 ID를 전달하는 데 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleeEndpoint</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>호출을 받은 끝점입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>CalleeUserAgent</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>호출을 받은 사용자가 사용한 사용자 에이전트입니다. 사용자 에이전트는 클라이언트 끝점 장치를 나타냅니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CalleeUri</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>호출을 받은 사용자의 SIP URI입니다.</p></td>
</tr>
</tbody>
</table>

