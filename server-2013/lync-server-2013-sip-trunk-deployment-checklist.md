---
title: 'Lync Server 2013: SIP 트렁크 배포 검사 목록'
TOCTitle: SIP 트렁크 배포 검사 목록
ms:assetid: 94f4f03e-19d5-4198-92be-e4076dbb959a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398755(v=OCS.15)
ms:contentKeyID: 49304418
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에 대한 SIP 트렁크 배포 검사 목록

 

_**마지막으로 수정된 항목:** 2012-09-21_

SIP 트렁크를 배포하기 전에 사용자와 사용자의 서비스 공급자는 각 SIP 트렁크 끝점에 대한 기본 연결 정보를 교환해야 합니다.

연결할 각 ITSP 게이트웨이에 대한 다음 정보를 얻도록 합니다.

  - IP 주소

  - FQDN(정규화된 도메인 이름)


> [!NOTE]
> 서비스 공급자가 둘 이상의 ITSP 게이트웨이에 연결하도록 요청할 수 있습니다. 그러한 경우 풀의 각 ITSP 게이트웨이와 각 중재 서버 간의 연결을 구성해야 합니다.



서비스 공급자에게 제공하는 정보는 SIP 트렁크 연결 유형에 따라 다릅니다.

  - MPLS(Multiprotocol Label Switching) 또는 사설망 연결의 경우 ITSP에 경계 네트워크(DMZ, 완충 지역 및 스크린된 서브넷이라고도 함)에 있는 라우터의 공개적으로 라우팅 가능한 IP 주소를 제공합니다. ITSP의 게이트웨이나 SBC(세션 경계 컨트롤러)가 이 주소에 연결할 수 있는지 확인합니다. 또한 ITSP에 중재 서버의 FQDN을 제공합니다.

  - VPN(가상 사설망) 연결의 경우 ITSP에 VPN 서버의 IP 주소를 제공합니다.

## 인증서 고려 사항

SIP 트렁크에 인증서가 필요한지를 확인하려면 ITSP에 프로토콜 지원에 대해 확인합니다.

1.  ITSP가 TCP(Transmission Control Protocol)만 지원하는 경우 인증서가 필요하지 않습니다.

2.  ITSP가 TLS(전송 계층 보안)를 지원하는 경우 ITSP가 사용자에게 인증서를 제공해야 합니다.


> [!NOTE]
> SIP는 VoIP(Voice over Internet Protocol) 통화에서 실제 음성 데이터를 관리하는 프로토콜인 RTP(Real-Time Transport Protocol) 또는 SRTP(Secure Real-time Transport Protocol)와 함께 작동합니다.



## 배포 프로세스

SIP 트렁크 연결의 Lync Server 쪽을 구현하려면 다음 단계를 수행합니다.

1.  Lync Server  토폴로지 작성기를 사용하여 SIP 도메인 토폴로지를 만들고 구성합니다. 자세한 내용은 배포 설명서에서 [Lync Server 2013에 대한 토폴로지 작성기에서 토폴로지 정의 및 구성](lync-server-2013-define-and-configure-a-topology-in-topology-builder.md)을 참조하십시오.

2.  Lync Server 제어판을 사용하여 새 SIP 도메인에 대한 음성 라우팅을 구성합니다. 자세한 내용은 배포 설명서에서 [Lync Server 2013에서 트렁크 구성](lync-server-2013-configuring-trunks.md)을 참조하십시오.

3.  **Test-CsPstnOutboundCall** cmdlet을 사용하여 연결을 테스트합니다. 자세한 내용은 Lync Server 관리 셸 설명서 또는 Lync Server 관리 셸에 대한 도움말을 참조하십시오.

