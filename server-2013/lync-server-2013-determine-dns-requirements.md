---
title: 'Lync Server 2013: DNS 요구 사항 확인'
TOCTitle: DNS 요구 사항 확인
ms:assetid: 95777017-6282-44c0-a685-f246af0501b4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398758(v=OCS.15)
ms:contentKeyID: 49304429
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에 대한 DNS 요구 사항 확인

 

_**마지막으로 수정된 항목:** 2015-03-09_

다음 순서도를 사용하여 DNS(Domain Name System) 요구 사항을 확인할 수 있습니다. Lync Server 2013용 누적 업데이트(2013년 2월)의 변경 내용은 해당하는 경우 표시되어 있습니다.


> [!IMPORTANT]
> Microsoft Lync Server 2013에서는 IPv6 주소 지정을 사용할 수 있도록 지원합니다. IPv6 주소를 사용하려면 IPv6 DNS에 대한 지원을 제공하고 DNS 호스트 AAAA(“4자리 A”라고도 함) 레코드를 구성해야 합니다. IPv4와 IPv6를 모두 사용하는 배포에서는 IPv4를 위한 호스트 A 레코드와 IPv6를 위한 호스트 AAAA를 모두 구성하고 관리하는 것이 좋습니다. 배포를 완전히 IPv6로 전환했더라도 외부 사용자가 아직 IPv4를 사용하는 경우 IPv4 DNS 호스트 레코드가 여전히 필요할 수 있습니다.



**DNS 요구 사항 확인 순서도**

![DNS 요구 사항 확인 순서도](images/Gg398758.175782ac-363e-408a-912f-8991bf152970(OCS.15).jpg "DNS 요구 사항 확인 순서도")


> [!IMPORTANT]
> 기본적으로 도메인에 가입되지 않은 컴퓨터의 컴퓨터 이름은 FQDN(정규화된 이름)이 아닌 호스트 이름입니다. 토폴로지 작성기에서는 호스트 이름이 아닌 FQDN을 사용합니다. 따라서 도메인이 가입되지 않은 에지 서버로 배포할 컴퓨터의 이름에 DNS 접미사를 구성해야 합니다. Lync Server, 에지 서버 및 풀의 FQDN을 지정할 때는 <STRONG>표준 문자만 사용</STRONG>하고(A-Z, a-z, 0-9, 하이픈 등) 유니코드 문자나 밑줄을 사용하지 마십시오. FQDN의 비표준 문자는 외부 DNS 및 공용 CA(인증서의 SN에 FQDN을 할당해야 하는 경우)에서 지원되지 않는 경우가 많습니다. 자세한 내용은 <A href="lync-server-2013-configure-dns-host-records.md">Lync Server 2013에 대한 DNS 호스트 레코드 구성</A>을 참조하십시오.



## Lync 클라이언트에서 서비스를 찾는 방법

Microsoft Lync 2010, Lync 2013 및 Lync Mobile에서는 클라이언트가 Lync Server 2013에서 서비스를 찾아 액세스하는 방법이 비슷합니다. 다른 서비스 위치 프로세스를 사용하는 Lync Windows 스토어 앱의 경우는 예외입니다. 이 섹션에서는 클라이언트가 서비스를 찾는 방법과 관련한 두 가지 시나리오에 대해 자세히 설명하는데, 그중 첫 번째는 일련의 SRV 및 A 호스트 레코드를 사용하는 기존의 방법이고 두 번째는 자동 검색 서비스 레코드만 사용하는 것입니다. 데스크톱 클라이언트에 누적 업데이트를 적용하면 Lync Server 2010에서 DNS 위치 프로세스가 변경됩니다. 모든 클라이언트에 대해 올바른 쿼리가 반환되거나 가능한 DNS 레코드 목록을 모두 확인하여 클라이언트로 최종 오류가 반환될 때까지 DNS 쿼리 프로세스는 계속됩니다.

Lync Windows 스토어 앱을 **제외**한 모든 클라이언트에 대해 DNS 조회 중에 SRV 레코드가 쿼리되어 다음 순서로 클라이언트에 반환됩니다.

