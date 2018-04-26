---
title: 자동 검색 지원 구성
TOCTitle: 자동 검색 지원 구성
ms:assetid: 3a266456-69a0-4539-ba99-d388b83799a8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ945622(v=OCS.15)
ms:contentKeyID: 52056839
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 자동 검색 지원 구성

 

_**마지막으로 수정된 항목:** 2013-01-21_

Lync Server 웹 서비스 **자동 검색 서비스**는 Lync Server 2010 누적 업데이트(2011년 11월)에서 처음으로 제공되었습니다. 이 업데이트는 Lync Mobile 클라이언트 최초 릴리스에 포함되었습니다. 자동 검색 서비스는 Mcx 서비스라는 Mobility Service를 제공했습니다.

자동 검색 서비스는 모든 클라이언트가 사용 가능한 서비스 및 기능과 해당 서비스에 연결하는 방법(FQDN(정규화된 도메인 이름) 또는 웹 URL(Uniform Resource Locator) 참조 사용)에 대한 정보를 요청하는 단일 위치로 작동합니다. 자동 검색을 통해 여러 기능이 표시되며, 각 클라이언트는 사용할 수 있는 기능에 따라 요청을 합니다. 예를 들어 데스크톱 Lync 2013 클라이언트는 자동 검색을 사용하여 외부 웹 서비스를 확인하지만 Mobility Service(Mcx)는 사용하지 않습니다. 클라이언트가 사용 가능한 기능을 사용하도록 올바르게 정의 및 설정하려면 클라이언트가 자동 검색 항목을 효율적으로 찾아서 사용하도록 허용하는 시나리오를 정의해야 합니다. 자동 검색을 사용하려면 배포에서 역방향 프록시가 Lync Server 웹 서비스를 게시해야 하고, Lync Server 자동 검색 서비스 및 Lync Server 웹 서비스에 대한 DNS 쿼리를 확인하도록 DNS 레코드를 구성해야 하며, 특정 시나리오에 대해 인증서 서비스를 적절하게 구성해야 합니다.


> [!TIP]
> 자동 검색 요청/응답 내의 요소가 수행하는 작업에 대한 자세한 내용은 <A href="lync-server-2013-understanding-autodiscover.md">Lync Server 2013의 자동 검색 이해</A>를 참조하십시오.



다음 정보와 표는 자동 검색 서비스를 완전하고 효율적으로 사용하기 위해 구현해야 하는 시나리오별 구성(있는 경우)을 정의합니다. 아래 항목의 정보는 Microsoft Lync Server 2013에 적용됩니다. Lync Server 2010에 대해 모바일 기능을 계획하는 방법에 대한 지침은 <http://go.microsoft.com/fwlink/?linkid=275113>를 참조하십시오. Lync Server 2010에 대해 모바일 기능을 배포하려면 <http://go.microsoft.com/fwlink/?linkid=275114>를 참조하십시오.

## 이 단원의 내용

  - [자동 검색용 DNS 구성](lync-server-2013-configuring-dns-for-autodiscover.md)

  - [자동 검색용 인증서 구성](lync-server-2013-configuring-certificates-for-autodiscover.md)

  - [자동 검색용 역방향 프록시 구성](lync-server-2013-configuring-a-reverse-proxy-for-autodiscover.md)

  - [하이브리드 배포용 자동 검색 구성](lync-server-2013-configuring-autodiscover-for-hybrid-deployments.md)

