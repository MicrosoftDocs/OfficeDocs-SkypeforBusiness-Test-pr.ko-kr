---
title: 'Lync Server 2013: tblComplianceParticipant'
TOCTitle: tblComplianceParticipant
ms:assetid: 5d7e0dea-74f7-46d1-badf-b94abc8f066d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg558655(v=OCS.15)
ms:contentKeyID: 49303772
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 tblComplianceParticipant

 

_**마지막으로 수정된 항목:** 2015-03-09_

tblComplianceParticipant에는 채널 및 서버별 현재 참가자가 포함됩니다.

### 열

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>열</th>
<th>유형</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>channelUri</p></td>
<td><p>nvarchar(255), null이 아님</p></td>
<td><p>채널 URI(Uniform Resource Identifier)입니다.</p></td>
</tr>
<tr class="even">
<td><p>userId</p></td>
<td><p>int, null이 아님</p></td>
<td><p>참가자의 계정 ID(tblPrincipal.prinID 테이블에 해당됨)입니다.</p></td>
</tr>
<tr class="odd">
<td><p>joinedAt</p></td>
<td><p>bigint, null이 아님</p></td>
<td><p>참가 이벤트의 타임스탬프입니다.</p></td>
</tr>
<tr class="even">
<td><p>partedAt</p></td>
<td><p>bigint</p></td>
<td><p>참가자가 아직 참가된 상태이면 Null입니다. Null이 아닌 경우 채널 나가기 이벤트의 타임스탬프입니다.</p>
<p>모든 변환기에서 이벤트를 처리하면 이러한 항목이 결국 제거됩니다.</p></td>
</tr>
<tr class="odd">
<td><p>userUri</p></td>
<td><p>nvarchar(255), null이 아님</p></td>
<td><p>사용자 URI입니다.</p></td>
</tr>
<tr class="even">
<td><p>serverID</p></td>
<td><p>int</p></td>
<td><p>서버 ID(tblServerIdentity.serverID 테이블에 해당됨)입니다.</p></td>
</tr>
<tr class="odd">
<td><p>sessionId</p></td>
<td><p>bigint</p></td>
<td><p>서버 세션입니다. 이 값은 채팅 서비스가 시작할 때마다 생성되는 임의의 숫자입니다. 고립된 참가자를 식별하기 위한 목적으로 세션을 구분하기 위해 사용됩니다.</p></td>
</tr>
</tbody>
</table>


### 키

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>열</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>&lt;channelUri, userId, joinedAt&gt;</p></td>
<td><p>기본 키입니다.</p></td>
</tr>
</tbody>
</table>

