---
title: 중앙 관리 저장소를 호스트하는 서버 복원
TOCTitle: 중앙 관리 저장소를 호스트하는 서버 복원
ms:assetid: 3bd6c82c-07fb-4798-b8f9-e7c78a5a83d5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh202172(v=OCS.15)
ms:contentKeyID: 52056822
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 중앙 관리 저장소를 호스트하는 서버 복원

 

_**마지막으로 수정된 항목:** 2013-02-21_

Lync Server 배포에는 단일 중앙 관리 저장소가 포함되며, 이 저장소의 복사본이 Lync Server 서버 역할을 실행하는 각 서버에 복제됩니다. 이 항목에서는 중앙 관리 저장소를 호스트하는 백 엔드 서버 또는 Standard Edition 서버를 복원하는 방법에 대해 설명합니다.

중앙 관리 서버가 있는 풀을 찾으려면 토폴로지 작성기를 열고 **Lync Server**를 클릭한 다음 오른쪽 창에서 **중앙 관리 서버** 아래를 확인합니다.

중앙 관리 저장소를 호스트하는 백 엔드 서버가 미러링 방식으로 설치되어 있고 미러 데이터베이스가 계속 작동하는 경우, 계속 작동하는 해당 미러의 백업을 만든 후 아래의 복원 절차에 따라 이 백업을 사용하여 기본 데이터베이스와 미러 데이터베이스에서 모두 전체 복원을 수행하는 것이 좋습니다. 이렇게 해야 하는 이유는, 백 엔드 복원을 수행하려면 토폴로지를 수정하여 게시해야 하는데 이 작업은 CMS를 호스트하는 기본 데이터베이스가 작동하는 경우에만 수행할 수 있기 때문입니다. 또한 토폴로지를 게시할 수 없으면 기본 데이터베이스 및 미러 데이터베이스 역할을 교환할 수 없습니다.


> [!NOTE]
> 중앙 관리 저장소를 호스트하지 않는 백 엔드 서버 또는 Standard Edition 서버에서 오류가 발생한 경우 <A href="lync-server-2013-restoring-an-enterprise-edition-back-end-server.md">Enterprise Edition 백 엔드 서버 복원</A> 또는 <A href="lync-server-2013-restoring-a-standard-edition-server.md">Standard Edition 서버 복원</A>을 참조하십시오. 중앙 관리 저장소를 호스트하는 백 엔드 서버가 미러링된 구성으로 되어 있으며 미러에서만 오류가 발생한 경우 <A href="lync-server-2013-restoring-a-mirrored-enterprise-edition-back-end-server-mirror.md">미러링된 Enterprise Edition 백 엔드 서버 복원 - 미러</A>를 참조하십시오. 다른 서버에서 오류가 발생한 경우에는 <A href="lync-server-2013-restoring-an-enterprise-edition-member-server.md">Enterprise Edition 구성원 서버 복원</A>을 참조하십시오.




> [!TIP]
> 복원을 시작하기 전에 시스템에 대한 이미지 복사본을 만드는 것이 좋습니다. 복원 중 오류가 발생하면 이 이미지를 롤백 지점으로 사용할 수 있습니다. 운영 체제 및 SQL Server를 설치한 후에 이미지 복사본을 만들고 인증서를 복원하거나 다시 등록할 수도 있습니다.



## 중앙 관리 저장소를 복원하려면

1.  오류가 발생한 컴퓨터와 FQDN(정규화된 도메인 이름)이 동일한 정상 상태의 서버 또는 새 서버에 운영 체제를 설치하고 인증서를 복원하거나 다시 등록합니다.
    

    > [!NOTE]
    > 조직의 서버 배포 절차에 따라 이 단계를 수행합니다.



2.  RTCUniversalServerAdmins 그룹 및 Local Administrators 그룹의 구성원인 사용자 계정을 사용하여 복원 중인 서버에 로그온합니다.

