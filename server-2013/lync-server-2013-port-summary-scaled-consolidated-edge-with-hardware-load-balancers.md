---
title: 'Lync Server 2013: 포트 요약 - 하드웨어 부하 분산 장치를 사용하는 조정된 통합 에지'
TOCTitle: 포트 요약 - 하드웨어 부하 분산 장치를 사용하는 조정된 통합 에지
ms:assetid: 91213b1e-f875-464b-83e8-fe3a351595a4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398739(v=OCS.15)
ms:contentKeyID: 49304384
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 포트 요약 - 하드웨어 부하 분산 장치를 사용하는 조정된 통합 에지

 

_**마지막으로 수정된 항목:** 2015-04-27_

이 시나리오 아키텍처에 설명된 Lync Server 2013, 에지 서버 기능은 Lync Server 2010에 구현된 기능과 매우 유사하며, 주요 차이점으로 XMPP(Extensible Messaging and Presence Protocol)를 위한 **5269/TCP** 포트 항목이 추가되었습니다. Lync Server 2013에서는 선택적으로 에지 서버 또는 에지 풀에 XMPP 프록시를 배포하고 프런트 엔드 서버 또는 프런트 엔드 풀에 XMPP 게이트웨이 서버를 배포합니다.

에지 서버는 이제 IPv4 이외에도 IPv6를 지원합니다. 이해를 돕기 위해 시나리오에서는 IPv4만 사용됩니다.

**하드 웨어 부하 분산을 사용하는 범위가 지정된 통합 에지**

![에지 서버 경계 네트워크 포트 및 프로토콜](images/Gg398739.063f7dd1-16db-4cc7-8708-bca9bc41184d(OCS.15).jpg "에지 서버 경계 네트워크 포트 및 프로토콜")

## 포트 및 프로토콜 세부 정보

외부 액세스를 제공하는 기능을 지원하는 데 필요한 포트만 여는 것이 좋습니다.

원격 액세스가 모든 에지 서비스에 대해 작동하도록 하려면 SIP 트래픽이 인바운드/아웃바운드 에지 트래픽 그림에 표시된 대로 양방향으로 이동할 수 있어야 합니다. 즉, 액세스 에지 서비스와 주고받는 SIP 메시징이 IM(인스턴트 메시징), 현재 상태, 웹 회의, A/V(오디오/비디오) 및 페더레이션에 포함되어야 합니다.

