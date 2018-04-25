---
title: 'Lync Server 2013: 고급 9-1-1 구성'
TOCTitle: 고급 9-1-1 구성
ms:assetid: 5967de00-c8b9-4923-86da-6ad3369a4cad
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398390(v=OCS.15)
ms:contentKeyID: 49303724
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 고급 9-1-1 구성

 

_**마지막으로 수정된 항목:** 2013-02-24_

E9-1-1(고급 9-1-1)은 발신자의 전화 번호와 주소 또는 번지를 연결하는 응급 알림 기능입니다. 이 정보를 사용하여 PSAP(Public Safety Answering Point)는 긴급 상황에 처한 발신자에게 즉시 긴급 서비스를 보낼 수 있습니다.

E9-1-1을 지원하려면 Lync Server 2013에서 위치를 클라이언트와 정확하게 연결한 다음 해당 정보를 사용하여 긴급 통화를 가장 가까운 PSAP에 라우팅할 수 있어야 합니다.

E9-1-1 배포 계획에 대한 자세한 내용은 [Lync Server 2013의 응급 서비스 계획(E9-1-1)](lync-server-2013-planning-for-emergency-services-e9-1-1.md)를 참조하십시오.


> [!IMPORTANT]
> Lync Server 2013은 미국 내에서만 E9-1-1을 지원합니다. E9-1-1을 배포하려면 적격한 E9-1-1 서비스 공급자에 대한 SIP 연결을 구성하거나 PSTN(공중 전화망) 기반 E9-1-1 서비스 공급자에 ELIN(emergency location identification number) 게이트웨이를 배포해야 합니다. 자세한 내용은 <A href="lync-server-2013-enhanced-9-1-1-e9-1-1-and-mediation-server.md">Lync Server 2013의 E9-1-1(고급 9-1-1) 및 중재 서버</A>를 참조하십시오. 트렁크 연결 구성에 대한 자세한 내용은 <A href="lync-server-2013-configure-a-trunk-with-media-bypass.md">Lync Server 2013에서 미디어 바이패스로 트렁크 구성</A>을 참조하십시오.



## 이 단원의 내용

  - [Lync Server 2013에서 E9-1-1 음성 경로 구성](lync-server-2013-configure-an-e9-1-1-voice-route.md)

  - [Lync Server 2013에서 위치 정책 만들기](lync-server-2013-create-location-policies.md)

  - [Lync Server 2013에서 E9-1-1에 대한 사이트 정보 구성](lync-server-2013-configure-site-information-for-e9-1-1.md)

  - [Lync Server 2013에서 위치 데이터베이스 구성](lync-server-2013-configure-the-location-database.md)

  - [Lync Server 2013에서 고급 E9-1-1 기능 구성](lync-server-2013-configure-advanced-e9-1-1-features.md)

