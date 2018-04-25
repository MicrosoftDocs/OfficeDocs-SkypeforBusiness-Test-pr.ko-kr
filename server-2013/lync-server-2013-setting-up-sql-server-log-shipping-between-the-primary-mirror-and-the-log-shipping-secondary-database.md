---
title: 'Lync Server 2013: 기본 미러와 로그 전달 보조 데이터베이스 간의 SQL Server 로그 전달 설정'
TOCTitle: 기본 미러와 로그 전달 보조 데이터베이스 간의 SQL Server 로그 전달 설정
ms:assetid: 4e8e9ce9-4301-47f2-a0c3-669afeb53295
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204887(v=OCS.15)
ms:contentKeyID: 49303584
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 기본 미러와 로그 전달 보조 데이터베이스 간의 SQL Server 로그 전달 설정

 

_**마지막으로 수정된 항목:** 2013-02-21_

기본 영구 채팅 데이터베이스가 미러 데이터베이스로 장애 조치(failover)된 경우 로그 전달을 계속하려면 다음 단계를 수행합니다.

1.  기본 영구 채팅 데이터베이스를 미러로 수동으로 장애 조치(failover)합니다. 이 작업을 수행하려면 Lync Server 관리 셸 및 **Invoke-CsDatabaseFailover** cmdlet을 사용합니다. 자세한 내용은 [Lync Server 2013에서 백 엔드 서버 고가용성을 위해 SQL 미러링 배포](lync-server-2013-deploying-sql-mirroring-for-back-end-server-high-availability.md)에서 " Lync Server 관리 셸 Cmdlet 사용"을 참조하십시오.

2.  SQL Server Management Studio를 사용하여 기본 영구 채팅 서버 미러 인스턴스에 연결합니다.

3.  SQL Server 에이전트가 실행 중인지 확인합니다.

4.  mgc 데이터베이스를 마우스 오른쪽 단추로 클릭하고 **속성** 을 클릭합니다.

5.  **페이지 선택** 에서 **트랜잭션 로그 전달** 을 클릭합니다.

6.  **이 데이터베이스를 로그 전달 구성의 주 데이터베이스로 사용** 확인란을 선택합니다.

7.  **트랜잭션 로그 백업** 에서 **백업 설정** 을 클릭합니다.

8.  **백업 폴더의 네트워크 경로** 상자에 트랜잭션 로그 백업 폴더에 대해 만든 공유의 네트워크 경로를 입력합니다.

9.  백업 폴더가 주 서버에 있는 경우 **백업 폴더가 주 서버에 있는 경우 폴더의 로컬 경로(예: c:\\backup)를 입력하십시오.** 상자에 백업 폴더의 로컬 경로를 입력합니다. 백업 폴더가 주 서버에 있지 않으면 이 상자를 비워 두면 됩니다.
    

    > [!IMPORTANT]
    > 주 서버의 SQL Server 서비스 계정이 로컬 시스템 계정에서 실행되는 경우에는 주 서버에 백업 폴더를 만들고 해당 폴더에 대한 로컬 경로를 지정해야 합니다.



10. **다음보다 오래된 파일 삭제** 및 **다음 기간 내에 백업이 발생하지 않으면 경고** 매개 변수를 구성합니다.

11. **백업 작업** 아래의 **예약** 상자에 나열된 백업 일정을 확인합니다. 설치 예약을 사용자 지정하려면 **예약** 을 클릭하고 필요에 따라 SQL Server 에이전트 예약을 조정합니다.
    

    > [!IMPORTANT]
    > 기본 데이터베이스에 사용한 것과 동일한 설정을 사용하십시오.



12. **압축** 아래에서 **주 서버 설정 사용** 을 선택하고 **확인** 을 클릭합니다.

13. **보조 서버 인스턴스 및 데이터베이스** 에서 **추가** 를 클릭합니다.

14. **연결** 을 클릭하고 보조 서버로 구성한 SQL Server 인스턴스에 연결합니다.

15. **보조 데이터베이스** 상자의 목록에서 **mgc** 데이터베이스를 선택합니다.

16. **보조 데이터베이스 초기화** 탭에서 **아니요, 보조 데이터베이스가 초기화되었습니다.** 옵션을 선택합니다.

17. **파일 복사** 탭의 **복사된 파일의 대상 폴더** 에 트랜잭션 로그 백업을 복사할 폴더 경로를 입력하고 **확인** 을 클릭합니다. 이 폴더는 주로 보조 서버에 있습니다.

18. **스크립트 구성** 드롭다운 목록에서 **구성을 새 쿼리 창으로 스크립팅** 을 선택합니다.

19. 새 쿼리 창의 **데이터베이스 속성** 에서 **확인** 을 클릭하여 구성 프로세스를 시작합니다.

20. \*\*\*\*\*\* End: Script to be run at Primary: \*\*\*\*\*\* 행까지 쿼리의 처음 절반을 선택하고 실행합니다(18단계 참조).
    

    > [!IMPORTANT]
    > SQL Server Management Studio에서는 SQL Server 로그 전달 구성에서 여러 개의 기본 데이터베이스를 지원하지 않기 때문에 이 스크립트를 수동으로 실행해야 합니다.



21. **취소** 를 선택하여 로그 파일 전달 구성 패널을 닫고 기본 데이터베이스 및 미러링된 데이터베이스(장애 조치(failover)의 경우) 모두 로그 파일 전달을 올바르게 구현하는 작동하는 설치를 설정합니다.

22. 기본 영구 채팅 데이터베이스를 기본 데이터베이스로 수동으로 복구(failover)합니다. 이 작업을 수행하려면 Lync Server 관리 셸 및 **Invoke-CsDatabaseFailover** cmdlet을 사용합니다. 자세한 내용은 [Lync Server 2013에서 백 엔드 서버 고가용성을 위해 SQL 미러링 배포](lync-server-2013-deploying-sql-mirroring-for-back-end-server-high-availability.md)에서 " Lync Server 관리 셸 Cmdlet 사용"을 참조하십시오.

## 참고 항목

#### 개념

[Lync Server 2013에서 백 엔드 서버 고가용성을 위해 SQL 미러링 배포](lync-server-2013-deploying-sql-mirroring-for-back-end-server-high-availability.md)  
[Lync Server 2013에서 백 엔드 서버 고가용성을 위해 SQL 미러링 배포](lync-server-2013-deploying-sql-mirroring-for-back-end-server-high-availability.md)

