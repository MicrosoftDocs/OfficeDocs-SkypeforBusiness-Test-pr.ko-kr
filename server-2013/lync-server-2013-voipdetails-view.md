---
title: VoIPDetails 보기
TOCTitle: VoIPDetails 보기
ms:assetid: 14c44736-71ba-4fc5-82c7-1df65bf6261c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ687973(v=OCS.15)
ms:contentKeyID: 49885656
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# VoIPDetails 보기

 

_**마지막으로 수정된 항목:** 2015-03-09_

VoIPDetails 보기에는 한 명 이상의 사용자가 VoIP 사용자인 피어 투 피어 세션에 대한 정보가 저장됩니다. 이 보기는 Microsoft Lync Server 2013에서 도입되었습니다.


> [!NOTE]
> VoIPDetails 보기는 아래에 나와 있는 열과 함께 <A href="lync-server-2013-sessiondetails-view.md">SessionDetails 보기</A>의 모든 열을 포함합니다.




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
<td><p><strong>FromPhone</strong></p></td>
<td><p>nvarchar(450)</p></td>
<td><p>세션을 시작한 사용자의 전화 URI입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>ToPhone</strong></p></td>
<td><p>nvarchar(450)</p></td>
<td><p>세션에 참가한 사용자의 전화 URI입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DisconnectedByUri</strong></p></td>
<td><p>nvarchar(450)</p></td>
<td><p>세션 연결을 끊은 사용자의 URI입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>DisconnectedByUriType</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>세션 연결을 끊은 사용자의 URI 유형입니다. 자세한 내용은 <a href="lync-server-2013-uritypes-table.md">Lync Server 2013의 UriTypes 테이블</a>을 참조하십시오.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DisconnectedByTenant</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>세션 연결을 끊은 사용자의 테넌트입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>DisconnectedByPhone</strong></p></td>
<td><p>nvarchar(450)</p></td>
<td><p>세션 연결을 끊은 사용자의 전화 URI입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>FromMediationServer</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>세션을 시작한 사용자가 사용하는 중재 서버입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>ToMediationServer</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>세션에 참가한 사용자가 사용하는 중재 서버입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>FromGateway</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>세션을 시작한 사용자가 사용하는 게이트웨이입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>ToGateway</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>세션에 참가한 사용자가 사용하는 게이트웨이입니다.</p></td>
</tr>
</tbody>
</table>

