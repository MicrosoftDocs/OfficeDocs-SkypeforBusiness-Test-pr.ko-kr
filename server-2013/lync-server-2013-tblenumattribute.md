---
title: 'Lync Server 2013: tblEnumAttribute'
TOCTitle: tblEnumAttribute
ms:assetid: 17f8b87e-36a6-4f6a-8630-7c76b61a7595
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg558617(v=OCS.15)
ms:contentKeyID: 49302939
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 tblEnumAttribute

 

_**마지막으로 수정된 항목:** 2015-03-09_

tblEnumAttribute는 Node 테이블에 사용된 Visibility 및 Behavior 특성이 들어 있는 하드코드된 테이블입니다.

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
<td><p>attributeID</p></td>
<td><p>smallint, null이 아님</p></td>
<td><p>특성의 ID입니다.</p></td>
</tr>
<tr class="even">
<td><p>attributeName</p></td>
<td><p>nvarchar(256), null이 아님</p></td>
<td><p>특성의 이름입니다.</p></td>
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
<td><p>attributeID</p></td>
<td><p>기본 키입니다.</p></td>
</tr>
</tbody>
</table>


### 테이블 값

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>attributeID</th>
<th>attributeName</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1</p></td>
<td><p>Visibility</p></td>
</tr>
<tr class="even">
<td><p>2</p></td>
<td><p>Behavior</p></td>
</tr>
</tbody>
</table>


## 참고 항목

#### 개념

[Lync Server 2013의 tblNode](lync-server-2013-tblnode.md)

