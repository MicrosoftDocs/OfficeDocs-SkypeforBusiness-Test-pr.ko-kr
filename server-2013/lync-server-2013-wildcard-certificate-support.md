---
title: Lync Server 2013 와일드카드 인증서 지원
TOCTitle: 와일드카드 인증서 지원
ms:assetid: 0bae2aa8-b6dc-46f5-a3be-3fe7581809d4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh202161(v=OCS.15)
ms:contentKeyID: 49302780
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 와일드카드 인증서 지원

 

_**마지막으로 수정된 항목:** 2013-03-21_

Lync Server 2013은 인증서를 사용하여 통신 암호화 및 서버 ID 인증을 제공합니다. 역방향 프록시를 통한 웹 게시와 같은 일부 경우에는 서비스를 제공하는 서버의 FQDN(정규화된 도메인 이름)에 대해 강력한 SAN(주체 대체 이름) 항목이 일치하는지 비교할 필요는 없습니다. 이러한 경우 와일드카드 SAN 항목(일반적으로 "와일드카드 인증서"라고 함)에 인증서를 사용하여 공용 인증 기관에서 요청되는 인증서 비용을 줄이고 인증서에 대한 계획 프로세스의 복잡성을 줄일 수 있습니다.


> [!WARNING]
> UC(통합 통신) 장치(예: 일반 전화기)의 기능을 보존하려면 와일드카드 인증서를 구현한 다음 장치가 올바르게 작동하도록 보장하기 위해 배포된 인증서를 신중하게 테스트해야 합니다.



와일드카드 항목은 어떠한 역할에 대해서도 주체 이름(및 CN(공용 이름)이라고도 함)으로 지원되지 않습니다. 다음은 SAN에서 와일드카드 항목을 사용할 때 지원되는 서버 역할입니다.

   **역방향 프록시.**   와일드카드 SAN 항목은 단순 URL(모임 및 전화 접속) 게시 인증서에 대해 지원됩니다.

   **역방향 프록시.**   와일드카드 SAN 항목은 게시 인증서의 LyncDiscover를 위한 SAN 항목에 대해 지원됩니다.

   **디렉터.**   와일드카드 SAN 항목은 디렉터 웹 구성 요소의 단순 URL(모임 및 전화 접속)과 LyncDiscover 및 LyncDiscoverInternal의 SAN 항목에 대해 지원됩니다.

   **프런트 엔드 서버( Standard Edition) 및 프런트 엔드 풀( Enterprise Edition).**   와일드카드 SAN 항목은 프런트 엔드 웹 구성 요소의 단순 URL(모임 및 전화 접속)과 LyncDiscover 및 LyncDiscoverInternal의 SAN 항목에 대해 지원됩니다.

   **Exchange 통합 메시징(UM).**   독립 실행형 서버로 배포된 서버에서는 SAN 항목이 사용되지 않습니다.

   **Microsoft Exchange Server 클라이언트 액세스 서버.**   SAN의 와일드카드 항목은 내부 및 외부 클라이언트에 대해 지원됩니다.

   **동일한 서버의 Exchange 통합 메시징(UM) 및 Microsoft Exchange Server 클라이언트 액세스 서버.**   와일드카드 SAN 항목이 지원됩니다.

이 항목에서 다루지 않는 서버 역할:

  - 내부 서버 역할( 중재 서버, 보관 및 모니터링 서버, SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버 등)

  - 외부 에지 서버 인터페이스

  - 내부 에지 서버
    

    > [!NOTE]
    > 내부 에지 서버 인터페이스의 경우 와일드카드 항목을 지원하며 SAN에 할당할 수 있습니다. 내부 에지 서버의 SAN은 쿼리되지 않으며 와일드카드 SAN 항목은 제한된 값을 가집니다.



인증서에서의 와일드카드 사용을 비롯한 인증서 구성에 대한 자세한 내용은 다음 항목을 참고하세요.

  - [Lync Server 2013의 내부 서버에 대한 인증서 요구 사항](lync-server-2013-certificate-requirements-for-internal-servers.md)

  - [Lync Server 2013의 외부 사용자 액세스에 대한 인증서 요구 사항](lync-server-2013-certificate-requirements-for-external-user-access.md)

  - [인증서 요약 - Lync Server 2013에서 DNS 및 HLB 부하 분산됨](lync-server-2013-certificate-summary-dns-and-hlb-load-balanced.md)

  - [Lync Server 2013의 인증서 요약 - 단일 디렉터](lync-server-2013-certificate-summary-single-director.md)

  - [Lync Server 2013의 인증서 요약 - 조정된 디렉터 풀, 하드웨어 부하 분산 장치](lync-server-2013-certificate-summary-scaled-director-pool-hardware-load-balancer.md)

  - [Lync Server 2013의 인증서 요약 - 역방향 프록시](lync-server-2013-certificate-summary-reverse-proxy.md)

  - [온-프레미스 통합 메시징과 Lync Server 2013의 통합에 대한 지침](lync-server-2013-guidelines-for-integrating-on-premises-unified-messaging.md)

Exchange용으로 인증서를 구성하는 방법(와일드카드 사용 포함)에 대한 자세한 내용은 Exchange 2013 제품 설명서를 참고하세요.

