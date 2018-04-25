---
title: 미러링된 Enterprise Edition 백 엔드 서버 복원 - 기본
TOCTitle: 미러링된 Enterprise Edition 백 엔드 서버 복원 - 기본
ms:assetid: bc555b46-70c5-4eee-ae91-e195df238293
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ945648(v=OCS.15)
ms:contentKeyID: 52056950
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 미러링된 Enterprise Edition 백 엔드 서버 복원 - 기본

 

_**마지막으로 수정된 항목:** 2013-02-17_

Enterprise Edition 백 엔드가 미러링되어 있으며 기본 데이터베이스에서만 오류가 발생하는 경우 이 섹션의 절차를 따르십시오. 기본 데이터베이스와 미러 데이터베이스에서 모두 오류가 발생하면[Enterprise Edition 백 엔드 서버 복원](lync-server-2013-restoring-an-enterprise-edition-back-end-server.md)을 참조하십시오. 미러에서만 오류가 발생하면 [미러링된 Enterprise Edition 백 엔드 서버 복원 - 미러](lync-server-2013-restoring-a-mirrored-enterprise-edition-back-end-server-mirror.md)을 참조하십시오. 중앙 관리 저장소를 호스트하는 데이터베이스에서 오류가 발생하면 [중앙 관리 저장소를 호스트하는 서버 복원](lync-server-2013-restoring-the-server-hosting-the-central-management-store.md)을 참조하십시오. 백 엔드 서버가 아닌 Enterprise Edition 구성원 서버에서 오류가 발생하면 [Enterprise Edition 구성원 서버 복원](lync-server-2013-restoring-an-enterprise-edition-member-server.md)을 참조하십시오.

복원을 시작하기 전에 시스템에 대한 이미지 복사본을 만드는 것이 좋습니다. 복원 중 오류가 발생하면 이 이미지를 롤백 지점으로 사용할 수 있습니다. 운영 체제 및 SQL Server를 설치한 후에 이미지 복사본을 만들고 인증서를 복원하거나 다시 등록할 수도 있습니다.

이 항목에서 예제 기본 데이터베이스의 FQDN(정규화된 도메인 이름)은 BE1.contoso.com이고 미러 데이터베이스의 FQDN은 BE2.contoso.com입니다.

## Enterprise Edition 백 엔드 서버 기본 데이터베이스를 복원하려면

1.  RTCUniversalServerAdmins 그룹의 구성원인 사용자 계정에서 프런트 엔드 서버에 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  구성된 모든 데이터베이스가 미러로 장애 조치(failover)되도록 강제 지정합니다. 이 서버에서 구성한 각 데이터베이스 유형에 대해 다음 cmdlet을 입력합니다.
    
        Invoke-CsDataBaseFailover -PoolFqdn <Pool FQDN> -DatabaseType <Configured Database Type> -NewPrincipal Mirror -Force -Verbose
    
    예를 들면 다음과 같습니다.
    
        Invoke-CsDataBaseFailover -PoolFqdn pool0.vdomain.com -DatabaseType User -NewPrincipal Mirror -Force -Verbose
    

    > [!WARNING]
    > 미러링 모니터 서버와 동기화된 미러링을 사용하도록 백 엔드 데이터베이스를 구성한 경우 장애 조치(failover)가 자동으로 수행됩니다.



