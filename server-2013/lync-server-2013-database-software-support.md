---
title: Lync Server 2013 데이터베이스 소프트웨어 지원
TOCTitle: 데이터베이스 소프트웨어 지원
ms:assetid: e05d0032-bbea-4e61-987d-d07b1c045fd5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398990(v=OCS.15)
ms:contentKeyID: 49305288
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 데이터베이스 소프트웨어 지원

 

_**마지막으로 수정된 항목:** 2014-12-01_

Lync Server 2013은 다음과 같은 데이터베이스 관리 시스템을 지원합니다.

  - **프런트 엔드 풀의 백 엔드 데이터베이스, 보관 데이터베이스, 모니터링 데이터베이스, 영구 채팅 데이터베이스 및 영구 채팅 준수 데이터베이스**
    
      - Microsoft SQL Server 2008 R2 Enterprise 데이터베이스 소프트웨어(64비트 버전). 최신 서비스 팩을 추가로 실행하는 것이 좋습니다.
    
      - Microsoft SQL Server 2008 R2 Standard(64비트 버전). 최신 서비스 팩을 추가로 실행하는 것이 좋습니다.
    
      - Microsoft SQL Server 2012 Enterprise(64비트 버전). 최신 서비스 팩을 추가로 실행하는 것이 좋습니다.
    
      - Microsoft SQL Server 2012 Standard(64비트 버전). 최신 서비스 팩을 추가로 실행하는 것이 좋습니다.

  - **Standard Edition 서버 데이터베이스 및 프런트 엔드 서버 데이터베이스**
    
      - Microsoft SQL Server 2012 Express(64비트 버전). 또한 최신 서비스 팩을 실행하는 것이 좋습니다.
        
        Microsoft는 프런트 엔드 서버 및 Standard Edition 서버에서 Microsoft SQL Server 패치 및 업그레이드를 지원합니다. 그러나 프런트 엔드 서버에서 어떤 종류의 업그레이드 및 패치를 만드는 경우에나 쿼럼 요구 사항을 확인해야 합니다. 자세한 내용은 [Lync Server 2013에서 프런트 엔드 서버 업그레이드 또는 업데이트](lync-server-2013-upgrade-or-update-front-end-servers.md) 및 [Lync Server 2013 의 프런트 엔드 서버, 메신저 및 현재 상태에 대한 토폴로지 및 구성 요소](lync-server-2013-topologies-and-components-for-front-end-servers-instant-messaging-and-presence.md)를 참조하세요.
    

    > [!NOTE]
    > Microsoft SQL Server 2012 Express(64비트 버전)는 각 Standard Edition 서버 및 각 프런트 엔드 서버 서버에서 Lync Server 2013으로 자동 설치됩니다.




> [!IMPORTANT]
> <UL>
> <LI>
> <P>Lync Server 2013에서는 SQL Server의 32비트 버전을 지원하지 않으므로 64비트 버전을 사용해야 합니다.</P>
> <LI>
> <P>SQL Server Web Edition 및 SQL Server Workgroup Edition은 지원되지 않으므로 Lync Server 2013에서 사용할 수 없습니다.</P>
> <LI>
> <P>Lync Server 2013에서는 기본 데이터베이스 미러링이 지원됩니다.</P>
> <LI>
> <P>모니터링 서버 역할을 사용하려면 SQL Server Reporting Services를 설치해야 합니다.</P></LI></UL>



프런트 엔드 풀에서는 백 엔드 데이터베이스가 단일 SQL Server 컴퓨터가 될 수 있습니다.


> [!IMPORTANT]
> Lync Server 데이터베이스를 다른 데이터베이스와 함께 배치하는 경우에는 가용성과 성능에 영향을 줄 수 있는 모든 요인을 평가하고 한 노드에 장애가 발생하면 나머지 노드에서 부하를 처리할 수 있도록 하는 것이 구성하는 것이 좋습니다. 장애 조치(failover) 기능을 확인하려면 모든 장애 조치(failover) 시나리오를 테스트하세요.



## SQL 미러링 및 SQL 클러스터링 사용

Lync Server 2013는 Lync Server 데이터베이스 각각에 대해 SQL 미러링 또는 SQL 클러스터링 사용을 지원합니다. SQL 미러링은 Lync Server 2013의 토폴로지 작성기 도구를 사용하여 손쉽게 설정할 수 있습니다. SQL 장애 조치(failover) 클러스터링의 경우 설정을 위해 SQL Server를 사용해야 합니다.

Lync Server 2013은 모든 배포에 대해 SQL 미러링과 SQL 클러스터링 토폴로지를 모두 지원합니다. 여기에는 신규 배포와 이전 버전의 Lync Server에서 업그레이드한 조직이 포함됩니다.

SQL 클러스터링 지원은 능동/수동 구성을 위한 것으로, 성능을 위해 수동 노드는 다른 SQL 인스턴스와 공유하지 말아야 합니다.

다음과 같은 지원이 포함됩니다.

  - 다음을 위한 2개 노드 장애 조치(failover) 클러스터링:
    
      - Microsoft SQL Server 2012 Standard(64비트 버전). 최신 서비스 팩을 추가로 실행하는 것이 좋습니다.
    
      - Microsoft SQL Server 2008 R2 Standard(64비트 버전). 최신 서비스 팩을 추가로 실행하는 것이 좋습니다.

  - 다음을 위한 최대 16개 노드 장애 조치(failover) 클러스터링:
    
      - Microsoft SQL Server 2012 Enterprise(64비트 버전). 최신 서비스 팩을 추가로 실행하는 것이 좋습니다.
    
      - Microsoft SQL Server 2008 R2 Enterprise 데이터베이스 소프트웨어(64비트 버전). 최신 서비스 팩을 추가로 실행하는 것이 좋습니다.

SQL 미러링에 대한 자세한 내용은 [Lync Server 2013의 백 엔드 서버 고가용성](lync-server-2013-back-end-server-high-availability.md)을 참고하세요. SQL 클러스터링을 배포하는 방법에 대한 자세한 내용은 [Lync Server 2013용 SQL 서버 클러스터링 구성](lync-server-2013-configure-sql-server-clustering.md)을 참고하세요.

SQL Server 2012의 장애 조치(failover) 클러스터링에 대한 자세한 내용 및 모범 사례는 <http://technet.microsoft.com/ko-kr/library/hh231721.aspx>를 참고하세요. SQL Server 2008의 장애 조치(failover) 클러스터링의 경우에는 <http://technet.microsoft.com/ko-kr/library/ms189134(v=sql.105).aspx>를 참고하세요.