1.  lyncdiscoverinternal. *\<도메인\>*    내부 웹 서비스의 자동 검색 서비스용 A(호스트) 레코드입니다.

2.  lyncdiscover. *\<도메인\>*    외부 웹 서비스의 자동 검색 서비스용 A(호스트) 레코드입니다.

3.  \_sipinternaltls.\_tcp. *\<도메인\>*    내부 TLS 연결용 SRV(서비스 로케이터) 레코드입니다.

4.  \_sipinternal.\_tcp. *\<도메인\>*    내부 TCP 연결용(TCP가 허용되는 경우에만 수행됨) SRV(서비스 로케이터) 레코드입니다.

5.  \_sip.\_tls. *\<도메인\>*    외부 TLS 연결용 SRV(서비스 로케이터) 레코드입니다.

6.  sipinternal. *\<도메인\>*     프런트 엔드 풀 또는 디렉터용 A(호스트) 레코드로, 내부 네트워크에서만 확인할 수 있습니다.

7.  sip. *\<도메인\>*    내부 네트워크의 프런트 엔드 풀 또는 디렉터용(클라이언트가 외부에 있는 경우에는 액세스 에지 서비스용) A(호스트) 레코드입니다.

8.  sipexternal. *\<도메인\>*    클라이언트가 외부에 있는 경우 액세스 에지 서비스용 A(호스트) 레코드입니다.

Lync Windows 스토어 앱은 다음의 2개 레코드를 사용하므로 프로세스가 완전히 변경됩니다.

1.  lyncdiscoverinternal. *\<도메인\>*    내부 웹 서비스의 자동 검색 서비스용 A(호스트) 레코드입니다.

2.  lyncdiscover. *\<도메인\>*    외부 웹 서비스의 자동 검색 서비스용 A(호스트) 레코드입니다.

다른 레코드 유형이 대체 항목으로 사용되지는 않습니다.

이전 클라이언트와 최신 클라이언트에 사용되는 방법 간의 차이는 자동 검색 서비스가 모든 서비스를 찾는 기본 방법으로 사용된다는 점입니다.

연결이 성공하면 자동 검색 서비스에서 Mobility Service(IIS에서 서비스용으로 작성된 가상 디렉터리에서는 Mcx로 확인됨), Microsoft Lync Web App 및 웹 스케줄러 URL을 비롯하여 사용자 홈 풀의 모든 웹 서비스 URL을 반환합니다. 그러나 내부 Mobility Service URL과 외부 Mobility Service URL은 모두 외부 웹 서비스 FQDN에 연결됩니다. 따라서 모바일 장치는 네트워크 내부에 있든 외부에 있든 관계없이 항상 역방향 프록시를 통해 외부적으로 Mobility Service에 연결합니다.

Lync Server 2013용 누적 업데이트(2013년 2월)를 설치한 경우 자동 검색 서비스는 내부/UCWA, 외부/UCWA 및 UCWA에 대한 참조도 반환합니다. 이러한 항목은 UCWA(통합 통신 웹 API) 웹 구성 요소를 참조합니다. 현재는 UCWA 항목만 사용되어 웹 구성 요소의 URL에 대한 참조를 제공합니다. UCWA는 Lync 2010 Mobile 클라이언트에서 사용하는 Mcx Mobility Service 대신 Lync 2013 모바일 클라이언트에서 사용됩니다.


> [!NOTE]
> SRV 레코드를 만들 때 이러한 레코드는 DNS SRV가 만들어진 곳과 같은 도메인에 있는 DNS A 및 AAAA(IPv6 주소 지정을 사용하는 경우) 레코드를 가리켜야 합니다. 예를 들어 SRV 레코드가 contoso.com에 있는 경우 이 레코드가 가리키는 A 및 AAAA(IPv6 주소 지정을 사용하는 경우) 레코드는 fabrikam.com에 있을 수 없습니다.




> [!TIP]
> 기본 구성은 모든 모바일 클라이언트 트래픽이 외부 사이트를 통과하도록 지정하는 것입니다. 요구 사항에 보다 적합한 경우에는 내부 URL만 반환되도록 설정을 수정할 수 있습니다. 이 구성의 경우 사용자는 회사 네트워크 내에 있을 때만 모바일 장치에서 Lync 모바일 응용 프로그램을 사용할 수 있습니다. 이 구성을 정의하려면 <STRONG>Set-CsMcxConfiguration</STRONG> cmdlet을 사용합니다.




