---
title: 'Lync Server 2013: 인터트렁크 라우팅'
TOCTitle: 인터트렁크 라우팅
ms:assetid: d3a33b4a-8bf4-4a8c-a371-8ef79e740780
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205272(v=OCS.15)
ms:contentKeyID: 49305143
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 인터트렁크 라우팅

 

_**마지막으로 수정된 항목:** 2012-10-20_

Lync Server 2013은 IP-PBX와 PSTN(공중 전화망) 게이트웨이를 상호 연결하여 PBX 전화의 통화를 PSTN으로 라우팅하고 수신 PSTN 호출은 PBX(Private Branch Exchange) 전화로 라우팅될 수 있습니다. 마찬가지로, Lync Server 2013을 둘 이상의 IP-PBX 시스템을 상호 연결하여 서로 다른 IP-PBX 시스템에서 PBX 전화 간에 통화를 배치하고 수신할 수 있습니다.

트렁크 간 라우팅 기능은 새 매개 변수 PstnUsages와 함께 Lync Server 관리 셸 cmdlet인 **set-cstrunkconfiguration**을 사용하여 구성할 수 있습니다. 이 매개 변수는 사용할 PSTN 사용 레코드 집합을 지정합니다. 트렁크는 이 PSTN 사용 정보를 사용하여 경로를 결정하고 모든 수신 통화를 그에 따라 라우팅합니다.

    set-cstrunkconfiguration -Identity <TrunkId> -PstnUsages @{add="<UsageString>"}

다음 다이어그램은 Lync Server 2013에서 제공하는 PSTN 게이트웨이 및 IP-PBX 간 상호 연결에 대해 보여줍니다.

**게이트웨이 및 IP PBX 사이의 트렁크 간 라우팅**

![Lync Server 연결 PSTN 게이트웨이/IP-PBX 다이어그램](images/JJ721940.cc3858ca-2ee3-4d51-8a51-db078366b50b(OCS.15).jpg "Lync Server 연결 PSTN 게이트웨이/IP-PBX 다이어그램")

다음 다이어그램은 두 IP-PBX 시스템을 상호 연결하는 Lync Server 2013에 대해 보여줍니다.

**두 IP PBX 사이의 트렁크 간 라우팅**

![Lync Server 상호 연결 IP-PAX 시스템 다이어그램](images/JJ721940.6ba18ec9-df70-498a-9cf7-7fc41e5ec432(OCS.15).jpg "Lync Server 상호 연결 IP-PAX 시스템 다이어그램")

