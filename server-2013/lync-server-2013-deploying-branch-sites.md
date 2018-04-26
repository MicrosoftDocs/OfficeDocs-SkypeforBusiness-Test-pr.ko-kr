---
title: 'Lync Server 2013: 분기 사이트 배포'
TOCTitle: 분기 사이트 배포
ms:assetid: 1475dee0-66ae-4ee5-b6f1-7409b4bbff45
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398217(v=OCS.15)
ms:contentKeyID: 49302891
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 분기 사이트 배포

 

_**마지막으로 수정된 항목:** 2012-09-21_

분기 사이트 사용자는 대부분의 Lync Server 2013 기능을 분기 사이트가 연결된 중앙 사이트의 서버에서 가져옵니다. 각 분기 사이트는 정확히 하나의 중앙 사이트에 연결됩니다. 공중 전화망(PSTN)과의 통화 기능을 제공하기 위해 분기 사이트는 다음 항목을 포함할 수 있습니다.

  - PSTN 게이트웨이 및 중재 서버

  - SIP 트렁크

  - PBX(Private Branch Exchange)와의 기존 음성 인프라

  - SBA(Survivable Branch Appliance)

  - 지속 가능 분기 서버

SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버가 있는 분기 사이트의 경우 광역 네트워크 또는 중앙 사이트 오류 시 이러한 솔루션 중 하나가 없는 분기 사이트에 비해 보다 쉽게 복구할 수 있습니다. 예를 들어 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버가 배포된 사이트에서 사용자는 분기 사이트를 중앙 사이트에 연결하는 네트워크가 다운되어도 PSTN 전화를 걸고 받을 수 있습니다. 분기 사이트에서 Lync Server가 전체 규모로 배포된 SIP 트렁크 또는 PSTN 게이트웨이를 사용하여 분기 사이트를 복구할 수도 있습니다.

필수 구성 요소 및 기타 계획 고려 사항을 비롯하여 조직에 적합한 분기 사이트 배포에 대한 자세한 내용은 계획 설명서에서 [Lync Server 2013의 PSTN 연결 계획](lync-server-2013-planning-for-pstn-connectivity.md) 및 [Lync Server 2013의 분기 사이트 음성 복구 계획](lync-server-2013-planning-for-branch-site-voice-resiliency.md)을 참조하십시오.

## 이 단원의 내용

  - [Lync Server 2013의 분기 사이트에서 PSTN 연결 제공](lync-server-2013-providing-pstn-connectivity-at-a-branch-site.md)

  - [Lync Server 2013을 통해 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버 배포](lync-server-2013-deploying-a-survivable-branch-appliance-or-server.md)

