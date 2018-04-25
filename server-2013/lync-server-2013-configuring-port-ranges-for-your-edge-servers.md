---
title: 에지 서버에 대한 포트 범위 구성
TOCTitle: 에지 서버에 대한 포트 범위 구성
ms:assetid: 6f0ae442-6624-4e3f-849a-5b9e387fb8cf
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204996(v=OCS.15)
ms:contentKeyID: 49303980
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 에지 서버에 대한 포트 범위 구성

 

_**마지막으로 수정된 항목:** 2015-07-24_

에지 서버를 사용하면 오디오, 비디오 및 응용 프로그램 공유를 위해 별도의 포트 범위를 구성할 필요가 없습니다. 마찬가지로 에지 서버에 사용되는 포트 범위는 회의, 응용 프로그램 및 중재 서버에 사용된 포트 범위와 일치할 필요가 없습니다. 하지만 관리를 보다 쉽게 수행하기 위해서는 다른 서버의 포트 범위와 일치하도록 에지 서버 포트 범위를 미리 변경해야 할 수 있습니다. 예를 들어 회의, 응용 프로그램 및 중재 서버가 다음과 같은 포트 범위를 사용하도록 구성했다고 가정해보십시오.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>패킷 유형</th>
<th>시작 포트</th>
<th>예약된 포트 수</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>응용 프로그램 공유</p></td>
<td><p>40803</p></td>
<td><p>8348</p></td>
</tr>
<tr class="even">
<td><p>오디오</p></td>
<td><p>49152</p></td>
<td><p>8348</p></td>
</tr>
<tr class="odd">
<td><p>비디오</p></td>
<td><p>57500</p></td>
<td><p>8034</p></td>
</tr>
<tr class="even">
<td><p><strong>합계</strong></p></td>
<td><p>--</p></td>
<td><p>24730</p></td>
</tr>
</tbody>
</table>


표시된 것처럼 오디오, 비디오 및 응용 프로그램에 대한 포트 범위는 포트 40803에서 시작되며, 총 24732개의 포트를 포함합니다. 필요에 따라 Lync Server 관리 셸 내에서 다음과 비슷한 명령을 실행하여 특정 에지 서버가 이러한 전반적인 포트 값을 사용하도록 구성할 수 있습니다.

    Set-CsEdgeServer -Identity EdgeServer:atl-edge-001.litwareinc.com -MediaCommunicationPortStart 40803 -MediaCommunicationPortCount 24730

또는 다음 명령을 실행해서 조직 내 모든 서버를 동시에 구성할 수 있습니다.

    Get-CsService -EdgeServer | ForEach-Object {Set-CsEdgeServer -Identity $_.Identity -MediaCommunicationPortStart 40803 -MediaCommunicationPortCount 24730}

Lync Server 관리 셸 명령을 사용하여 에지 서버의 현재 포트 설정을 확인할 수 있습니다.

    Get-CsService -EdgeServer | Select-Object Identity, MediaCommunicationPortStart, MediaCommunicationPortCount

