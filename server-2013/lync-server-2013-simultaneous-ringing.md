---
title: 'Lync Server 2013: 동시 연결'
TOCTitle: 동시 연결
ms:assetid: df02f919-4d50-4832-9300-6c51f8b4fc56
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994079(v=OCS.15)
ms:contentKeyID: 52056971
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 동시 연결

 

_**마지막으로 수정된 항목:** 2015-03-09_

수신자가 동시 연결을 설정한 경우, 위치 기반 라우팅이 발신자의 위치와 수신자의 끝점을 분석하여 통화의 라우팅 여부를 결정합니다.

다음 표에서는 동시 연결을 구성한 사용자와 동일한 네트워크 사이트, 다른 네트워크 사이트 또는 알 수 없는 네트워크 사이트에 있는 동시 연결 대상인 사용자를 보여줍니다.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>수신 PSTN 전화 대상</th>
<th>수신자와 같은 네트워크 사이트에 위치</th>
<th>수신자와 다른 네트워크 사이트에 위치</th>
<th>알 수 없거나 위치 기반 라우팅이 설정되지 않은 네트워크 사이트에 위치</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 사용자</p></td>
<td><p>동시 연결 허용됨</p></td>
<td><p>동시 연결 허용되지 않음</p></td>
<td><p>동시 연결 허용되지 않음</p></td>
</tr>
</tbody>
</table>

  
다음 표에서는 동일한 네트워크 사이트, 다른 네트워크 사이트 또는 알 수 없는 네트워크 사이트에서 Lync 사용자(예: Lync 발신자)가 건 전화를 보여줍니다. 수신자는 동시 연결 대상으로 PSTN 끝점(예: 휴대폰)을 구성했습니다. 이 시나리오에서 위치 기반 라우팅은 통화가 수신자의 동시 연결 대상(예: 휴대폰)으로 라우팅되는지 여부를 결정합니다.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>동시 연결 대상</th>
<th>수신자와 같은 네트워크 사이트에 위치</th>
<th>수신자와 다른 네트워크 사이트에 위치</th>
<th>알 수 없거나 위치 기반 라우팅이 설정되지 않은 네트워크 사이트에 위치</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>PSTN 끝점</p></td>
<td><p>발신자의 사이트 음성 라우팅 정책을 통해 동시 연결 허용됨</p></td>
<td><p>발신자의 사이트 음성 라우팅 정책을 통해 동시 연결 허용됨</p></td>
<td><p>위치 기반 라우팅이 설정되지 않은 트렁크에 대한 발신자의 음성 정책을 통해 동시 연결 허용되지 않음</p></td>
</tr>
</tbody>
</table>


## 참고 항목

#### 기타 리소스

[Lync Server 2013의 위치 기반 라우팅 시나리오](lync-server-2013-scenarios-for-location-based-routing.md)

