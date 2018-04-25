---
title: 'Lync Server 2013: 포트 요약 - 공용 IP 주소의 단일 통합 에지'
TOCTitle: 포트 요약 - 공용 IP 주소의 단일 통합 에지
ms:assetid: 28407acc-8b92-4f78-875c-fd6b4323b602
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204756(v=OCS.15)
ms:contentKeyID: 49303119
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 포트 요약 - 공용 IP 주소의 단일 통합 에지

 

_**마지막으로 수정된 항목:** 2015-03-09_

이 시나리오 아키텍처에서 설명하는 Lync Server 2013, 에지 서버 기능은 Lync Server 2010에서 구현되었던 것과 매우 비슷합니다. 가장 중요한 추가 항목은 XMPP(Extensible Messaging and Presence Protocol)를 위한 **TCP를 통한 포트 5269** 항목입니다. Lync Server 2013는 선택적으로 에지 서버 또는 에지 풀에 XMPP 프록시를 배포하고 프런트 엔드 서버 또는 프런트 엔드 풀에 XMPP 게이트웨이 서버를 배포합니다. 역방향 프록시 및 페더레이션 관련 계획 정보는 [Lync Server 2013의 역방향 프록시에 대한 시나리오](lync-server-2013-scenarios-for-reverse-proxy.md) 및 [Lync Server 2013에서 SIP, XMPP 페더레이션 및 공용 IM 계획](lync-server-2013-planning-for-sip-xmpp-federation-and-public-instant-messaging.md) 섹션에서 각각 확인할 수 있습니다.

에지 서버는 이제 IPv4 이외에도 IPv6를 지원합니다. 이해를 돕기 위해 시나리오에서는 IPv4만 사용됩니다.

**공용 IP 주소 지정을 사용하는 단일 통합 에지의 엔터프라이즈 경계 네트워크**

![단일 통합 에지 서버](images/Gg425891.f8c144c5-e5fb-498a-823e-eb39f26b6847(OCS.15).jpg "단일 통합 에지 서버")

## 포트 및 프로토콜 세부 정보

외부 액세스를 제공하는 기능을 지원하는 데 필요한 포트만 여는 것이 좋습니다.

원격 액세스가 모든 에지 서비스에 대해 작동하도록 하려면 SIP 트래픽이 인바운드/아웃바운드 에지 트래픽 그림에 표시된 대로 양방향으로 이동할 수 있어야 합니다. 즉, 액세스 에지 서비스와 주고받는 SIP 메시징이 IM(인스턴트 메시징), 현재 상태, 웹 회의, A/V(오디오/비디오) 및 페더레이션에 포함되어야 합니다.

