---
title: 백 엔드 서버에서 SQL Server 인스턴스 및 데이터베이스 제거
TOCTitle: 백 엔드 서버에서 SQL Server 인스턴스 및 데이터베이스 제거
ms:assetid: 32457df9-7dd9-4fca-9362-ea4de26b0296
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688016(v=OCS.15)
ms:contentKeyID: 49885714
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 백 엔드 서버에서 SQL Server 인스턴스 및 데이터베이스 제거

 

_**마지막으로 수정된 항목:** 2012-10-19_

종속된 Lync Server 2010 실행 서버를 제거한 후 또는 다른 데이터베이스를 사용하기 위해 Lync Server 2010 실행 서버를 다시 구성한 후 Microsoft SQL Server 데이터베이스 및 인스턴스를 제거합니다. 현재 SQL Server를 폐기하거나 Lync Server 2010을 실행하는 현재 서버를 다시 구성하여 데이터베이스가 오래된 데이터베이스가 되거나 사용할 수 없게 되는 경우 이 항목의 절차를 수행해야 합니다.

보관 서버 또는 모니터링 서버에 대한 데이터베이스 또는 인스턴스를 제거하려면 먼저 서버 역할을 제거해야 합니다. 마찬가지로 프런트 엔드 풀에 대한 인스턴스 또는 데이터베이스를 제거하려면 먼저 종속 서버 역할을 제거하거나 다시 구성해야 합니다. 이러한 절차는 배치된 데이터베이스나 개별 서버 인스턴스 간에 구분되지 않습니다. 데이터베이스 배치는 절차에 영향을 주지 않습니다.

## 이 단원의 내용

  - [프런트 엔드 풀에 대한 SQL Server 데이터베이스 제거](remove-the-sql-server-database-for-a-front-end-pool.md)

  - [모니터링 서버용 SQL Server 데이터베이스 제거](remove-the-sql-server-database-for-a-monitoring-server.md)

  - [보관 서버용 SQL Server 데이터베이스 제거](remove-the-sql-server-database-for-an-archiving-server.md)

