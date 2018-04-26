---
title: 'Lync Server 2013: 위치 기반 라우팅 배포 프로세스'
TOCTitle: 위치 기반 라우팅 배포 프로세스
ms:assetid: 9e923e72-83fc-4a4f-8937-28a55739ed3e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994055(v=OCS.15)
ms:contentKeyID: 52056909
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 위치 기반 라우팅 배포 프로세스

 

_**마지막으로 수정된 항목:** 2015-03-09_

이 항목에서는 위치 기반 라우팅 구성에 관한 프로세스 개요를 제공합니다. 위치 기반 라우팅을 구성하기 전에 Lync ServerEnterprise Edition 또는 Enterprise Voice가 포함된 Standard Edition을 배포해야 합니다. 위치 기반 라우팅에 필요한 구성 요소는 Enterprise Voice를 배포할 때 미리 설치되고 사용할 수 있도록 설정됩니다.

### 위치 기반 라우팅 배포 과정

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>단계</th>
<th>절차</th>
<th>필수 그룹 및 역할</th>
<th>배포 설명서</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Enterprise Voice 배포</p></td>
<td><ul>
<li><p>트렁크 구성</p></li>
<li><p>음성 정책 만들기</p></li>
<li><p>음성 경로 정의</p></li>
</ul></td>
<td><p>CSVoiceAdmins<br />
CsAdministrator<br />
CsServerAdministrator</p></td>
<td><p>Enterprise Voice 배포</p></td>
</tr>
<tr class="even">
<td><p>Enterprise Voice 배포 확인</p></td>
<td><p></p></td>
<td><p>CSVoiceAdmins<br />
CsAdministrator<br />
CsServerAdministrator</p></td>
<td> </td>
</tr>
<tr class="odd">
<td><p>네트워크 영역, 사이트 및 서브넷 구성</p></td>
<td><ul>
<li><p>네트워크 영역 만들기</p></li>
<li><p>네트워크 사이트 만들기</p></li>
<li><p>서브넷과 네트워크 사이트 연결</p></li>
</ul></td>
<td><p>CSVoiceAdmins<br />
CsAdministrator<br />
CsServerAdministrator</p></td>
<td><p>네트워크 영역, 사이트 및 서브넷 정보<br />
네트워크 영역 만들기 또는 수정<br />
네트워크 사이트 만들기 또는 수정<br />
네트워크 사이트와 서브넷 연결</p></td>
</tr>
<tr class="even">
<td><p>위치 기반 라우팅 구성</p></td>
<td><ul>
<li><p>음성 라우팅 정책 만들기</p></li>
<li><p>트렁크별 트렁크 구성 정의</p></li>
<li><p>음성 정책 수정</p></li>
<li><p>위치 기반 라우팅 구성 설정</p></li>
</ul></td>
<td><p>CSVoiceAdmins<br />
CsAdministrator<br />
CsServerAdministrator</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## 배포 예제

다음 배포 예제는 위치 기반 라우팅에서 사용할 수 있도록 설정된 메커니즘을 보다 자세히 설명하는 데 사용됩니다.

![위치 기반 라우팅 토폴로지](images/JJ994055.e1bd2230-44da-4784-b359-24572b6ce02d(OCS.15).png "위치 기반 라우팅 토폴로지")

## 수신 PSTN 통화

관리자는 위치 기반 라우팅에 대해 “사이트 1 게이트웨이”로 통화를 라우팅하도록 정의된 트렁크를 설정하고 “사이트 1 게이트웨이”를 사이트 1에 연결할 수 있습니다. 설정된 후에는 “사이트 1 게이트웨이“를 통해 라우팅된 통화는 사이트 1에 있는 사용자에게만 라우팅됩니다. 다른 사이트(예: 사이트 2)에 있는 사용자에게 전송되는 “사이트 1 게이트웨이” 트렁크를 통해 라우팅되는 모든 통화는 PSTN 유료 우회를 방지하기 위해 차단됩니다.