### 공용 IP 주소를 포함하는 단일 통합 에지에 대한 방화벽 요약 정보: 외부 인터페이스

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
<td><p>액세스/HTTP/TCP/80</p></td>
<td><p>에지 서버  액세스 에지 서비스 공용 IP 주소</p></td>
<td><p>모두</p></td>
<td><p>인증서 해지/CRL 검사 및 검색</p></td>
</tr>
<tr class="odd">
<td><p>액세스/DNS/TCP/53</p></td>
<td><p>에지 서버  액세스 에지 서비스 공용 IP 주소</p></td>
<td><p>모두</p></td>
<td><p>TCP를 통한 DNS 쿼리</p></td>
</tr>
<tr class="even">
<td><p>액세스/DNS/UDP/53</p></td>
<td><p>에지 서버  액세스 에지 서비스 공용 IP 주소</p></td>
<td><p>모두</p></td>
<td><p>UDP를 통한 DNS 쿼리</p></td>
</tr>
<tr class="odd">
<td><p>액세스/SIP(TLS)/TCP/443</p></td>
<td><p>모두</p></td>
<td><p>에지 서버  액세스 에지 서비스 공용 IP 주소</p></td>
<td><p>외부 사용자 액세스를 위한 클라이언트-서버 SIP 트래픽</p></td>
</tr>
<tr class="even">
<td><p>액세스/SIP(MTLS)/TCP/5061</p></td>
<td><p>모두</p></td>
<td><p>에지 서버  액세스 에지 서비스 공용 IP 주소</p></td>
<td><p>SIP를 사용한 페더레이션 및 공용 IM 연결용</p></td>
</tr>
<tr class="odd">
<td><p>액세스/SIP(MTLS)/TCP/5061</p></td>
<td><p>에지 서버  액세스 에지 서비스 공용 IP 주소</p></td>
<td><p>모두</p></td>
<td><p>SIP를 사용한 페더레이션 및 공용 IM 연결용</p></td>
</tr>
<tr class="even">
<td><p>웹 회의/PSOM(TLS)/TCP/443</p></td>
<td><p>모두</p></td>
<td><p>에지 서버 웹 회의 에지 서비스 공용 IP 주소</p></td>
<td><p>웹 회의 미디어</p></td>
</tr>
<tr class="odd">
<td><p>A/V/RTP/TCP/50,000-59,999</p></td>
<td><p>에지 서버  액세스 에지 서비스 공용 IP 주소</p></td>
<td><p>모두</p></td>
<td><p>Office Communications Server 2007, Office Communications Server 2007 R2, Lync Server 2010 및 Lync Server 2013을 실행하는 파트너와의 페더레이션에 필요합니다.</p></td>
</tr>
<tr class="even">
<td><p>A/V/RTP/UDP/50,000~59,999</p></td>
<td><p>에지 서버 A/V 에지 서비스 공용 IP 주소</p></td>
<td><p>모두</p></td>
<td><p>Office Communications Server 2007을 실행하는 파트너와의 페더레이션에만 필요</p></td>
</tr>
<tr class="odd">
<td><p>A/V/RTP/TCP/50,000-59,999</p></td>
<td><p>모두</p></td>
<td><p>에지 서버 A/V 에지 서비스 공용 IP 주소</p></td>
<td><p>Office Communications Server 2007을 실행하는 파트너와의 페더레이션에만 필요</p></td>
</tr>
<tr class="even">
<td><p>A/V/RTP/UDP/50,000~59,999</p></td>
<td><p>모두</p></td>
<td><p>에지 서버 A/V 에지 서비스 공용 IP 주소</p></td>
<td><p>Office Communications Server 2007을 실행하는 파트너와의 페더레이션에만 필요</p></td>
</tr>
<tr class="odd">
<td><p>A/V/STUN,MSTURN/UDP/3478</p></td>
<td><p>에지 서버 A/V 에지 서비스 공용 IP 주소</p></td>
<td><p>모두</p></td>
<td><p>3478 아웃바운드는 Lync Server에서 통신하는 에지 서버 버전을 확인하는 데 사용되며 에지 서버- 에지 서버 간 미디어 트래픽에도 사용됩니다. Lync Server 2010, Windows Live Messenger 및 Office Communications Server 2007 R2와의 페더레이션에 필요하며, 회사 내에 여러 에지 풀이 배포된 경우에도 필요합니다.</p></td>
</tr>
<tr class="even">
<td><p>A/V/STUN,MSTURN/UDP/3478</p></td>
<td><p>모두</p></td>
<td><p>에지 서버 A/V 에지 서비스 공용 IP 주소</p></td>
<td><p>UDP/3478을 통해 후보의 STUN/TURN 협상</p></td>
</tr>
<tr class="odd">
<td><p>A/V/STUN,MSTURN/TCP/443</p></td>
<td><p>모두</p></td>
<td><p>에지 서버 A/V 에지 서비스 공용 IP 주소</p></td>
<td><p>TCP/443을 통해 후보의 STUN/TURN 협상</p></td>
</tr>
<tr class="even">
<td><p>A/V/STUN,MSTURN/TCP/443</p></td>
<td><p>에지 서버 A/V 에지 서비스 공용 IP 주소</p></td>
<td><p>모두</p></td>
<td><p>TCP/443을 통해 후보의 STUN/TURN 협상</p></td>
</tr>
</tbody>
</table>