3.  Standard Edition 서버를 복원하는 경우 $Backup에서 서버의 파일 저장소 위치로 적합한 파일 저장소를 복사하여 파일 저장소를 복원한 후 폴더를 공유합니다.
    

    > [!IMPORTANT]
    > 복원된 파일 저장소의 경로 및 파일 이름은 파일을 사용하는 구성 요소가 액세스할 수 있도록 백업된 파일 저장소와 정확하게 동일해야 합니다.



4.  다음 중 하나를 수행합니다.
    
      - Standard Edition 서버를 설치하는 경우 Lync Server 설치 폴더 또는 미디어로 이동하여 Lync Server 배포 마법사(\\setup\\amd64\\Setup.exe)를 시작합니다. 배포 마법사에서 **첫 번째 Standard Edition 서버 준비**를 클릭하고 마법사의 지시에 따라 중앙 관리 저장소를 설치합니다.
    
      - 엔터프라이즈 백 엔드 서버를 설치하는 경우 SQL Server 2012 또는 SQL Server 2008 R2를 설치하고 인스턴스 이름은 오류 이전과 동일하게 유지합니다.
        

        > [!NOTE]
        > 복원하려는 서버 및 배포에 따라 서버에는 배치된 데이터베이스 또는 개별 데이터베이스가 여러 개 포함될 수 있습니다. SQL Server 권한 및 로그인을 포함하여 원래 서버를 배포할 때 사용한 동일한 절차에 따라 SQL Server를 설치합니다.



5.  프런트 엔드 서버에서 Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

6.  중앙 관리 저장소를 다시 만듭니다. 명령줄에 다음을 입력합니다.
    
        Install-CsDatabase -CentralManagementDatabase -Clean -SqlServerFqdn <FQDN> -SqlInstanceName <instance name> -Verbose
    
    예:
    
        Install-CsDatabase -CentralManagementDatabase -Clean -SqlServerFqdn Server01.contoso.com -SqlInstanceName cms -Verbose

7.  중앙 관리 저장소의 Active Directory 도메인 서비스 제어 지점을 설정합니다. 명령줄에 다음을 입력합니다.
    
        Set-CsConfigurationStoreLocation -SqlServerFqdn <FQDN> -SqlInstanceName <instance name> -Verbose
    
    예:
    
        Set-CsConfigurationStoreLocation -SqlServerFqdn Server01.contoso.com -SqlInstanceName cms -Verbose
    

    > [!NOTE]
    > 서비스 연결 지점이 손실될 경우 이 cmdlet을 다시 실행할 수 있습니다.



8.  $Backup에서 중앙 관리 저장소 데이터를 가져옵니다. 명령줄에 다음을 입력합니다.
    
        Import-CsConfiguration -FileName <CMS backup file name>
    
    예:
    
        Import-CsConfiguration -FileName "C:\Config.zip"

9.  변경한 내용을 사용하도록 설정합니다. 명령줄에 다음을 입력합니다.
    
        Enable-CsTopology
    

    > [!NOTE]
    > 토폴로지를 사용하도록 설정한 후에는 데이터베이스에서 토폴로지 문서를 찾을 수 있습니다.



