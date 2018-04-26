---
title: 'Lync Server 2013: tblConfig'
TOCTitle: tblConfig
ms:assetid: 7445e7db-c574-46fa-b964-8640d77047a8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg558663(v=OCS.15)
ms:contentKeyID: 49304037
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 tblConfig

 

_**마지막으로 수정된 항목:** 2015-03-09_

tblConfig에는 일부 지원되지 않는 영구 채팅 서버 구성이 한 행에 포함됩니다.

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
<td><p>configLabel</p></td>
<td><p>nvarchar(255), null이 아님</p></td>
<td><p>&quot;풀&quot;을 포함합니다.</p></td>
</tr>
<tr class="even">
<td><p>configContent</p></td>
<td><p>nvarchar(max)</p></td>
<td><p>구성 콘텐츠입니다.</p></td>
</tr>
<tr class="odd">
<td><p>configPoolID</p></td>
<td><p>GUID, null이 아님</p></td>
<td><p>데이터베이스 인스턴스의 고유한 ID입니다.</p></td>
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
<td><p>configLabel</p></td>
<td><p>기본 키입니다.</p></td>
</tr>
</tbody>
</table>

