---
title: 'Lync Server 2013: 외부 사용자 액세스를 위한 새 기능'
TOCTitle: 외부 사용자 액세스를 위한 새 기능
ms:assetid: 99da6bd5-ec14-4ad9-8f7d-37fbddf567dd
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398794(v=OCS.15)
ms:contentKeyID: 49304489
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 외부 사용자 액세스를 위한 새 기능

 

_**마지막으로 수정된 항목:** 2012-10-17_

Lync Server 2013에서는 사용자를 위한 기능 및 통신 방법을 확장하는 새로운 기능이 도입되었습니다. 또한 Lync Server 2013에서는 기존 서비스를 보다 효과적으로 통합하고 조직에 제공되는 서비스를 확장할 수 있도록 기능이 변경되었습니다. 다음은 Lync Server 2013  에지 서버 서비스의 계획 및 배포에 영향을 줄 수 있는 변경 내용들에 대한 요약 설명입니다.

  - **IPv6 주소 지정 지원**     Lync Server 2013은 모든 에지 서버 서비스에 대해 IPv6 주소 지정을 지원합니다. Windows Server에서의 구성을 통해 인터페이스에 대한 IPv6 주소를 지정한 경우 토폴로지 작성기에서 IP 주소를 구성하여 에지 서버 구성에서 IPv6 주소를 사용할 수 있습니다.
    

    > [!IMPORTANT]
    > Lync Server 2013에서의 IPv6 주소 사용은 조직에 배포된 라우터 및 방화벽의 IPv6 지원 여부에 따라, 그리고 인터넷 서비스 공급자를 통한 IPv6 지원 여부에 따라 달라집니다.



  - **XMPP(Extensible Messaging and Presence Protocol)**     Lync Server 2013에는 완전하게 통합된 XMPP 프록시( 에지 서버에 배포됨)와 프런트 엔드 서버에 배포되는 XMPP 게이트웨이가 도입되었습니다. 선택적 구성 요소로 XMPP 페더레이션을 배포할 수 있습니다. XMPP 프록시와 XMPP 게이트웨이를 추가하고 구성하면 Microsoft Lync 2013 사용자가 IM(인스턴트 메시징) 및 현재 상태에 XMPP 기반 파트너의 대화 상대를 추가할 수 있습니다.
    

    > [!NOTE]
    > 현재 Lync Server 2013의 XMPP 서비스는 Lync 클라이언트와 XMPP 기반 대화 상대 간의 인스턴트 메시징 및 현재 상태 기능만 제공합니다.



  - **모바일 클라이언트를 위한 Mobility Service**     Lync Server 2010의 고객 업데이트에 도입된 Lync Server 2013의 Mobility Service는 지원되는 Apple iOS, Android, Windows Phone 또는 Nokia 모바일 장치를 사용하는 휴대폰 및 태블릿 장치의 Microsoft Lync Mobile 클라이언트에서 인스턴트 메시지 주고받기, 대화 상대 보기, 현재 상태 보기 등의 작업을 수행할 수 있도록 합니다. 또한 모바일 장치에서 클릭으로 회의 참가, 회사번호로 전화, 단일 번호 연결, 음성 메일, 부재 중 통화 알림 등의 일부 Enterprise Voice 기능을 지원합니다.
    

    > [!NOTE]
    > Mobility Service는 프런트 엔드 서버에 배포된 역방향 프록시와 게시된 서비스를 사용하며 이를 위해 에지 서버에 대한 변경이 필요 없습니다.



  - **디렉터는 선택적 역할**     Lync Server 2013 토폴로지에서 디렉터 서버의 역할은 변경되지 않았습니다. 여전히 웹 서비스를 호스팅하고, 들어오는 사용자 요청을 미리 인증하고, 외부 사용자를 해당 홈 풀로 보냅니다. 디렉터가 권장 역할에서 선택적 역할로 변경된 것은 디렉터의 가치를 감소시키지 않으며, 기능 저하 없이 서버 수와 기타 하드웨어 요구 사항(예: 디렉터를 위한 하드웨어 부하 분산 장치)을 줄일 수 있다는 점을 부각시킵니다. 제공되는 서비스에 미치는 영향 없이 프런트 엔드 서버가 디렉터와 동일한 작업을 수행할 수 있기 때문에 디렉터는 원할 경우 선택적으로 배포할 수 있습니다. 프런트 엔드 서버가 동일한 서비스를 제공하므로 안심하고 디렉터를 제외할 수 있습니다.

## 참고 항목

#### 개념

[Lync Server 2013에서 IPv6 계획 및 구성](lync-server-2013-planning-for-and-configuring-ipv6.md)  

#### 기타 리소스

[Lync Server 2013의 외부 사용자 액세스 계획](lync-server-2013-planning-for-external-user-access.md)  
[Lync Server 2013의 XMPP(Extensible Messaging and Presence Protocol) 페더레이션 계획](lync-server-2013-planning-for-extensible-messaging-and-presence-protocol-xmpp-federation.md)

