---
title: 'Lync Server 2013: ProgressReport 테이블'
TOCTitle: ProgressReport 테이블
ms:assetid: 38e5f060-5e9b-4185-87b2-7ef61c4bb75f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425864(v=OCS.15)
ms:contentKeyID: 49303333
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 ProgressReport 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

진행률 보고서는 통화 또는 세션이 완료된 후에 클라이언트가 데이터베이스에 업로드한 데이터를 기반으로 작성됩니다. 진행률 보고서는 Lync Server 2013에서 진단 목적에 유용할 것으로 확인된 통화 및 세션에 대해서만 작성됩니다.

ErrorTime, ErrorReportSeq 및 ProgressReportSeq 필드가 반드시 오류를 참조할 필요는 없지만 통화 상태 또는 메시지를 나타내는 메시지를 참조합니다.


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
<td><p>기본, 외래</p></td>
<td><p>이 진행률 보고서를 포함하는 진행 상태 오류 보고서의 날짜 및 시간입니다. 자세한 내용은 <a href="lync-server-2013-errorreport-table.md">Lync Server 2013의 ErrorReport 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>ErrorId</strong></p></td>
<td><p>int</p></td>
<td><p>기본, 외래</p></td>
<td><p>ErrorTime, ProgressReportSeq와 함께 진행률 보고서를 고유하게 식별하기 위해 사용된 ID 번호입니다. 자세한 내용은 <a href="lync-server-2013-errorreport-table.md">Lync Server 2013의 ErrorReport 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ErrorReportSeq</strong></p></td>
<td><p>int</p></td>
<td><p>기본, 외래</p></td>
<td><p>오류 보고서를 식별하는 ID 번호입니다. ErrorReporSeq는 ErrorTime과 함께 오류 보고서를 고유하게 식별하는 데 사용됩니다. 자세한 내용은 <a href="lync-server-2013-errorreport-table.md">Lync Server 2013의 ErrorReport 테이블</a>을 참조하십시오.</p>
<p>이 필드는 Microsoft Lync Server 2013에 새로 도입되었습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>ProgressReportSeq</strong></p></td>
<td><p>int</p></td>
<td><p>기본</p></td>
<td><p>진행률 보고서를 식별하기 위한 ID 번호입니다. ErrorTime 및 ErrorReportSeq와 함께 진행률 보고서를 고유하게 식별하기 위해 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MsDiagId</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>진행률 보고서의 진단 ID입니다.</p>
<p>이 필드는 Microsoft Lync Server 2013에 새로 도입되었습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>SourceId</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>오류 보고서를 보낸 서버(서버 구성 요소가 보고서를 보낸 경우)입니다. 자세한 내용은 <a href="lync-server-2013-servers-table.md">Lync Server 2013의 Servers 테이블</a>을 참조하십시오. 이 필드는 Microsoft Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ApplicationId</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>보고서의 대상 Lync Server 프로세스입니다. 자세한 내용은 Application 테이블을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>Detail</strong></p></td>
<td><p>이미지</p></td>
<td><p></p></td>
<td><p>공간 절약을 위해 이진 형식으로 저장된 진행률 보고서 세부 정보입니다. 다음 구문을 사용하여 이 데이터를 텍스트 형식으로 변환할 수 있습니다.</p>
<p>cast(cast(Detail as varbinary(max)) as varchar(max))</p></td>
</tr>
<tr class="odd">
<td><p><strong>TelemetryId</strong></p></td>
<td><p>uniqueIdentifier</p></td>
<td><p></p></td>
<td><p>전화 회의에 참가하는 각 구성 요소의 참가 시간 정보에 대해 상관 관계를 지정하는 고유 식별자입니다.</p>
<p>이 필드는 Microsoft Lync Server 2013에 새로 도입되었습니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionSetupTime</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>특정 구성 요소가 전화 회의에 참가하는 시간(밀리초)입니다.</p>
<p>이 필드는 Microsoft Lync Server 2013에 새로 도입되었습니다.</p></td>
</tr>
</tbody>
</table>

