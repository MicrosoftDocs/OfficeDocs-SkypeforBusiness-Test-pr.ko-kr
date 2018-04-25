---
title: 'Lync Server 2013: Lync Server에 대해 SQL Server 구성'
TOCTitle: Lync Server 2013에 대해 SQL Server 구성
ms:assetid: 375e5cc4-e436-46dc-9b02-5063f35cdcc1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425848(v=OCS.15)
ms:contentKeyID: 49303301
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에 대해 SQL Server 구성

 

_**마지막으로 수정된 항목:** 2013-08-12_

이 섹션의 항목에서는 Lync Server의 엔터프라이즈 배포를 사용하도록 SQL Server를 배포 및 구성하는 방법을 설명합니다. Standard Edition 서버에서는 Standard Edition 서버의 작업에 맞게 적절한 크기로 지정된 SQL Server의 배치된 SQL Server Express 버전을 사용합니다.

Lync Server 2013  중앙 관리 저장소는 풀 내 모든 Enterprise Edition 서버의 사용자 데이터를 저장하며, SQL Server 기반 백 엔드 서버에 배치되도록 디자인됩니다. 중앙 리포지토리인 중앙 관리 저장소는 기타 Lync Server 2013 역할과 동일한 컴퓨터에 설치할 수 없습니다. 중앙 관리 저장소는 풀의 Enterprise Edition 서버에 있을 수 없습니다. 토폴로지를 처음으로 게시하고 데이터베이스를 만들도록 선택하면 중앙 관리 저장소가 자동으로 만들어집니다. 백 엔드 서버로 지정하는 컴퓨터에서 SQL Server 데이터베이스 소프트웨어를 실행 중이어야 설치가 정상적으로 진행됩니다.

## 이 단원의 내용

  - [Lync Server 2013에 대한 SQL Server 데이터 및 로그 파일 배치](lync-server-2013-sql-server-data-and-log-file-placement.md)

  - [Lync Server 2013에서 SQL Server 구성](lync-server-2013-configure-sql-server.md)

  - [Lync Server 2013의 SQL Server에 대한 배포 권한](lync-server-2013-deployment-permissions-for-sql-server.md)

  - [Lync Server 2013에서 Lync Server 관리 셸을 사용하여 데이터베이스 설치](lync-server-2013-database-installation-using-lync-server-management-shell.md)

  - [Lync Server 2013의 SQL Server에 대한 방화벽 요구 사항 이해](lync-server-2013-understanding-firewall-requirements-for-sql-server.md)

  - [Lync Server 2013용 SQL 서버 클러스터링 구성](lync-server-2013-configure-sql-server-clustering.md)

