---
title: 'Lync Server 2013: ClientVersions 테이블'
TOCTitle: ClientVersions 테이블
ms:assetid: 542316cf-a6db-4d52-ab28-8bf6d27a3b48
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398356(v=OCS.15)
ms:contentKeyID: 49303663
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 ClientVersions 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

ClientVersions 테이블은 데이터베이스에 기록되는 세션에 참여한 다양한 클라이언트 유형 및 버전 목록이 저장된 지원 테이블입니다. 테이블의 각 레코드는 하나의 클라이언트 버전을 나타냅니다.


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
<td><p><strong>VersionId</strong></p></td>
<td><p><strong>int</strong></p></td>
<td><p>기본</p></td>
<td><p>이 클라이언트 유형 및 버전을 식별하는 고유 번호입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>Version</strong></p></td>
<td><p><strong>nvarchar(256)</strong></p></td>
<td><p></p></td>
<td><p>버전 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ClientType</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>세션에 사용된 클라이언트 유형을 지정합니다. 자세한 내용은 <a href="lync-server-2013-useragentdef-table.md">Lync Server 2013의 UserAgentDef 테이블</a>을 참조하십시오.</p>
<p>이 필드는 Microsoft Lync Server 2013에 새로 도입되었습니다.</p></td>
</tr>
</tbody>
</table>

