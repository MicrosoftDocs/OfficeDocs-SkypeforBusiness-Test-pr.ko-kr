---
title: DNS(도메인 이름 시스템) 요구 사항
TOCTitle: DNS(도메인 이름 시스템) 요구 사항
ms:assetid: 586cf18e-0080-4eb1-aee5-56843277fdfc
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398386(v=OCS.15)
ms:contentKeyID: 49303701
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# DNS(도메인 이름 시스템) 요구 사항

 

_**마지막으로 수정된 항목:** 2012-06-18_

Lync Server를 배포하려면 클라이언트 및 서버 검색을 사용하도록 설정하는 DNS(Domain Name System) 레코드를 만들어야 하며, 원하는 경우 자동 클라이언트 로그인도 지원해야 합니다(조직에서 지원하려는 경우).

Lync Server에서는 다음과 같은 방식으로 DNS가 사용됩니다.

  - 서버 간 통신을 위한 내부 서버 또는 풀을 검색합니다.

  - 클라이언트가 다양한 SIP 트랜잭션에 사용되는 프런트 엔드 풀 또는 Standard Edition 서버를 검색할 수 있도록 합니다.

  - 로그온하지 않은 UC(통합 통신) 장치가 장치 업데이트 웹 서비스를 실행하는 프런트 엔드 풀 또는 Standard Edition 서버를 검색하고 업데이트를 가져오고 로그를 보낼 수 있도록 합니다.

  - 외부 서버 및 클라이언트가 IM(인스턴트 메시징) 또는 회의를 위해 에지 서버 또는 HTTP 역방향 프록시에 연결할 수 있도록 합니다.

  - 외부 UC 장치가 에지 서버 또는 HTTP 역방향 프록시를 통해 장치 업데이트 웹 서비스에 연결하고 업데이트를 가져올 수 있도록 합니다.

  - 사용자가 장치 설정에 URL을 수동으로 입력할 필요 없이 모바일 클라이언트가 웹 서비스 리소스를 자동으로 검색할 수 있도록 합니다.

## 이 단원의 내용

  - [Lync Server 2013에 대한 DNS 요구 사항 확인](lync-server-2013-determine-dns-requirements.md)

  - [프런트 엔드 풀에 대한 DNS 요구 사항](lync-server-2013-dns-requirements-for-front-end-pools.md)

  - [Standard Edition Server에 대한 DNS 요구 사항](lync-server-2013-dns-requirements-for-standard-edition-servers.md)

  - [Lync Server 2013의 단순 URL에 대한 DNS 요구 사항](lync-server-2013-dns-requirements-for-simple-urls.md)

  - [Lync Server 2013의 자동 클라이언트 로그인에 대한 DNS 요구 사항](lync-server-2013-dns-requirements-for-automatic-client-sign-in.md)

  - [모바일 기능에 대한 DNS 요구 사항](lync-server-2013-dns-requirements-for-mobility.md)

  - [Lync Server 2013의 DNS 부하 분산](lync-server-2013-dns-load-balancing.md)

