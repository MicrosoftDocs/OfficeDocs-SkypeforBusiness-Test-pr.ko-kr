---
title: 'Lync Server 2013: 외부 A/V 방화벽 및 포트 요구 사항 확인'
TOCTitle: 외부 A/V 방화벽 및 포트 요구 사항 확인
ms:assetid: 3b849dc7-175d-40d1-820d-80e6ade6d332
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425882(v=OCS.15)
ms:contentKeyID: 49303370
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에 대한 외부 A/V 방화벽 및 포트 요구 사항 확인

 

_**마지막으로 수정된 항목:** 2015-03-09_

A/V(오디오/비디오) 통신은 복잡할 수 있습니다. A/V에 사용되는 프로토콜의 특성과 클라이언트 및 서버가 프로토콜을 사용하는 방법으로 인해, 클라이언트 및 서버 버전 간의 차이를 설명하기 위한 특수한 섹션이 제공됩니다.

다음 A/V 방화벽 및 포트 표를 사용하여 방화벽 요구 사항 및 열어야 하는 포트를 확인할 수 있습니다. 그런 다음 NAT(Network Address Translation) 용어를 검토합니다(NAT는 여러 가지 방법으로 구현될 수 있기 때문임). 방화벽 포트 설정에 대한 자세한 예는 [Lync Server 2013의 외부 사용자 액세스에 대한 시나리오](lync-server-2013-scenarios-for-external-user-access.md)에서 참조 아키텍처를 참조하십시오.

### 오디오/비디오 및 미디어 트래픽의 UDP 및 TCP에 대한 일반 프로토콜 사용법

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>오디오/비디오 전송</th>
<th>사용</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>UDP</p></td>
<td><p>오디오 및 비디오에 기본적으로 사용되는 전송 계층 프로토콜</p></td>
</tr>
<tr class="even">
<td><p>TCP</p></td>
<td><p>오디오 및 비디오에 대한 대체 전송 계층 프로토콜</p>
<p>Office Communications Server 2007 R2, Lync Server 2010 및 Lync Server 2013에 대한 응용 프로그램 공유용 전송 계층 프로토콜 필요</p>
<p>Lync Server 2010 및 Lync Server 2013으로의 파일 전송용 전송 계층 프로토콜 필요</p></td>
</tr>
</tbody>
</table>


## 외부 사용자 액세스를 위한 외부 A/V 방화벽 포트 요구 사항

외부(및 내부) SIP 및 회의 인터페이스에 대한 방화벽 포트 요구 사항은 페더레이션 파트너의 버전 또는 클라이언트에 관계없이 동일합니다.

단, 오디오/비디오 에지 외부 인터페이스에는 예외입니다. Office Communications Server 2007과의 페더레이션에서는 A/V 에지 서비스에서 외부 방화벽 규칙이 포트 범위 50,000\~59,999의 RTP/TCP 및 RTP/UDP 트래픽이 양방향으로 이동하도록 허용해야 합니다. 위의 표에서는 Lync Server 2013이 기본 페더레이션 파트너이고 나열된 네 가지 페더레이션 파트너 유형 중 하나와 통신하도록 구성된 것으로 가정합니다.

오디오/비디오 포트 범위 50,000\~59,999를 구성할 때는 포트 범위에 페더레이션 파트너에 대한 통신용 원본 포트가 포함됨을 고려해야 합니다. 자세한 설명을 위해 페더레이션 파트너에서 통신이 시작된다고 가정해 보겠습니다. 50,000\~59,999 범위 내에 포함된 A/V 에지 서비스 포트로부터의 통신은 파트너 A/V 에지 서비스의 해당 포트인 TCP 443에 연결됩니다. 반대로 A/V 에지 서비스 포트 TCP 443으로의 인바운드 트래픽에서는 원본 포트가 50,000\~59,999 범위 내에 포함됩니다.

방화벽 관리를 위한 각 방화벽 및 정책에서는 대상 규칙만 구성하면 되거나 원본 및 대상을 모두 구성해야 할 수 있습니다. 대상 포트만 구성하면 되는 경우의 오디오/비디오 요구 사항은 다음과 같습니다.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>원본 IP</th>
<th>대상 IP</th>
<th>대상 포트</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>A/V 에지 서비스 인터페이스</p></td>
<td><p>모두</p></td>
<td><p>TCP 443</p></td>
</tr>
<tr class="even">
<td><p>A/V 에지 서비스 인터페이스</p></td>
<td><p>모두</p></td>
<td><p>UDP 3478</p></td>
</tr>
<tr class="odd">
<td><p>모두</p></td>
<td><p>A/V 에지 서비스 인터페이스</p></td>
<td><p>TCP 443</p></td>
</tr>
<tr class="even">
<td><p>모두</p></td>
<td><p>A/V 에지 서비스 인터페이스</p></td>
<td><p>UDP 3478</p></td>
</tr>
</tbody>
</table>


