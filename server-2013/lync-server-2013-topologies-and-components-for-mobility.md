---
title: 'Lync Server 2013: 모바일 기능의 토폴로지 및 구성 요소'
TOCTitle: 모바일 기능의 토폴로지 및 구성 요소
ms:assetid: be3cae7a-095d-4785-91ba-6fac99eba92a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh690037(v=OCS.15)
ms:contentKeyID: 49304887
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 모바일 기능의 토폴로지 및 구성 요소

 

_**마지막으로 수정된 항목:** 2013-02-17_

    The information in this topic pertains to Cumulative Updates for Lync Server 2013: February 2013.

모바일 장치에서 Lync 모바일 응용 프로그램을 지원하기 위해 Lync Server 2013에서는 Lync Server 2013 Mcx Mobility Service, Lync Server 2013 자동 검색 서비스, Lync Server 2013 푸시 알림 서비스의 세 가지 서비스를 제공합니다. Lync Server 2013용 누적 업데이트(2013년 2월)를 적용하면 Lync 2013 모바일 클라이언트용 고급 무료 서비스(UCWA(통합 통신 웹 API)를 사용한 모바일 기능 지원)가 추가됩니다. 이 섹션에서는 이러한 구성 요소에 대해 간략하게 설명하고 모바일 기능을 지원하는 Lync Server 2013 토폴로지에 대해 소개합니다.


> [!NOTE]
> Mobility Service는 하이브리드 배포에서도 사용할 수 있습니다. 사용자가 온라인에 배치된 경우 모바일 기능을 지원하기 위해 서비스를 배포할 필요가 없습니다. 모바일 사용자가 온라인 ID를 찾을 수 있도록 하려면 자동 검색 서비스에 대한 설정을 정의해야 합니다.




> [!IMPORTANT]
> 외부 사용자 연결(예: 페더레이션, 외부 사용자 액세스 또는 모바일 기능)을 계획하고 있는 경우 에지 서버를 Standard Edition 서버 및 프런트 엔드 서버 또는 프런트 엔드 풀과 함께 사용해야 합니다. 외부 사용자가 내부 배포에 액세스하거나, 내부 배포에서 외부 사용자와 통신하기 위해 Standard Edition 서버 및 프런트 엔드 서버 또는 프런트 엔드 풀에 필요한 구성 요소는 없습니다. 모바일 기능을 포함하여 외부 사용자가 내부 사용자와 공동 작업을 수행하거나 통신하는 모든 시나리오의 경우 하나 이상의 에지 서버와 하나의 역방향 프록시를 배포해야 합니다.<BR><EM>푸시 알림</EM> 은 PNCH(푸시 알림 클리어링 하우스)를 호스트하는 Lync Online 서비스에 대해 일종의 페더레이션을 사용합니다. 푸시 알림은 모바일 장치가 비활성 상태일 때 응용 프로그램에서 Apple iPhone, iPad 및 Windows Phone에 푸시하는 소리 알림, 화면 상의 알림(텍스트) 및 배지를 가리킵니다. PNCH는 Lync Server에서 푸시 알림을 받습니다. PNCH가 메시지 알림을 받으면 메시지 대상 모바일 클라이언트에 따라 Apple 푸시 알림 서비스 또는 Lync Server 2013 푸시 알림 서비스를 통해 알림을 모바일 클라이언트로 전달합니다. PNCH는 이러한 모바일 클라이언트에서 필수적인 서비스입니다. Lync Online에 페더레이션하기 위해 PNCH는 에지 서버 및 인증서를 사용하여 기밀성/인증, 정책 및 올바르게 구성된 DNS(Domain Name System) 레코드를 확인합니다. Nokia Symbian 및 Android 기반 Lync Mobile 클라이언트는 PNCH를 사용하지 않습니다. 에지 서버를 배포 및 계획하는 방법에 대한 자세한 내용은 <A href="lync-server-2013-planning-for-external-user-access.md">Lync Server 2013의 외부 사용자 액세스 계획</A> 및 <A href="lync-server-2013-deploying-external-user-access.md">Lync Server 2013에서 외부 사용자 액세스 배포</A>를 참조하십시오.<BR>Lync Server 2013용 누적 업데이트(2013년 2월)에 도입된 Apple 장치용 Lync 2013 모바일 클라이언트는 더 이상 푸시 알림 또는 PNCH(푸시 알림 클리어링 하우스)를 사용하지 않습니다. Windows Phone의 Lync 2013 모바일 클라이언트는 계속 푸시 알림과 PNCH(푸시 알림 클리어링 하우스)를 사용합니다.



