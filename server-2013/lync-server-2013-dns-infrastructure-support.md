---
title: 'Lync Server 2013: DNS 인프라 지원'
TOCTitle: DNS(Domain Name System) 인프라 지원
ms:assetid: 37777c16-94ce-436d-b517-bcf53a564513
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425850(v=OCS.15)
ms:contentKeyID: 49303307
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 DNS 인프라 지원

 

_**마지막으로 수정된 항목:** 2013-03-08_

Lync Server 2013에서는 DNS(Domain Name System)가 필요하며, 다음과 같은 방식으로 DNS를 사용합니다.

  - 서버 간 통신을 위한 내부 서버 또는 풀을 검색합니다.

  - 클라이언트가 다양한 SIP 트랜잭션에 사용되는 프런트 엔드 풀 또는 Standard Edition 서버를 검색할 수 있도록 합니다.

  - 회의용 단순 URL을 해당 회의를 호스팅하는 서버에 연결합니다.

  - 외부 서버 및 클라이언트가 IM(인스턴트 메시징) 또는 회의를 위해 에지 서버 또는 HTTP 역방향 프록시에 연결할 수 있도록 합니다.

  - 로그인하지 않은 UC(통합 통신) 장치가 장치 업데이트 웹 서비스를 실행하는 프런트 엔드 풀이나 Standard Edition 서버를 검색하고 업데이트를 가져오고 로그를 보낼 수 있도록 합니다.

  - 사용자가 장치 설정에 URL을 수동으로 입력할 필요 없이 모바일 클라이언트가 웹 서비스 리소스를 자동으로 검색할 수 있도록 합니다.

  - DNS 부하 분산에 사용합니다.


> [!NOTE]
> Lync Server 2013에서는 IDN(다국어 도메인 이름)은 지원하지 않습니다.




> [!IMPORTANT]
> 지정하는 이름은 서버에 구성된 컴퓨터 이름과 동일해야 합니다. 기본적으로 도메인에 가입되지 않은 컴퓨터의 컴퓨터 이름은 FQDN이 아닌 짧은 이름입니다. 토폴로지 작성기에서는 짧은 이름이 아닌 FQDN을 사용합니다. 따라서 도메인에 가입되지 않은 에지 서버로 배포할 컴퓨터의 이름에 DNS 접미사를 구성해야 합니다. Lync Server, 에지 서버, 풀의 FQDN을 지정할 때는 <STRONG>표준 문자만 사용하세요</STRONG>(A-Z, a-z, 0-9 및 하이픈 포함). 유니코드 문자 또는 밑줄을 사용해서는 안 됩니다. URL 또는 FQDN에 비표준 문자가 포함된 경우 외부 DNS 및 공용 CA에서 지원되지 않는 경우(인증서의 주체 이름 또는 주체 대체 이름에 URL 또는 FQDN을 할당해야 하는 경우)가 많습니다.