### 공용 IP 주소를 포함하는 단일 통합 에지에 대한 방화벽 요약 정보: 내부 인터페이스

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>프로토콜/TCP 또는 UDP/포트</th>
<th>원본 IP 주소</th>
<th>대상 IP 주소</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>XMPP/MTLS/TCP/23456</p></td>
<td><p>모두( Standard Edition 서버 IP, Standard Edition 서버 IP 주소 또는 XMPP 게이트웨이 서비스를 실행하는 풀 IP 주소로 정의할 수 있음)</p></td>
<td><p>에지 서버 내부 인터페이스</p></td>
<td><p>프런트 엔드 서버 또는 프런트 엔드 풀에서 실행되는 XMPP 게이트웨이 서비스로부터의 아웃바운드 XMPP 트래픽</p>
<p></p></td>
</tr>
<tr class="even">
<td><p>SIP/MTLS/TCP/5061</p></td>
<td><p>모두( 디렉터, 디렉터 풀 IP 주소, 프런트 엔드 서버 또는 프런트 엔드 풀 IP 주소로 정의할 수 있음)</p></td>
<td><p>에지 서버 IP 또는 내부 인터페이스를 포함하는 풀</p></td>
<td><p>디렉터, 디렉터 풀 IP 주소, 프런트 엔드 서버 또는 프런트 엔드 풀 IP 주소에서 에지 서버 내부 인터페이스로의 아웃바운드 SIP 트래픽</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p>SIP/MTLS/TCP/5061</p></td>
<td><p>에지 서버 내부 인터페이스</p></td>
<td><p>모두( 디렉터, 디렉터 풀 IP 주소, 프런트 엔드 서버 또는 프런트 엔드 풀 주소로 정의할 수 있음)</p></td>
<td><p>에지 서버 내부 인터페이스에서 디렉터, 디렉터 풀 IP 주소, 프런트 엔드 서버 또는 프런트 엔드 풀 IP 주소로의 인바운드 SIP 트래픽</p>
<p></p></td>
</tr>
<tr class="even">
<td><p>PSOM/MTLS/TCP/8057</p></td>
<td><p>모두( 프런트 엔드 서버 IP 주소 또는 프런트 엔드 풀의 각 프런트 엔드 서버 IP 주소로 정의할 수 있음)</p>
<p></p></td>
<td><p>에지 서버 내부 인터페이스</p></td>
<td><p>프런트 엔드 서버 또는 각 프런트 엔드 서버(풀에 포함된 경우)에서 에지 서버 내부 인터페이스로의 웹 회의 트래픽</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p>SIP/MTLS/TCP/5062</p></td>
<td><p>모두( 프런트 엔드 서버 IP 주소 또는 프런트 엔드 풀 IP 주소나 이 에지 서버를 사용하는 모든 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버로 정의할 수 있음)</p></td>
<td><p>에지 서버 내부 인터페이스</p></td>
<td><p>프런트 엔드 서버 또는 프런트 엔드 풀 IP 주소나 이 에지 서버를 사용하는 모든 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버의 A/V 사용자 인증(A/V 인증 서비스)</p></td>
</tr>
<tr class="even">
<td><p>STUN/MSTURN/UDP/3478</p></td>
<td><p>모두</p></td>
<td><p>에지 서버 내부 인터페이스</p></td>
<td><p>내부 사용자와 외부 사용자, SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버 간의 A/V 미디어 전송을 위한 기본 설정 경로</p></td>
</tr>
<tr class="odd">
<td><p>STUN/MSTURN/TCP/443</p></td>
<td><p>모두</p></td>
<td><p>에지 서버 내부 인터페이스</p></td>
<td><p>내부 사용자와 외부 사용자, SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버 간의 A/V 미디어 전송용 대체 경로이며 UDP 통신을 설정할 수 없는 경우 파일 전송과 데스크톱 공유에 TCP가 사용됩니다.</p></td>
</tr>
<tr class="even">
<td><p>HTTPS/TCP/4443</p></td>
<td><p>모두( 프런트 엔드 서버 IP 주소 또는 중앙 관리 저장소를 포함하는 풀로 정의할 수 있음)</p></td>
<td><p>에지 서버 내부 인터페이스</p></td>
<td><p>중앙 관리 저장소에서 에지 서버로 변경 내용 복제</p></td>
</tr>
<tr class="odd">
<td><p>MTLS/TCP/50001</p></td>
<td><p>모두</p></td>
<td><p>에지 서버 내부 인터페이스</p></td>
<td><p>Lync Server 관리 셸 및 중앙 로깅 서비스 cmdlet, ClsController 명령줄(ClsController.exe) 또는 에이전트(ClsAgent.exe) 명령과 로그 수집을 사용하는 중앙 로깅 서비스 컨트롤러</p></td>
</tr>
<tr class="even">
<td><p>MTLS/TCP/50002</p></td>
<td><p>모두</p></td>
<td><p>에지 서버 내부 인터페이스</p></td>
<td><p>Lync Server 관리 셸 및 중앙 로깅 서비스 cmdlet, ClsController 명령줄(ClsController.exe) 또는 에이전트(ClsAgent.exe) 명령과 로그 수집을 사용하는 중앙 로깅 서비스 컨트롤러</p></td>
</tr>
<tr class="odd">
<td><p>MTLS/TCP/50003</p></td>
<td><p>모두</p></td>
<td><p>에지 서버 내부 인터페이스</p></td>
<td><p>Lync Server 관리 셸 및 중앙 로깅 서비스 cmdlet, ClsController 명령줄(ClsController.exe) 또는 에이전트(ClsAgent.exe) 명령과 로그 수집을 사용하는 중앙 로깅 서비스 컨트롤러</p></td>
</tr>
</tbody>
</table>


