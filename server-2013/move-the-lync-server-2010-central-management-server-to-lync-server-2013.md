---
title: Lync Server 2013으로 Lync Server 2013 중앙 관리 서버 이동
TOCTitle: Lync Server 2013으로 Lync Server 2013 중앙 관리 서버 이동
ms:assetid: 30cc98f2-1916-4dbe-99d0-8df5368ed3ec
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688013(v=OCS.15)
ms:contentKeyID: 49885711
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013으로 Lync Server 2013 중앙 관리 서버 이동

 

_**마지막으로 수정된 항목:** 2013-11-25_

Lync Server 2010에서 Lync Server 2013으로 마이그레이션한 후에는 Lync Server 2010중앙 관리 서버를 Lync Server 2013프런트 엔드 서버 또는 풀로 이동해야 레거시 Lync Server 2010 서버를 제거할 수 있습니다.

중앙 관리 서버는 데이터베이스의 읽기/쓰기 복사본이 중앙 관리 서버를 포함하는 프런트 엔드 서버에 의해 저장되는 단일 마스터/다중 복제본 시스템입니다. 중앙 관리 서버를 포함한 프런트 엔드 서버를 비롯하여 토폴로지의 각 컴퓨터에는 설치 또는 배포 중에 컴퓨터에 설치된 SQL Server 데이터베이스(기본 이름 RTCLOCAL)의 중앙 관리 저장소 데이터에 대한 읽기 전용 복사본이 포함됩니다. 로컬 데이터베이스는 모든 컴퓨터에서 서비스로 실행되는 Lync Server 복제본 복제기 에이전트를 사용하여 복제본 업데이트를 수신합니다. 중앙 관리 서버 및 로컬 복제본에서 실제 데이터베이스의 이름은 xds.mdf 및 xds.ldf 파일로 구성된 XDS입니다. 마스터 데이터베이스 위치는 Active Directory 도메인 서비스에서 SCP(서비스 제어 지점)에 의해 참조됩니다. 중앙 관리 서버를 사용하여 Lync Server를 관리 및 구성하는 모든 도구는 SCP를 사용하여 중앙 관리 저장소를 찾습니다.

중앙 관리 서버를 성공적으로 이동한 후 원래 프런트 엔드 서버에서 중앙 관리 서버 데이터베이스를 제거합니다. 중앙 관리 서버 데이터베이스를 제거하는 방법에 대한 자세한 내용은 [프런트 엔드 풀에 대한 SQL Server 데이터베이스 제거](remove-the-sql-server-database-for-a-front-end-pool.md)를 참조하십시오.

Lync Server 관리 셸에서 Windows PowerShell cmdlet **Move-CsManagementServer**를 사용하여 Lync Server 2010 SQL Server 데이터베이스에서 Lync Server 2013 SQL Server 데이터베이스로 데이터베이스를 이동한 후 Lync Server 2013중앙 관리 서버 위치를 가리키도록 SCP를 업데이트합니다.

## 중앙 관리 서버 이동 전 Lync Server 2013프런트 엔드 서버 준비

Lync Server 2010중앙 관리 서버를 이동하기 전에 이 섹션의 절차에 따라 Lync Server 2013프런트 엔드 서버를 준비합니다.

## Enterprise Edition 프런트 엔드 풀을 준비하려면

1.  중앙 관리 서버를 다시 배치하려는 Lync Server 2013 Enterprise Edition 프런트 엔드 풀에서 Lync Server 관리 셸이 설치되어 있는 컴퓨터에 **RTCUniversalServerAdmins** 그룹 구성원으로 로그온합니다. 중앙 관리 저장소를 설치할 데이터베이스에 대한 SQL Server 데이터베이스 sysadmin 사용자 권한 및 사용 권한도 있어야 합니다.

2.  Lync Server 관리 셸을 엽니다.

3.  Lync Server 2013 SQL Server 데이터베이스에서 새 중앙 관리 저장소를 만들려면 Lync Server 관리 셸에 다음을 입력합니다.
    
        Install-CsDatabase -CentralManagementDatabase -SQLServerFQDN <FQDN of your SQL Server> -SQLInstanceName <name of instance>

4.  **Lync Server 프런트 엔드** 서비스의 상태가 **시작됨** 인지 확인합니다.

## Standard Edition 프런트 엔드 서버를 준비하려면

1.  중앙 관리 서버를 다시 배치할 Lync Server 2013 Standard Edition 프런트 엔드 서버에서 Lync Server 관리 셸이 설치되어 있는 컴퓨터에 **RTCUniversalServerAdmins** 그룹 구성원으로 로그온합니다.

2.  Lync Server 배포 마법사를 엽니다.

3.  Lync Server 배포 마법사에서 **첫 번째 Standard Edition 서버 준비** 를 클릭합니다.

4.  **명령 실행** 페이지에서 SQL Server Express가 중앙 관리 서버로 설치됩니다. 또한 필요한 방화벽 규칙이 만들어집니다. 데이터베이스 및 필수 구성 요소 소프트웨어 설치가 완료되면 **마침** 을 클릭합니다.
    

    > [!NOTE]
    > 초기 설치는 시간이 오래 걸릴 수 있으며 명령 출력 요약 화면에 업데이트가 표시되지 않을 수 있습니다. 이는 SQL Server Express가 설치되기 때문입니다. 데이터베이스 설치를 모니터링해야 하는 경우 작업 관리자를 사용하여 설치를 모니터링합니다.



