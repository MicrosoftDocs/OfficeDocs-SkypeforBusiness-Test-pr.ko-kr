---
title: Lync Server 2013 백업 및 복원
TOCTitle: Lync Server 2013 백업 및 복원
ms:assetid: 07dc1f5e-af66-4e18-bf39-881dceff8bc3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh202160(v=OCS.15)
ms:contentKeyID: 52056782
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 백업 및 복원

 

_**마지막으로 수정된 항목:** 2013-02-21_

이 섹션에서는 Lync Server 2013 데이터를 백업하고 오류 발생 시 해당 데이터를 복원하는 최상의 방법을 살펴봅니다. 이러한 최상의 방법은 다음과 같은 상황에 적용됩니다.

  - 모든 유형(프런트 엔드 서버, 에지 서버, 중재 서버, 영구 채팅 서버 또는 디렉터)의 전체 Lync Server 풀 또는 이러한 풀 중 하나의 개별 서버

  - 중앙 관리 서버

  - Standard Edition 서버

  - Enterprise Edition백 엔드 서버

  - 파일 저장소

  - 보관 데이터베이스, 모니터링 데이터베이스 또는 영구 채팅 데이터베이스

이 섹션에는 전체 사이트를 복원하거나 대기 사이트를 개발하는 방법에 대한 정보가 포함되어 있지 않습니다. 쌍으로 연결된 프런트 엔드 풀을 사용하여 재해 복구 솔루션을 개발하는 방법에 대한 자세한 내용은 [Lync Server 2013의 고가용성 및 재해 복구 계획](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md)을 참조하십시오. 재해 복구를 계획할 때는 이 방법을 사용하는 것이 좋습니다.

쌍으로 연결된 프런트 엔드 풀을 배포했는데 이러한 풀 중 하나에 오류가 발생하여 복구할 수 없는 상태가 되었다면 쌍으로 연결된 나머지 한 풀에서 새 FQDN(정규화된 도메인 이름)을 사용하여 이 풀을 복원할 수 있습니다. 이 복구를 수행하는 단계에 대한 자세한 내용은 [Lync Server 2013 에서 풀 장애 조치(failover)](lync-server-2013-failing-over-a-pool.md)를 참조하십시오. 또한 오류가 발생하여 복구할 수 없게 된 풀(프런트 엔드 쌍의 일부분이었던 풀)을 나중에 다시 만들려면 [ABC 프런트 엔드 풀 장애 조치(failover) 수행](lync-server-2013-performing-an-abc-front-end-pool-failover.md)의 단계를 수행하면 됩니다.

이 문서에서 설명하는 방법에는 계획 단계 중의 특별한 고려 사항이 포함됩니다. 자세한 내용은 [백업 및 복원 계획 설정](lync-server-2013-establishing-a-backup-and-restoration-plan.md)을 참조하십시오.

## 이 단원의 내용

  - [Lync Server 백업 및 복원 준비](lync-server-2013-preparing-for-lync-server-backup-and-restoration.md)

  - [데이터 및 설정 백업](lync-server-2013-backing-up-data-and-settings.md)

  - [데이터 및 설정 복원](lync-server-2013-restoring-data-and-settings.md)

  - [백업 및 복원 워크시트](lync-server-2013-backup-and-restoration-worksheets.md)

