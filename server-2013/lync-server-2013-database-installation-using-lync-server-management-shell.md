---
title: 'Lync Server 2013: Lync Server 관리 셸을 사용하여 데이터베이스 설치'
TOCTitle: Lync Server 관리 셸을 사용하여 데이터베이스 설치
ms:assetid: c90a6449-4dd5-4b18-b21c-ea2c2a64dc3c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398832(v=OCS.15)
ms:contentKeyID: 49305013
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 Lync Server 관리 셸을 사용하여 데이터베이스 설치

 

_**마지막으로 수정된 항목:** 2014-02-05_

서버 관리자와 SQL Server 관리자의 역할 및 직무를 구분하면 구현이 지연될 수 있습니다. Lync Server 2013은 RBAC(역할 기반 액세스 제어)를 사용하여 이러한 문제를 완화합니다. 경우에 따라 SQL Server 관리자는 RBAC 외부의 SQL Server 기반 서버에서 데이터베이스 설치를 관리해야 합니다. Lync Server 2013 관리 셸을 통해 SQL Server 관리자는 올바른 데이터 및 로그 파일을 사용하여 데이터베이스를 구성하도록 설계된 Windows PowerShell cmdlet를 실행할 수 있습니다. 자세한 내용은 [Lync Server 2013의 SQL Server에 대한 배포 권한](lync-server-2013-deployment-permissions-for-sql-server.md)을 참조하십시오.


> [!IMPORTANT]
> 다음 절차에서는 최소한 Lync Server 2013 OCSCore.msi, SQL Server Native Client(sqlncli.msi), Microsoft SQL Server 2012 Management Objects, CLR Types for Microsoft SQL Server 2012 및 Microsoft SQL Server 2012 ADOMD.NET이 설치되어 있다고 가정합니다. OCSCore.msi는 \Setup\AMD64\Setup 디렉터리의 설치 미디어에 있습니다. 나머지 구성 요소는 \Setup\amd64에 위치합니다. 또한 Lync Server 2013에 대한 Active Directory 준비가 완료되어야 합니다.



**Install-CsDatabase**는 데이터베이스를 설치하는 데 사용하는 Windows PowerShell cmdlet입니다. **Install-CsDatabase** cmdlet는 수많은 매개 변수를 가지며 여기에서는 그 중 몇 가지만 설명합니다. 사용 가능한 매개 변수에 대한 자세한 내용은 Lync Server 2013 관리 셸 설명서를 참조하십시오.


> [!WARNING]
> 성능 및 가능한 시간 제한 문제를 피하려면 SQL Server 기반 서버를 참조할 때 항상 FQDN(정규화된 도메인 이름)을 사용하십시오. 호스트 이름 전용 참조는 사용하지 마십시오. 예를 들어 sqlbe01.contoso.net을 사용하고 SQLBE01은 사용하지 마십시오.



데이터베이스 설치를 위해 **Install-CsDatabase**는 준비된 SQL Server 기반 서버에 데이터베이스를 배치하기 위한 세 가지 기본 방법을 사용합니다.

  - **Install-CsDatabase**를 DatabasePaths 또는 UseDefaultSqlPath 없이 실행합니다. cmdlet는 기본 제공 알고리즘을 사용하여 최적의 로그 및 데이터 파일 배치를 결정합니다. 알고리즘은 단독 실행형 SQL Server 구현에서만 작동합니다.

  - **Install-CsDatabase** 를 DatabasePaths 매개 변수와 함께 실행합니다. 매개 변수가 정의된 경우 로그 및 데이터 파일 위치를 최적화하는 기본 제공 알고리즘은 사용되지 않습니다. 이 매개 변수를 사용하면 로그 및 데이터 파일을 배포할 위치를 정의할 수 있습니다.

  - **Install-CsDatabase**를 UseDefaultSqlPaths와 함께 실행합니다. 이 옵션은 기본 제공 알고리즘을 사용하여 로그 및 데이터 파일 위치를 최적화하지 않습니다. 로그 및 데이터 파일은 SQL Server 관리자가 설정한 기본값에 따라 배포됩니다. 이러한 경로는 일반적으로 SQL Server에서 로그 및 데이터 파일 자동 관리를 위해 미리 설정되며 Lync Server 2013의 설치와 관련이 없습니다.

  - DatabasePathMap 매개 변수를 사용하여 각 데이터베이스의 위치 및 각 로그 파일을 명시적으로 지정하는 데 사용할 수도 있습니다.

## Windows PowerShell cmdlet을 사용하여 SQL Server 중앙 관리 저장소를 구성하려면