## 모바일 기능 구성 요소

모바일 기능을 지원하는 서비스는 다음과 같습니다.

  - **Lync Server 2013 UCWA(통합 통신 웹 API)**    Lync Server 2013에서 모바일 및 웹 클라이언트와의 실시간 통신을 위한 서비스를 제공합니다. Lync Server 2013용 누적 업데이트(2013년 2월)를 프런트 엔드 서버 및 디렉터에 배포하여 설치하면 내부 및 외부 웹 서비스에 가상 디렉터리(Ucwa)가 만들어집니다. Ucwa 가상 디렉터리에 포함된 웹 구성 요소가 UCWA 사용 가능 클라이언트로부터의 호출을 수락합니다. 클라이언트 앱은 RSET 인터페이스를 통해 현재 상태, 대화 상대, 인스턴트 메시징, VoIP, 비디오 회의 및 공동 작업 관련 정보를 전달합니다. UCWA는 P-GET 기반 채널을 사용하여 수신 전화, 수신 인스턴트 메시지 또는 클라이언트 앱에 대한 메시지와 같은 이벤트를 보냅니다.
    

    > [!NOTE]
    > <EM>REST</EM> (Representational State Transfer)는 다양한 형식에서 널리 도입된 분산 시스템용 소프트웨어 아키텍처 스타일이며, 일반적인 웹 서비스의 요구 사항에 적합합니다.



  - **Lync Server 2013 Mobility Service(Mcx)**   이 서비스는 모바일 장치에서 IM(인스턴트 메시징), 현재 상태, 대화 상대 등의 Lync 기능을 지원합니다. Mobility Service는 모바일 장치에서 Lync 기능을 지원하려는 각 풀의 모든 프런트 엔드 서버에 설치됩니다. Lync Server 2013을 설치하면 프런트 엔드 서버의 내부 웹 사이트와 외부 웹 사이트에 모두 새 가상 디렉터리(Mcx)가 만들어집니다.
    

    > [!IMPORTANT]
    > Lync Server 2013용 누적 업데이트(2013년 2월)가 적용된 Lync Server 2013에서는 Lync Server 2010용 누적 업데이트(2011년 11월)에 도입된 Mcx라는 Mobility Service와 UCWA 웹 구성 요소를 모두 지원합니다. 이 두 Mobility Service가 조합되어 상호 운용성을 제공하며, Lync Server 2013의 Lync 2010 Mobile 및 Lync 2013 모바일 클라이언트 사용자가 두 서비스를 사용할 수 있습니다.



  - **Lync Server 2013 자동 검색 서비스**   이 서비스는 사용자의 위치를 파악하고 네트워크 위치에 관계없이 모바일 장치 및 기타 Lync 클라이언트에서 Lync Server 2013 웹 서비스의 내부/외부 URL, Mcx 또는 UCWA의 URL과 같은 리소스를 찾을 수 있도록 합니다. 자동 검색은 하드 코드된 호스트 이름(네트워크 내부 사용자의 경우 lyncdiscoverinternal, 네트워크 외부 사용자의 경우 lyncdiscover) 및 사용자의 SIP 도메인을 사용합니다. 자동 검색에서는 HTTP 또는 HTTPS를 사용하는 클라이언트 연결을 지원합니다.
    
    자동 검색 서비스는 모바일 장치에서 Lync 기능을 지원할 각 풀의 모든 프런트 엔드 서버 및 모든 디렉터에 설치됩니다. 자동 검색 서비스를 설치하면 프런트 엔드 서버 및 디렉터의 내부 웹 사이트와 외부 웹 사이트에 새 가상 디렉터리(Autodiscover)가 만들어집니다.
    

    > [!NOTE]
    > 이 문서에서 자동 검색 서비스를 소개하는 이유는 해당 서비스가 모바일 클라이언트 서비스 제공 시 여전히 중요한 구성 요소이기 때문입니다. Lync Server 2013에서는 자동 검색의 역할이 확장되어 모든 클라이언트에 대해 서비스를 제공합니다. 자동 검색 서비스를 계획하는 방법에 대한 자세한 내용은 <A href="lync-server-2013-planning-for-autodiscover.md">Lync Server 2013의 자동 검색 계획</A>을 참조하십시오.



  - **푸시 알림 서비스**    이 서비스는 Lync Online 데이터 센터에 있는 클라우드 기반 서비스입니다. 지원되는 Apple iOS 장치 또는 Windows Phone의 Lync 모바일 응용 프로그램은 비활성 상태인 경우 새 IM(메신저 대화) 초대, 부재 중 메신저 대화, 부재 중 통화, 음성 사서함 등의 새로운 이벤트에 응답할 수 없습니다. 이러한 장치에서는 백그라운드에서 실행되는 모바일 응용 프로그램을 지원하지 않기 때문입니다. 그러한 경우에는 *푸시 알림*이라는 새 이벤트 알림이 모바일 장치로 발송됩니다. 모바일 서비스가 알림을 클라우드 기반 푸시 알림 서비스로 보내면 푸시 알림 서비스는 알림을 APNS(Apple 푸시 알림 서비스, 지원되는 Apple iOS 장치의 경우) 또는 MPNS(Microsoft 푸시 알림 서비스, Windows Phone의 경우)로 보내며, 이들 서비스에서 알림을 모바일 장치로 보냅니다. 그러면 사용자가 모바일 장치에서 알림에 응답하여 응용 프로그램을 활성화할 수 있습니다.
    
    Apple and Windows Phone 장치의 Lync 2010 Mobile에서는 푸시 알림을 사용합니다. Lync Server 2013용 누적 업데이트(2013년 2월)에 도입된 Apple 장치용 Lync 2013 모바일 클라이언트는 더 이상 푸시 알림 또는 PNCH(푸시 알림 클리어링 하우스)를 사용하지 않습니다.

