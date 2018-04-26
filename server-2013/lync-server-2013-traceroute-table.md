---
title: Lync Server 2013의 TraceRoute 테이블
TOCTitle: Lync Server 2013의 TraceRoute 테이블
ms:assetid: b9493cef-6ece-4f13-bf68-dbf132aab4f4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205205(v=OCS.15)
ms:contentKeyID: 49304835
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 TraceRoute 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

TraceRoute 테이블에는 통화의 라우팅 정보가 포함됩니다. 이 테이블은 Microsoft Lync Server 2013에서 도입되었습니다.


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
<td><p><strong>ConferenceDateTime</strong></p></td>
<td><p>datetime</p></td>
<td><p>기본, 외래</p></td>
<td><p>통화가 시작된 날짜 및 시간입니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionSeq</strong></p></td>
<td><p>int</p></td>
<td><p>기본, 외래</p></td>
<td><p>같은 날짜와 시간에 시작되었을 수 있는 여러 통화를 서로 구별하기 위해 사용되는 고유한 식별자입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MediaLineLabel</strong></p></td>
<td><p>tinyint</p></td>
<td><p>기본, 외래</p></td>
<td><p>통화에 사용된 비디오 회선 유형을 나타냅니다. 허용되는 값은 다음과 같습니다.</p>
<ul>
<li><p>0 - 오디오</p></li>
<li><p>1 - 비디오</p></li>
<li><p>2 -- 파노라마 비디오</p></li>
<li><p>3 - 응용 프로그램/데스크톱 공유</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>FromCaller</strong></p></td>
<td><p>bit</p></td>
<td><p>기본</p></td>
<td><p>전화를 건 끝점입니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Hop</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>네트워크 홉/</p></td>
</tr>
<tr class="even">
<td><p><strong>IPAddressKey</strong></p></td>
<td><p>int</p></td>
<td><p>외래</p></td>
<td><p>IP 주소의 고유한 식별자입니다. IP 주소 정보는 <a href="lync-server-2013-ipaddress-table.md">Lync Server 2013의 IPAddress 테이블</a>에 저장됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><strong>RTT</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>왕복 시간입니다. 왕복 시간은 음성 패킷이 대상에 도착하고 수신되었다는 알림을 돌려 보내기까지 소요되는 시간을 측정합니다.</p></td>
</tr>
</tbody>
</table>

