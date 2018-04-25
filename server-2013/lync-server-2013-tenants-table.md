---
title: 'Lync Server 2013: Tenants 테이블'
TOCTitle: Tenants 테이블
ms:assetid: c1b070c1-2c59-4ca9-910b-43f673f97fda
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412950(v=OCS.15)
ms:contentKeyID: 49304924
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 Tenants 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

Tenants 테이블은 다양한 테넌트 목록이 저장된 지원 테이블입니다. 테이블의 각 레코드는 하나의 테넌트를 나타냅니다.


> [!NOTE]
> 온-프레미스 배포의 경우 CDR은 기본 제공되는 테넌트 ID를 사용하여 공용 IM 연결, 페더레이션 및 익명과 같은 서로 다른 인증 유형을 나타냅니다.




<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>열</th>
<th>데이터 형식</th>
<th>키/인덱스</th>
<th>세부 정보</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>TenantId</strong></p></td>
<td><p>int</p></td>
<td><p>기본</p></td>
<td><p>이 테넌트 ID를 식별하는 고유 번호입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>TenantKey</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p></p></td>
<td><p>허용되는 값:</p>
<ul>
<li><p>00000000-0000-0000-0000-000000000000 - 엔터프라이즈</p></li>
<li><p>00000000-0000-0000-0000-000000000001 - 페더레이션</p></li>
<li><p>00000000-0000-0000-0000-000000000002 - 익명</p></li>
<li><p>00000000-0000-0000-0000-000000000003 - 익명 IM 연결</p></li>
</ul></td>
</tr>
</tbody>
</table>

