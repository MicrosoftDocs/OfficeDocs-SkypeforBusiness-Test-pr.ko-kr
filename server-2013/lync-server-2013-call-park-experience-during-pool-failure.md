---
title: 'Lync Server 2013: 풀 오류 발생 시 통화 대기 환경'
TOCTitle: 풀 오류 발생 시 통화 대기 환경
ms:assetid: f6303e69-8771-492a-9e8b-c3d7ba231309
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205383(v=OCS.15)
ms:contentKeyID: 49305552
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 풀 오류 발생 시 Lync Server 2013의 통화 대기 환경

 

_**마지막으로 수정된 항목:** 2015-03-09_

계획되지 않은 사고로 인해 프런트 엔드 풀을 사용할 수 없게 되는 경우 대기되었지만 아직 재개되지 않은 통화가 끊어집니다. 백업 풀로 장애 조치(failover)하는 중에는 사용자가 백업 풀로 리디렉션되고 복구 모드에 있게 됩니다. 복구 모드에서는 사용자가 통화를 대기시킬 수는 없지만 대기 상태로 설정하고 전송할 수는 있습니다. 장애 조치(failover)가 완료되면 통화가 보통 때처럼 다시 대기되었다고 재개될 수 있습니다. 장애 복구(failback) 중에는 사용자가 복구 모드가 끝날 때까지 통화를 대기시킬 수 없습니다.

재해 복구 중에는 장애 조치(failover) 프로세스의 일부로서 백업 풀로 리디렉션된 사용자가 백업 풀에 배포되는 통화 대기 응용 프로그램을 사용합니다. 따라서 백업 풀로 리디렉션되는 사용자가 백업 풀의 통화 대기 응용 프로그램에 대해 구성된 통화 대기 설정을 사용합니다.

다음 표에는 재해 복구 단계에서 겪게 되는 통화 대기 경험이 요약되어 있습니다.

### 재해 복구 시 사용자 환경

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>통화 상태</th>
<th>중단이 발생하는 경우</th>
<th>장애 조치(failover) 시</th>
<th>장애 복구(failback) 시</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>통화가 아직 대기되지 않았음</p></td>
<td><p>통화가 연결되었지만 대기될 수 없습니다.</p></td>
<td><ul>
<li><p>장애 조치(failover) 중에는 사용자가 복구 모드에 있는 동안 통화를 대기할 수 없지만 대기 상태로 설정하고 전송할 수 있습니다.</p></li>
<li><p>장애 조치(failover)가 완료되면 통화를 대기하고 재개할 수 있습니다.</p></li>
</ul></td>
<td><ul>
<li><p>장애 복구(failback) 중에는 사용자가 복구 모드에 있는 동안 통화를 대기할 수 없지만, 대기 상태로 설정하고 전송할 수 있습니다.</p></li>
<li><p>장애 복구(failback)가 완료되면 통화를 대기하고 재개할 수 있습니다.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>통화가 대기되었지만 아직 재개되지 않았음</p></td>
<td><p>통화가 끊어졌습니다.</p></td>
<td><p>이 상태의 통화가 없습니다.</p></td>
<td><p>통화가 대기 상태로 유지됩니다.</p></td>
</tr>
<tr class="odd">
<td><p>대기된 통화가 이미 재개됨</p></td>
<td><p>통화가 연결된 상태로 유지됩니다.</p></td>
<td><p>통화가 연결된 상태로 유지됩니다.</p></td>
<td><p>통화가 연결된 상태로 유지됩니다.</p></td>
</tr>
</tbody>
</table>

