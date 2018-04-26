---
title: 'Lync Server 2013: tblADUpdates'
TOCTitle: tblADUpdates
ms:assetid: ba19fa16-4d2d-4635-ac32-f93e09469546
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg615033(v=OCS.15)
ms:contentKeyID: 49304845
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 tblADUpdates

 

_**마지막으로 수정된 항목:** 2015-03-09_

tblADUpdates에는 이후 Active Directory 동기화 단계에서 아직 처리되지 않은 Active Directory 도메인 서비스 변경 사항이 포함됩니다.

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
<td><p>prinGuid</p></td>
<td><p>GUID, null이 아님</p></td>
<td><p>변경된 개체의 사용자 GUID입니다.</p></td>
</tr>
<tr class="even">
<td><p>prinADPath</p></td>
<td><p>nvarchar(384), null이 아님</p></td>
<td><p>개체의 고유 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p>prinAttributesChanged</p></td>
<td><p>bit, null이 아님</p></td>
<td><p>개체의 특성이 하나 이상 변경된 경우 True입니다.</p></td>
</tr>
<tr class="even">
<td><p>prinMembersChanged</p></td>
<td><p>bit, null이 아님</p></td>
<td><p>구성원 자격이 변경된 경우 True입니다.</p></td>
</tr>
<tr class="odd">
<td><p>prinAffiliationsChanged</p></td>
<td><p>bit, null이 아님</p></td>
<td><p>사용되지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p>prinDeleted</p></td>
<td><p>bit, null이 아님</p></td>
<td><p>개체가 삭제된 경우 True입니다.</p></td>
</tr>
<tr class="odd">
<td><p>lastUpdated</p></td>
<td><p>datetime, null이 아님</p></td>
<td><p>행이 삽입되었을 때의 타임스탬프입니다.</p></td>
</tr>
</tbody>
</table>

