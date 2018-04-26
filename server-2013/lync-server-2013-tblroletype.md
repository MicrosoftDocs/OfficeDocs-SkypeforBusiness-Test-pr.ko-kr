---
title: 'Lync Server 2013: tblRoleType'
TOCTitle: tblRoleType
ms:assetid: 1eac3a54-656a-40ac-b771-edfc64d6e34b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg558623(v=OCS.15)
ms:contentKeyID: 49303007
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 tblRoleType

 

_**마지막으로 수정된 항목:** 2015-03-09_

tblRoleType은 역할 유형 및 연관된 권한 집합이 있는 정적 조회 테이블입니다.

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
<td><p>rtypeID</p></td>
<td><p>int, null이 아님</p></td>
<td><p>역할 유형 ID입니다.</p></td>
</tr>
<tr class="even">
<td><p>rtypeDesc</p></td>
<td><p>nvarchar(256), null이 아님</p></td>
<td><p>역할 유형 설명입니다. 다음 네 가지 역할을 사용할 수 있습니다.</p>
<ul>
<li><p>구성원: 대화방 구성원</p></li>
<li><p>관리자: 대화방 관리자</p></li>
<li><p>음성: 강당 대화방의 발표자</p></li>
<li><p>작성자: 채팅방을 만들 수 있음</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>rtypeAllowedPermSet</p></td>
<td><p>bigint, null이 아님</p></td>
<td><p>역할에 대해 설정된 권한입니다. 사용되는 비트는 다음과 같습니다.</p>
<ul>
<li><p>2: 역할이 노드를 관리할 수 있는 경우 True입니다.</p></li>
<li><p>4: 역할이 자식 노드를 만들 수 있는 경우 True입니다.</p></li>
<li><p>7: 역할이 대화방(또는 특정 범주의 자식 대화방)에 참가할 수 있는 경우 True입니다.</p></li>
<li><p>8: 역할이 대화방(또는 특정 범주의 자식 대화방)에서 채팅할 수 있는 경우 True입니다.</p></li>
<li><p>10: 역할이 대화방에 참가하지 않은 경우에도 채팅 기록을 읽을 수 있는 경우 True입니다.</p></li>
<li><p>11: 역할이 대화방을 볼 수 있는 경우 True입니다. 이 설정은 범위 및 표시 여부와 같은 요소로 세분화됩니다.</p></li>
<li><p>12: 역할이 강당 대화방에서 채팅할 수 있는 경우 True입니다.</p></li>
<li><p>13: 역할이 노드를 볼 때 표시 여부 규칙을 바이패스할 수 있는 경우 True입니다.</p></li>
</ul></td>
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
<td><p>rtypeID</p></td>
<td><p>기본 키입니다.</p></td>
</tr>
</tbody>
</table>

