---
title: 'Lync Server 2013: 역방향 프록시 서버 설치'
TOCTitle: 역방향 프록시 서버 설치
ms:assetid: 00bc138a-243f-4389-bfa5-9c62fcc95132
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398069(v=OCS.15)
ms:contentKeyID: 49302607
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에 대한 역방향 프록시 서버 설치

 

_**마지막으로 수정된 항목:** 2014-05-08_

Microsoft Lync Server 2013 에지 서버 배포의 경우, 외부 클라이언트가 디렉터 및 사용자 홈 풀에서 Lync Server 2013 웹 서비스( Office Communications Server에서는 *웹 구성 요소* 라고 함)에 액세스하려면 경계 네트워크에 HTTPS 역방향 프록시가 필요합니다. 다음은 역방향 프록시를 통한 외부 액세스가 필요한 몇 가지 기능입니다.

  - 외부 사용자가 모임의 모임 콘텐츠를 다운로드할 수 있도록 설정

  - 원격 사용자가 메일 그룹을 확장할 수 있도록 설정

  - 원격 사용자가 주소록 서비스에서 파일을 다운로드할 수 있도록 설정

  - Lync Web App 클라이언트 액세스

  - 전화 접속 회의 설정 웹 페이지 액세스

  - 외부 장치에서 장치 업데이트 웹 서비스에 연결하여 업데이트를 받을 수 있도록 설정

  - 모바일 응용 프로그램이 인터넷에서 모바일 기능(Mcx) URL을 자동으로 검색하고 사용할 수 있도록 설정

  - Lync 2013 클라이언트, Lync Windows 스토어 앱, Lync 2013 모바일 클라이언트가 Lync Discover(자동 검색) URL을 찾고 UCWA(통합 통신 웹 API)를 사용할 수 있도록 설정

모든 풀에서 모든 웹 서비스를 게시하려면 HTTP 역방향 프록시를 구성하는 것이 좋습니다. https:// *ExternalFQDN* /\*를 게시하면 풀의 모든 IIS 가상 디렉터리를 게시합니다. 조직의 각 Standard Edition 서버, 프런트 엔드 풀 또는 디렉터 또는 디렉터 풀에 대해 게시 규칙이 하나 필요합니다.

또한 단순 URL도 게시해야 합니다. 조직에 디렉터 또는 디렉터 풀이 있는 경우, HTTP 역방향 프록시는 단순 URL에 대한 HTTP/HTTPS 요청을 수신하고 이를 디렉터 또는 디렉터 풀에 있는 외부 웹 서비스 가상 디렉터리에 프록시합니다. 디렉터를 배포하지 않은 경우에는 단순 URL에 대한 요청을 처리하는 풀 하나를 지정해야 합니다. 이 풀이 사용자 홈 풀이 아닌 경우에는 사용자 홈 풀의 웹 서비스로 리디렉션됩니다. 단순 URL은 전용 웹 게시 규칙을 통해 처리할 수도 있고, 디렉터에 대한 웹 게시 규칙의 공용 이름에 추가할 수도 있습니다. 또한 외부 자동 검색 서비스 URL도 게시해야 합니다.

Microsoft Forefront Threat Management Gateway 2010, Microsoft Internet Security and Acceleration(ISA) Server 2006 SP1 또는 IIS ARR(Internet Information Server Application Request Routing) 7.0, 7.5 또는 8.0을 역방향 프록시로 사용할 수 있습니다. 이 섹션의 세부 단계에서는 Forefront Threat Management Gateway 2010을 구성하는 방법에 대해 설명합니다. ISA Server 2006을 구성하는 단계도 거의 비슷합니다. IIS ARR에 대한 지침도 제공됩니다. 다른 역방향 프록시를 사용하는 경우 해당 제품의 설명서를 참고하고, 여기에 정의되어 있는 요구 사항을 다른 역방향 프록시의 관련 기능에 매핑하세요.


