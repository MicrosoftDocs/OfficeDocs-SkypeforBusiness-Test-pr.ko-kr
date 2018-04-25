---
title: 'Lync Server 2013: tblAdminLock'
TOCTitle: tblAdminLock
ms:assetid: 785a43c0-6892-474c-821c-fa9cdbeb99d8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg558665(v=OCS.15)
ms:contentKeyID: 49304100
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 tblAdminLock

 

_**마지막으로 수정된 항목:** 2015-03-09_

tblAdminLock은 일부 관리자 명령을 실행하는 데 필요한 관리자 잠금을 포함합니다.

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
<td><p>lockExpiresTime</p></td>
<td><p>datetime, null이 아님</p></td>
<td><p>잠금 만료 날짜 및 시간입니다. 소유자는 이 값을 주기적으로 연장할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p>lockServerID</p></td>
<td><p>int, null이 아님</p></td>
<td><p>잠금을 소유하는 서버의 ID입니다.</p></td>
</tr>
<tr class="odd">
<td><p>lockActorID</p></td>
<td><p>int, null이 아님</p></td>
<td><p>잠금을 소유하는 사용자의 ID입니다.</p></td>
</tr>
</tbody>
</table>

