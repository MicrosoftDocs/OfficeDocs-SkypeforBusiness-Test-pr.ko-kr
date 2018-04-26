---
title: 중재 서버 마이그레이션
TOCTitle: 중재 서버 마이그레이션
ms:assetid: b0b77121-2c8f-413e-b276-dbf1038361d3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205173(v=OCS.15)
ms:contentKeyID: 49304741
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 중재 서버 마이그레이션

 

_**마지막으로 수정된 항목:** 2012-09-28_

병합 마법사를 실행하면 중재 서버가 Lync Server 2013 파일럿 토폴로지에 병합됩니다. 하지만 Office Communications Server 2007 R2 풀이 Lync Server 2013 중재 서버와 통신할 수 없으므로 모든 사용자가 마이그레이션된 다음에 Lync Server 2013 중재 서버를 구성해야 합니다. 단계별 마이그레이션 중에는 Lync Server 2013 풀이 Office Communications Server 2007 R2 중재 서버와 통신합니다.

Lync Server 2013 중재 서버를 구성할 때는 Office Communications Server 2007 R2 게이트웨이도 업그레이드하거나 교체해야 합니다. Office Communications Server 2007 R2 게이트웨이는 Lync Server 2013 중재 서버를 지원하지 않습니다. Lync Server 2013에 대해 인증된 게이트웨이를 배포하고 이를 Lync Server 2013 중재 서버와 연결해야 합니다. Office Communications Server 2007 R2 배포를 완전히 해제하려면 이 단계를 먼저 수행해야 합니다.

이 섹션의 항목에서는 Lync Server 2013 중재 서버 마이그레이션을 완료한 후 수행해야 하는 구성 작업에 대해 설명합니다. 배치된 중재 서버를 독립 실행형 중재 서버로 변환하는 작업은 선택적으로 수행할 수 있습니다.

  - [중재 서버 구성](configure-mediation-server.md)

  - [새 Lync Server 2013 중재 서버를 사용하도록 음성 경로 변경](change-voice-routes-to-use-the-new-lync-server-2013-mediation-server.md)

  - [배치된 중재 서버를 독립 실행형 중재 서버로 전환(선택 사항)](transition-a-collocated-mediation-server-to-a-stand-alone-mediation-server-optional.md)

