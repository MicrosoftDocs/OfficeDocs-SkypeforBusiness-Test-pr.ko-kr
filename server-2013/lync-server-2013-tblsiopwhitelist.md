---
title: 'Lync Server 2013: tblSiopWhiteList'
TOCTitle: tblSiopWhiteList
ms:assetid: 05fc1df4-32eb-4d46-9d1c-e0b607091142
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg558607(v=OCS.15)
ms:contentKeyID: 49302685
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 tblSiopWhiteList

 

_**마지막으로 수정된 항목:** 2015-03-09_

tblSiopWhiteList는 노드와 연결할 수 있는 등록된 추가 기능 목록입니다.

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
<td><p>siopID</p></td>
<td><p>GUID, null이 아님</p></td>
<td><p>추가 기능의 GUID입니다.</p></td>
</tr>
<tr class="even">
<td><p>siopName</p></td>
<td><p>nvarchar(50), null이 아님</p></td>
<td><p>추가 기능의 표시 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p>siopUrl</p></td>
<td><p>nvarchar(255), null이 아님</p></td>
<td><p>추가 기능의 URL입니다.</p></td>
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
<td><p>siopID</p></td>
<td><p>기본 키입니다.</p></td>
</tr>
</tbody>
</table>