## 페더레이션에 대한 방화벽 요약


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
<td><p>액세스 에지 서비스 공용 IP 주소</p></td>
<td><p>모두</p></td>
<td><p>SIP를 사용한 페더레이션 및 공용 IM 연결용</p></td>
</tr>
</tbody>
</table>


## 방화벽 요약 - 공용 IM 연결


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
<td><p>공용 IM 연결 파트너</p></td>
<td><p>에지 서버 액세스 에지 서비스</p></td>
<td><p>SIP를 사용한 페더레이션 및 공용 IM 연결용</p></td>
</tr>
<tr class="even">
<td><p>액세스/SIP(MTLS)/TCP/5061</p></td>
<td><p>에지 서버 액세스 에지 서비스</p></td>
<td><p>공용 IM 연결 파트너</p></td>
<td><p>SIP를 사용한 페더레이션 및 공용 IM 연결용</p></td>
</tr>
<tr class="odd">
<td><p>액세스/SIP(TLS)/TCP/443</p></td>
<td><p>클라이언트</p></td>
<td><p>에지 서버 액세스 에지 서비스</p></td>
<td><p>외부 사용자 액세스를 위한 클라이언트-서버 SIP 트래픽</p></td>
</tr>
<tr class="even">
<td><p>A/V/RTP/TCP/50,000-59,999</p></td>
<td><p>에지 서버 A/V 에지 서비스</p></td>
<td><p>Live Messenger 클라이언트</p></td>
<td><p>공용 IM 연결이 구성된 경우 Windows Live Messenger와의 A/V 세션에 사용됨</p></td>
</tr>
<tr class="odd">
<td><p>A/V/STUN,MSTURN/UDP/3478</p></td>
<td><p>에지 서버 A/V 에지 서비스</p></td>
<td><p>Live Messenger 클라이언트</p></td>
<td><p>Windows Live Messenger와의 공용 IM 연결 시 필수</p></td>
</tr>
<tr class="even">
<td><p>A/V/STUN,MSTURN/UDP/3478</p></td>
<td><p>Live Messenger 클라이언트</p></td>
<td><p>에지 서버 A/V 에지 서비스</p></td>
<td><p>Windows Live Messenger와의 공용 IM 연결 시 필수</p></td>
</tr>
</tbody>
</table>


## XMPP(Extensible Messaging and Presence Protocol)의 방화벽 요약


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>프로토콜/TCP 또는 UDP/포트</th>
<th>원본(IP 주소)</th>
<th>대상(IP 주소)</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>XMPP/TCP/5269</p></td>
<td><p>모두</p></td>
<td><p>에지 서버액세스 에지 서비스 인터페이스 IP 주소</p></td>
<td><p>XMPP용 표준 서버 간 통신 포트입니다. 페더레이션 XMPP 파트너에서 에지 서버 XMPP 프록시로의 통신을 허용합니다.</p></td>
</tr>
<tr class="even">
<td><p>XMPP/TCP/5269</p></td>
<td><p>에지 서버액세스 에지 서비스 인터페이스 IP 주소</p></td>
<td><p>모두</p></td>
<td><p>XMPP용 표준 서버 간 통신 포트입니다. 에지 서버 XMPP 프록시에서 페더레이션 XMPP 파트너로의 통신을 허용합니다.</p></td>
</tr>
<tr class="odd">
<td><p>XMPP/MTLS/TCP/23456</p></td>
<td><p>모두</p></td>
<td><p>각 내부 에지 서버 인터페이스 IP</p></td>
<td><p>프런트 엔드 서버 또는 프런트 엔드 풀의 XMPP 게이트웨이에서 에지 서버 내부 IP 주소 또는 각 에지 풀 멤버 내부 IP 주소로의 내부 XMPP 트래픽</p></td>
</tr>
</tbody>
</table>

