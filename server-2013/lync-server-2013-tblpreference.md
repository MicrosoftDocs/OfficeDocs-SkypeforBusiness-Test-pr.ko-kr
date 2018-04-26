---
title: 'Lync Server 2013: tblPreference'
TOCTitle: tblPreference
ms:assetid: f94eb128-f782-42ff-a568-ed3529573bc8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg615052(v=OCS.15)
ms:contentKeyID: 49305586
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 tblPreference

 

_**마지막으로 수정된 항목:** 2015-03-09_

tblPreference에는 사용자의 클라이언트 기본 설정이 들어 있습니다. 이 설정은 일반적으로 Lync 2013 이전 클라이언트에 사용됩니다.

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
<td><p>prefLabel</p></td>
<td><p>nvarchar(255), null이 아님</p></td>
<td><p>&lt;사용자 SIP URI&gt;|사용자 이름.&lt;기본 설정 집합&gt; 형식의 레이블입니다.</p></td>
</tr>
<tr class="even">
<td><p>prefSeqID</p></td>
<td><p>int, null이 아님</p></td>
<td><p>버전 관리 목적의 일련 번호(레이블당)입니다.</p></td>
</tr>
<tr class="odd">
<td><p>prefContent</p></td>
<td><p>nvarchar(max)</p></td>
<td><p>인코딩된 콘텐츠입니다.</p></td>
</tr>
<tr class="even">
<td><p>lastModifiedBy</p></td>
<td><p>int, null이 아님</p></td>
<td><p>기본 설정을 업데이트한 사용자의 ID입니다.</p></td>
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
<td><p>&lt;prefLabel, prefSeqID&gt;</p></td>
<td><p>기본 키입니다.</p></td>
</tr>
</tbody>
</table>