### 하드웨어 부하 분산을 사용하는 확장 통합 에지에 대한 방화벽 요약 정보: 외부 인터페이스 - 노드 1 및 노드 2(예제)

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>역할/프로토콜/TCP 또는 UDP/포트</th>
<th>원본 IP 주소</th>
<th>대상 IP 주소</th>
<th>참고</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>액세스/HTTP/TCP/80</p></td>
<td><p>에지 서버  액세스 에지 서비스 공용 IP 주소</p></td>
<td><p>모두</p></td>
<td><p>인증서 해지/CRL 검사 및 검색</p></td>
</tr>
<tr class="even">
<td><p>액세스/DNS/TCP/53</p></td>
<td><p>에지 서버  액세스 에지 서비스 공용 IP 주소</p></td>
<td><p>모두</p></td>
<td><p>TCP를 통한 DNS 쿼리</p></td>
</tr>
<tr class="odd">
<td><p>액세스/DNS/UDP/53</p></td>
<td><p>에지 서버  액세스 에지 서비스 공용 IP 주소</p></td>
<td><p>모두</p></td>
<td><p>UDP를 통한 DNS 쿼리</p></td>
</tr>
<tr class="even">
<td><p>A/V/RTP/TCP/50,000-59,999</p></td>
<td><p>에지 서버  A/V 에지 서비스 IP 주소</p></td>
<td><p>모두</p></td>
<td><p>Office Communications Server 2007, Office Communications Server 2007 R2, Lync Server 2010 및 Lync Server 2013을 실행하는 파트너와의 페더레이션에 필요합니다.</p></td>
</tr>
<tr class="odd">
<td><p>A/V/RTP/UDP/50,000~59,999</p></td>
<td><p>에지 서버 A/V 에지 서비스 공용 IP 주소</p></td>
<td><p>모두</p></td>
<td><p>Office Communications Server 2007을 실행하는 파트너와의 페더레이션에만 필요</p></td>
</tr>
<tr class="even">
<td><p>A/V/RTP/TCP/50,000-59,999</p></td>
<td><p>모두</p></td>
<td><p>에지 서버 A/V 에지 서비스 공용 IP 주소</p></td>
<td><p>Office Communications Server 2007을 실행하는 파트너와의 페더레이션에만 필요</p></td>
</tr>
<tr class="odd">
<td><p>A/V/RTP/UDP/50,000~59,999</p></td>
<td><p>모두</p></td>
<td><p>에지 서버 A/V 에지 서비스 공용 IP 주소</p></td>
<td><p>Office Communications Server 2007을 실행하는 파트너와의 페더레이션에만 필요</p></td>
</tr>
<tr class="even">
<td><p>A/V/STUN,MSTURN/UDP/3478</p></td>
<td><p>에지 서버 A/V 에지 서비스 공용 IP 주소</p></td>
<td><p>모두</p></td>
<td><p>3478 아웃바운드는 Lync Server에서 통신하는 에지 서버 버전을 확인하는 데 사용되며 에지 서버- 에지 서버 간 미디어 트래픽에도 사용됩니다. Lync Server 2010, Windows Live Messenger 및 Office Communications Server 2007 R2와의 페더레이션에 필요하며, 회사 내에 여러 에지 풀이 배포된 경우에도 필요합니다.</p></td>
</tr>
<tr class="odd">
<td><p>A/V/STUN,MSTURN/UDP/3478</p></td>
<td><p>모두</p></td>
<td><p>에지 서버 A/V 에지 서비스 공용 IP 주소</p></td>
<td><p>UDP/3478을 통해 후보의 STUN/TURN 협상</p></td>
</tr>
<tr class="even">
<td><p>A/V/STUN,MSTURN/TCP/443</p></td>
<td><p>모두</p></td>
<td><p>에지 서버 A/V 에지 서비스 공용 IP 주소</p></td>
<td><p>TCP/443을 통해 후보의 STUN/TURN 협상</p></td>
</tr>
<tr class="odd">
<td><p>A/V/STUN,MSTURN/TCP/443</p></td>
<td><p>에지 서버 A/V 에지 서비스 공용 IP 주소</p></td>
<td><p>모두</p></td>
<td><p>TCP/443을 통해 후보의 STUN/TURN 협상</p></td>
</tr>
</tbody>
</table>


