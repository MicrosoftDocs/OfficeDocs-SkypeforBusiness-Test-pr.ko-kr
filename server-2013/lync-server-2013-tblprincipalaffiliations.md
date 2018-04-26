---
title: 'Lync Server 2013: tblPrincipalAffiliations'
TOCTitle: tblPrincipalAffiliations
ms:assetid: 45fd8484-5837-44d2-85bb-45c83546607c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg558642(v=OCS.15)
ms:contentKeyID: 49303493
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 tblPrincipalAffiliations

 

_**마지막으로 수정된 항목:** 2015-03-09_

tblPrincipalAffiliations에는 Active Directory 도메인 서비스 보안 그룹을 포함한 위치, Active Directory 컨테이너, 도메인에서의 구성원 자격을 설명하는 계정 회원 정보가 포함됩니다.

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
<td><p>principalID</p></td>
<td><p>int, null이 아님</p></td>
<td><p>연관된 사용자의 ID입니다.</p></td>
</tr>
<tr class="even">
<td><p>affiliationID</p></td>
<td><p>int, null이 아님</p></td>
<td><p>회원 정보를 나타내는 사용자의 ID입니다. 각 사용자(system-user-types 제외)에는 self-affiliation도 포함됩니다.</p></td>
</tr>
<tr class="odd">
<td><p>index</p></td>
<td><p>int, null이 아님</p></td>
<td><p>인덱스입니다. self-affiliations의 값은 -1이고, 다른 회원 정보의 경우 각 &lt;principalID, affiliationId&gt; 버킷 내에서 1부터 순차적으로 증가합니다.</p></td>
</tr>
<tr class="even">
<td><p>updatedBy</p></td>
<td><p>int, null이 아님</p></td>
<td><p>최근 업데이트를 수행한 사용자입니다. 이 값은 일반적으로 Active Directory 동기화를 의미하는 1입니다.</p></td>
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
<td><p>&lt;principalID, index, affiliationID&gt;</p></td>
<td><p>기본 키입니다.</p></td>
</tr>
<tr class="even">
<td><p>principalID</p></td>
<td><p>tblPrincipal.prinID 테이블에서 조회 기능이 있는 외래 키입니다.</p></td>
</tr>
<tr class="odd">
<td><p>affiliationID</p></td>
<td><p>tblPrincipal.prinID 테이블에서 조회 기능이 있는 외래 키입니다.</p></td>
</tr>
</tbody>
</table>

