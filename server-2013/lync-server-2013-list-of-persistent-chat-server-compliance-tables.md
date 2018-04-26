---
title: 'Lync Server 2013: 영구 채팅 서버 준수 테이블 목록'
TOCTitle: 영구 채팅 서버 준수 테이블 목록
ms:assetid: 8563446e-90cc-47cc-8a8e-4883decfe195
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ215878(v=OCS.15)
ms:contentKeyID: 49304267
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 영구 채팅 서버 준수 테이블 목록

 

_**마지막으로 수정된 항목:** 2015-03-09_

영구 채팅 준수 데이터베이스 스키마는 다음 테이블로 구성됩니다.

## 영구 채팅 서버 준수 테이블 목록


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>테이블</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-tblcompliancedata.md">Lync Server 2013의 tblComplianceData</a></p></td>
<td><p>구성된 어댑터에서 아직 처리되지 않은 준수 이벤트를 포함합니다.</p>
<p>이 테이블에는 채팅 메시지 및 파일 다운로드와 같은 영구 채팅 관련 이벤트가 포함됩니다. 참가자 이벤트는 tblComplianceParticipant 테이블에서 추적됩니다.</p>
<p>이 테이블의 이벤트를 처리한 서버는 tblComplianceFanout 테이블에 나열됩니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblcompliancefanout.md">Lync Server 2013의 tblComplianceFanout</a></p></td>
<td><p>준수 이벤트를 처리한 서버를 포함합니다. 이 테이블은 tblComplianceData 테이블과 밀접하게 결합되어 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tblcomplianceparticipant.md">Lync Server 2013의 tblComplianceParticipant</a></p></td>
<td><p>채팅 서비스 및 서버별 현재 참가자를 포함합니다. 이 테이블은 영구 채팅 서비스에서 수신된 참가 및 부분 준수 이벤트를 기반으로 유지 관리됩니다.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblcompliancestate.md">Lync Server 2013의 tblComplianceState</a></p></td>
<td><p>풀 전반의 준수 상태 정보를 포함합니다.</p></td>
</tr>
</tbody>
</table>