5.  Lync Server 2013 Standard Edition 프런트 엔드 서버에서 새 중앙 관리 저장소를 만들려면 Lync Server 관리 셸에 다음을 입력합니다.
    
        Install-CsDatabase -CentralManagementDatabase -SQLServerFQDN <FQDN of your Standard Edition Server> -SQLInstanceName <name of instance - RTC by default>

6.  **Lync Server 프런트 엔드** 서비스의 상태가 **시작됨** 인지 확인합니다.

## Lync Server 2010중앙 관리 서버를 Lync Server 2013으로 이동하려면

1.  중앙 관리 서버로 지정할 Lync Server 2013 서버에서 Lync Server 관리 셸이 설치되어 있는 컴퓨터에 **RTCUniversalServerAdmins** 그룹 구성원으로 로그온합니다. SQL Server 데이터베이스 관리자 사용자 권한 및 사용 권한도 있어야 합니다.

2.  Lync Server 관리 셸을 엽니다.

3.  Lync Server 관리 셸에 다음을 입력합니다.
    
        Enable-CsTopology
    

    > [!WARNING]
    > <CODE>Enable-CsTopology</CODE>가 실패하면 계속하기 전에 명령 실행을 방지하는 문제를 해결합니다. <STRONG>Enable-CsTopology</STRONG>가 성공하지 않으면 이동이 실패하고 토폴로지가 중앙 관리 저장소가 없는 상태로 될 수 있습니다.



4.  Lync Server 2013프런트 엔드 서버 또는 프런트 엔드 풀의 Lync Server 관리 셸에 다음을 입력합니다.
    
        Move-CsManagementServer

5.  Lync Server 관리 셸에는 현재 상태 및 제안됨 상태의 서버, 파일 저장소, 데이터베이스 저장소 및 서비스 연결 지점이 표시됩니다. 정보를 주의해서 읽고 원래 의도된 원본과 대상인지 확인합니다. 계속하려면 **Y** 를 입력하고 이동을 중지하려면 **N** 을 입력합니다.

6.  **Move-CsManagementServer** 명령으로 생성된 경고 또는 오류를 검토하고 해결합니다.

7.  Lync Server 2013 서버에서 Lync Server 배포 마법사를 엽니다.

8.  Lync Server 배포 마법사에서 **Lync Server 시스템 설치 또는 업데이트** 를 클릭한 후 **2단계: Lync Server 구성 요소 설치 또는 제거** 를 클릭하고, **다음** 을 클릭하고, 요약 정보를 검토한 후 **마침** 을 클릭합니다.

9.  Lync Server 2010 서버에서 Lync Server 배포 마법사를 엽니다.

10. Lync Server 배포 마법사에서 **Lync Server 시스템 설치 또는 업데이트** 를 클릭한 후 **2단계: Lync Server 구성 요소 설치 또는 제거** 를 클릭하고, **다음** 을 클릭하고, 요약 정보를 검토한 후 **마침** 을 클릭합니다.

11. Lync Server 2013 서버를 다시 부팅합니다. 이는 중앙 관리 서버 데이터베이스에 액세스할 수 있는 그룹 구성원이 변경되었기 때문에 필요합니다.

12. 새 중앙 관리 저장소를 사용한 복제가 수행되는지 확인하려면 Lync Server 관리 셸에 다음을 입력합니다.
    
        Get-CsManagementStoreReplicationStatus
    

    > [!NOTE]
    > 복제로 모든 현재 복제본을 업데이트하려면 시간이 다소 걸릴 수 있습니다.



## 이동 후 Lync Server 2010중앙 관리 저장소 파일을 제거하려면

1.  Lync Server 2010 서버에서 Lync Server 관리 셸이 설치되어 있는 컴퓨터에 **RTCUniversalServerAdmins** 그룹 구성원으로 로그온합니다. SQL Server 데이터베이스 관리자 사용자 권한 및 사용 권한도 있어야 합니다.

2.  Lync Server 관리 셸을 엽니다.
    

    > [!WARNING]
    > 복제가 완료되고 안정화되기 전까지는 이전 데이터베이스 파일의 제거를 진행하지 마십시오. 복제 완료 전에 파일을 제거할 경우 복제 프로세스가 중단되어 새로 이동한 중앙 관리 서버가 알 수 없는 상태가 될 수 있습니다. <STRONG>Get-CsManagementStoreReplicationStatus</STRONG> cmdlet을 사용하여 복제 상태를 확인합니다.



3.  Lync Server 2010중앙 관리 서버에서 중앙 관리 저장소 데이터베이스 파일을 제거하려면 다음을 입력합니다.
    
        Uninstall-CsDatabase -CentralManagementDatabase -SqlServerFqdn <FQDN of SQL Server> -SqlInstanceName <Name of source server>
    
    예를 들면 다음과 같습니다.
    
        Uninstall-CsDatabase -CentralManagementDatabase -SqlServerFqdn sql.contoso.net -SqlInstanceName rtc
    
    여기서 *\<FQDN of SQL Server\>* 는 Enterprise Edition 배포의 Lync Server 2010 백 엔드 서버 또는 Standard Edition 서버의 FQDN입니다.

