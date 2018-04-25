---
title: 'Lync Server 2013: 하드웨어 부하 분산 장치를 사용하는 조정된 통합 에지'
TOCTitle: 하드웨어 부하 분산 장치를 사용하는 조정된 통합 에지
ms:assetid: 6783e225-9677-415a-8731-0bf2e2c4cf8b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398478(v=OCS.15)
ms:contentKeyID: 49303883
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 하드웨어 부하 분산 장치를 사용하는 조정된 통합 에지

 

_**마지막으로 수정된 항목:** 2012-10-21_

에지 풀 토폴로지에서는 두 개 이상의 에지 서버가 데이터 센터의 경계 네트워크에 부하 분산 풀로 배포됩니다. 하드웨어 부하 분산은 외부 및 내부 에지 서버 인터페이스 모두에 대한 트래픽에 사용됩니다.

조직에서 15,000개 이상의 액세스 에지 서비스 클라이언트 연결, 1,000개 이상의 활성 웹 회의 에지 서비스 클라이언트 연결 또는 500개 이상의 동시 A/V 에지 서비스 세션을 지원해야 하고 에지 서버의 고가용성이 중요한 경우 이 토폴로지는 확장성 및 장애 조치(Failover)를 지원하는 이점을 제공합니다.

에지 서버 및 프런트 엔드 풀 또는 서버 사이의 내부 네트워크에 배포된 디렉터의 선택적 서버 역할은 그림에 표시되지 않았습니다. 디렉터의 토폴로지에 대한 자세한 내용은 [Lync Server 2013의 디렉터에 필요한 구성 요소](lync-server-2013-components-required-for-the-director.md)를 참조하십시오.


> [!NOTE]
> 표시된 그림은 설명을 위한 예제 IP 주소 지정을 보여주며, 정확한 수신 및 송신 트래픽을 사용한 실제 통신 흐름을 나타내지는 않습니다. 이 그림은 발생 가능한 트래픽을 대략적으로 보여줍니다. 수신(수신 대기 중인 포트로) 및 송신(대상 서버 또는 클라이언트로)과 관련된 트래픽 흐름의 세부 사항은 각 시나리오의 포트 요약 다이어그램에 표시되어 있습니다. 예를 들어 TCP 443은 실제로 인바운드( 에지 서버 또는 역방향 프록시) 전용이며 프로토콜(TCP)의 관점에서만 양방향 흐름입니다. 또한 이 그림에서는 NAT(network address translation)가 발생할 때 변경되는 트래픽의 특성을 보여줍니다(인바운드 시 대상 주소가 변경되고 아웃바운드 시 원본 주소가 변경됨). 외부 및 내부 방화벽 예와 서버 인터페이스는 참조 목적으로만 표시되어 있습니다. 마지막으로 적용 가능한 경우 기본 게이트웨이 및 경로 관계 예가 표시되었습니다. 또한 이 다이어그램에서는 <EM>.com</EM> DNS 영역을 사용해서 역방향 프록시 및 에지 서버 모두에 대한 외부 DNS 영역을 표시하며, <EM>.net</EM> DNS 영역은 내부 DNS 영역을 나타냅니다.



Microsoft Lync Server 2013의 새로운 기능으로 IPv6 주소 지정이 지원됩니다. IPv4 주소 지정과 마찬가지로, IPv6 주소도 주소가 할당된 IPv6 주소 공간의 일부가 되도록 할당해야 합니다. 이 항목의 주소는 예일 뿐입니다. 해당 배포에서 작동하고 올바른 범위를 제공하며 내부 및 외부 주소 지정과 상호 작동할 IPv6 주소를 가져와야 합니다. Windows Server에서는 기존 IPv6 작동과 *이중 스택* 이라는 IPv4와 IPv6 간 통신에 중요한 기능을 제공합니다. 이중 스택은 각각 IPv4와 IPv6용 개별 네트워크 스택입니다. 이중 스택을 통해 IPv4와 IPv6에 대한 주소를 동시에 할당할 수 있으며 서버에서 해당 요구 사항에 따라 다른 호스트 및 클라이언트와 통신할 수 있습니다.

IPv6 주소 지정에 사용할 일반적인 주소 형식은 IPv6 전역 주소(공용 IPv4 주소와 유사), IPv6 고유 로컬 주소(개인 IPv4 주소 범위와 유사) 및 IPv6 링크-로컬 주소(IPv4용 Windows Server의 자동 개인 IP 주소와 유사)입니다.

NAT IPv6과 IPv4 간(일반적으로 NAT64라고 함)과 NAT IPv6 간(일반적으로 NAT66이라고 함)에 허용되는 IPv6용 NAT(Network Address Translation) 기술이 있습니다. NAT 기술의 존재는 Lync Server에지 서버에 대해 제공되는 5가지 시나리오가 여전히 유효함을 의미합니다.


> [!WARNING]
> IPv6은 복잡한 항목이므로 Windows 서버 수준과 Lync Server 2013 수준에서 할당하는 주소가 예상대로 작동하도록 하려면 네트워크 팀 및 인터넷 공급자와 함께 신중하게 계획해야 합니다. IPv6 주소 지정 및 계획에 대한 추가 리소스는 이 항목 끝에 나오는 링크를 참조하십시오.



**하드웨어 부하 분산 장치 구성**

자세한 내용은 [Lync Server 2013의 외부 사용자 액세스에 필요한 구성 요소](lync-server-2013-components-required-for-external-user-access.md)에서 "A/V 에지를 위한 하드웨어 부하 분산 장치 요구 사항" 섹션을 참조하십시오.

**확장 통합 에지 토폴로지(하드웨어 부하 분산됨)**

![확장된 통합 에지 토폴로지](images/Gg398478.3a57cd0d-8de4-4ecc-a783-4dff5b3456a2(OCS.15).jpg "확장된 통합 에지 토폴로지")


> [!IMPORTANT]
> CAC(통화 허용 제어)를 사용하는 경우에도 IPv4 주소를 에지 서버 내부 인터페이스에 할당해야 합니다. CAC에는 IPv4 주소가 사용되므로 이러한 주소가 작동될 수 있도록 해야 합니다.



## 이 단원의 내용

  - [Lync Server 2013의 인증서 요약 - 하드웨어 부하 분산 장치를 사용하는 조정된 통합 에지](lync-server-2013-certificate-summary-scaled-consolidated-edge-with-hardware-load-balancers.md)

  - [Lync Server 2013의 포트 요약 - 하드웨어 부하 분산 장치를 사용하는 조정된 통합 에지](lync-server-2013-port-summary-scaled-consolidated-edge-with-hardware-load-balancers.md)

  - [Lync Server 2013의 DNS 요약 - 하드웨어 부하 분산 장치를 사용하는 조정된 통합 에지](lync-server-2013-dns-summary-scaled-consolidated-edge-with-hardware-load-balancers.md)

## 참고 항목

#### 기타 리소스

[IP 버전 6 주소 지정 구조](http://tools.ietf.org/html/rfc4291)  
[IPv6 전역 유니캐스트 주소 형식](http://tools.ietf.org/html/rfc3587)  
[고유 로컬 IPv6 유니캐스트 주소](http://tools.ietf.org/html/rfc4193)

