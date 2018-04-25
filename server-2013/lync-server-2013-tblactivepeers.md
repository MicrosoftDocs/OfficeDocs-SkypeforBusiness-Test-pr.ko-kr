---
title: 'Lync Server 2013: tblActivePeers'
TOCTitle: tblActivePeers
ms:assetid: b50c3f4a-bab6-4cb9-b40e-016cf1a9c607
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg615030(v=OCS.15)
ms:contentKeyID: 49304784
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 tblActivePeers

 

_**마지막으로 수정된 항목:** 2015-03-09_

tblActivePeers에는 채팅 서비스 간의 현재 피어-투-피어 연결이 포함됩니다.

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
<td><p>aplServerID</p></td>
<td><p>int, null이 아님</p></td>
<td><p>항목을 게시한 서버의 ID입니다.</p></td>
</tr>
<tr class="even">
<td><p>aplPeerID</p></td>
<td><p>int, null이 아님</p></td>
<td><p>게시 서버가 연결된 피어의 ID입니다.</p></td>
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
<td><p>&lt;aplServerID, aplPeerID&gt;</p></td>
<td><p>기본 키입니다.</p></td>
</tr>
<tr class="even">
<td><p>aplServerID</p></td>
<td><p>tblServerIdentity.serverID 테이블에서 조회 기능이 있는 외래 키입니다.</p></td>
</tr>
<tr class="odd">
<td><p>aplPeerID</p></td>
<td><p>tblServerIdentity.serverID 테이블에서 조회 기능이 있는 외래 키입니다.</p></td>
</tr>
</tbody>
</table>

