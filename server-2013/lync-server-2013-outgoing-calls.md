---
title: 'Lync Server 2013: 발신 전화'
TOCTitle: 발신 전화
ms:assetid: 885ffe6f-cd51-4f21-8d4f-a1ff8d818858
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994049(v=OCS.15)
ms:contentKeyID: 52056899
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 발신 전화

 

_**마지막으로 수정된 항목:** 2015-03-09_

위치 기반 라우팅을 사용할 수 있는 사용자의 아웃바운드 통화 라우팅은 사용자의 끝점이 있는 네트워크 위치의 영향을 받습니다. 다음 표는 발신자의 끝점 위치에 따라 아웃바운드 통화의 라우팅에 위치 기반 라우팅이 어떤 영향을 주는지 보여줍니다.

### PSTN에 아웃바운드 전화를 거는 발신자

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>위치 기반 라우팅을 사용할 수 있는 네트워크 사이트에 있는 사용자 끝점</th>
<th>알 수 없는 네트워크 사이트에 있거나 위치 기반 라우팅을 사용할 수 없는 사용자 끝점</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>아웃바운드 통화 권한</p></td>
<td><p>사용자의 음성 정책을 기반으로 통화의 권한이 부여됨</p></td>
<td><p>사용자의 음성 정책을 기반으로 통화의 권한이 부여됨</p></td>
</tr>
<tr class="even">
<td><p>아웃바운드 통화의 라우팅</p></td>
<td><p>네트워크 사이트의 음성 라우팅 정책에 따라 통화가 라우팅됨</p></td>
<td><p>사용자의 음성 정책에 따라 통화가 라우팅되며 위치 기반 라우팅을 사용할 수 없는 트렁크를 통해서만 통화가 라우팅됨(사용 가능한 경우)</p></td>
</tr>
</tbody>
</table>


## 참고 항목

#### 기타 리소스

[Lync Server 2013의 위치 기반 라우팅 시나리오](lync-server-2013-scenarios-for-location-based-routing.md)