### 하드웨어 부하 분산을 사용하는 확장 통합 에지에 대한 방화벽 요약 정보: 내부 인터페이스 - 노드 1 및 노드 2

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>역할/프로토콜/TCP 또는 UDP/포트</th>
<th>원본 IP 주소</th>
<th>대상 IP 주소</th>
<th>참고</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>XMPP/MTLS/TCP/23456</p></td>
<td><p>모두( 프런트 엔드 서버 주소 또는 XMPP 게이트웨이 서비스를 실행하는 프런트 엔드 풀 가상 IP 주소로 정의할 수 있음)</p></td>
<td><p>에지 서버 내부 인터페이스</p></td>
<td><p>프런트 엔드 서버 또는 프런트 엔드 풀에서 실행되는 XMPP 게이트웨이 서비스로부터의 아웃바운드 XMPP 트래픽</p></td>
</tr>
<tr class="even">
<td><p>HTTPS/TCP/4443</p></td>
<td><p>모두( 프런트 엔드 서버 서버 IP 또는 중앙 관리 저장소를 유지하는 풀로 정의할 수 있음)</p></td>
<td><p>에지 서버 내부 인터페이스</p></td>
<td><p>중앙 관리 저장소에서 에지 서버로 변경 내용 복제</p></td>
</tr>
<tr class="odd">
<td><p>PSOM/MTLS/TCP/8057</p></td>
<td><p>모두( 디렉터 IP, 프런트 엔드 서버 IP 또는 풀 가상 IP로 정의될 수 있음)</p></td>
<td><p>에지 서버 내부 인터페이스</p></td>
<td><p>내부 배포에서 내부 에지 서버 인터페이스로 나가는 웹 회의 트래픽</p></td>
</tr>
<tr class="even">
<td><p>STUN/MSTURN/UDP/3478</p></td>
<td><p>모두( 디렉터 IP, 프런트 엔드 서버 IP 또는 풀 가상 IP로 정의될 수 있음)</p></td>
<td><p>에지 서버 내부 인터페이스</p></td>
<td><p>내부 사용자와 외부 사용자, SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버 간의 A/V 미디어 전송을 위한 기본 설정 경로</p></td>
</tr>
<tr class="odd">
<td><p>STUN/MSTURN/TCP/443</p></td>
<td><p>모두( 디렉터 IP, 프런트 엔드 서버 IP 또는 풀 가상 IP로 정의될 수 있음)</p></td>
<td><p>에지 서버 내부 인터페이스</p></td>
<td><p>내부 사용자와 외부 사용자, SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버 간의 A/V 미디어 전송용 대체 경로이며 UDP 통신을 설정할 수 없는 경우 파일 전송과 데스크톱 공유에 TCP가 사용됩니다.</p></td>
</tr>
<tr class="even">
<td><p>MTLS/TCP/50001</p></td>
<td><p>모두</p></td>
<td><p>에지 서버 내부 인터페이스</p></td>
<td><p>Lync Server 관리 셸 및 중앙 로깅 서비스 cmdlet, ClsController 명령줄(ClsController.exe) 또는 에이전트(ClsAgent.exe) 명령과 로그 수집을 사용하는 중앙 로깅 서비스 컨트롤러</p></td>
</tr>
<tr class="odd">
<td><p>MTLS/TCP/50002</p></td>
<td><p>모두</p></td>
<td><p>에지 서버 내부 인터페이스</p></td>
<td><p>Lync Server 관리 셸 및 중앙 로깅 서비스 cmdlet, ClsController 명령줄(ClsController.exe) 또는 에이전트(ClsAgent.exe) 명령과 로그 수집을 사용하는 중앙 로깅 서비스 컨트롤러</p></td>
</tr>
<tr class="even">
<td><p>MTLS/TCP/50003</p></td>
<td><p>모두</p></td>
<td><p>에지 서버 내부 인터페이스</p></td>
<td><p>Lync Server 관리 셸 및 중앙 로깅 서비스 cmdlet, ClsController 명령줄(ClsController.exe) 또는 에이전트(ClsAgent.exe) 명령과 로그 수집을 사용하는 중앙 로깅 서비스 컨트롤러</p></td>
</tr>
</tbody>
</table>


Lync Server에 가용성 및 부하 분산을 제공하기 위해 하드웨어 부하 분산 장치를 배포하는 경우 특정 요구 사항을 따라야 합니다. 다음 표와 그림에 이러한 요구 사항이 나와 있습니다. 타사 공급업체의 경우 여기 나온 요구 사항에 다른 용어를 사용할 수 있습니다. 하드웨어 부하 분산 장치 공급업체가 제공하는 기능 및 구성 옵션에 맞춰 Lync Server의 요구 사항을 파악해야 합니다.

