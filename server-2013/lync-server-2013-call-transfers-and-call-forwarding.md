---
title: 'Lync Server 2013: 통화 전송 및 착신 전환'
TOCTitle: 통화 전송 및 착신 전환
ms:assetid: 978610ec-63c7-4cf6-ad7a-9ef91559bf12
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994051(v=OCS.15)
ms:contentKeyID: 52056895
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 통화 전송 및 착신 전환

 

_**마지막으로 수정된 항목:** 2015-03-09_

PSTN 끝점이 포함된 경우 위치 기반 라우팅은 수신자의 끝점과 통화가 전송 또는 착신 전환되는 끝점(예: 전송/착신 전환 대상)의 위치를 분석합니다. 위치 기반 라우팅은 두 끝점의 위치에 따라 통화가 전송 또는 착신 전환되는지 여부를 결정합니다.

다음 표에서는 Lync 사용자가 PSTN 끝점에서 통화 중이며 Lync 사용자가 통화를 다른 Lync 사용자에게 전송하는 시나리오를 보여줍니다. 전송 대상자 끝점의 네트워크 사이트 위치에 따라 위치 기반 라우팅이 통화 전송 또는 착신 전환 라우팅에 영향을 줍니다.

### 통화 전송 또는 착신 전환 시작

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>통화 전송 또는 착신 전환을 시작한 사용자</th>
<th>대상 끝점이 통화 전송 또는 착신 전환을 시작한 사용자와 같은 네트워크 사이트에 있음</th>
<th>대상 끝점이 통화 전송 또는 착신 전환을 시작한 사용자와 다른 네트워크 사이트에 있음</th>
<th>대상 끝점이 알 수 없는 네트워크 사이트 또는 위치 기반 라우팅이 설정되지 않은 네트워크 사이트에 있음</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 사용자</p></td>
<td><p>통화 전달 또는 전송이 허용됨</p></td>
<td><p>통화 전달 또는 전송이 허용되지 않음</p></td>
<td><p>통화 전달 또는 전송이 허용되지 않음</p></td>
</tr>
</tbody>
</table>

  

예를 들어, PSTN 끝점에서 통화 중인 Lync 사용자가 통화를 동일한 네트워크 사이트에 있는 다른 Lync 사용자에게 전송하는 경우 통화 전송이 허용됩니다.

다음 표에서는 Lync 사용자가 다른 Lync 사용자와 통화 중이며, 사용자 중 한 명이 통화를 PSTN 끝점으로 전송하는 시나리오를 보여줍니다. 통화가 전송되는 사용자의 위치에 따라 위치 기반 라우팅이 통화에 주는 영향이 표에 설명되어 있습니다.

### PSTN 끝점으로 통화 전송 또는 착신 전환

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>통화 전송/착신 전환 끝점 대상</th>
<th>동일한 네트워크 사이트에 있는 Lync 사용자</th>
<th>다른 네트워크 사이트에 있는 Lync 사용자</th>
<th>알 수 없는 네트워크 사이트 또는 위치 기반 라우팅이 설정되지 않은 네트워크 사이트에 있는 한 명 또는 모든 Lync 사용자</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>PSTN 끝점</p></td>
<td><p>전송되는 사용자의 사이트 음성 라우팅 정책에 의해 통화 전송 또는 착신 전환 허용됨</p></td>
<td><p>전송되는 사용자의 사이트 음성 라우팅 정책에 의해 통화 전송 또는 착신 전환 허용됨</p></td>
<td><p>위치 기반 라우팅이 설정되지 않은 트렁크를 통하는 경우에만 전송되는 사용자의 음성 정책에 의해 통화 전송 및 착신 전환 허용됨</p></td>
</tr>
</tbody>
</table>

  
예를 들어, 동일한 네트워크 사이트에 있는 다른 Lync 사용자와 통화 중인 Lync 사용자가 통화를 PSTN 끝점으로 전송하는 경우 통화 전송이 허용됩니다.

## 참고 항목

#### 기타 리소스

[Lync Server 2013의 위치 기반 라우팅 시나리오](lync-server-2013-scenarios-for-location-based-routing.md)