아래 다이어그램에는 푸시 알림 서비스가 UCWA 및 Lync 2013 모바일 클라이언트를 사용하는 Lync Server 2013 토폴로지에서 작동하는 방식이 나와 있습니다.

![푸시 알림 서비스 UCWA](images/Hh690037.166d60fd-ff71-4ffe-9f66-3c8bbde0b5ae(OCS.15).jpg "푸시 알림 서비스 UCWA")

Lync Server 2010용 누적 업데이트(2011년 11월)에 도입된 Mcx 서비스는 Lync 2010 Mobile 클라이언트에 대해 서비스를 제공합니다. 다음 다이어그램에서는 Mcx 및 Lync 2010 Mobile 클라이언트를 사용하는 토폴로지에 적용되는 푸시 알림 서비스를 보여 줍니다.

![푸시 알림 서비스 MCX](images/Hh690037.3081634e-60e7-4348-b24e-bbbf05a90f5f(OCS.15).jpg "푸시 알림 서비스 MCX")

## 지원되는 토폴로지

Lync Server 2013용 누적 업데이트(2013년 2월)를 적용하면 UCWA 웹 구성 요소가 추가되어 다음 토폴로지에서 Lync 2013 모바일 클라이언트 기능을 위한 모바일 기능이 지원됩니다.

  - Lync Server 2013 Standard Edition

  - Lync Server 2013 Enterprise Edition

에지 서버는 Lync Server 2010  에지 서버일 수 있습니다.

Lync Server 2013용 누적 업데이트(2013년 2월)가 적용되지 않은 Lync Server 2013 배포에서는 Mcx Mobility Service를 사용하며 Lync 2010 Mobile에 대해서만 서비스를 제공할 수 있습니다.


> [!IMPORTANT]
> Mobility Service는 네트워크 인터페이스 2개를 사용하여 중재 서버 역할과 함께 배치된 프런트 엔드 서버에서 지원되지만 이러한 인터페이스를 구성하려면 적절한 단계를 수행해야 합니다. 즉, 특정 인터페이스에 중재 서버로 통신할 IP 주소를 할당하고 프런트 엔드 서버로 통신할 네트워크 인터페이스 IP를 할당해야 합니다. 이 작업은 토폴로지 작성기에서 기본값인 <STRONG>구성된 모든 IP 주소 사용</STRONG>을 사용하는 대신 각 서비스에 대해 올바른 IP 주소를 선택하여 수행할 수 있습니다.



## 참고 항목

#### 기타 리소스

[Lync Server 2013의 외부 사용자 액세스 계획](lync-server-2013-planning-for-external-user-access.md)  
[Lync Server 2013에서 외부 사용자 액세스 배포](lync-server-2013-deploying-external-user-access.md)  
[Lync Server 2013의 자동 검색 계획](lync-server-2013-planning-for-autodiscover.md)