“사이트 1 게이트웨이”를 통해 수신되는 모든 PSTN 통화는 사이트 1의 끝점으로만 라우팅될 수 있습니다. 예를 들어 “Lync 사용자 1”이 사이트 2로 이동하면 “사이트 1 게이트웨이”를 통해 수신되는 모든 PSTN 통화는 사이트 2에 있는 “Lync 사용자 1” 끝점으로 라우팅되지 않습니다. “Lync 사용자 1”이 위치를 확인할 수 없는 알 수 없는 네트워크 사이트로 이동한 경우에도 동일한 라우팅 규칙이 적용됩니다.

다음 표에서는 이 경우 "Lync 사용자 1"의 사용자 환경을 간략하게 설명합니다.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>네트워크 사이트 1에 있는 Lync 사용자 1 끝점</th>
<th>네트워크 사이트 2에 있는 Lync 사용자 1 끝점</th>
<th>알 수 없는 네트워크 사이트에 있는 Lync 사용자 1 끝점</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 사용자 1에 대한 인바운드 PSTN 통화</p></td>
<td><p>통화가 이 위치의 끝점으로 라우팅됨</p></td>
<td><p>통화가 이 위치의 끝점으로 라우팅되지 않음</p></td>
<td><p>통화가 이 위치의 끝점으로 라우팅되지 않음</p></td>
</tr>
</tbody>
</table>


## 발신 PSTN 통화

음성 경로는 사용자에게 직접 할당되는 음성 정책과 네트워크에 할당되는 음성 라우팅 정책에서 모두 참조됩니다. 두 정책 모두에 통화 경로를 다르게 지정하는 데 사용할 수 있는 경로에 대한 참조가 포함되어 있습니다. 예를 들어 관리자는 네트워크 사이트 1에 있는 모든 사용자에 대해 "사이트 1 게이트웨이"를 통한 모든 아웃바운드 통화를 라우팅하도록 하고, 일부 사용자에 대한 음성 정책은 "사이트 2 게이트웨이"를 통해 모든 아웃바운드 통화에 대한 경로를 지정하도록 음성 라우팅 정책을 정의할 수 있습니다. 이러한 사용자가 네트워크 사이트 1에 있는 동안에는 이들의 아웃바운드 통화가 “사이트 1 게이트웨이”를 통해 라우팅됩니다.

사용자가 위치 기반 라우팅을 위해 구성된 네트워크 사이트에 있는 경우 네트워크 사이트의 음성 라우팅 정책 경로가 사용자의 음성 정책 경로보다 우선합니다. 이 규칙은 임시로 다른 사이트로 이동하는 사용자에게 특히 유용합니다. 이 경우 사용자는 현재 위치에서 항상 로컬 게이트웨이를 사용합니다. 만일 “Lync 사용자 3”이 “사이트 2”에 있으면 해당 사용자의 모든 아웃바운드 통화가 “사이트 2 게이트웨이”를 통해 라우팅되지만, 이 사용자가 사이트 1로 이동할 경우 사이트 1에 있는 동안의 아웃바운드 통화는 모두 “사이트 1 게이트웨이”를 통해 라우팅됩니다.

다음 표는 다음 네트워크 사이트에서 아웃바운드 통화를 거는 Lync 사용자 1의 사용자 환경을 보여줍니다.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>네트워크 사이트 1</th>
<th>네트워크 사이트 2</th>
<th>알 수 없는 네트워크 사이트 또는 위치 기반 라우팅을 사용할 수 없음</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>아웃바운드 통화 권한</p></td>
<td><p>Lync 사용자 1 음성 정책</p></td>
<td><p>Lync 사용자 1 음성 정책</p></td>
<td><p>Lync 사용자 1 음성 정책</p></td>
</tr>
<tr class="even">
<td><p>아웃바운드 통화의 라우팅</p></td>
<td><p>사이트 1 음성 라우팅 정책</p></td>
<td><p>사이트 2 음성 라우팅 정책</p></td>
<td><p>사용자의 음성 정책 및 위치 기반 라우팅을 사용할 수 없는 시스템으로만 라우팅됨</p></td>
</tr>
</tbody>
</table>


## 통화 전송 및 전달