> [!NOTE]
> 모바일 응용 프로그램은 주소록 서비스 등의 다른 Lync Server 2013 서비스에도 연결할 수 있지만, 내부 모바일 응용 프로그램 웹 요청은 Mobility Service에 대해서만 외부 웹 FQDN으로 이동합니다. 주소록 요청 등의 다른 서비스 요청에는 이 구성이 필요하지 않습니다.



모바일 장치는 서비스를 수동으로 검색할 수 있습니다. 이 경우 각 사용자는 프로토콜과 경로를 포함하여 전체 내부/외부 자동 검색 서비스 URI로 모바일 장치 설정을 다음과 같이 구성해야 합니다.

  - https:// *\<외부 풀 FQDN\>* /Autodiscover/autodiscoverservice.svc/외부 액세스 루트

  - https:// *\<내부 풀 FQDN\>* /AutoDiscover/AutoDiscover.svc/내부 액세스 루트

가능한 경우에는 수동 검색보다 자동 검색을 사용하는 것이 좋습니다. 그러나 모바일 장치 연결 문제를 해결하려는 경우에는 수동 설정을 사용하는 것이 유용합니다.

## Lync Server를 사용하여 분할 DNS 구성

분할 DNS(split-brain DNS)는 여러 가지 이름(예: split DNS 또는 split-horizon DNS)으로 알려져 있는데, 간단히 말해 네임스페이스가 동일한 두 DNS 영역이 있는 DNS 구성을 나타냅니다. 분할 DNS의 한 DNS 영역은 내부 전용 요청을 처리하고 다른 DNS 영역은 외부 전용 요청을 처리합니다. 그러나 내부 DNS에 포함된 많은 DNS SRV 및 A 레코드가 외부 DNS에는 포함되지 않으며, 그 반대의 경우도 마찬가지입니다. 또한 같은 DNS 레코드가 내부 DNS와 외부 DNS(예: www.contoso.com)에 존재하는 경우 DNS 쿼리가 실행된 위치(내부 또는 외부)에 따라 반환되는 IP 주소가 다릅니다.


> [!IMPORTANT]
> 모바일 기능(구체적으로는 LyncDiscover 및 LyncDiscoverInternal DNS 레코드)에 대해서는 현재 분할 DNS가 지원되지 않습니다. LyncDiscover는 외부 DNS 서버에 대해 정의해야 하며 LyncDiscoverInternal은 내부 DNS 서버에 대해 정의해야 합니다.



이 항목에서는 분할 DNS라는 용어를 사용하겠습니다.

분할 DNS를 구성하는 경우 다음 내부 및 외부 영역에 각 영역에서 필요한 DNS 레코드 유형에 대한 요약이 포함됩니다. 자세한 내용은 [Lync Server 2013의 외부 사용자 액세스에 대한 시나리오](lync-server-2013-scenarios-for-external-user-access.md)를 참조하십시오.

