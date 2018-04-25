---
title: ClientVersions 보기
TOCTitle: ClientVersions 보기
ms:assetid: caf7678f-83a0-46c8-83cc-fee4c3991f52
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721891(v=OCS.15)
ms:contentKeyID: 49885983
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# ClientVersions 보기

 

_**마지막으로 수정된 항목:** 2015-03-09_

ClientVersions 보기에는 데이터베이스에 기록되는 세션에 참여한 다양한 클라이언트 유형 및 버전 정보가 저장되어 있습니다. 보기의 각 레코드는 하나의 클라이언트 버전을 나타냅니다. 이 보기는 Microsoft Lync Server 2013에서 도입되었습니다.


> [!NOTE]
> 특정 열에 여러 레코드가 있을 수 있습니다.




<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>열</th>
<th>데이터 형식</th>
<th>세부 정보</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>VersionId</strong></p></td>
<td><p>int</p></td>
<td><p>이 클라이언트 유형 및 버전을 식별하는 고유 번호입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>Version</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p>사용자 에이전트를 나타냅니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ClientType</strong></p></td>
<td><p>int</p></td>
<td><p>클라이언트 유형입니다</p></td>
</tr>
<tr class="even">
<td><p><strong>ClientCategory</strong></p></td>
<td><p>nvarchar(64)</p></td>
<td><p>클라이언트가 속한 범주입니다. 예를 들어 Conferencing_Attendant_1.0 클라이언트는 ClientCategory CAA에 속합니다.</p></td>
</tr>
</tbody>
</table>

