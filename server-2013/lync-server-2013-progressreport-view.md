---
title: ProgressReport 보기
TOCTitle: ProgressReport 보기
ms:assetid: b49f3fc7-0e2f-498f-8505-aaaf54e435f9
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721857(v=OCS.15)
ms:contentKeyID: 49885938
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# ProgressReport 보기

 

_**마지막으로 수정된 항목:** 2015-03-09_

ProgressReport 보기에는 완료된 세션에 대한 정보가 저장됩니다. 진행률 보고서는 Lync Server 2013에서 진단 목적에 유용할 것으로 확인된 통화 및 세션에 대해서만 작성됩니다. 이 보기는 Microsoft Lync Server 2013에서 도입되었습니다.


> [!NOTE]
> ErrorTime, ErrorReportSeq 및 ProgressReportSeq 필드가 반드시 오류를 참조할 필요는 없지만 통화 상태 또는 메시지를 나타내는 메시지를 참조합니다.




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
<td><p><strong>ErrorTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>오류가 발생한 시간입니다. ErrorReportSeq와 함께 오류를 고유하게 식별하기 위해 사용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>ErrorReportSeq</strong></p></td>
<td><p>int</p></td>
<td><p>오류를 식별하기 위한 ID 번호입니다. ErrorTime과 함께 오류 보고서를 고유하게 식별하기 위해 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ProgressReportSeq</strong></p></td>
<td><p>int</p></td>
<td><p>진행률 보고서를 식별하기 위한 ID입니다. 동일한 오류 보고서에 대한 여러 진행률 보고서를 구별하기 위해 사용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>MsDiagId</strong></p></td>
<td><p>int</p></td>
<td><p>오류 보고서의 진단 ID입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Source</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>오류를 일으킨 서버의 이름입니다(보고서가 서버 구성 요소에서 전송된 경우).</p></td>
</tr>
<tr class="even">
<td><p><strong>Application</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>오류를 일으킨 응용 프로그램의 이름입니다(보고서가 서버 구성 요소에서 전송된 경우).</p></td>
</tr>
<tr class="odd">
<td><p><strong>TelemetryId</strong></p></td>
<td><p>uniqueidentifier</p></td>
<td><p>전화 회의에 사용된 서로 다른 구성 요소의 참가 시간 정보를 상호 연관시키는 고유한 식별자입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionSetupTime</strong></p></td>
<td><p>int</p></td>
<td><p>특정 구성 요소가 전화 회의에 참가하기까지 소요된 시간(밀리초)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MsDiagHeader</strong></p></td>
<td><p>varchar(max)</p></td>
<td><p>추가 오류 정보입니다.</p></td>
</tr>
</tbody>
</table>

