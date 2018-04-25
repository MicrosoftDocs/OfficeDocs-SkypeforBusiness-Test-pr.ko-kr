---
title: Enterprise Voice 구성
TOCTitle: Enterprise Voice 구성
ms:assetid: 7df179fa-d3a2-4b23-a433-b750aedf980b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994041(v=OCS.15)
ms:contentKeyID: 52056878
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Enterprise Voice 구성

 

_**마지막으로 수정된 항목:** 2015-03-09_

Enterprise Voice를 배포하려면 다음을 구성해야 합니다.

  - 트렁크 만들기

  - 음성 정책 정의

  - 음성 경로 정의

  - 사용자가 Enterprise Voice를 사용할 수 있도록 설정

## 트렁크 만들기

Enterprise Voice 배포에서 트렁크를 정의해야 합니다. 위치 기반 라우팅의 경우 트렁크당 하나의 트렁크 구성을 만들어야 합니다. Lync Server토폴로지 작성기를 사용하여 트렁크를 정의하고, Lync ServerWindows PowerShell 명령, New-CsTrunkConfiguration 또는 Lync Server 제어판을 사용하여 해당 트렁크 구성을 정의합니다. 트렁크 구성에서 위치 기반 라우팅을 사용하도록 설정하는 방법에 대한 자세한 내용은 [위치 기반 라우팅 사용](lync-server-2013-enabling-location-based-routing.md) 항목의 '트렁크에 대한 위치 기반 라우팅 설정' 섹션을 참고하세요. 다음 표에서는 이 시나리오에 사용되는 트렁크를 보여줍니다.

자세한 내용은 [Lync Server 2013의 토폴로지 작성기에서 추가 트렁크 정의](lync-server-2013-define-additional-trunks-in-topology-builder.md)를 참고하세요.


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>트렁크 이름</th>
<th>시스템 유형</th>
<th>이름</th>
<th>위치</th>
<th>중재 서버</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>트렁크 1 DEL-GW</p></td>
<td><p>PSTN 게이트웨이</p></td>
<td><p>DEL-GW</p></td>
<td><p>델리</p></td>
<td><p>MS1</p></td>
</tr>
<tr class="even">
<td><p>트렁크 2 HYD-GW</p></td>
<td><p>PSTN 게이트웨이</p></td>
<td><p>HYD-GW</p></td>
<td><p>히드라바드</p></td>
<td><p>MS1</p></td>
</tr>
<tr class="odd">
<td><p>트렁크 3 DEL-PBX</p></td>
<td><p>PBX</p></td>
<td><p>DEL-PBX</p></td>
<td><p>델리</p></td>
<td><p>MS1</p></td>
</tr>
<tr class="even">
<td><p>트렁크 4 HYD-PBX</p></td>
<td><p>PBX</p></td>
<td><p>HYD-PBX</p></td>
<td><p>히드라바드</p></td>
<td><p>MS1</p></td>
</tr>
</tbody>
</table>



## 음성 정책 정의

Enterprise Voice 배포를 위한 음성 정책을 정의해야 합니다. 사용자의 하위 집합만 위치 기반 라우팅을 사용해야 하는 경우 위치 기반 라우팅 제한을 이 하위 집합에 적용하도록 음성 정책을 정의합니다. 다음 표에서는 이 시나리오에서 사용되는 음성 정책을 보여줍니다.이 표에는 위치 기반 라우팅에 해당되는 설정만 포함되어 있습니다.

자세한 내용은 [Lync Server 2013에서 통화 기능 및 권한을 부여하도록 음성 정책 및 PSTN 사용 레코드 구성](lync-server-2013-configuring-voice-policies-and-pstn-usage-records-to-authorize-calling-features-and-privileges.md)를 참고하세요.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>음성 정책 1</th>
<th>음성 정책 2</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>음성 정책 ID</p></td>
<td><p>델리 음성 정책</p></td>
<td><p>히드라바드 음성 정책</p></td>
</tr>
<tr class="even">
<td><p>PSTN 사용법</p></td>
<td><p>델리 사용법, PBX Del 사용법, PBX Hyd 사용법</p></td>
<td><p>히드라바드 사용법, PBX Hyd 사용법, PBX Del 사용법</p></td>
</tr>
<tr class="odd">
<td><p>PreventPSTNTollBypass</p></td>
<td><p>False</p></td>
<td><p>False</p></td>
</tr>
</tbody>
</table>



## 음성 경로 지정

Enterprise Voice 배포를 위한 음성 경로를 정의해야 합니다. 다음 표에서는 이 시나리오에서 사용되는 음성 경로를 보여줍니다. 이 표에는 위치 기반 라우팅에 해당되는 설정만 포함되어 있습니다.

자세한 내용은 [Lync Server 2013에서 아웃바운드 통화에 대한 음성 경로 구성](lync-server-2013-configuring-voice-routes-for-outbound-calls.md)을 참고하세요.


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>음성 경로 1</th>
<th>음성 경로 2</th>
<th>음성 경로 3</th>
<th>음성 경로 4</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>이름</p></td>
<td><p>델리 경로</p></td>
<td><p>히드라바드 경로</p></td>
<td><p>PBX Del 경로</p></td>
<td><p>PBX Hyd 경로</p></td>
</tr>
<tr class="even">
<td><p>PSTN 사용법</p></td>
<td><p>델리 사용법</p></td>
<td><p>히드라바드 사용법</p></td>
<td><p>PBX Del 사용법</p></td>
<td><p>PBX Hyd 사용법</p></td>
</tr>
<tr class="odd">
<td><p>트렁크</p></td>
<td><p>트렁크 1 DEL-GW</p></td>
<td><p>트렁크 2 HYD-GW</p></td>
<td><p>트렁크 3 DEL-PBX</p></td>
<td><p>트렁크 4 HYD-PBX</p></td>
</tr>
</tbody>
</table>



## 사용자가 Enterprise Voice를 사용할 수 있도록 설정

사용자가 Enterprise Voice를 사용할 수 있도록 설정하고 사용자에게 이전에 정의한 음성 정책을 할당합니다. 다음 표에서는 이 시나리오에 사용되는 할당을 보여줍니다. 이 표에는 위치 기반 라우팅에 해당되는 설정만 포함되어 있습니다.

자세한 내용은 [Lync Server 2013에서 사용자가 Enterprise Voice를 사용할 수 있도록 설정](lync-server-2013-enable-users-for-enterprise-voice.md)를 참고하세요.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>델리에 위치한 사용자</th>
<th>히드라바드에 위치한 사용자</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>연결된 음성 정책</p></td>
<td><p>델리 음성 정책</p></td>
<td><p>히드라바드 음성 정책</p></td>
</tr>
<tr class="even">
<td><p>사용자 예제</p></td>
<td><p>DEL-LYNC-1,DEL-LYNC-2,DEL-LYNC-3</p></td>
<td><p>HYD-LYNC-1, HYD-LYNC-2, HYD-LYNC-3</p></td>
</tr>
</tbody>
</table>



## 참고 항목

#### 기타 리소스

[Lync Server 2013에서 위치 기반 라우팅 구성](lync-server-2013-configuring-location-based-routing.md)

