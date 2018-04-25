---
title: 'Lync Server 2013: 조정된 통합 에지, 공용 IP 주소의 DNS 부하 분산'
TOCTitle: 조정된 통합 에지, 공용 IP 주소의 DNS 부하 분산
ms:assetid: 2b854f6d-3d3f-4961-a5f8-a03f47740df0
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204761(v=OCS.15)
ms:contentKeyID: 49303148
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 조정된 통합 에지, 공용 IP 주소의 DNS 부하 분산

 

_**마지막으로 수정된 항목:** 2012-09-08_

에지 서버 풀 토폴로지에서는 둘 이상의 에지 서버가 데이터 센터의 경계 네트워크에 부하 분산 풀로 배포됩니다. 외부 및 내부 에지 인터페이스로의 트래픽에는 모두 DNS(도메인 이름 시스템) 부하 분산이 사용됩니다.

조직에서 지원해야 하는 액세스 에지 서비스 클라이언트 연결 수가 15,000개, 활성 Lync Server 웹 회의 서비스 클라이언트 연결 수가 1,000개, 또는 동시 A/V 에지 세션 수가 500개보다 많으며 에지 서버의 고가용성이 중요한 경우 이 토폴로지는 확장성 및 장애 조치(failover)를 지원하는 이점을 제공합니다.

이 그림에는 에지 서버와 프런트 엔드 풀 또는 서버 사이의 내부 네트워크에 배포된 선택적 서버 역할인 디렉터가 표시되지 않습니다. 디렉터 토폴로지에 대한 자세한 내용은 [Lync Server 2013의 디렉터에 필요한 구성 요소](lync-server-2013-components-required-for-the-director.md)를 참조하십시오. 이 그림은 단일 역방향 프록시를 나타냅니다.


> [!NOTE]
> 표시된 그림은 IP 주소 지정을 보여 주는 예로 제공되었을 뿐, 트래픽이 들어오고 나가는 실제 통신 흐름을 나타내기 위한 것이 아니며 트래픽을 개략적으로 보여 줍니다. 그림은 가능한 트래픽을 간략하게 보여줍니다. 수신 포트로의 수신 및 대상 서버/클라이언트로의 발신과 관련된 트래픽 흐름에 대한 세부 정보는 각 시나리오의 포트 요약 다이어그램에 나타납니다. 예를 들어 실제로 TCP 443은 에지 또는 역방향 프록시로의 인바운드만 수행하지만 TCP 프로토콜 관점에서는 양방향 흐름입니다. 또한 그림은 NAT(Network Address Translation)가 발생하는 경우, 즉 대상 주소가 인바운드에서 변경되거나 원본 주소가 아웃바운드에서 변경된 경우 변경되는 트래픽의 특성도 보여줍니다. 외부 및 내부 방화벽 예와 서버 인터페이스 예는 참고용일 뿐입니다. 마지막으로 해당되는 경우 기본 게이트웨이 및 경로 관계 예가 표시됩니다. 이 다이어그램에서는 <EM>.com</EM> DNS 구역을 사용하여 역방향 프록시와 에지 서버 모두에 대한 외부 DNS 구역을 표현하며 <EM>.net</EM> DNS 구역은 내부 DNS 구역을 나타냅니다.



Microsoft Lync Server 2013의 새로운 기능으로 IPv6 주소 지정이 지원됩니다. IPv4 주소 지정과 마찬가지로, IPv6 주소도 주소가 할당된 IPv6 주소 공간의 일부가 되도록 할당해야 합니다. 이 항목의 주소는 예일 뿐입니다. 해당 배포에서 작동하고 올바른 범위를 제공하며 내부 및 외부 주소 지정과 상호 작동할 IPv6 주소를 가져와야 합니다. Windows Server에서는 기존 IPv6 작동과 *이중 스택* 이라는 IPv4와 IPv6 간 통신에 중요한 기능을 제공합니다. 이중 스택은 각각 IPv4와 IPv6용 개별 네트워크 스택입니다. 이중 스택을 통해 IPv4와 IPv6에 대한 주소를 동시에 할당할 수 있으며 서버에서 해당 요구 사항에 따라 다른 호스트 및 클라이언트와 통신할 수 있습니다.

IPv6 주소 지정에 사용할 일반적인 주소 형식은 IPv6 전역 주소(공용 IPv4 주소와 유사), IPv6 고유 로컬 주소(개인 IPv4 주소 범위와 유사) 및 IPv6 링크-로컬 주소(IPv4용 Windows Server의 자동 개인 IP 주소와 유사)입니다.

NAT IPv6과 IPv4 간(일반적으로 NAT64라고 함)과 NAT IPv6 간(일반적으로 NAT66이라고 함)에 허용되는 IPv6용 NAT(Network Address Translation) 기술이 있습니다. NAT 기술의 존재는 Lync Server에지 서버에 대해 제공되는 5가지 시나리오가 여전히 유효함을 의미합니다.


> [!WARNING]
> IPv6은 복잡한 항목이므로 Windows 서버 수준과 Lync Server 2013 수준에서 할당하는 주소가 예상대로 작동하도록 하려면 네트워크 팀 및 인터넷 공급자와 함께 신중하게 계획해야 합니다. IPv6 주소 지정 및 계획에 대한 추가 리소스는 이 항목 끝에 나오는 링크를 참조하십시오.



![확장된 통합 에지 토폴로지](images/JJ204761.7c1e3e6b-9b1b-4ac6-b0e7-9c256dbc2537(OCS.15).jpg "확장된 통합 에지 토폴로지")


> [!IMPORTANT]
> CAC(통화 허용 제어)를 사용하는 경우에도 IPv4 주소를 에지 서버 내부 인터페이스에 할당해야 합니다. CAC에는 IPv4 주소가 사용되므로 이러한 주소가 작동될 수 있도록 해야 합니다.



## 이 단원의 내용

  - [Lync Server 2013의 인증서 요약 - 조정된 통합 에지, 공용 IP 주소의 DNS 부하 분산](lync-server-2013-certificate-summary-scaled-consolidated-edge-dns-load-balancing-with-public-ip-addresses.md)

  - [Lync Server 2013의 포트 요약 - 조정된 통합 에지, 공용 IP 주소의 DNS 부하 분산](lync-server-2013-port-summary-scaled-consolidated-edge-dns-load-balancing-with-public-ip-addresses.md)

  - [Lync Server 2013의 DNS 요약 - 조정된 통합 에지, 공용 IP 주소의 DNS 부하 분산](lync-server-2013-dns-summary-scaled-consolidated-edge-dns-load-balancing-with-public-ip-addresses.md)

## 참고 항목

#### 기타 리소스

[IP 버전 6 주소 지정 구조](http://tools.ietf.org/html/rfc4291)  
[IPv6 전역 유니캐스트 주소 형식](http://tools.ietf.org/html/rfc3587)  
[고유 로컬 IPv6 유니캐스트 주소](http://tools.ietf.org/html/rfc4193)