하드웨어 부하 분산 장치를 구성할 때 고려해야 할 요구 사항은 다음과 같습니다.

  - 액세스 에지 서비스 및 웹 회의 에지 서비스의 경우 HLB(하드웨어 부하 분산 장치)에 SNAT(Source Network Address Translation)를 구성할 수 있습니다.

  - A/V 에지 서비스에 대해서는 SNAT를 구성할 수 없습니다. STUN(Simple Traversal of UDP over NAT), TURN(Traversal Using Relay NAT), FTURN(Federation TURN)이 제대로 작동하려면 A/V 에지 서비스가 HLB VIP(가상 IP)가 아닌 실제 서버 주소를 사용하여 응답해야 합니다.

  - 각 서버 인터페이스와 HLB VIP에는 공용 IP 주소가 사용됩니다. 공용 IP 주소 요구 사항은 N+1로, 각 실제 서버 인터페이스에 하나와 각 HLB VIP에 하나씩 공용 IP 주소가 있어야 합니다. 풀에 에지 서버가 2개 있는 경우 HLB VIP에 3개, 각 에지 서버 인터페이스에 하나씩 총 9개의 공용 IP 주소가 서버에 사용됩니다.

  - 액세스 에지 서비스 및 웹 회의 에지 서비스의 경우(그리고 HLB에 NAT를 사용하는 경우) 클라이언트가 VIP에 연결하고 VIP가 클라이언트의 원본 IP 주소를 자체 IP 주소로 변경합니다. 서버 인터페이스는 반환된 주소를 VIP에 전송하고 VIP는 서버 인터페이스 IP 주소의 원본 주소를 변경하여 해당 패킷을 클라이언트에 전송합니다.

  - A/V 에지 서비스의 경우 VIP가 원본 IP 주소를 변경해서는 안 되고, 실제 서버 주소가 클라이언트에 직접 반환되어야 합니다. AV 트래픽에 대한 HLB에는 NAT를 구성할 수 없습니다.

  - AV의 경우 외부 방화벽에 모든 패킷의 실제 서버 공용 IP 주소가 유지됩니다.

  - 클라이언트와 A/V 에지 서비스 간의 통신이 설정된 경우 HLB가 아닌 실제 서버에 대해 통신이 이루어집니다.

  - 내부 서버 및 클라이언트에 대한 내부 에지는 라우팅되어야 하며, 서버 또는 클라이언트를 호스트하는 모든 내부 네트워크에 대해 영구 경로를 설정해야 합니다.

  - HLB 액세스 에지 서비스 VIP는 각 에지 서버 인터페이스의 기본 게이트웨이로 작동합니다.

![에지 서버 포트 및 프로토콜 세부 정보](images/Gg398739.1c193b80-98ab-4d59-a854-dbfdb5e209e2(OCS.15).jpg "에지 서버 포트 및 프로토콜 세부 정보")

### 하드웨어 부하 분산을 사용하는 확장 통합 에지에 필요한 외부 포트 설정: 외부 인터페이스 가상 IP

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>역할/프로토콜/TCP 또는 UDP/포트</th>
<th>원본 IP 주소</th>
<th>대상 IP 주소</th>
<th>참고</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>XMPP/TCP/5269</p></td>
<td><p>모두</p></td>
<td><p>XMPP 프록시 서비스( 액세스 에지 서비스와 IP 주소 공유)</p></td>
<td><p>XMPP 프록시 서비스는 정의된 XMPP 페더레이션에 있는 XMPP 대화 상대의 트래픽을 허용</p></td>
</tr>
<tr class="even">
<td><p>XMPP/TCP/5269</p></td>
<td><p>XMPP 프록시 서비스( 액세스 에지 서비스와 IP 주소 공유)</p></td>
<td><p>모두</p></td>
<td><p>XMPP 프록시 서비스가 정의된 XMPP 페더레이션의 XMPP 연락처에 트래픽 전송</p></td>
</tr>
<tr class="odd">
<td><p>액세스/SIP(TLS)/TCP/443</p></td>
<td><p>모두</p></td>
<td><p>액세스 에지 서비스 공용 VIP 주소</p></td>
<td><p>외부 사용자 액세스를 위한 클라이언트-서버 SIP 트래픽</p></td>
</tr>
<tr class="even">
<td><p>액세스/SIP(MTLS)/TCP/5061</p></td>
<td><p>모두</p></td>
<td><p>액세스 에지 서비스 공용 VIP 주소</p></td>
<td><p>SIP 신호, SIP를 사용한 페더레이션 및 공용 IM 연결용</p></td>
</tr>
<tr class="odd">
<td><p>액세스/SIP(MTLS)/TCP/5061</p></td>
<td><p>액세스 에지 서비스 공용 VIP 주소</p></td>
<td><p>페더레이션 파트너</p></td>
<td><p>SIP 신호, SIP를 사용한 페더레이션 및 공용 IM 연결용</p></td>
</tr>
<tr class="even">
<td><p>웹 회의/PSOM(TLS)/TCP/443</p></td>
<td><p>모두</p></td>
<td><p>에지 서버  웹 회의 에지 서비스 공용 VIP 주소</p></td>
<td><p>웹 회의 미디어</p></td>
</tr>
<tr class="odd">
<td><p>A/V/STUN,MSTURN/UDP/3478</p></td>
<td><p>모두</p></td>
<td><p>에지 서버 A/V 에지 서비스 공용 VIP 주소</p></td>
<td><p>UDP/3478을 통해 후보의 STUN/TURN 협상</p></td>
</tr>
<tr class="even">
<td><p>A/V/STUN,MSTURN/TCP/443</p></td>
<td><p>모두</p></td>
<td><p>에지 서버 A/V 에지 서비스 공용 VIP 주소</p></td>
<td><p>TCP/443을 통해 후보의 STUN/TURN 협상</p></td>
</tr>
</tbody>
</table>


