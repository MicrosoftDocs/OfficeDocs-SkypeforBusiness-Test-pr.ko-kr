---
title: Enterprise Edition 백 엔드 서버 복원
TOCTitle: Enterprise Edition 백 엔드 서버 복원
ms:assetid: 1450eb4e-3315-4d02-8f02-6e1791fb1550
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh202163(v=OCS.15)
ms:contentKeyID: 52056791
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Enterprise Edition 백 엔드 서버 복원

 

_**마지막으로 수정된 항목:** 2013-02-18_

다음의 두 사례에 대해 이 항목에서 설명하는 절차를 따릅니다.

  - 미러링된 Enterprise Edition 백 엔드 서버의 기본 데이터베이스와 미러 데이터베이스에서 모두 오류가 발생하는 경우

  - 미러링되지 않은 Enterprise Edition 백 엔드 서버에서 오류가 발생하는 경우

Enterprise Edition 백 엔드가 미러링되어 있으며 미러링 또는 기본 데이터베이스에서만 오류가 발생하는 경우 기본 데이터베이스를 복원하는 방법은 [미러링된 Enterprise Edition 백 엔드 서버 복원 - 기본](lync-server-2013-restoring-a-mirrored-enterprise-edition-back-end-server-primary.md)을, 미러를 복원하는 방법은 [미러링된 Enterprise Edition 백 엔드 서버 복원 - 미러](lync-server-2013-restoring-a-mirrored-enterprise-edition-back-end-server-mirror.md)를 참조하십시오.

중앙 관리 저장소에서 오류가 발생하면 [중앙 관리 저장소를 호스트하는 서버 복원](lync-server-2013-restoring-the-server-hosting-the-central-management-store.md)을 참조하십시오. 백 엔드 서버가 아닌 Enterprise Edition 구성원 서버에서 오류가 발생하면 [Enterprise Edition 구성원 서버 복원](lync-server-2013-restoring-an-enterprise-edition-member-server.md)을 참조하십시오.


> [!TIP]
> 복원을 시작하기 전에 시스템에 대한 이미지 복사본을 만드는 것이 좋습니다. 복원 중 오류가 발생하면 이 이미지를 롤백 지점으로 사용할 수 있습니다. 운영 체제 및 SQL Server를 설치한 후에 이미지 복사본을 만들고 인증서를 복원하거나 다시 등록할 수도 있습니다.



## Enterprise Edition 백 엔드 서버를 복원하려면

1.  오류가 발생한 컴퓨터와 FQDN(정규화된 도메인 이름)이 동일한 정상 상태의 서버 또는 새 서버에 운영 체제를 설치하고 인증서를 복원하거나 다시 등록합니다.
    

    > [!NOTE]
    > 조직의 서버 배포 절차에 따라 이 단계를 수행합니다.



2.  RTCUniversalServerAdmins 그룹의 구성원인 사용자 계정을 사용하여 복원 중인 서버에 로그온합니다.

3.  SQL Server 2012 또는 SQL Server 2008 R2를 설치하고 인스턴스 이름은 오류 이전과 동일하게 유지합니다.
    

    > [!NOTE]
    > 배포에 따라 백 엔드 서버에는 여러 개의 배치되었거나 개별적인 데이터베이스가 포함될 수 있습니다. SQL Server 권한 및 로그인을 포함하여 원래 서버를 배포할 때 사용한 동일한 절차에 따라 SQL Server를 설치합니다.



4.  SQL Server를 설치한 후 다음을 수행합니다.
    
    1.  토폴로지 작성기 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 토폴로지 작성기**를 클릭합니다.
    
    2.  **기존 배포에서 토폴로지 다운로드**를 클릭한 후 **확인**을 클릭합니다.
    
    3.  토폴로지를 선택한 후 **저장**을 클릭합니다. **예**를 클릭하여 선택을 확인합니다.
    
    4.  **Lync Server 2013** 노드를 마우스 오른쪽 단추로 클릭하고 **토폴로지 게시**를 클릭합니다.
    
    5.  **토폴로지 게시** 마법사를 따릅니다. **데이터베이스 만들기** 페이지에서 다시 만들려는 데이터베이스를 선택합니다.
        

        > [!NOTE]
        > 독립 실행형 데이터베이스만 <STRONG>데이터베이스 만들기</STRONG> 페이지에 표시됩니다.

    
    6.  미러링된 백 엔드 서버를 복원하는 경우 **미러 데이터베이스 만들기** 메시지가 표시될 때까지 마법사의 나머지 단계를 계속 수행합니다. 해당 메시지가 표시되면 설치할 데이터베이스를 선택하고 프로세스를 완료합니다.
    
    7.  나머지 마법사의 단계를 따른 후 **마침**을 클릭합니다.
    

    > [!TIP]
    > 토폴로지 작성기를 실행하는 대신 <STRONG>Install-CsDatabase</STRONG> cmdlet을 사용하여 각 데이터베이스를 만들고 <STRONG>Install-CsMirrorDatabase</STRONG> cmdlet을 사용하여 미러링을 구성할 수 있습니다. 자세한 내용은 Lync Server 관리 셸 설명서를 참조하십시오.



5.  다음을 수행하여 사용자 데이터를 복원합니다.
    
    1.  ExportedUserData.zip을 $Backup\\에서 로컬 디렉터리로 복사합니다.
    
    2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.
    
    3.  사용자 데이터를 복원하기 전에 Lync 서비스를 중지해야 합니다. 이렇게 하려면 다음을 입력합니다.
        
            Stop-CsWindowsService
    
    4.  사용자 데이터를 복원하려면 명령줄에 다음을 입력합니다.
        
            Import-CsUserData -PoolFqdn <Fqdn> -FileName <String>
        
        예:
        
            Import-CsUserData -PoolFqdn "atl0cs-001.litwareinc.com" -FileName "C:\Logs\ExportedUserDatal.zip"
    
    5.  다음을 입력하여 Lync 서비스를 다시 시작합니다.
        
            Start-CsWindowsService

6.  이 풀에 응답 그룹을 배포한 경우 응답 그룹 구성 데이터를 복원합니다. 자세한 내용은 [응답 그룹 설정 복원](lync-server-2013-restoring-response-group-settings.md)을 참조하십시오.

7.  보관 또는 모니터링 데이터베이스가 포함된 백 엔드 서버를 복원 중인 경우 SQL Server 도구(예: SQL Server Management Studio)를 사용하여 보관 또는 모니터링 데이터를 복원합니다. 자세한 내용은 [모니터링 또는 보관 데이터 복원](lync-server-2013-restoring-monitoring-or-archiving-data.md)을 참조하십시오.

