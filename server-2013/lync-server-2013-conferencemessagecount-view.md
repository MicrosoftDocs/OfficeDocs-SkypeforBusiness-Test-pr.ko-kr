---
title: ConferenceMessageCount 보기
TOCTitle: ConferenceMessageCount 보기
ms:assetid: 8ee3ee95-fb78-4d4e-bcdd-6ce5a0a23b44
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688129(v=OCS.15)
ms:contentKeyID: 49885868
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# ConferenceMessageCount 보기

 

_**마지막으로 수정된 항목:** 2015-03-09_

ConferenceMessageCount 보기에는 사용자가 회의에 전송한 메시지 수에 대한 정보가 저장됩니다. 이 보기는 Microsoft Lync Server 2013에서 도입되었습니다.


> [!NOTE]
> ConferenceMessageCount 보기에는 아래 나열된 열 외에도 <A href="lync-server-2013-conferencesessiondetails-view.md">ConferenceSessionDetails 보기</A>의 모든 열이 포함됩니다.




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
<td><p><strong>UserUri</strong></p></td>
<td><p>nvarchar(450)</p></td>
<td><p>메시지를 보낸 사용자의 URI입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserUriType</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>메시지를 보낸 사용자 URI의 형식입니다. 자세한 내용은 <a href="lync-server-2013-uritypes-table.md">Lync Server 2013의 UriTypes 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserTenant</strong></p></td>
<td><p>uniqueidentifier</p></td>
<td><p>메시지를 보낸 사용자의 테넌트입니다. 자세한 내용은 <a href="lync-server-2013-tenants-table.md">Lync Server 2013의 Tenants 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserMessageCount</strong></p></td>
<td><p>smallint</p></td>
<td><p>회의 세션 중 사용자가 보낸 메시지 수입니다.</p></td>
</tr>
</tbody>
</table>