### 하드웨어 부하 분산을 사용하는 확장 통합 에지에 대한 방화벽 요약 정보: 내부 인터페이스 가상 IP

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>역할/프로토콜/TCP 또는 UDP/포트</th>
<th>원본 IP 주소</th>
<th>대상 IP 주소</th>
<th>참고</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>액세스/SIP(MTLS)/TCP/5061</p></td>
<td><p>모두( 디렉터, 디렉터 풀 가상 IP 주소, 프런트 엔드 서버 또는 프런트 엔드 풀 가상 IP 주소로 정의할 수 있음)</p></td>
<td><p>에지 서버 내부 VIP 인터페이스</p></td>
<td><p>디렉터, 디렉터 풀 가상 IP 주소, 프런트 엔드 서버 또는 프런트 엔드 풀 가상 IP 주소에서 내부 에지 VIP로 나가는 아웃바운드 SIP 트래픽</p></td>
</tr>
<tr class="even">
<td><p>액세스/SIP(MTLS)/TCP/5061</p></td>
<td><p>에지 서버 내부 VIP 인터페이스</p></td>
<td><p>모두( 디렉터, 디렉터 풀 가상 IP 주소, 프런트 엔드 서버 또는 프런트 엔드 풀 가상 IP 주소로 정의할 수 있음)</p></td>
<td><p>에지 서버 내부 인터페이스에서 디렉터, 디렉터 풀 가상 IP 주소, 프런트 엔드 서버 또는 프런트 엔드 풀 가상 IP 주소로의 인바운드 SIP 트래픽</p></td>
</tr>
<tr class="odd">
<td><p>SIP/MTLS/TCP/5062</p></td>
<td><p>모두( 프런트 엔드 서버 IP 주소 또는 프런트 엔드 풀 IP 주소나 이 에지 서버를 사용하는 모든 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버로 정의할 수 있음)</p></td>
<td><p>에지 서버 내부 VIP 인터페이스</p></td>
<td><p>프런트 엔드 서버 또는 프런트 엔드 풀 IP 주소나 이 에지 서버를 사용하는 모든 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버의 A/V 사용자 인증(A/V 인증 서비스)</p></td>
</tr>
<tr class="even">
<td><p>STUN/MSTURN/UDP/3478</p></td>
<td><p>모두</p></td>
<td><p>에지 서버 내부 VIP 인터페이스</p></td>
<td><p>내부 사용자와 외부 사용자 간의 A/V 미디어 전송을 위한 기본 설정 경로</p></td>
</tr>
<tr class="odd">
<td><p>STUN/MSTURN/TCP/443</p></td>
<td><p>모두</p></td>
<td><p>에지 서버 내부 VIP 인터페이스</p></td>
<td><p>UDP 통신을 설정할 수 없는 경우 내부 사용자와 외부 사용자 간의 A/V 미디어 전송을 위한 장애 복구(failback) 경로(파일 전송 및 데스크톱 공유를 위해 TCP가 사용됨)</p></td>
</tr>
<tr class="even">
<td><p>STUN/MSTURN/TCP/443</p></td>
<td><p>에지 서버 내부 VIP 인터페이스</p></td>
<td><p>모두</p></td>
<td><p>UDP 통신을 설정할 수 없는 경우 내부 사용자와 외부 사용자 간의 A/V 미디어 전송을 위한 장애 복구(failback) 경로(파일 전송 및 데스크톱 공유를 위해 TCP가 사용됨)</p></td>
</tr>
</tbody>
</table>