> [!IMPORTANT]  
> IIS ARR(Internet Information Server 응용 프로그램 요청 라우팅)은 확실한 테스트를 거쳤으며 Lync Server 2010 및 Lync Server 2013의 역방향 프록시를 구현하기 위해 지원되는 옵션입니다. 2012년 11월을 기점으로 Microsoft는 ForeFront Threat Management Gateway 2010 또는 TMG의 라이선스 판매를 중단했습니다. TMG는 여전히 완벽 지원되며, 타사가 판매하는 장비를 통해 계속해서 이용할 수 있습니다. 또한 많은 타사 하드웨어 부하 분산 장치와 방화벽이 역방향 프록시 지원을 제공하고 있습니다. 역방향 프록시 기능을 제공하는 하드웨어 부하 분산 장치 및 방화벽에 대한 자세한 내용은 Lync Server에 역방향 프록시 지원을 제공하도록 제품을 구성하는 방법에 대해 공급 업체에서 제공하는 구체적인 지침을 참고하세요. 또한 Microsoft에 제품에 대한 설명서를 제출한 타사도 확인할 수 있습니다. 타사의 솔루션에 대한 지원은 타사가 제공합니다. 솔루션을 적극적으로 제공하고 있는 타사를 확인하려면 <A href="http://go.microsoft.com/fwlink/?linkid=268730">Infrastructure qualified for Microsoft Lync</A>를 참고하세요.



다음 항목 및 절차에서는 Forefront Threat Management Gateway 2010 및 IIS ARR을 배포 및 구성 절차의 기준으로 사용합니다.

  - [Lync Server 2013에 대한 웹 팜 FQDN 구성](lync-server-2013-configure-web-farm-fqdns.md)

  - [Lync Server 2013에서 네트워크 어댑터 구성](lync-server-2013-configure-network-adapters.md)

  - [Lync Server 2013에서 HTTP 역방향 프록시에 대한 인증서 요청 및 구성](lync-server-2013-request-and-configure-a-certificate-for-your-reverse-http-proxy.md)

  - [Lync Server 2013에서 단일 내부 풀에 대한 웹 게시 규칙 구성](lync-server-2013-configure-web-publishing-rules-for-a-single-internal-pool.md)

  - [Lync Server 2013에서 IIS 가상 디렉터리에 대한 인증 확인 또는 구성](lync-server-2013-verify-or-configure-authentication-and-certification-on-iis-virtual-directories.md)

  - [Lync Server 2013에서 역방향 프록시 서버에 대한 DNS 레코드 만들기](lync-server-2013-create-dns-records-for-reverse-proxy-servers.md)

  - [Lync Server 2013에서 역방향 프록시를 통해 액세스 확인](lync-server-2013-verify-access-through-your-reverse-proxy.md)

## 시작하기 전에

Forefront Threat Management Gateway 2010을 역방향 프록시로 올바르게 배포하려면 Forefront Threat Management Gateway 2010 설명서에 정의되어 있는 필수 구성 요소 및 하드웨어 요구 사항에 따라 서버를 설치 및 구성해야 합니다. 계속하기 전에 서버에서 적절하게 하드웨어를 구성하고 Forefront Threat Management Gateway 2010을 설치하려면 다음 항목을 참고하세요.

  -   
    [Forefront Threat Management Gateway(TMG) 2010](http://go.microsoft.com/fwlink/?linkid=291292)

  -   
    [Forefront TMG 2010 하드웨어 권장 사항](http://go.microsoft.com/fwlink/?linkid=291293)

IIS ARR을 역방향 프록시로 성공적으로 배포하려면 다음 항목을 검토하여 하드웨어 및 소프트웨어 필수 구성 요소를 구성하세요.

  -   
    Windows Server 2008 또는 Windows Server 2008 R2에 IIS를 설치하려면 [Windows Server 2008 또는 Windows Server 2008 R2에 IIS 7 설치(영어)](http://go.microsoft.com/fwlink/?linkid=291296)를 참고하세요.

  -   
    Windows Server 2012에 IIS를 설치하려면 [Windows Server 2012에 IIS 8 설치(영어)](http://go.microsoft.com/fwlink/?linkid=291297)를 참고하세요.

  -   
    Windows Server 2012 R2에 IIS를 설치하려면 [Windows Server 2012 R2에 IIS 8.5 설치(영어)](http://go.microsoft.com/fwlink/?linkid=330687)를 참고하세요.

  -   
    IIS용 ARR(Application Request Routing) 확장 프로그램을 다운로드하려면 [Application Request Routing v2.5 다운로드(영어)](http://go.microsoft.com/fwlink/?linkid=291298)의 지침을 따르세요.

  -   
    ARR을 설치하려면 [Application Request Routing Version 2(영어)](http://go.microsoft.com/fwlink/?linkid=291299)의 지침을 따르세요.
    

    > [!NOTE]  
    > 현재 게시된 지침은 ARR 2.0에 적용됩니다. 확장 프로그램 설치는 두 버전 간 차이가 없습니다.


