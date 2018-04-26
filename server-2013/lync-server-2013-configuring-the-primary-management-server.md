---
title: 기본 관리 서버 구성
TOCTitle: 기본 관리 서버 구성
ms:assetid: 44e2e9a8-c130-4c66-9871-80b1ff11b27c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204844(v=OCS.15)
ms:contentKeyID: 49303482
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 기본 관리 서버 구성

 

_**마지막으로 수정된 항목:** 2014-03-19_

Microsoft Lync Server 2013에 포함된 새로운 상태 모니터링 기능을 완전히 활용하기 위해서는 관리자가 먼저 기본 관리 서버로 작동할 컴퓨터를 지정해야 합니다. 그런 다음에는 이 컴퓨터에서 System Center Operations Manager 2007 R2 또는 System Center Operations Manager 2012를 설치해야 합니다. 또한 Operations Manager 백 엔드 데이터베이스로 작동할 지원되는 SQL Server 버전을 설치해야 합니다. System Center Operations Manager 2012를 사용하는 경우 다음 중 아무 SQL Server 버전이나 백 엔드 데이터베이스로 사용할 수 있습니다.

  - SQL Server 2008 R2 서비스 팩 1

  - SQL Server 2008 R2 서비스 팩 2

System Center Operations Manager 2007 R2를 사용하는 경우 SQL Server 2005 서비스 팩 4 또는 SQL Server 2008 서비스 팩 3을 설치하는 것이 좋습니다. 또한 SQL Server 2008 R2를 System Center Operations Manager 2007 R2에 대한 백 엔드 데이터베이스로 사용할 수 있습니다. System Center Operations Manager 2007 R2에서 사용하도록 SQL Server 2008 R2를 구성하는 방법에 대한 자세한 내용은 이 설명서의 부록 1을 참조하십시오.

System Center Operations Manager 2012 또는 System Center Operations Manager 2007 R2를 설치할 때는 다음을 포함하여 해당 제품의 모든 구성 요소를 설치해야 합니다.

  - 운영 데이터베이스

  - 서버

  - 콘솔

  - Windows PowerShell cmdlet

  - 웹 콘솔

  - 보고

  - 데이터 웨어하우스

이러한 구성 요소 및 구성 요소의 설치에 대해서는 이 문서에서 자세히 설명하지 않습니다. System Center Operations Manager 2007 R2에 대한 자세한 내용은 [http://go.microsoft.com/fwlink/?linkid=257526\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=257526%26clcid=0x412)의 Operations Manager 2007 R2 설명서 및 [http://go.microsoft.com/fwlink/?linkid=257527\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=257527%26clcid=0x412)의 System Center Operations Manager 2012 설명서를 참조하십시오. SQL Server 2005 또는 SQL Server 2008 서비스 팩 1을 백 엔드 데이터베이스로 사용하려는 경우 해당 지침을 따라야 합니다.

System Center Operations Manager 2012를 사용하는 경우 SQL Server 2012를 백 엔드 데이터베이스로 사용할 수 있습니다. SQL Server 2012에 대한 자세한 내용은 [http://go.microsoft.com/fwlink/?linkid=257528\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=257528%26clcid=0x412)에서 SQL Server 2012 온라인 설명서를 참조하십시오.

기본 관리 서버는 Lync Server 배포당 하나만 설정할 수 있습니다. 또한 System Center Operations Manager 2012 또는 System Center Operations Manager 2007 R2를 사용할 수 있지만 두 응용 프로그램을 동시에 실행할 수 없으며 하나만 선택해야 합니다. 예를 들어 System Center Operations Manager 2012를 실행하는 경우 모든 System Center 에이전트도 System Center Operations Manager 2012를 실행해야 합니다. 일부 에이전트에서 System Center Operations Manager 2012를 실행하고 다른 에이전트에서 System Center Operations Manager 2007 R2를 실행할 수는 없습니다.

