---
title: Lync Server 2013용 SQL 서버 클러스터링 구성
TOCTitle: Lync Server 2013용 SQL 서버 클러스터링 구성
ms:assetid: d7b52ef1-573c-48ed-bb94-34e37b49645c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn383982(v=OCS.15)
ms:contentKeyID: 56558971
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013용 SQL 서버 클러스터링 구성

 

_**마지막으로 수정된 항목:** 2014-01-10_

Microsoft Lync Server 2013은 SQL Server 2012 및 SQL Server 2008 R2에 대한 클러스터링을 지원합니다. 지원되는 항목에 대한 자세한 내용은 [Lync Server 2013의 데이터베이스 소프트웨어 지원](lync-server-2013-database-software-support.md)을 참고하세요.

Enterprise Edition 프런트 엔드 서버와 백 엔드 데이터베이스를 설치하고 배포하기 전에 SQL Server 클러스터를 설정하고 구성해야 합니다. SQL Server 2012의 장애 조치(failover) 클러스터링에 대한 모범 사례 및 설치 지침은 <http://technet.microsoft.com/ko-kr/ko-kr/library/hh231721.aspx>를 참고하세요. SQL Server 2008의 장애 조치(failover) 클러스터링의 경우에는 <http://technet.microsoft.com/ko-kr/library/ms189134(v=sql.105).aspx>를 참고하세요.

SQL Server를 설치한 경우 SQL Server Management Studio를 설치하여 데이터베이스의 위치와 로그 파일 위치를 관리해야 합니다. SQL Server Management Studio는 SQL Server를 설치할 때 선택적 구성 요소로 설치됩니다.


> [!IMPORTANT]
> SQL Server 기반 서버에서 데이터베이스를 설치하고 배포하려면, 사용자가 데이터베이스 파일을 설치하는 SQL Server 기반 서버의 SQL Server sysadmin 그룹 구성원이어야 합니다. SQL Server sysadmin 그룹의 구성원이 아닌 경우 데이터베이스 파일이 배포될 때까지 그룹에 추가해 달라고 요청해야 합니다. sysadmin 그룹의 구성원이 될 수 없는 경우 SQL Server 데이터베이스 관리자에게 데이터베이스를 구성하고 배포하기 위한 스크립트를 제공해야 합니다. 절차를 완료하는 데 필요한 올바른 사용자 권한 및 사용 권한에 대한 자세한 내용은 <A href="lync-server-2013-deployment-permissions-for-sql-server.md">Lync Server 2013의 SQL Server에 대한 배포 권한</A>을 참고하세요.



## SQL Server 클러스터링을 구성하려면

1.  SQL Server 클러스터링의 설치 및 구성을 완료한 후에 SQL Server 클러스터링 설정에서 구성한 SQL Server 인스턴스 가상 클러스터 이름 및 SQL Server 데이터베이스의 인스턴스 이름을 사용하여 토폴로지 작성기에서 SQL Server 저장소를 정의합니다. 단일 SQL Server 기반 서버와 달리 클러스터링된 SQL Server 기반 서버의 경우 가상 노드 FQDN(정규화된 도메인 이름)을 사용합니다.
    

    > [!NOTE]
    > 토폴로지 작성기에 대해 개별 Windows Server 클러스터 노드를 구성하지 않아도 됩니다. 가상 SQL Server 클러스터 이름만 사용합니다.



2.  토폴로지 작성기를 사용하여 데이터베이스를 배포할 경우 SQL Server sysadmin 그룹의 구성원이어야 합니다. SQL Server sysadmin 그룹의 구성원이지만 도메인에 권한이 없는 경우(예: SQL Server 데이터베이스 관리자 역할) Lync Server에서 데이터베이스를 만들 수 있는 권한은 있지만 필요한 정보를 읽을 수 있는 권한은 없는 것입니다. Lync Server를 배포하는 데 필요한 사용자 권한과 사용 권한에 대한 자세한 내용은 [Lync Server 2013의 SQL Server에 대한 배포 권한](lync-server-2013-deployment-permissions-for-sql-server.md)을 참고하세요.

3.  SQL Server Management Studio를 사용하여 SQL Server 클러스터의 공유 디스크로 데이터베이스 폴더와 로그 파일 폴더 기본값이 올바르게 매핑되는지 확인합니다. 이는 토폴로지 작성기를 사용하여 데이터베이스를 만드는 경우의 필수 절차입니다.
    

    > [!NOTE]
    > SQL Server Management Studio를 설치하지 않은 경우 SQL Server 설치를 다시 실행한 다음 기존 SQL Server 배포를 위한 추가 기능으로 관리 도구를 선택하여 설치할 수 있습니다.



4.  토폴로지 작성기 또는 Windows PowerShell cmdlet을 사용하여 SQL Server 기반 서버에 대한 데이터베이스를 설치합니다. 토폴로지 작성기를 사용하려면 다음 절차를 사용합니다. Windows PowerShell cmdlet을 사용하려면 [Lync Server 2013에서 Lync Server 관리 셸을 사용하여 데이터베이스 설치](lync-server-2013-database-installation-using-lync-server-management-shell.md)를 참고하세요.

## 토폴로지 작성기를 사용하여 데이터베이스를 만들려면

1.  토폴로지 작성기를 시작합니다(**시작**, **모든 프로그램**, **Microsoft Lync Server 2013**, **Lync Server 토폴로지 작성기**를 차례로 클릭).
    

    > [!WARNING]
    > 다음 절차는 토폴로지를 정의하고 구성했다고 가정합니다. 토폴로지를 정의하는 방법에 대한 자세한 내용은 <A href="lync-server-2013-defining-and-configuring-the-topology.md">Lync Server 2013에서 토폴로지 정의 및 구성</A>을 참고하세요. 토폴로지 작성기를 사용하여 토폴로지를 게시하고 데이터베이스를 구성하려면 올바른 사용자 권한과 그룹 멤버 자격으로 로그온해야 합니다. 필요한 권한과 그룹 멤버 자격에 대한 자세한 내용은 <A href="lync-server-2013-deployment-permissions-for-sql-server.md">Lync Server 2013의 SQL Server에 대한 배포 권한</A>을 참고하세요.



2.  토폴로지 작성기에서 토폴로지를 게시할 때 **데이터베이스 만들기** 페이지에서 **고급**을 클릭합니다.

3.  **데이터베이스 파일 위치 선택** 페이지에는 데이터베이스 파일을 SQL Server 클러스터에 배포하는 방법을 결정하는 두 개의 옵션이 있습니다. 다음 중 하나를 선택합니다.
    
      - **데이터 파일 위치 자동 결정.** 이 옵션을 선택하면 SQL Server 기반 서버의 드라이브 구성을 기반으로 데이터베이스 로그와 데이터 파일 위치를 결정하는 데 알고리즘이 사용됩니다. 파일은 최적의 성능을 제공하기 위한 방식으로 배포됩니다.
    
      - SQL Server 인스턴스 기본값 사용. 이 옵션을 선택하면 SQL Server 인스턴스 설정에 따라 로그 및 데이터 파일이 설치됩니다. 데이터베이스 파일을 SQL Server에 배포한 후에 SQL Server 데이터베이스 관리자가 특정 SQL Server 구성 요구 사항에 맞게 성능을 최적화하기 위해 파일의 위치를 조정할 수 있습니다.

4.  토폴로지의 게시를 완료하고 작업 중에 오류가 발생하지 않았는지 확인합니다.

