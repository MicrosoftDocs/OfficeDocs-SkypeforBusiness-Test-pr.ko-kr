---
title: 'Lync Server 2013: tblLastChatId'
TOCTitle: tblLastChatId
ms:assetid: 17a4ffbe-cca9-4ec5-ae46-38a15274889a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg558616(v=OCS.15)
ms:contentKeyID: 49302934
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 tblLastChatId

 

_**마지막으로 수정된 항목:** 2015-03-09_

tblLastChatId에는 각 사용자에 대해 생성(및 tblChat 테이블에서 사용)된 마지막 채팅 ID가 포함됩니다.

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
<td><p>nodeID</p></td>
<td><p>int, null이 아님</p></td>
<td><p>노드 ID(대화방 유형 전용)입니다.</p></td>
</tr>
<tr class="even">
<td><p>lastChatID</p></td>
<td><p>bigint, null이 아님</p></td>
<td><p>마지막으로 사용된 채팅 ID입니다.</p></td>
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
<td><p>&lt;nodeID, lastChatID&gt;</p></td>
<td><p>기본 키(처리를 위해서는 nodeID만으로도 충분함)입니다.</p></td>
</tr>
<tr class="even">
<td><p>nodeID</p></td>
<td><p>tblNode.nodeID 테이블에서 조회 기능이 있는 외래 키입니다.</p></td>
</tr>
</tbody>
</table>


## 참고 항목

#### 개념

[Lync Server 2013의 tblChat](lync-server-2013-tblchat.md)

