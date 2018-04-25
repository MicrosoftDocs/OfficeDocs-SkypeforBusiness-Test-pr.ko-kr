---
title: 'Lync Server 2013: 새로운 재해 복구 및 고가용성 기능'
TOCTitle: 새로운 재해 복구 및 고가용성 기능
ms:assetid: 4fa7cd0f-784b-4d3f-b839-432c2ecaf7c1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204892(v=OCS.15)
ms:contentKeyID: 49303609
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 새로운 재해 복구 및 고가용성 기능

 

_**마지막으로 수정된 항목:** 2012-09-20_

Lync Server 2010에서와 같이 Lync Server 2013에 대한 주요 HA(고가용성) 체계는 풀링을 통한 서버 중복성을 기반으로 합니다. 특정 서버 역할을 실행하는 서버가 실패할 경우 풀에서 동일 역할을 실행하는 다른 서버가 해당 서버의 부하를 맡습니다. 이러한 방식은 프런트 엔드 서버, 에지 서버, 중재 서버 및 디렉터에 적용됩니다.

Lync Server 2013은 두 개의 데이터 센터에 있는 프런트 엔드 풀을 쌍으로 지정할 수 있도록 설정하여 새로운 재해 복구 방법을 추가로 제공합니다. 쌍으로 연결된 풀 중 하나가 다운되면 관리자가 사용자를 해당 풀에서 다른 풀로 장애 조치(failover)하여 서비스를 계속해서 제공할 수 있습니다. 이 기능에는 저장소 네트워크 또는 공유 디스크와 같이 고비용의 네트워크 또는 하드웨어 솔루션이 필요하지 않습니다.

Lync Server 2013에서는 또한 백 엔드 서버의 고가용성이 지원됩니다. 이것은 프런트 엔드 풀에 대해 2개의 백 엔드 서버를 배포하고, 백 엔드 서버에서 실행되는 모든 Lync 데이터베이스의 동시 SQL 미러링을 설정하는 선택적인 토폴로지입니다. 미러에 대해 미러링 모니터를 배포할지 여부를 선택할 수 있습니다.

## 참고 항목

#### 개념

[Lync Server 2013의 고가용성 및 재해 복구 계획](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md)

