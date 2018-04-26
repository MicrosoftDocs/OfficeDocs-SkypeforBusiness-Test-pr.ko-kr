---
title: 'Lync Server 2013: 프런트 엔드 풀 연결 계획'
TOCTitle: 프런트 엔드 풀 연결 계획
ms:assetid: cca5773d-57ff-45ce-a7b4-f82ae697c477
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205293(v=OCS.15)
ms:contentKeyID: 49305056
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 프런트 엔드 풀 연결 계획

 

_**마지막으로 수정된 항목:** 2012-09-28_

Lync Server 2013의 재해 복구 기능을 최적화하기 위해 지리적으로 분산된 두 사이트 간에 프런트 엔드 풀을 배포해야 합니다. 각 사이트에는 상대 사이트의 프런트 엔드 포트와 쌍으로 연결된 프런트 엔드 풀이 있습니다. 두 사이트 모두 활성 상태이고 Lync Server 백업 서비스는 실시간 데이터 복제 기능을 제공하여 각 풀이 동기화된 상태를 유지할 수 있도록 합니다. 백업 서비스는 Lync Server 2013에 새로 도입된 기능으로, 재해 복구 솔루션을 지원하기 위해 고안되었습니다. 백업 서비스는 다른 쪽 프런트 엔드 풀과 쌍으로 연결된 프런트 엔드 풀에 설치됩니다.

한 사이트의 풀에 오류가 발생하면 다른 사이트의 풀로 오류가 발생한 풀의 사용자를 장애 조치(failover)할 수 있습니다. 그러면 두 풀의 모든 사용자에게 서비스를 계속 제공할 수 있습니다. 용량 계획 목적으로 각 풀은 재해에 대비하여 두 풀의 모든 사용자 작업 부하를 처리할 수 있도록 설계되어야 합니다.

## 이 섹션의 내용

  - [Lync Server 2013에 대한 지원되는 풀 연결 옵션 및 모범 사례](lync-server-2013-supported-pool-pairing-options-and-best-practices.md)

  - [Lync Server 2013의 백업 등록자 관계](lync-server-2013-backup-registrar-relationships.md)

  - [Lync Server 2013의 풀 장애 조치(Failover) 및 풀 장애 복구(Failback)를 위한 복구 시간](lync-server-2013-recovery-time-for-pool-failover-and-pool-failback.md)

  - [Lync Server 2013의 중앙 관리 저장소 장애 조치(failover)](lync-server-2013-central-management-store-failover.md)

  - [Lync Server 2013의 프런트 엔드 풀 연결 데이터 보안](lync-server-2013-front-end-pool-pairing-data-security.md)