통화를 전송하거나 전달할 경우 통화의 라우팅은 위치 기반 라우팅의 영향을 받습니다.

다음 표는 PSTN 통화를 다른 Lync 사용자에게 전송하거나 전달하는 Lync 사용자 1을 보여줍니다.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>통화 전송 또는 전달을 시작하는 사용자</th>
<th>Lync 사용자 2</th>
<th>Lync 사용자 4</th>
<th>위치 기반 라우팅을 사용할 수 없는 네트워크 사이트의 Lync 사용자</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 사용자 1</p></td>
<td><p>통화 전달 또는 전송이 허용됨</p></td>
<td><p>통화 전달 또는 전송이 허용되지 않음</p></td>
<td><p>통화 전달 또는 전송이 허용되지 않음</p></td>
</tr>
</tbody>
</table>

  
다음 표에서는 위치 기반 라우팅이 PSTN 끝점으로 전송되는 Lync 사용자(Lync 사용자 2, Lync 사용자 4 등)의 위치를 기반으로 라우팅되는 방식에 어떤 영향을 주는지 보여줍니다.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>통화가 전송되거나 전달되는 끝점</th>
<th>Lync 사용자 2</th>
<th>Lync 사용자 4</th>
<th>위치 기반 라우팅을 사용할 수 없는 네트워크 사이트의 Lync 사용자</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>PSTN 끝점</p></td>
<td><p>통화 전달 또는 전송이 사이트 1 음성 라우팅 정책을 통해 라우팅되며 사이트 1 게이트웨이를 통해 이동함</p></td>
<td><p>통화 전달 또는 전송이 사이트 2 음성 라우팅 정책을 통해 라우팅되며 사이트 2 게이트웨이를 통해 이동함</p></td>
<td><p>통화 전달 또는 전송이 Lync 사용자 음성 정책을 통해 라우팅되며 위치 기반 라우팅(제공되는 경우)을 사용할 수 없는 게이트웨이를 통해 이동함</p></td>
</tr>
</tbody>
</table>


## 동시 연결

예제 토폴로지에서 위치 기반 라우팅을 구성한 후에는 다음과 같은 상호 작용이 일어납니다.

다음 표는 위치 기반 라우팅이 여러 Lync 사용자(예: Lync 사용자 2, Lync 사용자 4 등)에 대해 동시 연결을 허용하는지 여부를 보여줍니다.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>수신 PSTN 통화 대상</th>
<th>Lync 사용자 2</th>
<th>Lync 사용자 4</th>
<th>위치 기반 라우팅을 사용할 수 없는 네트워크 사이트의 Lync 사용자</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 사용자 1</p></td>
<td><p>동시 연결이 허용됨</p></td>
<td><p>동시 연결이 허용되지 않음</p></td>
<td><p>동시 연결이 허용되지 않음</p></td>
</tr>
</tbody>
</table>

  
다음 표는 위치 기반 라우팅이 여러 Lync 사용자(예: Lync 사용자2, Lync 사용자 4 등)에서 PSTN 끝점으로 동시 연결을 허용하는지 여부를 보여줍니다.


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
<th>Lync 사용자 2</th>
<th>Lync 사용자 4</th>
<th>위치 기반 라우팅을 사용할 수 없는 네트워크 사이트의 Lync 사용자</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 사용자 1 휴대폰(PSTN 끝점)</p></td>
<td><p>네트워크 사이트 1의 음성 라우팅 정책을 통해 통화가 라우팅되며 사이트 1 게이트웨이를 통해 이동함</p></td>
<td><p>네트워크 사이트 2의 음성 라우팅 정책을 통해 통화가 라우팅되며 사이트 2 게이트웨이를 통해 이동함</p></td>
<td><p>발신자 음성 정책을 통해 통화가 라우팅되며 위치 기반 라우팅을 사용할 수 있는 PSTN 게이트웨이를 통해 이동함</p></td>
</tr>
</tbody>
</table>


## 참고 항목

#### 기타 리소스

[Lync Server 2013의 위치 기반 라우팅 계획](lync-server-2013-planning-for-location-based-routing.md)

