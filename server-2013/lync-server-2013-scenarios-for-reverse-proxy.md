---
title: 'Lync Server 2013: 역방향 프록시에 대한 시나리오'
TOCTitle: 역방향 프록시에 대한 시나리오
ms:assetid: 13108f59-a660-4ff1-8404-079d1cb646f2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204691(v=OCS.15)
ms:contentKeyID: 49302880
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 역방향 프록시에 대한 시나리오

 

_**마지막으로 수정된 항목:** 2013-01-21_

역방향 프록시는 Lync Server 2013에서 모임, 전화 접속 단순 URL, 주소록, 모임 콘텐츠, 메일 그룹 확장, 모바일 서비스 등의 서비스와 리소스에 대한 액세스를 제공하는 데 필요합니다. Lync Server 2013의 일반적인 역방향 프록시 시나리오는 데스크톱 클라이언트나 Lync Web App 클라이언트와 같은 외부 클라이언트가 디렉터 또는 프런트 엔드 서버 외부 웹 서비스에 액세스하도록 허용하는 것입니다.

**역방향 프록시 및 외부 웹 서비스**

![역방향 프록시 및 외부 웹 서비스](images/JJ204932.13142405-d5c9-45b7-a8b7-a8c89f09c97c(OCS.15).jpg "역방향 프록시 및 외부 웹 서비스")

계획 단계 중에 Lync Server 2013 배포에서 역방향 프록시에 대한 요구 사항을 정의합니다. 역방향 프록시를 사용하면 다음과 같은 외부 클라이언트의 기능에 액세스할 수 있습니다.

  - Microsoft Lync 2013 데스크톱 클라이언트

  - Microsoft Lync Web App

  - Microsoft Lync Mobile

  - Lync Windows 스토어 앱

Lync Server 2013 배포를 계획할 때는 Lync Server 2013의 실제 요구 사항을 역방향 프록시 기능에 맞게 조정합니다.

1.  외부 클라이언트는 TCP 443 포트에서 역방향 프록시에 연결하며 SSL(Secure Sockets Layer) 또는 TLS(전송 계층 보안)를 사용합니다. Microsoft Lync Mobile 클라이언트는 TCP 80 포트에서 연결할 수 있지만 이 포트는 Lync 검색 서비스에 대한 초기 연결을 수행할 때 관리자가 적절한 DNS(Domain Name System) CNAME 또는 별칭 레코드를 구성했으며 해당 통신이 암호화되지 않음을 수락하는 경우에만 연결 가능합니다.

2.  프런트 엔드 서버 및/또는 디렉터에서 배포되는 Lync Server 2013 외부 웹 서비스는 TCP 4443 포트의 역방향 프록시에서 연결해야 하며 해당 연결은 SSL/TLS여야 합니다.
    

    > [!IMPORTANT]
    > 외부 웹 서비스에 대한 권장 기본 수신 대기 포트는 HTTP 트래픽의 경우 TCP 8080이고 HTTPS 트래픽의 경우 TCP 4443입니다. 토폴로지 작성기에서는 기본값을 재정의하고 외부 웹 서비스에 대해 원하는 수신 대기 포트를 정의할 수 있습니다. 이때 역방향 프록시는 외부 웹 서비스와 통신하고 외부 클라이언트는 역방향 프록시와 통신한다는 점을 기억해야 합니다. 외부 클라이언트는 TCP 443 포트에서 역방향 프록시와 통신하지만 역방향 프록시가 외부 웹 서비스와 통신하는 데 사용하는 포트를 다시 정의할 수 있습니다. 웹 서비스에 대해 기본 수신 대기 포트를 재정의하는 토폴로지 작성기의 옵션을 통해 인프라에서 발생할 수 있는 수신 대기 포트 충돌을 해결할 수 있습니다.



3.  Lync Server 2013 외부 웹 서비스에서는 클라이언트의 수정되지 않은 호스트 헤더가 클라이언트에서 사용하려는 서비스 및 웹 서버 디렉터리를 식별해야 합니다. 요청은 역방향 프록시에서 들어온 것처럼 표시되어야 합니다.

4.  외부 웹 서비스는 클라이언트에게 제공된 서비스를 제공하는 정의된 웹 서버 vDir(가상 디렉터리)을 사용합니다. 외부에서 식별 가능한 구체적인 웹 서비스는 다음과 같습니다.
    
      - 웹 회의 모임용 “Meet” vDir
    
      - 전화 액세스 및 전화 회의용 “Dialin” vDir
    
      - Lync Windows 스토어 앱, Lync Mobile 및 데스크톱 클라이언트 Lync 2013용 "Autodiscover" vDir. Lync Server 2013에서 자동 검색의 DNS 이름은 "lyncdiscover"입니다.
    
      - 외부 클라이언트는 외부 웹 서비스를 직접 호출하여 정의되지 않은 서비스에 액세스합니다. 예를 들어 DLX(메일 그룹 확장) 및 ABS(주소록 서비스)는 외부 웹 서비스 및 연결된 vDir을 직접 호출하여 액세스합니다. 클라이언트는 vDir의 실제 경로를 알고 있으며, 이 정보를 기반으로 URL(Uniform Record Locator)을 생성합니다. 클라이언트는 `https://externalweb.contoso.com/abs/handler`와 같은 URL을 사용하여 주소록 서비스에 액세스합니다.
    
      - Office Web Apps 서버( Lync Server 토폴로지의 일부분으로 회의가 정의 및 구성된 경우)
        

        > [!NOTE]
        > Office Web Apps 서버는 별도의 역할 서버이며 외부 웹 서비스의 일부분으로 구성되지 않습니다. 이 서버는 클라이언트 액세스를 위해 별도로 게시됩니다.



5.  각 서비스에 대해 SSL 브리징 구성. 외부 포트 TCP 443은 외부 웹 서비스 포트 TCP 4443에 매핑됩니다. 암호화되지 않은 HTTP의 경우 TCP 80 포트는 외부 웹 서비스 포트 TCP 8080에 매핑됩니다.

6.  웹 서버 리소스를 게시하도록 역방향 프록시 수신기 계획

7.  제공하려는 서비스를 기준으로 역방향 프록시용 인증서를 요청하여 구성합니다. 올바른 주체 대체 이름을 사용하여 구성하는 경우 역방향 프록시 서버에 구성된 모든 수신기가 이 인증서를 공유할 수 있습니다.

역방향 프록시 배포 계획 시 사용 가능한 리소스

  - [Lync Server 2013의 데이터 수집](lync-server-2013-data-collection.md)

  - [Lync Server 2013의 인증서 요약 - 역방향 프록시](lync-server-2013-certificate-summary-reverse-proxy.md)

  - [Lync Server 2013의 포트 요약 - 역방향 프록시](lync-server-2013-port-summary-reverse-proxy.md)

  - [Lync Server 2013의 DNS 요약 - 역방향 프록시](lync-server-2013-dns-summary-reverse-proxy.md)