**내부 DNS**

  - 신뢰할 수 있는 contoso.com이라는 DNS 영역을 포함합니다.

  - 내부 contoso.com 영역에는 다음이 포함됩니다.
    
      - 내부 Lync Server 2013 클라이언트 자동 구성을 위한 DNS A 및 AAAA(IPv6 주소 지정을 사용하는 경우) 및 SRV 레코드(선택 사항)
    
      - Lync Server 2013 웹 서비스 자동 검색을 위한 DNS A 및 AAAA(IPv6 주소 지정을 사용하는 경우) 및 CNAME 레코드(선택 사항)
    
      - 프런트 엔드 풀 이름, 디렉터 또는 디렉터 풀 이름 및 회사 네트워크에서 Lync Server 2013을 실행하는 모든 내부 서버에 대한 DNS A 및 AAAA(IPv6 주소 지정을 사용하는 경우) 레코드
    
      - 경계 네트워크에 있는 각 Lync Server 2013, 에지 서버의 에지 내부 인터페이스에 대한 DNS A 및 AAAA(IPv6 주소 지정을 사용하는 경우)
    
      - 경계 네트워크에 있는 각 역방향 프록시 서버의 내부 인터페이스에 대한 DNS A 및 AAAA(IPv6 주소 지정을 사용하는 경우) 레코드(역방향 프록시 관리를 위한 선택 사항)
    
      - 경계 네트워크의 모든 Lync Server 2013에지 서버 내부 에지 인터페이스는 contoso.com에 대한 쿼리를 확인하기 위해 내부 DSN 영역을 사용합니다.
    
      - 회사 네트워크에서 Lync Server 2013을 실행하는 모든 서버와 Lync 2013을 실행하는 모든 클라이언트는 contoso.com에 대한 쿼리를 확인하기 위해 내부 DSN 서버를 가리키거나 각 에지 서버에 있는 HOSTS 파일을 사용하고 다음 홉 서버, 특히 디렉터 또는 디렉터 VIP, 프런트 엔드 풀 VIP 또는 Standard Edition Server에 대한 A 및 AAAA(IPv6 주소 지정을 사용하는 경우) 레코드를 나열합니다.

**외부 DNS**

  - 신뢰할 수 있는 contoso.com이라는 DNS 영역을 포함합니다.

  - 외부 contoso.com 영역에는 다음이 포함됩니다.
    
      - Lync Server 2013 클라이언트 자동 구성을 위한 DNS A 및 AAAA(IPv6 주소 지정을 사용하는 경우) 및 SRV 레코드(선택 사항)
    
      - 모바일 기능과 함께 사용할 Lync Server 2013 웹 서비스의 자동 검색을 위한 DNS A 및 AAAA(IPv6 주소 지정을 사용하는 경우) 및 CNAME 레코드
    
      - 경계 네트워크에 있는 각 Lync Server 2013, 에지 서버 또는 하드웨어 부하 분산 장치 VIP(가상 IP)의 에지 외부 인터페이스에 대한 DNS A 및 AAAA(IPv6 주소 지정을 사용하는 경우) 및 SRV 레코드
    
      - 경계 네트워크에 있는 역방향 프록시 서버 또는 역방향 프록시 서버 풀 VIP의 외부 인터페이스에 대한 DNS A 및 AAAA(IPv6 주소 지정을 사용하는 경우) 레코드

## 분할 DNS를 사용하지 않는 자동 구성

분할 DNS를 사용하면 내부적으로 로그인한 Lync Server 2013 사용자가 내부 DNS 영역에 사용 중인 각 SIP의 \_sipinternaltls.\_tcp SRV 레코드가 포함된 경우 자동 구성을 사용할 수 있습니다. 그러나 분할 DNS를 사용하지 않는 경우에는 이 섹션의 뒷부분에 설명된 해결 방법 중 하나를 구현하지 않는 한 Lync를 실행하는 클라이언트의 내부 자동 구성이 작동하지 않습니다. Lync Server 2013에서는 사용자의 SIP URI가 자동 구성용으로 지정된 프런트 엔드 풀의 도메인과 일치해야 하기 때문입니다. 이는 이전 버전의 Communicator에서도 마찬가지였습니다.

예를 들어 두 개의 SIP 도메인을 사용 중인 경우 다음 DNS 서비스(SRV) 레코드가 필요합니다.

  - 사용자가 bob@contoso.com으로 로그인한 경우 사용자의 SIP 도메인(contoso.com)이 자동 구성 프런트 엔드 풀의 도메인과 일치하므로 자동 구성에 대해 다음 SRV 레코드가 작동합니다.
    
     \_sipinternaltls.\_tcp.contoso.com. 86400 IN SRV 0 0 5061 pool01.contoso.com

  - 사용자가 alice@fabrikam.com으로 로그인한 경우 두 번째 SIP 도메인의 자동 구성에 대해 다음 DNS SRV 레코드가 작동합니다.
    
     \_sipinternaltls.\_tcp.fabrikam.com. 86400 IN SRV 0 0 5061 pool01.fabrikam.com

