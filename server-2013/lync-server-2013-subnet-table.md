---
title: 'Lync Server 2013: Subnet 테이블'
TOCTitle: Subnet 테이블
ms:assetid: 76f5c995-96c8-4aa3-bc30-1d74991d7c42
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398582(v=OCS.15)
ms:contentKeyID: 49304081
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 Subnet 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

Subnet 테이블은 지원 테이블입니다. 각 레코드는 네트워크 구성 설정에 정의된 하나의 서브넷을 나타냅니다.


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
<td><p><strong>SubnetIP</strong></p></td>
<td><p>int</p></td>
<td><p>기본, 외래</p></td>
<td><p>정수로 표시된 서브넷 IP입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>SubnetMask</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>서브넷 마스크입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>UserSiteKey</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p><a href="lync-server-2013-usersite-table.md">Lync Server 2013의 UserSite 테이블</a>을 참고하세요.</p></td>
</tr>
<tr class="even">
<td><p><strong>SubnetDescription</strong></p></td>
<td><p>nvarchar(512)</p></td>
<td><p></p></td>
<td><p>서브넷에 대한 설명입니다.</p></td>
</tr>
</tbody>
</table>

