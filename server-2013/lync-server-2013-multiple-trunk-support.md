---
title: 'Lync Server 2013: 여러 트렁크 지원'
TOCTitle: 여러 트렁크 지원
ms:assetid: a1309c09-ad9a-4c54-9650-4e3f5b2a4a00
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205127(v=OCS.15)
ms:contentKeyID: 49304571
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 여러 트렁크 지원

 

_**마지막으로 수정된 항목:** 2012-11-01_

Lync Server 2013 기능은 게이트웨이와 중재 서버 간의 여러 연결을 지원합니다. 이러한 연결은 중재 서버 풀과 PSTN(공중 전화망) 게이트웨이, SBC(세션 경계 컨트롤러) 또는 IP-PBX 간의 논리적 연결인 트렁크를 정의하여 이루어집니다. 게이트웨이를 중재 서버와 연결하는 트렁크를 정의하려면 토폴로지 작성기를 사용합니다.

  - Lync Server 2013에서 트렁크를 할당하거나 제거하려면 먼저 토폴로지 작성기에서 트렁크를 정의해야 합니다. 트렁크는 중재 서버 FQDN(정규화된 도메인 이름), 중재 서버 수신 포트, 게이트웨이 FQDN 및 게이트웨이 수신 포트 연결로 구성됩니다.

  - 여러 트렁크를 구성하기 위해 동일한 게이트웨이와 중재 서버 간에 여러 연결을 만들 수 있습니다. 이는 Enterprise Voice 인프라의 복원력을 향상시키며 특히 PBX(Private Branch Exchange) 상호 운용 시나리오에 유용합니다.

트렁크를 정의할 때는 경로에 연결해야 합니다. 트렁크를 경로에 연결하려면 토폴로지 작성기에서 트렁크의 단순 이름을 정의합니다. 이 단순 이름은 트렁크를 경로와 연결할 수 있는 Lync Server 제어판에서 트렁크 이름으로 사용되며, Lync Server 관리 셸에서 게이트웨이 이름으로 사용됩니다.

    New-CsVoiceRoute -Identity <RouteId> -NumberPattern <String> -PstnUsages @{add="<UsageString>"} -PstnGatewayList @{add="<TrunkSimpleName>"}

관리자는 중재 서버와 연결된 기본 트렁크를 선택해야 합니다. 토폴로지 작성기에서 연결된 중재 서버를 마우스 오른쪽 단추로 클릭하고 **속성** 을 클릭한 후 중재 서버의 기본 게이트웨이를 지정합니다.

다음 다이어그램에서는 각 중재 서버 및 게이트웨이에 대해 정의된 여러 트렁크를 보여 줍니다.

**M-N 트렁크 라우팅**

![여러 트렁크 할당.](images/JJ205127.c61cd9a7-d8d9-4e02-83b9-ab62519a48c4(OCS.15).jpg "여러 트렁크 할당.")