반면, 사용자가 tim@litwareinc.com으로 로그인한 경우에는 클라이언트의 SIP 주소(litwareinc.com)가 풀이 있는 도메인(fabrikam.com)과 일치하지 않으므로 자동 구성에 대해 다음 DNS SRV 레코드가 작동하지 않습니다.

 \_sipinternaltls.\_tcp.litwareinc.com. 86400 IN SRV 0 0 5061 pool01.fabrikam.com

Lync를 실행하는 클라이언트에 자동 구성이 필요한 경우 다음 옵션 중 하나를 선택합니다.

  - **그룹 정책 개체**   GPO(그룹 정책 개체)를 사용하여 올바른 서버 값을 채웁니다.
    

    > [!NOTE]
    > 이 옵션은 자동 구성을 사용하지 않도록 설정하지만 수동 구성 프로세스를 자동화하므로 이 접근 방법을 사용할 경우 자동 구성과 연결된 SRV 레코드가 필요하지 않습니다.



  - **일치하는 내부 영역**   내부 DNS에 외부 DNS 영역(예: contoso.com)과 일치하는 영역을 만들고 자동 구성에 사용되는 Lync Server 2013 풀에 해당하는 DNS A 및 AAAA(IPv6 주소 지정을 사용하는 경우) 레코드를 만듭니다. 예를 들어 사용자가 pool01.contoso.net에 속해 있지만 Lync에 bob@contoso로 로그인한 경우 contoso.com이라는 내부 DNS 영역을 만들고 그 안에 pool01.contoso.com에 대한 DNS A 및 AAAA(IPv6 주소 지정을 사용하는 경우) 레코드를 만듭니다.

  - **핀 포인트 내부 영역**   내부 DNS에 전체 영역을 만드는 것이 옵션이 아닌 경우 자동 구성에 필요한 SRV 레코드에 해당하는 핀 포인트(즉, 전용) 영역을 만들고 dnscmd.exe를 사용하여 이러한 영역을 채울 수 있습니다. Dnscmd.exe는 DNS 사용자 인터페이스가 핀 포인트 영역 만들기를 지원하지 않기 때문에 필요합니다. 예를 들어 SIP 도메인이 contoso.com이고 두 개의 프런트 엔드 서버가 포함된 pool01이라는 프런트 엔드 풀이 있는 경우 내부 DNS에 다음 핀 포인트 영역과 A 레코드가 필요합니다.
    
        dnscmd . /zoneadd _sipinternaltls._tcp.contoso.com. /dsprimary
        dnscmd . /recordadd _sipinternaltls._tcp.contoso.com. @ SRV 0 0 5061 pool01.contoso.com.
        dnscmd . /zoneadd pool01.contoso.com. /dsprimary
        dnscmd . /recordadd pool01.contoso.com. @ A 192.168.10.90
        dnscmd . /recordadd pool01.contoso.com. @ AAAA <IPv6 address>
        dnscmd . /recordadd pool01.contoso.com. @ A 192.168.10.91 
        dnscmd . /recordadd pool01.contoso.com. @ AAAA <IPv6 address>
    
    환경에 두 번째 SIP 도메인(예: fabrikam.com)이 있는 경우 내부 DNS에 다음 핀 포인트 영역과 A 레코드가 필요합니다.
    
        dnscmd . /zoneadd _sipinternaltls._tcp.fabrikam.com. /dsprimary
        dnscmd . /recordadd _sipinternaltls._tcp.fabrikam.com. @ SRV 0 0 5061 pool01.fabrikam.com.
        dnscmd . /zoneadd pool01.fabrikam.com. /dsprimary
        dnscmd . /recordadd pool01.fabrikam.com. @ A 192.168.10.90
        dnscmd . /recordadd pool01.contoso.com. @ AAAA <IPv6 address>
        dnscmd . /recordadd pool01.fabrikam.com. @ A 192.168.10.91
        dnscmd . /recordadd pool01.contoso.com. @ AAAA <IPv6 address>


