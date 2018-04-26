---
title: 'Lync Server 2013: VideoClientEvent 테이블'
TOCTitle: VideoClientEvent 테이블
ms:assetid: e8ab963b-fe1d-45b3-b9bd-66a5f44c1629
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399039(v=OCS.15)
ms:contentKeyID: 49305385
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 VideoClientEvent 테이블

 

_**마지막으로 수정된 항목:** 2015-03-09_

각 레코드에는 비디오 통화의 한 끝점에 대한 클라이언트 이벤트가 포함됩니다. 일반적으로 하나의 통화에는 발신자용 레코드와 수신자용 레코드의 두 레코드가 포함됩니다.


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
<td><p>기본</p></td>
<td><p><a href="lync-server-2013-medialine-table.md">Lync Server 2013의 MediaLine 테이블</a>을 참고하세요.</p></td>
</tr>
<tr class="even">
<td><p><strong>SessionSeq</strong></p></td>
<td><p>int</p></td>
<td><p>기본</p></td>
<td><p><a href="lync-server-2013-medialine-table.md">Lync Server 2013의 MediaLine 테이블</a>을 참고하세요.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MediaLineLabel</strong></p></td>
<td><p>tinyint</p></td>
<td><p>기본</p></td>
<td><p><a href="lync-server-2013-medialine-table.md">Lync Server 2013의 MediaLine 테이블</a>을 참고하세요.</p></td>
</tr>
<tr class="even">
<td><p><strong>FromCaller</strong></p></td>
<td><p>bit</p></td>
<td><p>기본</p></td>
<td><p>0: 수신자 데이터</p>
<p>1: 발신자 데이터</p></td>
</tr>
<tr class="odd">
<td><p><strong>NetworkBandwidthLowEventRatio</strong></p></td>
<td><p></p></td>
<td><p> </p></td>
<td><p>'나쁨' 상태로 LowBandwidth 이벤트가 발생한 세션의 비율입니다. 허용 가능한 수준의 음성 환경을 위해 사용할 수 있는 대역폭이 부족합니다.</p></td>
</tr>
<tr class="even">
<td><p><strong>NetworkReceiveQualityEventRatio</strong></p></td>
<td><p></p></td>
<td><p> </p></td>
<td><p>'나쁨' 상태로 ReceiveSendQuality 이벤트가 발생한 세션의 비율입니다.</p>
<p>지터 또는 패킷 손실 측면의 네트워크 품질이 심각하고 수신 중인 오디오 품질에 영향을 줍니다.</p></td>
</tr>
</tbody>
</table>