4.  장애 조치(failover)를 완료한 후에 다음을 수행합니다.
    
      - 토폴로지 작성기 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 토폴로지 작성기**를 클릭합니다.
    
      - 백 엔드 서버에서 미러링을 사용하지 않도록 설정합니다. 이렇게 하려면 **Enterprise Edition 프런트 엔드 풀** 아래의 풀을 마우스 오른쪽 단추로 클릭하고 **속성 편집**을 선택합니다. 그런 다음 **일반** 탭의 **연결**에서 **SQL Server 저장소 미러링 사용** 확인란 선택을 취소합니다. 필요에 따라 보관 및 모니터링에 대해 이 작업을 수행합니다. 그리고 나서 **확인**을 클릭합니다.
    
      - Lync Server 2013 노드를 마우스 오른쪽 단추로 클릭하고 **토폴로지**, **게시**를 차례로 클릭합니다.
    
      - 아직 작동하는 백 엔드(BE2.contoso.com)를 새 SQL 저장소로 선택합니다. 이렇게 하려면 **Enterprise Edition 프런트 엔드 풀** 아래의 풀을 마우스 오른쪽 단추로 클릭하고 **속성 편집**을 선택합니다. 그런 다음 **일반** 탭의 **연결** 아래 **SQL Server 저장소** 필드에 작동하는 백 엔드의 FQDN(이 예제에서는 BE2.contoso.com)을 입력합니다.
    
      - Lync Server 2013 노드를 마우스 오른쪽 단추로 클릭하고 **토폴로지**, **게시**를 차례로 클릭합니다.
    
      - 각 서버가 새 토폴로지를 읽을 수 있도록 서비스를 다시 시작합니다. Lync Server 관리 셸에서 이 풀에 속하는 각 프런트 엔드 서버에 대해 다음 cmdlet을 실행합니다.
        
            Stop-CsWindowsService
            Start-CsWindowsService

5.  미러링을 제거합니다. Lync Server 관리 셸에서 다음 cmdlet을 실행합니다.
    
        Uninstall-CsMirrorDatabase -DatabaseType User -SqlServerFqdn <MirrorServerFqdn> -SqlInstanceName <SQLInstance> -verbose
    
    예를 들면 다음과 같습니다.
    
        Uninstall-CsMirrorDatabase -DatabaseType User -SqlServerFqdn DB2.contoso.com -SqlInstanceName rtc -verbose
    
    이 서버의 모든 데이터베이스 유형에 대해 이 작업을 수행합니다.

6.  오류가 발생한 컴퓨터와 FQDN이 DB1.contoso.com으로 동일한 정상 상태의 서버 또는 새 서버를 만들고 운영 체제를 설치한 다음 인증서를 복원하거나 다시 등록합니다. 이 서버는 새 미러로 작동합니다.

7.  RTCUniversalServerAdmins 그룹의 구성원인 사용자 계정에서 새 서버에 로그온합니다.

8.  SQL Server 2012 또는 SQL Server 2008 R2를 설치하고 인스턴스 이름은 오류 이전과 동일하게 유지합니다.

9.  RTCUniversalServerAdmins 그룹의 구성원인 사용자 계정에서 프런트 엔드 서버에 로그온합니다.

10. 토폴로지 작성기를 사용하여 미러 DB를 설치합니다. 이렇게 하려면 다음 단계를 수행합니다.
    
      - 토폴로지 작성기 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 토폴로지 작성기**를 클릭합니다.
    
      - 백 엔드 서버에서 미러링을 사용하도록 설정합니다. 이렇게 하려면 **Enterprise Edition 프런트 엔드 풀** 아래의 풀을 마우스 오른쪽 단추로 클릭하고 **속성 편집**을 선택합니다. 그런 다음 **일반** 탭의 **연결**에서 **SQL Server 저장소 미러링 사용** 확인란을 선택합니다. 또한 필요한 경우 보관 및 모니터링에 대해 이 작업을 수행합니다.
        
        그런 다음 **미러링 SQL Server 저장소** 필드에 새 서버의 FQDN(이 예제에서는 BE1.contoso.com)을 입력합니다. 그리고 **확인**을 클릭합니다.
    
      - Lync Server 2013 노드를 마우스 오른쪽 단추로 클릭하고 **토폴로지**, **데이터베이스 설치**를 차례로 클릭합니다.
    
      - **데이터베이스 설치** 마법사를 따릅니다. **데이터베이스 만들기** 페이지에서 다시 만들 데이터베이스를 선택합니다.
    
      - **미러 데이터베이스 만들기** 메시지가 나타날 때까지 마법사를 계속 진행합니다. 해당 메시지가 표시되면 설치할 데이터베이스를 선택하고 이 프로세스를 완료합니다.

