---
title: Lync Server 2013의 자동 검색 계획
TOCTitle: Lync Server 2013의 자동 검색 계획
ms:assetid: 51f1ff94-1d64-4e6d-a878-b86fa07edc2d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ945628(v=OCS.15)
ms:contentKeyID: 52056857
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 자동 검색 계획

 

_**마지막으로 수정된 항목:** 2013-02-16_

자동 검색은 Lync Server 2010용 누적 업데이트(2011년 11월)에서 Lync Server용으로 도입되었습니다. 이 초기 자동 검색 구현은 기본적으로 Lync Mobile에서 Mobility Service(Mcx)를 찾는 방법을 제공하는 용도로 사용되었습니다. 이제 Lync Server 2013의 자동 검색 서비스는 모든 클라이언트가 서버 및 사용자 서비스를 찾는 데 사용되는 서비스입니다. Microsoft Lync Server 2013 자동 검색 서비스는 디렉터 및 프런트 엔드 서버에서 실행됩니다.


> [!TIP]
> 자동 검색 및 클라이언트로의 통신 내용에 대한 자세한 기술 정보는 <A href="lync-server-2013-understanding-autodiscover.md">Lync Server 2013의 자동 검색 이해</A>를 참조하십시오.<BR>이처럼 서비스의 용도는 바뀌었지만 모바일 기능은 여전히 가장 대표적인 시나리오이며 이 시나리오에서는 계속해서 몇 가지 특별한 계획이 필요합니다. 자세한 내용은 <A href="lync-server-2013-planning-for-mobility.md">Lync Server 2013의 모바일 기능 계획</A>을 참조하십시오.



Lync Server 2010에 자동 검색이 도입되었을 때는 서비스를 구현하기 위해 보안이 저하되는 설정을 적용해야 했으며, 이로 인해 기존 서버 배포의 인증서를 변경해야 할 수 있었습니다. 자동 검색은 HTTPS의 경우 TCP 443 포트에서, HTTP의 경우 TCP 80 포트에서 사용할 수 있습니다. HTTPS를 사용하려는 경우 역방향 프록시, 디렉터 및 프런트 엔드 서버의 인증서를 다시 발급하여 필요한 `lyncdiscover.<도메인>` 및 `lyncdiscoverinternal.<도메인>` DNS 레코드를 포함해야 했습니다. HTTP를 사용하려는 경우에는 DNS CNAME 또는 별칭 레코드를 통해 인증서의 기존 이름을 사용하면 인증서를 다시 발급하지 않아도 됩니다. 그러나 HTTP 사용 시에는 초기 통신이 암호화되지 않습니다.

Lync Server 2013에서는 모든 클라이언트에 대해 자동 검색을 사용하므로 기본적으로 항상 HTTPS만 사용되며 역방향 프록시, 디렉터 및 프런트 엔드 서버의 구성 일부로 lyncdiscover.\<도메인\>을 사용하여 인증서를 만듭니다. Lync Server 2010에서 업그레이드된 배포에서 자동 검색을 구현하는 경우에는 인증서를 다시 발급하지 않아도 되도록 HTTP를 사용할 수 있습니다. 다음 섹션에는 이 두 시나리오에 대한 지침이 제공됩니다.


> [!IMPORTANT]
> 외부 웹 서비스 게시 규칙에서 사용하는 인증서의 주체 대체 이름 목록에는 조직 내의 각 SIP 도메인에 대한 <EM>lyncdiscover.&lt;SIP 도메인&gt;</EM> 항목이 포함되어 있어야 합니다. 디렉터, 프런트 엔드 서버 및 역방향 프록시에 필요한 주체 대체 이름 항목에 대한 자세한 내용은 <A href="lync-server-2013-certificate-summary-autodiscover.md">인증서 요약 - 자동 검색</A>을 참조하십시오.



## 이 단원의 내용

  - [인증서 요약 - 자동 검색](lync-server-2013-certificate-summary-autodiscover.md)

  - [포트 요약 - Lync Server 2013에서 자동 검색](lync-server-2013-port-summary-autodiscover.md)

  - [DNS 요약 - Lync Server 2013에서 자동 검색](lync-server-2013-dns-summary-autodiscover.md)

  - [하이브리드 및 분할 도메인 - 자동 검색](lync-server-2013-hybrid-and-split-domain-autodiscover.md)

