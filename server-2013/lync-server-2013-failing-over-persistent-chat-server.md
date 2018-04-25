---
title: 'Lync Server 2013: 영구 채팅 서버 장애 조치(failover)'
TOCTitle: 영구 채팅 서버 장애 조치(failover)
ms:assetid: 2cd79ffd-fee6-44ce-96cf-b98bf25e2690
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204772(v=OCS.15)
ms:contentKeyID: 49303161
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 영구 채팅 서버 장애 조치(failover)

 

_**마지막으로 수정된 항목:** 2014-02-05_

영구 채팅 서버에 대한 장애 조치(failover)는 기본적으로 수동 프로세스로 디자인됩니다.

장애 조치(failover) 절차는 보조 데이터 센터가 작동하며 실행 중이지만 다음을 비롯하여 주 영구 채팅 데이터베이스가 있는 영구 채팅 서버 서비스는 완전히 사용할 수 없다는 가정을 기반으로 합니다.

  - 영구 채팅 서버 주 데이터베이스 및 영구 채팅 서버 미러 데이터베이스가 다운되었습니다.

  - Lync Server프런트 엔드 서버가 다운되었습니다.

이 절차는 다음과 같은 두 기본 단계를 기반으로 합니다.

  - 주 영구 채팅 데이터베이스(mgc)를 복구합니다.

  - 새 주 데이터베이스에 대해 미러링을 설정합니다.

영구 채팅 준수 데이터베이스(mgccomp)는 장애 조치(failover)되지 않습니다. 이 데이터베이스의 콘텐츠는 일시적인 항목이며 준수 어댑터가 데이터를 처리하면 삭제됩니다. 영구 채팅 관리자는 데이터 손실을 방지하기 위해 어댑터를 올바르게 관리해야 합니다.

## 영구 채팅 서버 장애 조치(failover)를 수행하려면

1.  영구 채팅 서버 백업 로그 전달 데이터베이스에서 로그 전달을 제거합니다.
    
    1.  SQL Server Management Studio를 사용하여 영구 채팅 서버 백업 mgcc 데이터베이스가 있는 데이터베이스 인스턴스에 연결합니다.
    
    2.  마스터 데이터베이스에 대한 쿼리 창을 엽니다.
    
    3.  다음 명령을 사용하여 로그 전달을 삭제합니다.
        
            exec sp_delete_log_shipping_secondary_database mgc

2.  복사되지 않은 백업 파일을 백업 공유에서 백업 서버의 복사 대상 폴더로 복사합니다.

3.  시퀀스에서 적용되지 않은 트랜잭션 로그 백업을 보조 데이터베이스에 적용합니다. 자세한 내용은 "방법: 트랜잭션 로그 백업 적용(Transact-SQL)"(http://go.microsoft.com/fwlink/?linkid=247428\&clcid=0x412)을 참조하십시오.

4.  백업 mgc 데이터베이스를 온라인 상태로 설정합니다. 1b단계에서 연 쿼리 창을 사용하여 다음을 수행합니다.
    
    1.  mgc 데이터베이스에 대한 연결이 있는 경우 모두 종료합니다.
        
        1.  **exec sp\_who2** 를 사용하여 mgc 데이터베이스에 대한 연결을 식별합니다.
        
        2.  **kill \<SPID\>** 를 사용하여 해당 연결을 종료합니다.
    
    2.  데이터베이스를 온라인 상태로 설정합니다.
        
        1.  **restore database mgc with recovery를 실행합니다.**

5.  Lync Server 관리 셸에서 **Set-CsPersistentChatState -Identity "service:atl-cs-001.litwareinc.com" –PoolState FailedOver** 명령을 사용하여 mgc 백업 데이터베이스에 대한 장애 조치를 수행합니다. atl-cs-001.litwareinc.com에 대한 영구 채팅 풀의 정규화된 도메인 이름을 대체해야 합니다.
    
    이제 mgc 백업 데이터베이스가 주 데이터베이스로 사용됩니다.

6.  Lync Server 관리 셸에서 **Install-CsMirrorDatabase** cmdlet을 사용하여 이제 주 데이터베이스로 사용되는 백업 데이터베이스에 대한 고가용성 미러를 설정합니다. 백업 데이터베이스 인스턴스를 주 데이터베이스로, 백업 미러 데이터베이스 인스턴스를 미러 인스턴스로 사용합니다. 이 미러는 설치 중에 주 데이터베이스에 대해 처음 구성한 미러와는 다릅니다. 자세한 내용은 [Lync Server 2013에서 백 엔드 서버 고가용성을 위해 SQL 미러링 배포](lync-server-2013-deploying-sql-mirroring-for-back-end-server-high-availability.md)에서 " Lync Server 관리 셸 cmdlet 사용"을 참조하십시오.

7.  영구 채팅 서버를 활성 서버로 설정합니다. Lync Server 명령 셸에서 **Set-CsPersistentChatActiveServer** cmdlet을 사용하여 활성 서버 목록을 설정합니다.
    

    > [!IMPORTANT]
    > 모든 활성 서버는 새 기본 데이터베이스와 동일한 데이터 센터 내에 배치하거나 데이터베이스에 대한 연결 대기 시간이 낮고 대역폭이 높은 데이터 센터에 배치해야 합니다.

    
    이제 영구 채팅 서버 주 데이터베이스에서 영구 채팅 서버 백업 데이터베이스로의 장애 조치(failover)가 정상적으로 완료됩니다.