1.  원하는 컴퓨터에서 SQL Server 기반 서버에 데이터베이스를 만들 수 있도록 관리 자격 증명을 사용하여 로그온합니다. 자세한 내용은 [Lync Server 2013의 SQL Server에 대한 배포 권한](lync-server-2013-deployment-permissions-for-sql-server.md)을 참조하십시오.

2.  Lync Server 2013 관리 셸을 엽니다. Windows PowerShell에 대한 실행 정책을 조정하지 않은 경우 정책을 조정하여 Windows PowerShell 스크립트가 실행되도록 허용해야 합니다. 자세한 내용은 "실행 정책 검토"( <http://go.microsoft.com/fwlink/?linkid=203093>)를 참조하십시오.

3.  **Install-CsDatabase** cmdlet를 사용하여 중앙 관리 저장소를 설치합니다.
    
        Install-CsDatabase -CentralManagementDatabase -SqlServerFqdn <fully qualified domain name of SQL Server> 
        -SqlInstanceName <named instance> -DatabasePaths <logfile path>,<database file path> 
        -Report <path to report file>
    
        Install-CsDatabase -CentralManagementDatabase -SqlServerFqdn sqlbe.contoso.net -SqlInstanceName rtc -DatabasePaths "C:\CSDB-Logs","C:\CSDB-CMS" -Report "C:\Logs\InstallDatabases.html"
    

    > [!TIP]
    > Report 매개 변수는 선택적이지만 설치 프로세스를 문서화하는 경우에 유용합니다.



4.  **Install-CsDatabase –DatabasePaths**는 최대 6개의 경로 매개 변수를 사용할 수 있으며, 각 드라이브 경로는 "SQL Server 데이터 및 로그 파일 배치"에 정의된 대로 정의합니다. Lync Server 2013에서 데이터베이스 구성의 논리적 규칙에 따라 드라이브는 2, 4 또는 6개의 버킷으로 구문 분석됩니다. SQL Server 구성 및 버킷 수에 따라 2, 4 또는 6개의 경로를 제공합니다.
    
    드라이브가 세 개인 경우 로그가 우선 적용되며 데이터 파일은 이후에 배포됩니다. 드라이브가 6개로 구성된 SQL Server 기반 서버 예:
    
        Install-CsDatabase -ConfiguredDatases -SqlServerFqdn sqlbe.contoso.net -DatabasePaths "D:\CSDynLogs","E:\CSRtcLogs","F:\MonCdrArcLogs","G:\MonCdrArchData","H:\AbsAppLog","I:\DynRtcAbsAppData" -Report "C:\Logs\InstallDatabases.html"

5.  데이터베이스 설치가 완료되면 Lync Server 2013 관리 셸을 닫거나 토폴로지 작성기에 정의된 Lync Server 2013 구성 데이터베이스의 설치를 계속 진행할 수 있습니다.

## Windows PowerShell cmdlet을 사용하여 SQL Server 토폴로지 구성 데이터베이스를 구성하려면

1.  Lync Server 2013의 토폴로지 작성기 구성 데이터베이스를 설치하려면 Lync Server 2013 관리자가 토폴로지를 게시해야 합니다. 자세한 내용은 배포 설명서에서 [Lync Server 2013에서 토폴로지 게시](lync-server-2013-publish-the-topology.md) 섹션을 참조하십시오.

2.  원하는 컴퓨터에서 SQL Server 기반 서버에 데이터베이스를 만들 수 있도록 관리 자격 증명을 사용하여 로그온합니다. 자세한 내용은 [Lync Server 2013의 SQL Server에 대한 배포 권한](lync-server-2013-deployment-permissions-for-sql-server.md)을 참조하십시오.
    

    > [!IMPORTANT]
    > SQL Server 기반 데이터베이스를 구성할 수 있으려면 여기에 설명된 단계를 실행하기 위해 사용되는 SQL Server 관리자 계정이 SQL Server를 실행하고 중앙 관리 서버 역할을 보유하는 서버에서 sysadmins 그룹(또는 이에 상응하는 그룹)의 구성원인지 확인합니다. 이러한 구성은 SQL Server 데이터베이스 설치 또는 구성이 필요한 추가 Lync Server 2013 풀을 확인하는 데 특히 중요합니다. 예를 들어 두 번째 풀(pool02)을 배포 중이지만 중앙 관리 서버 역할을 pool01이 보유하고 있는 경우가 있을 수 있습니다. SQL Server 그룹(또는 이에 상응하는 그룹)에는 SQL Server 기반 데이터베이스 모두에 대한 권한이 있어야 합니다.



3.  Lync Server 2013 관리 셸을 아직 열지 않은 경우 엽니다.

4.  **Install-CsDatabase** cmdlet를 사용하여 토폴로지 작성기에서 구성된 데이터베이스를 설치합니다.
    
        Install-CsDatabase -ConfiguredDatabases -SqlServerFqdn <fully qualified domain name of SQL Server> 
         -DatabasePaths <logfile path>,<database file path> -Report <path to report file>
    
        Install-CsDatabase -ConfiguredDatabases -SqlServerFqdn sqlbe.contoso.net 
        -Report "C:\Logs\InstallDatabases.html"
    

    > [!TIP]
    > Report 매개 변수는 선택적이지만 설치 프로세스를 문서화하는 경우에 유용합니다.



5.  데이터베이스 설치가 완료되면 Lync Server 2013 관리 셸을 닫으십시오.

## Windows PowerShell cmdlet에서 DatabasePathMap을 사용하여 SQL Server 토폴로지를 구성하려면

1.  Lync Server 2013용 데이터베이스를 설치하려면 Lync Server 관리자가 미리 정의된 규칙 집합에 따라 경로를 만들고 데이터베이스 파일 및 로그 파일을 배포해야 합니다.

2.  원하는 컴퓨터에서 SQL Server 기반 서버에 데이터베이스를 만들 수 있도록 관리 자격 증명을 사용하여 로그온합니다. 자세한 내용은 [Lync Server 2013의 SQL Server에 대한 배포 권한](lync-server-2013-deployment-permissions-for-sql-server.md)을 참조하십시오.
    

    > [!IMPORTANT]
    > SQL Server 기반 데이터베이스를 구성할 수 있으려면 여기에 설명된 단계를 실행하기 위해 사용되는 SQL Server 관리자 계정이 SQL Server를 실행하고 중앙 관리 서버 역할을 보유하는 서버에서 sysadmins 그룹(또는 이에 상응하는 그룹)의 구성원인지 확인합니다. 이러한 구성은 SQL Server 데이터베이스 설치 또는 구성이 필요한 추가 Lync Server 풀을 확인하는 데 특히 중요합니다. 예를 들어 두 번째 풀(pool02)을 배포 중이지만 중앙 관리 서버 역할을 pool01이 보유하고 있는 경우가 있을 수 있습니다. SQL Server sysadmin 그룹(또는 이에 상응하는 그룹)에는 SQL Server 기반 데이터베이스 모두에 대한 권한이 있어야 합니다.



3.  Lync Server 관리 셸을 아직 열지 않은 경우 여십시오.

4.  **Install-CsDatabase** cmdlet을 DatabasePathMap 매개 변수 및 PowerShell 해시 테이블과 함께 사용하여 토폴로지 작성기 구성 데이터베이스를 설치합니다.

5.  코드 예에서 데이터베이스를 정의하는 경로는 다음과 같이 –DatabasePathsMap 매개 변수 및 정의된 해시 테이블을 사용하여 세부적인 수준까지 확인할 수 있습니다. 참고로, 예에서는 모든 데이터베이스 파일(.mdf)에 “C:\\CSData”를 사용하고 모든 로그 파일(.ldf)에 “C:\\CSLogFiles”를 사용합니다. 폴더는 필요한 경우 Install-CsDatabase에 의해 만들어집니다.
    
        $pathmap = @{
        "BackendStore:BlobStore:DbPath"="C:\CsData";"BackendStore:BlobStore:LogPath"="C:\CsLogFiles"
        "BackendStore:RtcSharedDatabase:DbPath"="C:\CsData";"BackendStore:RtcSharedDatabase:LogPath"="C:\CsLogFiles"
        "ABSStore:AbsDatabase:DbPath"="C:\CsData";"ABSStore:AbsDatabase:LogPath"="C:\CsLogFiles"
        "ApplicationStore:RgsConfigDatabase:DbPath"="C:\CsData";"ApplicationStore:RgsConfigDatabase:LogPath"="C:\CsLogFiles"
        "ApplicationStore:RgsDynDatabase:DbPath"="C:\CsData";"ApplicationStore:RgsDynDatabase:LogPath"="C:\CsLogFiles"
        "ApplicationStore:CpsDynDatabase:DbPath"="C:\CsData";"ApplicationStore:CpsDynDatabase:LogPath"="C:\CsLogFiles"
        "ArchivingStore:ArchivingDatabase:DbPath"="C:\CsData";"ArchivingStore:ArchivingDatabase:LogPath"="C:\CsLogFiles"
        "MonitoringStore:MonitoringDatabase:DbPath"="C:\CsData";"MonitoringStore:MonitoringDatabase:LogPath"="C:\CsLogFiles"
        "MonitoringStore:QoEMetricsDatabase:DbPath"="C:\CsData";"MonitoringStore:QoEMetricsDatabase:LogPath"="C:\CsLogFiles"
        }
        Install-CsDatabase -ConfigureDatabases -SqlServerFqdn sqlbe01.contoso.net -DatabasePathsMap $pathmap

6.  데이터베이스와 로그 파일의 이름이 대상 데이터베이스 서버 위치를 사용하여 명시적으로 지정되었으므로 각 서비스 유형의 실제 데이터베이스 및 로그 위치에 특정 위치를 정의할 수 있습니다. 다음 예에서는 각 서비스 유형의 데이터베이스를 별도의 디스크에 배치하고 관련 로그 파일은 또 다른 디스크에 배치합니다. 예를 들면 다음과 같습니다.
    
      - 모든 RTC 데이터베이스는 “D:\\RTCDatabase”에 배치
    
      - 모든 RTC 로그 파일은 “E:\\RTCLogs”에 배치
    
      - 모든 응용 프로그램 저장소 데이터베이스는 “F:\\CPSDatabases”에 배치
    
      - 모든 응용 프로그램 저장소 로그는 “G:\\CPSLogs”에 배치
    
      - 모든 응답 그룹 저장소 데이터베이스는 “H:\\RGSDatabases”에 배치
    
      - 모든 응답 그룹 저장소 로그는 “I:\\RGSLogs”에 배치
    
      - 모든 주소록 저장소 데이터베이스는 “J:\\ABSDatabases”에 배치
    
      - 모든 주소록 저장소 로그는 “K:\\ABSLogs”에 배치
    
      - 모든 보관 저장소 데이터베이스는 “L:\\ArchivingDatabases”에 배치
    
      - 모든 보관 저장소 로그는 “M:\\ArchivingLogs”에 배치
    
      - 모든 모니터링 저장소 데이터베이스는 “N:\\MonitoringDatabases”에 배치
    
      - 모든 모니터링 저장소 로그 파일은 “O:\\MonitoringLogfiles”에 배치
    
    <!-- end list -->
    
    ``` 
    
    $pathmap = @{
    "BackendStore:BlobStore:DbPath"="D:\RTCDatabase";"BackendStore:BlobStore:LogPath"="E:\RTCLogs"
    "BackendStore:RtcSharedDatabase:DbPath"="D:\RTCDatabase";"BackendStore:RtcSharedDatabase:LogPath"="E:\RTCLogs"
    "ABSStore:AbsDatabase:DbPath"="J:\ABSDatabases";"ABSStore:AbsDatabase:LogPath"="K:\ABSLogs"
    "ApplicationStore:RgsConfigDatabase:DbPath"="H:\RGSDatabases";"ApplicationStore:RgsConfigDatabase:LogPath"="G:\CPSLogs"
    "ApplicationStore:RgsDynDatabase:DbPath"="H:\RGSDatabases";"ApplicationStore:RgsDynDatabase:LogPath"="I:\RGSLogs"
    "ApplicationStore:CpsDynDatabase:DbPath"="F:\CPSDatabases";"ApplicationStore:CpsDynDatabase:LogPath"="G:\CsLogFiles"
    "ArchivingStore:ArchivingDatabase:DbPath"="M:\ArchivingLogs";"ArchivingStore:ArchivingDatabase:LogPath"="N:\MonitoringDatabases"
    "MonitoringStore:MonitoringDatabase:DbPath"="N:\MonitoringDatabases";"MonitoringStore:MonitoringDatabase:LogPath"="O:\MonitoringLogfiles"
    "MonitoringStore:QoEMetricsDatabase:DbPath"="N:\MonitoringDatabases";"MonitoringStore:QoEMetricsDatabase:LogPath"="O:\MonitoringLogfiles"
    }
    
    Install-CsDatabase -ConfiguredDatabases -SqlServerFqdn sqlbe01.contoso.net -DatabasePathMap $pathmap
    ```
    
    \-DatabasePathMap 매개 변수를 사용하여 SQL Server 성능 및 배치 요구 사항에 대한 최적의 솔루션을 제공하는 논리 드라이브 문자 매핑 조합을 정의할 수 있습니다.

토폴로지 작성기를 사용하는 경우와 달리 **DatabasePathMap** 메서드를 사용하여 데이터베이스 데이터 파일 및 로그 파일을 구성하면 일반 프로세스가 다소 달라집니다. 일반적으로, 선택할 토폴로지를 정의하고, 토폴로지를 게시한 후, 데이터베이스 배포 옵션을 선택합니다.

**DatabasePathMap**을 사용하는 경우 토폴로지 작성기 프로세스의 세 번째 부분이 이미 완료된 것입니다. 토폴로지 작성기를 실행하기 전에 데이터베이스 서버를 모두 구성한 경우라도 서버 역할과 옵션을 모두 정의해야 하지만 데이터베이스를 만드는 옵션은 선택 취소해야 합니다.

