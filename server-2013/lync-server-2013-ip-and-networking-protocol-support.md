---
title: 'Lync Server 2013: IP 및 네트워킹 프로토콜 지원'
TOCTitle: IP 및 네트워킹 프로토콜 지원
ms:assetid: b0cffb10-3478-445c-89c7-8cb8b5027424
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412848(v=OCS.15)
ms:contentKeyID: 49304743
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 IP 및 네트워킹 프로토콜 지원

 

_**마지막으로 수정된 항목:** 2012-09-21_

Lync Server 2013에서 지원되는 IP 및 네트워킹 프로토콜은 다음과 같습니다.

  - **IP 프로토콜.**  Lync Server 2013에서는 서버 네트워크에 IPv4(IP 버전 4) 또는 IPv6(IP 버전 6)를 지원합니다.
    

    > [!NOTE]
    > Lync Server 2013은 이중 IP 스택이 설정된 네트워크에서 작동할 수 있습니다.



  - **SIP 전송 프로토콜.** 일반적으로 SIP에서는 UDP(User Datagram Protocol), TCP(Transmission Control Protocol) 및 TLS(Transport Layer Security) 등과 같은 세 개 이상의 전송 유형을 사용할 수 있습니다. 기본 SIP 전송 구성에서 TLS는 TCP를 통해 실행되며, Lync Server 2013 네트워크에서 사용됩니다. 네트워크 경계에서 Lync Server 2013은 TCP를 통해 상호 작용할 수 있습니다. Lync Server 2013에서는 엔터프라이즈 통신 보안, 신뢰성 및 확장성을 위한 최소 표준을 충족하지 않으므로 SIP 전송에 대해 UDP가 지원되지 않습니다. 자세한 내용은 NextHop 팀 블로그 문서, "UDP를 포함할 것인가 말 것인가 그것이 문제"( [http://go.microsoft.com/fwlink/?linkid=185369\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=185369%26clcid=0x412))를 참조하십시오.
    

    > [!NOTE]
    > 각 블로그의 콘텐츠와 해당 URL은 공지 없이 변경될 수 있습니다.


