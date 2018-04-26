---
title: Lync Server 2013의 PurgeSettings 테이블(QoE)
TOCTitle: Lync Server 2013의 PurgeSettings 테이블(QoE)
ms:assetid: 31b85d1c-3f32-4f67-94bf-9389cdd282c5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204788(v=OCS.15)
ms:contentKeyID: 49303226
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 PurgeSettings 테이블(QoE)

 

_**마지막으로 수정된 항목:** 2015-03-09_

PurgeSettings 테이블은 오래된 체감 품질 레코드가 QoE 데이터베이스에서 자동으로 삭제되는지 여부 및 삭제되는 시간을 지정하는 정보를 포함합니다. 삭제 관련 정보는 Microsoft Lync Server 2013 관리 셸 내에서 다음 명령을 실행하여 가져올 수도 있습니다.

    Get-CsQoEConfiguration

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
<th><strong>열</strong></th>
<th><strong>데이터 형식</strong></th>
<th><strong>키/인덱스</strong></th>
<th><strong>세부 정보</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>ID</strong></p></td>
<td><p>int</p></td>
<td><p>Primary</p></td>
<td><p>QoE 삭제 설정 컬렉션의 고유 식별자입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>EnablePurge</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>True(1)로 설정하면 Microsoft Lync Server 2013에서는 QoE 데이터베이스에서 오래된 레코드를 정기적으로 삭제합니다. 삭제는 매일 PurgeHour 설정으로 지정된 시간에 수행됩니다. False(0)로 설정하면 레코드가 데이터베이스에서 자동으로 삭제되지 않습니다. 기본값은 True입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>KeepQoEDataForDays</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>QoE 레코드가 데이터베이스에서 삭제되는 기간(일)을 지정합니다. 삭제가 사용하도록 설정된 경우 이 값보다 오래된 QoE 레코드가 데이터베이스에서 제거됩니다. 기본값은 60일입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>PurgeHour</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>데이터베이스 삭제가 수행되는 로컬 시간을 지정합니다. 시간은 24시간제를 사용하여 지정되며 0이 자정(오전 12시)을, 23이 오후 11시를 나타냅니다. 시간 단위만 지정할 수 있습니다. 즉, 오전 10시를 나타내는 10은 값으로 허용되지만 오전 10시 30분을 나타내는 10:30 또는 10.5는 값으로 허용되지 않습니다. 기본값은 1(오전 1시)입니다.</p></td>
</tr>
</tbody>
</table>

