---
title: 'Lync Server 2013: 배포 개요'
TOCTitle: 배포 개요
ms:assetid: da67555e-f410-4c37-9996-d511f37da8d1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205305(v=OCS.15)
ms:contentKeyID: 49305229
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에 대한 배포 개요

 

_**마지막으로 수정된 항목:** 2013-03-12_

Lync Server 2013  Enterprise Edition과 Lync Server 2013  Standard Edition의 주요 차이점은 Standard Edition에서는 Enterprise Edition에 포함된 고가용성 기능을 지원하지 않는다는 점입니다. 고가용성을 원할 경우 여러 프런트 엔드 서버를 풀에 배포해야 합니다. 그러면 SQL Server를 실행하는 서버를 미러링할 수 있습니다. Enterprise Edition을 사용하는 경우 독립 실행형 중재 서버를 배치하거나 정의하도록 선택할 수 있습니다. 모니터링 서버 및 보관 서버에서는 SQL Server를 실행하는 독립 실행형 서버를 사용할 수 있습니다. 또는 프런트 엔드 서버 및 풀에 대해 데이터베이스 서버에서 SQL Server의 인스턴스를 실행할 수 있습니다.

Lync Server 2013Standard Edition을 실행하는 서버는 소규모 조직 및 원격 위치용이므로, 조직의 기본 배포에서 지리적으로 제거됩니다. 재해 시 장애 조치(failover)를 위해 쌍으로 묶인 2개의 Standard Edition 서버 서버가 사용자를 5천 명까지 지원할 수 있습니다. Enterprise Edition에서 프런트 엔드 서버를 풀링하는 것처럼 Standard Edition 서버를 풀링할 수는 없습니다. 또한 Standard Edition에서 사용되는 SQL Server 데이터베이스는 Standard Edition 서버 작업량을 처리할 수 있는 SQL Server Express를 실행 중인 배치된 서버입니다. 이는 모든 역할이 Standard Edition 서버에 상주해야 한다는 의미는 아닙니다. 독립 실행형 중재 서버 및 에지 서버를 사용할 수 있습니다. 중앙 관리 저장소 및 Lync Server 2013용 SQL Server 데이터베이스는 SQL Server를 실행 중인 서버를 사용하여 배치된 Standard Edition 서버에 상주해야 합니다. 모니터링 서버 및 보관 서버에서는 SQL Server 데이터베이스와 함께 독립 실행형 서버를 사용합니다.

