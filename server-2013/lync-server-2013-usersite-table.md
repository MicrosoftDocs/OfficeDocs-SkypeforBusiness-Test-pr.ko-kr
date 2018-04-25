---
title: 'Lync Server 2013: UserSite 테이블'
TOCTitle: UserSite 테이블
ms:assetid: 1c2a3cf2-dc05-472e-8097-a31f3a1aafcb
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398256(v=OCS.15)
ms:contentKeyID: 49302979
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 UserSite 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

UserSite 테이블은 지원 테이블입니다. 각 레코드는 네트워크 구성 설정에 정의된 하나의 사용자 사이트를 나타냅니다.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>열</strong></th>
<th><strong>데이터 형식</strong></th>
<th><strong>키/인덱스</strong></th>
<th><strong>세부 정보</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>UserSiteKey</strong></p></td>
<td><p>int</p></td>
<td><p>기본</p></td>
<td><p>사용자 사이트를 식별하는 고유 번호입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>UserSiteName</strong></p></td>
<td><p>nvarchar(128)</p></td>
<td><p>Unique</p></td>
<td><p>사용자 사이트의 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RegionKey</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p><a href="lync-server-2013-region-table.md">Lync Server 2013의 Region 테이블</a>에서 참조됩니다.</p></td>
</tr>
</tbody>
</table>

