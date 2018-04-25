---
title: Lync Server 2013의 PurgeSettings 테이블
TOCTitle: Lync Server 2013의 PurgeSettings 테이블
ms:assetid: 9ff2c8fc-4ae8-4f22-96a8-1f4d5eecbf2d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205121(v=OCS.15)
ms:contentKeyID: 49304561
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 PurgeSettings 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

PurgeSettings 테이블에는 오래된 통화 정보 기록을 CDR 데이터베이스에서 자동으로 삭제할지 여부 및 시기를 지정하는 정보가 포함됩니다. 또한 삭제 관련 정보는 Microsoft Lync Server 2013 관리 셸 내에서 다음 명령을 실행하여도 얻을 수 있습니다.

    Get-CsCdrConfiguration

관리자는 PurgeSettings 테이블을 읽기 전용으로 간주해야 합니다. 즉, 통화 정보 삭제 설정은 [New-CsCdrConfiguration](new-cscdrconfiguration.md) 또는 [Set-CsCdrConfiguration](set-cscdrconfiguration.md) cmdlet을 사용해서만 변경해야 합니다.

이 테이블은 Microsoft Lync Server 2013에서 도입되었습니다.


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
<td><p><strong>Id</strong></p></td>
<td><p>int</p></td>
<td><p>Primary</p></td>
<td><p>CDR 삭제 설정 컬렉션에 대한 고유 식별자입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>EnablePurge</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>True(1)로 설정된 경우 Microsoft Lync Server 2013이 CDR 데이터베이스에서 오래된 기록을 자동으로 삭제합니다. 삭제는 매일 PurgeHour 설정에 지정된 시간에 수행됩니다. False(0)로 설정된 경우 기록이 데이터베이스에서 자동으로 삭제되지 않습니다. 기본값은 True입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>KeepCallDetailForDays</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>데이터베이스에서 삭제할 CDR 레코드의 기간(일)을 지정합니다. 삭제를 사용하도록 설정한 경우 이 값보다 오래된 CDR 레코드가 데이터베이스에서 삭제됩니다. 기본값은 60일입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>KeepErrorReportForDays</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>데이터베이스에서 삭제할 오류 보고서 레코드의 기간(일)을 지정합니다. 삭제를 사용하도록 설정한 경우 이 값보다 오래된 오류 보고서 레코드가 데이터베이스에서 삭제됩니다. 기본값은 60일입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>PurgeHour</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>데이터베이스 삭제가 수행되는 현지 시간을 지정합니다. 시간은 24시간제를 사용하여 지정합니다. 0은 자정(오전 12:00)을 나타내고 23은 오후 11:00를 나타냅니다. 시간만 지정할 수 있습니다. 즉, 값으로 10(오전 10:00)은 사용할 수는 있지만, 10:30 또는 10.5(오전 10:30)는 사용할 수 없습니다. 기본값은 2(오전 2:00)입니다.</p></td>
</tr>
</tbody>
</table>

