---
title: 'Lync Server 2013: 재해 복구를 위해 연장된 영구 채팅 서버 풀 사용'
TOCTitle: 재해 복구를 위해 연장된 영구 채팅 서버 풀 사용
ms:assetid: 74c5287e-d70d-490a-9adc-ab419917ddd9
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205007(v=OCS.15)
ms:contentKeyID: 49304064
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 재해 복구를 위해 연장된 영구 채팅 서버 풀 사용

 

_**마지막으로 수정된 항목:** 2012-10-06_

영구 채팅 서버에 대한 재해 복구 솔루션은 확장된 영구 채팅 서버 풀을 기반으로 구축되었습니다. 이 솔루션은 Lync Server 2010의 대도시 사이트 복구 솔루션과 비슷하지만 VLAN(가상 LAN) 확장에 대한 요구 사항이 없습니다. 영구 채팅 서버 풀을 확장하면 토폴로지에 로컬로 하나의 풀이 구성되지만 두 개의 서로 다른 데이터 센터의 풀에 서버를 물리적으로 배치하게 됩니다. 데이터베이스에 대해 SQL Server 미러링을 동일 방식으로 구성하고 동일한 데이터 센터에 데이터베이스 및 미러를 배포합니다. 보조 데이터 센터에는 백업 데이터베이스를 구성해야 합니다(재해 복구 중 고가용성을 제공하기 위한 선택적인 미러 포함). 이러한 백업 데이터베이스는 재해 복구 중 장애 조치(Failover)를 위해 사용됩니다.

고가용성을 위한 SQL Server 미러링 구성 방법에 대한 자세한 내용은 [Lync Server 2013의 SQL Server 미러링](lync-server-2013-sql-server-mirroring.md)을 참조하십시오. 재해 복구를 위한 장애 조치(Failover) 방법에 대한 자세한 내용은 [영구 채팅 서버 기본 데이터베이스에 대해 Lync Server 2013의 SQL Server 로그 전달 설정](lync-server-2013-setting-up-sql-server-log-shipping-for-the-persistent-chat-server-primary-database.md) 및 [Lync Server 2013에서 기본 미러와 로그 전달 보조 데이터베이스 간의 SQL Server 로그 전달 설정](lync-server-2013-setting-up-sql-server-log-shipping-between-the-primary-mirror-and-the-log-shipping-secondary-database.md)을 참조하십시오.

