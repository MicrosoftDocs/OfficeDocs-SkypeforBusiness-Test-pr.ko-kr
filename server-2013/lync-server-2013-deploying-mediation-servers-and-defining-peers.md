---
title: 'Lync Server 2013: 중재 서버 배포 및 피어 정의'
TOCTitle: 중재 서버 배포 및 피어 정의
ms:assetid: a684f1da-6671-4011-adf6-2db49e2528e2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412780(v=OCS.15)
ms:contentKeyID: 49304635
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 중재 서버 배포 및 피어 정의

 

_**마지막으로 수정된 항목:** 2012-09-21_

Enterprise Voice 작업, 전화 접속 회의 및 고급 Enterprise Voice 응용 프로그램( 응답 그룹 응용 프로그램, 통화 대기 응용 프로그램, CAC(통화 허용 제어) 등)은 프런트 엔드 풀에서 제공됩니다. Lync Server 2013에서는 중재 서버의 기능이 프런트 엔드 서버에 기본 제공됩니다. 별도의 독립 실행형 중재 서버가 더 이상 필요 없습니다. 프런트 엔드 풀에서 지원되는 게이트웨이(PSTN(공중 전화망) 또는 IP-PBX)와 직접 통신할 수 있으므로 중계자 역할을 위한 중재 서버를 사용할 필요가 없습니다.

단, ITSP(인터넷 전화 통신 서비스 공급자)에 대한 SBC(세션 경계 컨트롤러)에 연결하도록 SIP 트렁크를 구성하는 경우는 예외입니다. Enterprise Voice 인프라를 SIP 트렁크 공급자에 연결하려면 별도의 중재 서버를 배포해야 합니다.

Lync Server( 프런트 엔드 풀의 중재 서버 구성 요소 또는 독립 실행형 중재 서버)와 게이트웨이 간의 연결은 *트렁크* 라고 하는 논리적 연결로 정의됩니다. 이 섹션의 항목은 트렁크를 정의하는 방법과 SIP 트렁크에 연결하기 위해 독립 실행형 중재 서버를 배포하는 방법에 대해 설명합니다.

## 이 단원의 내용

  - [Lync Server 2013의 토폴로지 작성기에서 중재 서버 정의](lync-server-2013-define-a-mediation-server-in-topology-builder.md)

  - [Lync Server 2013의 토폴로지 작성기에서 게이트웨이 정의](lync-server-2013-define-a-gateway-in-topology-builder.md)

  - [Lync Server 2013에서 중재 서버용 파일 설치](lync-server-2013-install-the-files-for-mediation-server.md)

  - [Lync Server 2013의 토폴로지 작성기에서 추가 트렁크 정의](lync-server-2013-define-additional-trunks-in-topology-builder.md)

## 관련 단원

[Lync Server 2013에서 전화 접속 회의 구성](lync-server-2013-configuring-dial-in-conferencing.md)

