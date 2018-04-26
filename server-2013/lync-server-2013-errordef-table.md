---
title: 'Lync Server 2013: ErrorDef 테이블'
TOCTitle: ErrorDef 테이블
ms:assetid: 6acf3b86-da61-4923-9812-300db6f66dec
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398503(v=OCS.15)
ms:contentKeyID: 49303931
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 ErrorDef 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

ErrorDef 테이블에는 발생 가능한 각 오류 유형에 대한 정보가 저장됩니다. 각 레코드는 한 가지 오류 유형을 나타냅니다.


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
<td><p><strong>ErrorId</strong></p></td>
<td><p>int</p></td>
<td><p>기본</p></td>
<td><p>이 오류 유형을 식별하는 고유 ID 번호입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>ResponseCode</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>이 오류와 연결된 표준 SIP 응답 코드입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MsDiagId</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>Microsoft 진단 ID입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>CallTypeId</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>통화 유형입니다. 자세한 내용은 <a href="lync-server-2013-calltype-table.md">Lync Server 2013의 CallType 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RequestType</strong></p></td>
<td><p>varbinary(33)</p></td>
<td><p> </p></td>
<td><p>실패한 요청 유형입니다.</p>
<p>이 데이터는 다음 구문을 사용하여 텍스트 형식으로 변환할 수 있습니다.</p>
<p><code>cast(cast(RequestType as varbinary(max)) as varchar(max))</code></p></td>
</tr>
<tr class="even">
<td><p><strong>ContentType</strong></p></td>
<td><p>varbinary(257)</p></td>
<td><p> </p></td>
<td><p>실패한 요청의 콘텐츠 유형입니다.</p>
<p>이 데이터는 다음 구문을 사용하여 텍스트 형식으로 변환할 수 있습니다.</p>
<p><code>cast(cast(ContentType as varbinary(max)) as varchar(max))</code></p></td>
</tr>
</tbody>
</table>

