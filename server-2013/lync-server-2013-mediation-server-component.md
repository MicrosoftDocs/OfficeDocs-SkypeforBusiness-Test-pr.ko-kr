---
title: 'Lync Server 2013: 중재 서버 구성 요소'
TOCTitle: 중재 서버 구성 요소
ms:assetid: 5b19edef-4a54-43c9-aa12-5643b8108355
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398399(v=OCS.15)
ms:contentKeyID: 49303743
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 중재 서버 구성 요소

 

_**마지막으로 수정된 항목:** 2012-09-21_

Enterprise Voice 작업을 배포하는 경우 Lync Server 2013, 중재 서버를 배포해야 합니다. 이 섹션에서는 기본 기능, 종속성, 기본 토폴로지 및 계획 지침을 설명합니다.

중재 서버는 내부 Lync Server 2013, Enterprise Voice 인프라와 PSTN(공중 전화망) 게이트웨이 또는 SIP(Session Initiation Protocol) 트렁크 간의 신호 및 미디어(일부 구성의 경우)를 변환합니다. Lync Server 2013 쪽에서 중재 서버는 단일 MTLS(Mutual TLS) 전송 주소에서 수신 대기합니다. 게이트웨이 쪽에서 중재 서버는 토폴로지 문서에 정의된 트렁크와 연결된 모든 연관된 수신 대기 포트에서 수신 대기합니다. 해당하는 모든 게이트웨이는 TLS를 지원해야 하지만, TCP도 사용하도록 설정할 수 있습니다. TLS를 지원하지 않는 게이트웨이의 경우 TCP가 지원됩니다.

환경에 기존 PBX(Public Branch Exchange)도 있는 경우 중재 서버는 Enterprise Voice 사용자와 PBX 간의 통화를 처리합니다. PBX가 IP-PBX인 경우 PBX와 중재 서버 간에 직접 SIP 연결을 만들 수 있습니다. PBX가 TDM(Time Division Multiplex) PBX인 경우에는 중재 서버와 PBX 간에 PSTN 게이트웨이도 배포해야 합니다.

중재 서버는 기본적으로 프런트 엔드 서버와 함께 배치됩니다. 성능상의 이유로 중재 서버를 독립 실행형 풀에 배포할 수도 있으며, SIP 트렁크를 배포하는 경우에는 독립 실행형 풀에 중재 서버를 배포하는 것이 좋습니다.

미디어 바이패스 및 DNS 부하 분산을 지원하는 적격한 PSTN 게이트웨이에 직접 SIP 연결을 배포한 경우 독립 실행형 중재 서버 풀이 필요하지 않습니다. 독립 실행형 중재 서버 풀은 적격한 게이트웨이가 중재 서버 풀로 DNS를 부하 분산할 수 있으며 풀의 모든 중재 서버로부터 트래픽을 받을 수 있기 때문에 필요하지 않습니다.

또한 IP-PBX를 배포했거나 인터넷 전화 통신 서버 공급자의 SBC(세션 경계 컨트롤러)에 연결할 경우 다음 조건 중 하나라도 충족되면 프런트 엔드 풀에서 중재 서버를 배치하는 것이 좋습니다.

  - IP-PBX 또는 SBC가 풀의 중재 서버에서 트래픽을 수신하도록 구성되었고 풀의 모든 중재 서버에 트래픽을 단일 방식으로 라우팅할 수 있습니다.

  - IP-PBX가 미디어 바이패스를 지원하지 않지만 중재 서버를 호스팅하는 프런트 엔드 풀은 미디어 바이패스가 적용되지 않는 통화에 대한 음성 변환을 처리할 수 있습니다.

Microsoft Lync Server 2013, 계획 도구를 사용하여 중재 서버를 배치하려는 프런트 엔드 풀에서 부하를 처리할 수 있는지 여부를 확인할 수 있습니다. 사용자 환경에서 이러한 요구 사항을 충족할 수 없는 경우 독립 실행형 중재 서버 풀을 배포해야 합니다.

중재 서버의 주요 기능은 다음과 같습니다.

  - Lync Server 쪽에서 SRTP를 암호화하고 암호를 해독합니다.

  - TCP(TLS를 지원하지 않는 게이트웨이의 경우)를 통한 SIP를 Mutual TLS를 통한 SIP로 변환합니다.

  - 중재 서버의 게이트웨이 피어와 Lync Server 간에 미디어 스트림을 변환합니다.

  - 미디어가 NAT 및 방화벽을 통과할 수 있도록 네트워크 외부에 있는 클라이언트를 내부 ICE 구성 요소에 연결합니다.

  - 원격 작업자가 Enterprise Voice 클라이언트에서 건 전화와 같이 게이트웨이가 지원하지 않는 통화 흐름에 대해 중계 장치 역할을 합니다.

  - SIP 트렁크가 포함된 배포에서 SIP 트렁크 서비스 공급자와 함께 PSTN 지원을 제공하므로 PSTN 게이트웨이를 사용할 필요가 없습니다.

다음 그림은 기본 PSTN 게이트웨이와 Enterprise Voice 인프라를 사용하여 통신할 때 중재 서버에서 사용되는 신호 및 미디어 프로토콜을 보여 줍니다.

**중재 서버에서 사용되는 신호 및 미디어 프로토콜**

![중재 서버 프로토콜 다이어그램](images/Gg398399.c3d39ba0-e323-4a58-8f07-4e80d3278af2(OCS.15).jpg "중재 서버 프로토콜 다이어그램")


> [!NOTE]
> PSTN 게이트웨이와 중재 서버 간의 네트워크에서 SRTP 또는 SRTCP 대신 TCP 또는 RTP/RTCP를 사용하는 경우에는 네트워크의 보안을 유지하고 개인 정보를 보호하기 위한 조치를 취하는 것이 좋습니다.



## 이 섹션의 내용

  - [Lync Server 2013의 M:N 트렁크](lync-server-2013-m-n-trunk.md)

  - [Lync Server 2013의 통화 허용 제어 서비스 및 중재 서버](lync-server-2013-call-admission-control-and-mediation-server.md)

  - [Lync Server 2013의 E9-1-1(고급 9-1-1) 및 중재 서버](lync-server-2013-enhanced-9-1-1-e9-1-1-and-mediation-server.md)

  - [Lync Server 2013의 미디어 바이패스 및 중재 서버](lync-server-2013-media-bypass-and-mediation-server.md)

  - [Lync Server 2013의 중재 서버의 구성 요소 및 토폴로지](lync-server-2013-components-and-topologies-for-mediation-server.md)

  - [Lync Server 2013의 중재 서버 배포 지침](lync-server-2013-deployment-guidelines-for-mediation-server.md)

