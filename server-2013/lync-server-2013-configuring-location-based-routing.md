---
title: 'Lync Server 2013: 위치 기반 라우팅 구성'
TOCTitle: 위치 기반 라우팅 구성
ms:assetid: 63cdc474-e80f-43b1-a237-9d9ed673300a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994036(v=OCS.15)
ms:contentKeyID: 52056867
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 위치 기반 라우팅 구성

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 2013 CU1, 위치 기반 라우팅은 Enterprise Voice의 기능입니다. 위치 기반 라우팅은 Lync Server 2013 CU1에서 통화가 라우팅되는 방법을 제어하는 통화 관리 기능입니다. Lync 발신자의 위치에 따라 PBX 또는 PSTN 대상 중 어디로 통화가 라우팅되는지에 대한 제한이 적용됩니다. 위치 기반 라우팅은 발신자의 네트워크 위치를 기반으로 모든 권한 부여 규칙을 PSTN 통화에 적용합니다. 발신자의 위치는 발신자가 연결되어 있는 네트워크 서브넷과 연결된 네트워크 사이트를 기준으로 결정됩니다. 위치 기반 라우팅을 구성하려면 먼저 Enterprise Voice를 배포한 뒤 네트워크 영역, 사이트 및 서브넷을 구성해야 합니다. 이렇게 하면 위치 기반 라우팅을 설정할 수 있는 준비가 끝납니다.

위치 기반 라우팅을 배포하기 전에 먼저 Enterprise Voice를 배포하고 네트워크 영역, 사이트를 구성하고 네트워크 사이트에 네트워크 서브넷을 연결해야 합니다. 이 과정을 마치면 위치 기반 라우팅을 구성할 수 있습니다. 네트워크 영역, 사이트 및 서브넷을 구성하는 단계는 [Lync Server 2013에서 고급 Enterprise Voice 기능 배포](lync-server-2013-deploying-advanced-enterprise-voice-features.md)를 참고하세요.

이 섹션에서는 다음 예제를 통해 위치 기반 라우팅의 구성 과정을 설명합니다.

![Enterprise Voice 위치 기반 라우팅 예제](images/JJ994036.b6ef5afc-36ac-406f-8ec2-a87532b20612(OCS.15).png "Enterprise Voice 위치 기반 라우팅 예제")

  
다음 표는 이 예에서 정의된 사용자를 나타냅니다.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>끝점 유형</th>
<th>위치</th>
<th>사용자</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync</p></td>
<td><p>델리 사무실</p></td>
<td><p>DEL-LYNC-1,DEL-LYNC-2,DEL-LYNC-3</p></td>
</tr>
<tr class="even">
<td><p>Lync</p></td>
<td><p>히드라바드 사무실</p></td>
<td><p>HYD-LYNC-1, HYD-LYNC-2, HYD-LYNC-3</p></td>
</tr>
<tr class="odd">
<td><p>Lync</p></td>
<td><p>알 수 없음(예: 호텔)</p></td>
<td><p>UNK-LYNC-1</p></td>
</tr>
<tr class="even">
<td><p>PBX</p></td>
<td><p>델리 사무실</p></td>
<td><p>DEL-PBX-1, DEL-PBX-2</p></td>
</tr>
<tr class="odd">
<td><p>PBX</p></td>
<td><p>히드라바드 사무실</p></td>
<td><p>HYD-PBX-1, HYD-PBX-2</p></td>
</tr>
<tr class="even">
<td><p>PSTN</p></td>
<td><p>알 수 없음</p></td>
<td><p>PSTN-1, PSTN-2, PSTN-3</p></td>
</tr>
</tbody>
</table>

  

다음 표는 이 예제 환경의 시스템을 나타냅니다.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>시스템</th>
<th>위치</th>
<th>이름</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync Server 2013 CU1 풀</p></td>
<td><p>모두</p></td>
<td><p>LS-PL1</p></td>
</tr>
<tr class="even">
<td><p>Lync Server 2013 CU1, 중재 서버</p></td>
<td><p>모두</p></td>
<td><p>MS-PL1</p></td>
</tr>
<tr class="odd">
<td><p>PSTN 게이트웨이 1</p></td>
<td><p>델리</p></td>
<td><p>DEL-GW</p></td>
</tr>
<tr class="even">
<td><p>PSTN 게이트웨이 2</p></td>
<td><p>히드라바드</p></td>
<td><p>HYD-GW</p></td>
</tr>
<tr class="odd">
<td><p>PBX 1</p></td>
<td><p>델리</p></td>
<td><p>DEL-PBX</p></td>
</tr>
<tr class="even">
<td><p>PBX 2</p></td>
<td><p>히드라바드</p></td>
<td><p>RED-PBX</p></td>
</tr>
</tbody>
</table>


## 이 단원의 내용

  - [Enterprise Voice 구성](lync-server-2013-configuring-enterprise-voice.md)

  - [네트워크 지역, 사이트, 서브넷 배포](lync-server-2013-deploying-network-regions-sites-and-subnets.md)

  - [위치 기반 라우팅 사용](lync-server-2013-enabling-location-based-routing.md)

## 참고 항목

#### 기타 리소스

[Lync Server 2013에서 고급 Enterprise Voice 기능 배포](lync-server-2013-deploying-advanced-enterprise-voice-features.md)