정책상 인바운드 및 아웃바운드 방화벽 규칙 정의가 모두 필요한 경우의 오디오/비디오 요구 사항은 다음과 같습니다.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>원본 IP</th>
<th>대상 IP</th>
<th>원본 포트</th>
<th>대상 포트</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>A/V 에지 서비스 인터페이스</p></td>
<td><p>모두</p></td>
<td><p>TCP 50,000~59,999</p></td>
<td><p>TCP 443</p></td>
</tr>
<tr class="even">
<td><p>A/V 에지 서비스 인터페이스</p></td>
<td><p>모두</p></td>
<td><p>UDP 3478</p></td>
<td><p>UDP 3478</p></td>
</tr>
<tr class="odd">
<td><p>모두</p></td>
<td><p>A/V 에지 서비스 인터페이스</p></td>
<td><p>모두</p></td>
<td><p>TCP 443</p></td>
</tr>
<tr class="even">
<td><p>모두</p></td>
<td><p>A/V 에지 서비스 인터페이스</p></td>
<td><p>모두</p></td>
<td><p>UDP 3478</p></td>
</tr>
</tbody>
</table>



> [!IMPORTANT]
> Microsoft Office Communications Server 2007에서는 약간 다른 구성을 사용해야 합니다. 즉, TCP 및 UDP 포트 범위 50,000\~59,999를 인바운드 및 아웃바운드로 열어야 합니다. 이 요구 사항은 Office Communicator 2007에만 적용됩니다. Office Communications Server 2007 R2, Lync Server 2010 및 Lync Server 2013에서는 TCP 범위 50,000\~59,999만 아웃바운드로 열면 됩니다.



## 외부 사용자 액세스를 위한 NAT 요구 사항

NAT는 일반적으로 라우팅 기능이었지만, 방화벽과 같은 새로운 장치와 하드웨어 부하 분산 장치도 NAT를 사용하도록 구성할 수 있습니다. 이 항목에서는 NAT를 수행하는 장치에 중점을 두기보다는 필요한 NAT 동작에 대해 설명합니다.

Lync Server 2013  통신 소프트웨어는 에지 외부 인터페이스로 들어오고 나가는 트래픽에 대해 NAT를 지원하지 않지만 에지 외부 인터페이스에는 다음과 같은 NAT 동작이 필요합니다.


> [!IMPORTANT]
> 들어오는 트래픽과 나가는 트래픽에 대해 대칭 NAT를 구성해야 합니다. 대칭 NAT는 이 항목에서 설명하는 NAT 기술입니다.



이 설명서의 표에서는 머리글자어 ChangeDST 및 ChangeSRC와 그림을 사용하여 다음과 같은 필요한 동작을 정의합니다.

  - **ChangeDST**   NAT를 사용하는 네트워크로 전송되는 패킷의 대상 IP 주소를 변경하는 프로세스입니다. 이를 투명성, 포트 전달, 대상 NAT 모드 또는 반 NAT 모드라고도 합니다.

  - **ChangeSRC**   NAT를 사용하는 네트워크에서 나가는 패킷의 원본 IP 주소를 변경하는 프로세스입니다. 이를 프록시, 보안 NAT, 상태 유지 NAT, 원본 NAT 또는 전 NAT 모드라고도 합니다.

사용되는 명명 규칙에 관계없이 에지 서버의 외부 인터페이스에 필요한 NAT 동작은 다음과 같습니다.

  - 인터넷에서 에지 외부 인터페이스로 들어오는 트래픽의 경우
    
      - 에지 외부 인터페이스 공용 IP 주소에서 에지 외부 인터페이스의 변환된 IP 주소로 들어오는 패킷의 대상 IP 주소를 변경합니다.
    
      - 원본 IP 주소를 트래픽의 복귀 경로가 되도록 그대로 유지합니다.

  - 에지 외부 인터페이스에서 인터넷으로 나가는 트래픽의 경우
    
      - 내부 에지 IP 주소는 라우팅할 수 없는 IP 주소이므로 이 IP 주소가 노출되지 않도록 에지 외부 인터페이스의 변환된 IP 주소에서 공용 IP 주소로 나가는 패킷의 원본 IP 주소를 변경합니다.
    
      - 나가는 패킷의 대상 IP 주소를 그대로 유지합니다.

다음 그림에서는 인바운드 트래픽에 대한 대상 IP 주소를 변경하는 프로세스(ChangeDST)와 A/V 에지를 사용하는 아웃바운드 트래픽에 대한 원본 IP 주소를 변경하는 프로세스(ChangeSRC) 간의 차이점을 보여 줍니다.

**인바운드 트래픽에 대한 대상 IP 주소를 변경하는 프로세스(ChangeDST)와 원본 IP 주소를 변경하는 프로세스(ChangeSRC)**

![대상/원본 IP 주소 변경](images/Gg425882.0fee7ec5-4cb8-4aff-9164-e7fbab73336d(OCS.15).jpg "대상/원본 IP 주소 변경")

핵심 사항은 다음과 같습니다.

  - A/V 에지 서비스를 실행하는 서버에 대한 인바운드 트래픽의 경우 원본 IP 주소는 변경되지 않고 대상 IP 주소는 131.107.155.30에서 변환된 IP 주소 10.45.16.10으로 변경됩니다.

  - A/V 에지 서비스를 실행하는 서버에서 다시 워크스테이션으로 이동하는 아웃바운드 트래픽의 경우 원본 IP 주소는 서버의 공용 IP 주소에서 A/V 에지 서비스를 실행하는 서버의 공용 IP 주소로 변경됩니다. 대상 IP는 워크스테이션의 공용 IP 주소 그대로 유지됩니다. 패킷이 첫 번째 NAT 장치에서 나가면 해당 NAT 장치에 대한 규칙에 따라 A/V 에지 서비스를 실행하는 서버의 원본 IP 주소가 외부 인터페이스 IP 주소(10.45.16.10)에서 해당 공용 IP 주소(131.107.155.30)로 변경됩니다.