10. CMS도 호스트했던 Enterprise Edition백 엔드 서버를 복원하거나 CMS의 미러를 다시 만들어야 하는 경우 이 단계를 수행합니다. 그렇지 않으면 11단계로 건너뜁니다.
    
    다음을 수행하여 독립 실행형 데이터베이스를 설치합니다.
    
    1.  토폴로지 작성기 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 토폴로지 작성기**를 클릭합니다.
    
    2.  **기존 배포에서 토폴로지 다운로드**를 클릭한 후 **확인**을 클릭합니다.
    
    3.  토폴로지를 선택한 후 **저장**을 클릭합니다. **예**를 클릭하여 선택을 확인합니다.
    
    4.  **Lync Server 2013** 노드를 마우스 오른쪽 단추로 클릭하고 **데이터베이스 설치**를 클릭합니다.
    
    5.  **데이터베이스 설치** 마법사를 따릅니다. 이 서버에서 중앙 관리 저장소 이외의 데이터베이스를 복원하는 경우 **데이터베이스 만들기** 페이지에서 다시 만들려는 데이터베이스를 선택합니다.
        

        > [!NOTE]
        > 독립 실행형 데이터베이스만 <STRONG>데이터베이스 만들기</STRONG> 페이지에 표시됩니다. Lync Server 배포 마법사를 실행하면 배치된 데이터베이스가 만들어집니다.

    
    6.  미러링된 백 엔드 서버를 복원하는 경우 미러 데이터베이스 만들기 메시지가 표시될 때까지 마법사의 나머지 단계를 계속 수행합니다. 해당 메시지가 표시되면 설치할 데이터베이스를 선택하고 프로세스를 완료합니다.
    
    7.  나머지 마법사의 단계를 따른 후 **마침**을 클릭합니다.
    

    > [!TIP]
    > 토폴로지 작성기를 실행하는 대신 <STRONG>Install-CsDatabase</STRONG> cmdlet을 사용하여 각 데이터베이스를 만들고 <STRONG>Install-CsMirrorDatabase</STRONG> cmdlet을 사용하여 미러링을 구성할 수 있습니다. 자세한 내용은 <A href="https://docs.microsoft.com/en-us/powershell/module/skype/Install-CsDatabase">Install-CsDatabase</A> 및 <A href="https://docs.microsoft.com/en-us/powershell/module/skype/Install-CsMirrorDatabase">Install-CsMirrorDatabase</A>를 참조하십시오.



11. Standard Edition 서버를 복원하는 경우 Lync Server 설치 폴더 또는 미디어로 이동하여 Lync Server 배포 마법사(\\setup\\amd64\\Setup.exe)를 시작합니다. Lync Server 배포 마법사를 사용하여 다음을 수행합니다.
    
    1.  **1단계: 로컬 구성 저장소 설치**를 실행하여 로컬 구성 파일을 설치합니다.
    
    2.  **2단계: Lync Server 구성 요소 설치 또는 제거**를 실행하여 Lync Server 서버 역할을 설치합니다.
    
    3.  **3단계: 인증서 요청, 설치 또는 지정**을 실행하여 인증서를 지정합니다.
    
    4.  **4단계: 서비스 시작**을 실행하여 서버에서 서비스를 시작합니다.
    
    배포 마법사 실행에 대한 자세한 내용은 복원 중인 서버 역할에 대한 배포 설명서를 참조하십시오.

12. 다음을 수행하여 사용자 데이터를 복원합니다.
    
    1.  ExportedUserData.zip을 $Backup\\에서 로컬 디렉터리로 복사합니다.
    
    2.  사용자 데이터를 복원하기 전에 Lync 서비스를 중지해야 합니다. 이렇게 하려면 다음을 입력합니다.
        
            Stop-CsWindowsService
    
    3.  사용자 데이터를 복원하려면 명령줄에 다음을 입력합니다.
        
            Import-CsUserData -PoolFqdn <Fqdn> -FileName <String>
        
        예:
        
            Import-CsUserData -PoolFqdn "atl0cs-001.litwareinc.com" -FileName "C:\Logs\ExportedUserDatal.zip"
    
    4.  다음을 입력하여 Lync 서비스를 다시 시작합니다.
        
            Start-CsWindowsService

13. 위치 정보 데이터를 중앙 관리 저장소로 복원합니다. 명령줄에 다음을 입력합니다.
    
        Import-CsLisConfiguration -FileName <LIS backup file name>
    
    예:
    
        Import-CsLisConfiguration -FileName "D:\E911Config.zip"

14. 이 풀 또는 Standard Edition 서버에 응답 그룹을 배포한 경우 응답 그룹 구성 데이터를 복원합니다. 자세한 내용은 [응답 그룹 설정 복원](lync-server-2013-restoring-response-group-settings.md)을 참조하십시오.

15. 보관 또는 모니터링 데이터베이스가 포함된 백 엔드 서버를 복원 중인 경우 SQL Server 관리 도구(예: SQL Server Management Studio)를 사용하여 보관 또는 모니터링 데이터를 복원합니다. 자세한 내용은 [모니터링 또는 보관 데이터 복원](lync-server-2013-restoring-monitoring-or-archiving-data.md)을 참조하십시오.

