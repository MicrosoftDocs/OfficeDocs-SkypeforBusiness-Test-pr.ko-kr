---
title: 'Lync Server 2013: 인터트렁크 라우팅'
TOCTitle: 인터트렁크 라우팅
ms:assetid: f687a548-1f2e-48ed-9745-a13dc1f3698f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721940(v=OCS.15)
ms:contentKeyID: 49886062
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 인터트렁크 라우팅

 

_**마지막으로 수정된 항목:** 2012-10-08_

Lync Server 2013에서는 트렁크 간 라우팅 지원을 통해 기본 세션 관리를 제공합니다. 이 새로운 기능을 사용하면 Lync Server에서 다운스트림 전화 시스템에 통화 제어 기능을 제공할 수 있습니다. 트렁크 간 라우팅은 IP-PBX를 PSTN(공중 전화망) 게이트웨이에 상호 연결할 수 있으므로 PBX(Private Branch eXchange) 전화의 통화를 PSTN으로 라우팅하고 들어오는 PSTN 통화를 PBX 전화로 라우팅할 수 있습니다. 마찬가지로 Lync Server에서는 두 개 이상의 IP-PBX 시스템을 서로 연결할 수 있으므로 서로 다른 IP-PBX 시스템 간에 전화를 발신 및 수신할 수 있습니다.

다음 그림은 PSTN 게이트웨이와 IP-PBX 간 상호 연결을 제공하는 Lync Server 2013을 보여 줍니다.

![Lync Server 연결 PSTN 게이트웨이/IP-PBX 다이어그램](images/JJ721940.cc3858ca-2ee3-4d51-8a51-db078366b50b(OCS.15).jpg "Lync Server 연결 PSTN 게이트웨이/IP-PBX 다이어그램")

다음 그림은 두 IP-PBX 시스템을 연결하는 Lync Server 2013을 보여 줍니다.

![Lync Server 상호 연결 IP-PAX 시스템 다이어그램](images/JJ721940.6ba18ec9-df70-498a-9cf7-7fc41e5ec432(OCS.15).jpg "Lync Server 상호 연결 IP-PAX 시스템 다이어그램")

