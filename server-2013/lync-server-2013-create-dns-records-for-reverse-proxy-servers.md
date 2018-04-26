---
title: 'Lync Server 2013: 역방향 프록시 서버에 대한 DNS 레코드 만들기'
TOCTitle: 역방향 프록시 서버에 대한 DNS 레코드 만들기
ms:assetid: b3513339-e49b-4665-80f1-b5a1c81a0e2e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg429719(v=OCS.15)
ms:contentKeyID: 49304772
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 역방향 프록시 서버에 대한 DNS 레코드 만들기

 

_**마지막으로 수정된 항목:** 2013-03-29_

[Lync Server 2013에서 에지 지원에 대한 DNS 구성](lync-server-2013-configure-dns-for-edge-support.md)에서 설명된 대로 Microsoft Internet Security and Acceleration(ISA) Server 2006 SP1, Forefront Threat Management Gateway 2010 Server 또는 Internet Information Server Application Request Routing의 공용 외부 인터페이스를 가리키는 외부 DNS A 레코드를 만듭니다. 각 풀의 외부 웹 서비스 FQDN, 디렉터( 디렉터 풀) 및 단순한 각 URL에 대한 DNS 레코드가 필요합니다.

클라이언트의 역방향 프록시 확인을 위한 최소한의 DNS 레코드를 위해 다음 레코드를 만들어야 합니다.

  - 디렉터 및 디렉터 풀에 대한 게시된 외부 웹 서비스를 정의하는 호스트 (A) 레코드(예: **webdirext.contoso.com** )

  - 프런트 엔드 풀 및 Standard Edition 서버 역할에 호스트되는 외부 웹 서비스를 위한 게시된 외부 웹 서비스를 정의하는 호스트 (A) 레코드(예: **webext.contoso.com** )

  - 단순 URL에 대한 호스트 (A) 레코드(예: **dialin.contoso.com** 및 **meet.contoso.com** )

  - Lync Discover External 레코드에 대한 호스트(A) 레코드. 또한 Lync Web App, 스케줄러 및 모바일 기능(예: **lyncdiscover.contoso.com** )을 비롯한 모든 Web Apps에 대한 자동 검색 포인터를 제공합니다.

  - Office Web Apps 서버 URL에 대한 호스트 (A) 레코드(예: **officewebapp01.contoso.com** )

자세한 내용은 [Lync Server 2013의 DNS 요약 - 역방향 프록시](lync-server-2013-dns-summary-reverse-proxy.md)을 참고하세요.

