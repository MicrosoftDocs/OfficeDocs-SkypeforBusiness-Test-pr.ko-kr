---
title: Lync Server 2013 백업 등록자 관계
TOCTitle: 백업 등록자 관계
ms:assetid: 7e078271-84b9-4666-989c-c4507a0cdf4a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205033(v=OCS.15)
ms:contentKeyID: 49304168
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 백업 등록자 관계

 

_**마지막으로 수정된 항목:** 2012-06-28_

재해 복구 기능을 제공하는 것 외에도 쌍으로 연결된 두 개의 풀이 서로 백업 등록자로 사용됩니다. Lync Server 2013에서 프런트 엔드 풀 사이의 백업 등록자 관계는 항상 1:1이고 상호 전환할 수 있습니다. 즉, P1이 P2의 백업이면 P2도 P1의 백업이어야 하며, 둘 중 어느 것도 다른 프런트 엔드 풀의 백업이 될 수 없습니다. 이러한 방식은 프런트 엔드 풀 백업 관계가 다대일일 수 있었던 Lync Server 2010과 달라진 개념입니다.

두 프런트 엔드 풀 사이의 백업 관계가 1:1이고 대칭적이어야 하지만 각 프런트 엔드 풀은 Lync Server 2010에서처럼 임의 개수의 SBA(Survivable Branch Appliance)에 대한 백업 등록자일 수도 있습니다.

Lync Server 2013은 재해 복구 지원을 SBA(Survivable Branch Appliance)에 있는 사용자로 확장하지 않습니다. SBA(Survivable Branch Appliance)의 백업 역할을 수행하는 프런트 엔드 풀이 작동 중지되면 프런트 엔드 풀에 있는 사용자가 백업 프런트 엔드 풀로 장애 조치(Failover)된 후에도 SBA(Survivable Branch Appliance)에 로그인한 사용자가 복구 모드로 설정됩니다.