> [!NOTE]
> 프런트 엔드 풀 FQDN이 두 번 나타나지만 서로 다른 IP 주소를 사용합니다. 이는 DNS 부하 분산이 사용되지만 하드웨어 부하 분산이 사용되는 경우 프런트 엔드 풀 항목이 하나만 있기 때문입니다. 또한 프런트 엔드 풀 FQDN 값은 contoso.com 예와 fabrikam.com 예 간에 변경되지만 IP 주소는 동일하게 유지됩니다. 이는 SIP 도메인에서 로그인한 사용자가 자동 구성에 동일한 프런트 엔드 풀을 사용하기 때문입니다.



자세한 내용은 DMTF 블로그 문서 "Communicator 자동 구성 및 분할 DNS"( <http://go.microsoft.com/fwlink/?linkid=200707>)를 참조하십시오.


> [!NOTE]
> 각 블로그의 콘텐츠와 해당 URL은 공지 없이 변경될 수 있습니다.



## 재해 복구를 위한 DNS(Domain Name System) 구성

DNS에서 Lync Server 2013 웹 트래픽을 재해 복구 및 장애 조치(failover) 사이트로 리디렉션하도록 구성하려면 GeoDNS를 지원하는 DNS 공급자를 사용해야 합니다. 전체 프런트 엔드 풀 하나가 다운되는 경우에도 웹 서비스를 사용하는 기능이 계속 작동하도록 웹에 대한 DNS 레코드가 재해 복구를 지원하게 설정할 수 있습니다. 이 재해 복구 기능은 자동 검색(Lyncdiscover URL), 모임 및 전화 접속 단순 URL을 지원합니다.

GeoDNS 공급자에서 웹 서비스를 내부적 및 외부적으로 확인하도록 추가 DNS 호스트(A 및 AAAA(IPv6를 사용하는 경우)) 레코드를 정의하고 구성해야 합니다. 다음 표의 내용은 지리적으로 분산된 한 쌍의 풀과 공급자가 지원하는 GeoDNS를 사용하며, 라운드 로빈 DNS를 사용하거나 Pool1을 주 풀로 사용하고 통신이 끊기거나 하드웨어 오류가 발생할 경우 Pool2로 장애 조치하도록 구성하는 것으로 가정합니다.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>GeoDNS 레코드(예)</th>
<th>풀 레코드(예)</th>
<th>CNAME 레코드(예)</th>
<th>DNS 설정(한 가지 옵션 선택)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Meet-int.geolb.contoso.com</p></td>
<td><p>Pool1InternalWebFQDN.contoso.com</p>
<p>Pool2InternalWebFQDN.contoso.com</p></td>
<td><p>Pool1InternalWebFQDN.contoso.com에 대한 Meet.contoso.com 별칭</p>
<p>Pool2InternalWebFQDN.contoso.com에 대한 Meet.contoso.com 별칭</p></td>
<td><p>풀 간의 라운드 로빈</p>
<p>주 풀을 사용하고 장애 발생 시 보조 풀에 연결</p></td>
</tr>
<tr class="even">
<td><p>Meet-ext.geolb.contoso.com</p></td>
<td><p>Pool1ExternalWebFQDN.contoso.com</p>
<p>Pool2ExternalWebFQDN.contoso.com</p></td>
<td><p>Pool1ExternalWebFQDN.contoso.com에 대한 Meet.contoso.com 별칭</p>
<p>Pool2ExternalWebFQDN.contoso.com에 대한 Meet.contoso.com 별칭</p></td>
<td><p>풀 간의 라운드 로빈</p>
<p>주 풀을 사용하고 장애 발생 시 보조 풀에 연결</p></td>
</tr>
<tr class="odd">
<td><p>Dialin-int.geolb.contoso.com</p></td>
<td><p>Pool1InternalWebFQDN.contoso.com</p>
<p>Pool2InternalWebFQDN.contoso.com</p></td>
<td><p>Pool1InternalWebFQDN.contoso.com에 대한 Dialin.contoso.com 별칭</p>
<p>Pool2InternalWebFQDN.contoso.com에 대한 Dialin.contoso.com 별칭</p></td>
<td><p>풀 간의 라운드 로빈</p>
<p>주 풀을 사용하고 장애 발생 시 보조 풀에 연결</p></td>
</tr>
<tr class="even">
<td><p>Dialin-ext.geolb.contoso.com</p></td>
<td><p>Pool1ExternalWebFQDN.contoso.com</p>
<p>Pool2ExternalWebFQDN.contoso.com</p></td>
<td><p>Pool1ExternalWebFQDN.contoso.com에 대한 Dialin.contoso.com 별칭</p>
<p>Pool2ExternalWebFQDN.contoso.com에 대한 Dialin.contoso.com 별칭</p></td>
<td><p>풀 간의 라운드 로빈</p>
<p>주 풀을 사용하고 장애 발생 시 보조 풀에 연결</p></td>
</tr>
<tr class="odd">
<td><p>Lyncdiscoverint-int.geolb.contoso.com</p></td>
<td><p>Pool1InternalWebFQDN.contoso.com</p>
<p>Pool2InternalWebFQDN.contoso.com</p></td>
<td><p>Pool1InternalWebFQDN.contoso.com에 대한 Lyncdiscoverinternal.contoso.com 별칭</p>
<p>Pool2InternalWebFQDN.contoso.com에 대한 Lyncdiscoverinternal.contoso.com 별칭</p></td>
<td><p>풀 간의 라운드 로빈</p>
<p>주 풀을 사용하고 장애 발생 시 보조 풀에 연결</p></td>
</tr>
<tr class="even">
<td><p>Lyncdiscover-ext.geolb.contoso.com</p></td>
<td><p>Pool1ExternalWebFQDN.contoso.com</p>
<p>Pool2ExternalWebFQDN.contoso.com</p></td>
<td><p>Pool1ExternalWebFQDN.contoso.com에 대한 Lyncdiscover.contoso.com 별칭</p>
<p>Pool2ExternalWebFQDN.contoso.com에 대한 Lyncdiscover.contoso.com 별칭</p></td>
<td><p>풀 간의 라운드 로빈</p>
<p>주 풀을 사용하고 장애 발생 시 보조 풀에 연결</p></td>
</tr>
<tr class="odd">
<td><p>Scheduler-int.geolb.contoso.com</p></td>
<td><p>Pool1InternalWebFQDN.contoso.com</p>
<p>Pool2InternalWebFQDN.contoso.com</p></td>
<td><p>Pool1InternalWebFQDN.contoso.com에 대한 Scheduler.contoso.com 별칭</p>
<p>Pool2InternalWebFQDN.contoso.com에 대한 Scheduler.contoso.com 별칭</p></td>
<td><p>풀 간의 라운드 로빈</p>
<p>주 풀을 사용하고 장애 발생 시 보조 풀에 연결</p></td>
</tr>
<tr class="even">
<td><p>Scheduler-ext.geolb.contoso.com</p></td>
<td><p>Pool1ExternalWebFQDN.contoso.com</p>
<p>Pool2ExternalWebFQDN.contoso.com</p></td>
<td><p>Pool1ExternalWebFQDN.contoso.com에 대한 Scheduler.contoso.com 별칭</p>
<p>Pool2ExternalWebFQDN.contoso.com에 대한 Scheduler.contoso.com 별칭</p></td>
<td><p>풀 간의 라운드 로빈</p>
<p>주 풀을 사용하고 장애 발생 시 보조 풀에 연결</p></td>
</tr>
</tbody>
</table>


## DNS 부하 분산

DNS 부하 분산은 일반적으로 응용 프로그램 수준에서 구현됩니다. 응용 프로그램(예: Lync를 실행하는 클라이언트)에서는 풀 FQDN(정규화된 도메인 이름)에 대한 DNS A 및 AAAA(IPv6 주소 지정을 사용하는 경우) 레코드 쿼리에서 반환되는 IP 주소 중 하나에 연결하여 풀의 서버에 연결합니다.

예를 들어 pool01.contoso.com이라는 풀에 세 개의 프런트 엔드 서버가 있는 경우 다음과 같은 상황이 발생합니다.

  - Lync을 실행하는 클라이언트는 DNS에서 pool01.contoso.com을 쿼리하며, 이 쿼리는 세 개의 IP 주소를 반환하여 다음과 같이 캐시합니다(순서에 관계없음).
    
    pool01.contoso.com      192.168.10.90
    
    pool01.contoso.com      192.168.10.91
    
    pool01.contoso.com      192.168.10.92

  - 그러면 클라이언트에서 IP 주소 중 하나에 대한 TCP(Transmission Control Protocol) 연결을 설정합니다. 연결에 실패하면 캐시의 다음 IP 주소에 연결합니다.

  - TCP 연결에 성공하면 클라이언트에서 TLS와 협상하여 pool01.contoso.com의 기본 등록자에 연결합니다.

  - 캐시의 항목 연결에 모두 성공하지 못한 경우 사용자에게 지금은 Lync Server 2013 실행 서버를 사용할 수 없다는 알림이 제공됩니다.


> [!NOTE]
> DNS 기반 부하 분산은 DNS RR(DNS 라운드 로빈)과 다릅니다. DNS RR은 일반적으로 DNS를 기반으로 풀의 서버에 해당하는 다른 순서의 IP 주소를 제공하는 부하 분산을 참조합니다. 또한 DNS RR은 일반적으로 부하 분산만 지원하고 장애 조치는 지원하지 않습니다. 예를 들어 DNS A 및 AAAA(IPv6 주소 지정을 사용하는 경우) 쿼리에서 반환된 IP 주소 중 하나에 대한 연결에 실패하면 연결되지 않습니다. 따라서 DNS 라운드 로빈 자체는 DNS 기반 부하 분산보다 안정적이지 않습니다. DNS 라운드 로빈을 DNS 부하 분산과 함께 사용할 수 있습니다.



DNS 부하 분산은 다음에 사용됩니다.

  - 서버 간 SIP를 에지 서버에 부하 분산

  - 회의 자동 길잡이, 응답 그룹 및 통화 대기와 같은 UCAS(Unified Communications Application Services) 응용 프로그램 부하 분산

  - UCAS 응용 프로그램에 대한 새 연결 방지("드레이닝"이라고도 함)

  - 클라이언트와 에지 서버 간의 모든 클라이언트-서버 트래픽 부하 분산

DNS 부하 분산은 다음에 사용할 수 없습니다.

  - 디렉터 또는프런트 엔드 서버에 대한 클라이언트-서버 웹 트래픽

DNS 부하 분산 및 페더레이션 트래픽

DNS SRV 쿼리에서 여러 개의 DNS 레코드가 반환되는 경우 액세스 에지 서비스는 항상 숫자 우선 순위는 가장 낮고 가중치는 가장 큰 DNS SRV 레코드를 선택합니다. Internet Engineering Task Force 문서 "서비스 위치 지정을 위한 DNS RR(DNS SRV)"( <http://www.ietf.org/rfc/rfc2782.txt>)에서는 DNS SRV 레코드가 여러 개 정의된 경우 우선 순위가 먼저 사용된 다음 가중치가 사용된다고 지정되어 있습니다. 예를 들어 DNS SRV 레코드 A의 가중치가 20, 우선 순위가 40이고 DNS SRV 레코드 B의 가중치는 10, 우선 순위는 50이라고 가정해 보겠습니다. 이 경우 우선 순위가 40인 DNS SRV 레코드 A가 선택됩니다. DNS SRV 레코드 선택 시에는 다음 규칙이 적용됩니다.

  - 우선 순위를 먼저 고려합니다. 클라이언트는 연결 가능한 가장 낮은 숫자 우선 순위의 DNS SRV 레코드로 정의된 대상 호스트에 연결을 시도해야 합니다. 대상의 우선 순위가 같은 경우에는 가중치 필드로 정의된 순서로 연결을 시도해야 합니다.

  - 가중치 필드는 우선 순위가 같은 항목의 상대 가중치를 지정합니다. 가중치가 클수록 그에 비례하여 선택될 가능성도 커집니다. DNS 관리자는 서버를 선택하지 않는 경우 가중치로 0을 사용해야 합니다. 가중치가 0보다 큰 레코드가 있으면 가중치가 0인 레코드가 선택될 확률은 매우 낮습니다.

우선 순위와 가중치가 동일한 여러 DNS SRV 레코드가 반환되는 경우 액세스 에지 서비스는 DNS 서버에서 가장 먼저 반환된 SRV 레코드를 선택합니다.

