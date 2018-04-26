---
title: 'Lync Server 2013: Dialogs 테이블'
TOCTitle: Dialogs 테이블
ms:assetid: 487a430b-af66-4ea6-b28e-4e33cfdb7f9e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425954(v=OCS.15)
ms:contentKeyID: 49303514
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 Dialogs 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

Dialogs 테이블은 피어 투 피어 세션의 DialogIDs에 대한 정보를 저장하는 지원 테이블입니다.


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
<td><p>기본</p></td>
<td><p>세션 요청 시간입니다. SessionIDSeq와 함께 세션을 고유하게 식별하기 위해 사용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionIdSeq</strong></p></td>
<td><p>int</p></td>
<td><p>기본</p></td>
<td><p>세션을 식별하기 위한 ID 번호입니다. SessionIdTime과 함께 세션을 고유하게 식별하기 위해 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ExternalChecksum</strong></p></td>
<td><p>int</p></td>
<td><p> </p></td>
<td><p>ExternalID의 체크섬입니다. 이 필드는 데이터베이스 검색 속도를 높이는 데 사용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>ExternalId</strong></p></td>
<td><p>varbinary(775)</p></td>
<td><p> </p></td>
<td><p>바이너리로 저장된 SIP 대화 ID입니다. 바이너리 형식은 다음과 같습니다.</p>
<p>dialog;from-tag;to-tag</p>
<p>이 데이터는 다음 구문을 사용하여 텍스트 형식으로 변환할 수 있습니다.</p>
<p><code>cast(cast(ExternalId as varbinary(max)) as varchar(max))</code></p></td>
</tr>
</tbody>
</table>

