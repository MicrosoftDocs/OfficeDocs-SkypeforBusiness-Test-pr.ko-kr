---
title: 'Lync Server 2013: 풀 장애 조치(failover)'
TOCTitle: 풀 장애 조치(failover)
ms:assetid: 10b13732-bc80-4cb2-a71c-56b1d6cb5bbb
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204678(v=OCS.15)
ms:contentKeyID: 49302838
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 에서 풀 장애 조치(failover)

 

_**마지막으로 수정된 항목:** 2014-10-10_

단일 프런트 엔드 풀에 오류가 발생하여 장애 조치(failover)를 수행해야 하는 경우 다음 절차를 따릅니다. 이 절차에서 Datacenter1은 Pool1을 포함하며 Pool1에서 오류가 발생한 상태입니다. Pool1을 Datacenter2에 있는 Pool2로 장애 조치(failover)합니다.

풀 장애 조치(failover)를 위한 대부분의 작업에서는 필요한 경우 중앙 관리 저장소를 장애 조치(failover)합니다. 풀 사용자를 장애 조치(failover)할 때 중앙 관리 저장소가 작동해야 하므로 이 작업은 중요합니다.

또한 프런트 엔드 풀에 오류가 발생했는데 해당 사이트의 에지 풀은 계속 실행되는 경우에는 에지 풀이 오류가 발생한 풀을 다음 홉 풀로 사용하는지 여부를 확인해야 합니다. 오류가 발생한 풀이 다음 홉 풀로 사용되는 경우에는 해당 프런트 엔드 풀을 장애 조치(failover)하기 전에 다른 프런트 엔드 풀을 사용하도록 에지 풀을 변경해야 합니다. 다음 홉 설정을 변경하는 방법은 에지가 에지 풀과 같은 사이트의 풀을 사용하는지 아니면 다른 사이트의 풀을 사용하는지에 따라 달라집니다.

**에지 풀이 같은 사이트의 다음 홉 풀을 사용하도록 설정하려면**

1.  토폴로지 작성기를 열고 변경해야 하는 에지 풀을 마우스 오른쪽 단추로 클릭한 후에 **속성 편집** 을 클릭합니다.

2.  **다음 홉** 을 클릭합니다. **다음 홉 풀:** 목록에서 다음 홉 풀로 사용할 풀을 선택합니다.

3.  **확인** 을 클릭하고 변경 내용을 게시합니다.

**에지 풀이 다른 사이트의 다음 홉 풀을 사용하도록 설정하려면**

1.  Lync Server 관리 셸 창을 열고 다음 cmdlet을 입력합니다.
    
        Set-CsEdgeServer -Identity EdgeServer:<Edge Server pool FQDN> -Registrar Registrar:<NextHopPoolFQDN>

**재해 발생 시 풀을 장애 조치(failover)하려면**

1.  Pool2의 프런트 엔드 서버에서 다음 cmdlet을 입력하여 중앙 관리 서버에 대한 호스트인 풀을 찾습니다.
    
        Invoke-CsManagementServerFailover -Whatif
    
    이 cmdlet의 결과는 현재 중앙 관리 서버를 호스팅하는 풀을 표시합니다. 이 절차의 나머지 부분에서는 이 풀을 CMS\_Pool로 지칭합니다.

2.  토폴로지 작성기를 사용하여 CMS\_Pool에서 실행 중인 Lync Server의 버전을 찾습니다. Lync Server 2013을 실행 중인 경우에는 다음 cmdlet을 사용하여 Pool1의 백업 풀을 찾습니다.
    
        Get-CsPoolBackupRelationship -PoolFQDN <CMS_Pool FQDN>
    
    Backup\_Pool을 백업 풀로 지정합니다.

3.  다음 cmdlet을 사용하여 중앙 관리 저장소의 상태를 확인합니다.
    
        Get-CsManagementStoreReplicationStatus -CentralManagementStoreStatus 
    
    이 cmdlet은 ActiveMasterFQDN 및 ActiveFileTransferAgents가 모두 CMS\_Pool의 FQDN을 가리키는 것으로 표시해야 합니다. 이 두 항목이 비어 있으면 중앙 관리 서버를 사용할 수 없으므로 장애 조치(failover)를 수행해야 합니다.

4.  중앙 관리 저장소를 사용할 수 없거나 Pool1(오류가 발생한 풀)에서 중앙 관리 저장소를 실행 중이었던 경우에는 풀을 장애 조치(failover)하기 전에 중앙 관리 서버를 장애 조치(failover)해야 합니다. Lync Server 2013을 실행하는 풀에서 호스팅되었던 중앙 관리 서버를 장애 조치(failover)해야 하는 경우에는 이 절차의 5단계에 나와 있는 cmdlet을 사용하세요. Lync Server 2010을 실행하는 풀에서 호스팅되었던 중앙 관리 서버를 장애 조치(failover)해야 하는 경우에는 이 절차의 6단계에 나와 있는 cmdlet을 사용하세요. 중앙 관리 서버를 장애 조치(failover)하지 않아도 되는 경우에는 이 절차의 7단계로 건너뜁니다.

5.  Lync Server 2013을 실행하는 풀에서 중앙 관리 저장소를 장애 조치(failover) 하려면 다음을 수행합니다.
    
      - 먼저 다음을 입력하여 Backup\_Pool에서 중앙 관리 저장소의 기본 인스턴스를 실행하는 백 엔드 서버를 확인합니다.
        
            Get-CsDatabaseMirrorState -DatabaseType Centralmgmt -PoolFqdn <Backup_Pool Fqdn>
    
      - Backup\_Pool의 주 백 엔드 서버가 기본 항목이면 다음을 입력합니다.
        
            Invoke-CSManagementServerFailover -BackupSQLServerFqdn <Backup_Pool Primary BackEnd Server FQDN> -BackupSQLInstanceName <Backup_Pool Primary SQL Instance Name>
        
        Backup\_Pool의 미러 백 엔드 서버가 기본 항목이면 다음을 입력합니다.
        
            Invoke-CSManagementServerFailover -MirrorSQLServerFqdn <Backup_Pool Mirror BackEnd Server FQDN> -MirrorSQLInstanceName <Backup_Pool Mirror SQL Instance Name>
    
      - 중앙 관리 서버 장애 조치(failover)가 완료되었는지 확인합니다. 다음을 입력합니다.
        
            Get-CsManagementStoreReplicationStatus -CentralManagementStoreStatus 
        
        ActiveMasterFQDN 및 ActiveFileTransferAgents가 모두 Backup\_Pool의 FQDN을 가리키는지 확인합니다.
    
      - 마지막으로 다음을 입력하여 모든 프런트 엔드 서버의 복제 상태를 확인합니다.
        
            Get-CsManagementStoreReplicationStatus 
        
        모든 복제본의 값이 True인지 확인합니다.
        
        이 절차의 7단계로 건너뜁니다.

6.  Backup\_Pool의 백 엔드 서버에 중앙 관리 저장소를 설치합니다.
    
      - 먼저 다음 명령을 실행합니다.
        
        ``` 
        Install-CsDatabase -CentralManagementDatabase -Clean -SqlServerFqdn <Backup_Pool Back End Server FQDN> -SqlInstanceName rtc  
        ```
    
      - Backup\_Pool의 프런트 엔드 서버 중 하나에서 다음 명령을 실행하여 중앙 관리 저장소를 강제로 이동합니다.
        
            Move-CsManagementServer -ConfigurationFileName c:\CsConfigurationFile.zip -LisConfigurationFileName c:\CsLisConfigurationFile.zip -Force 
    
      - 이동이 완료되었는지 확인합니다.
        
            Get-CsManagementStoreReplicationStatus -CentralManagementStoreStatus 
        
        ActiveMasterFQDN 및 ActiveFileTransferAgents가 모두 Backup\_Pool의 FQDN을 가리키는지 확인합니다.
    
      - 다음을 입력하여 모든 프런트 엔드 서버의 복제 상태를 확인합니다.
        
            Get-CsManagementStoreReplicationStatus 
        
        모든 복제본의 값이 True인지 확인합니다.
    
      - Backup\_Pool의 나머지 프런트 엔드 서버에 중앙 관리 서버 서비스를 설치합니다. 이렇게 하려면 이 절차의 이전 단계에서 중앙 관리 저장소를 강제로 이동할 때 사용한 프런트 엔드 서버를 제외한 모든 프런트 엔드 서버에서 다음 명령을 실행합니다.
        
            Bootstrapper /Setup 

7.  Lync Server 관리 셸 창에서 다음 cmdlet을 실행하여 사용자를 Pool1에서 Pool2로 장애 조치(failover)합니다.
    
        Invoke-CsPoolFailover -PoolFQDN <Pool1 FQDN> -DisasterMode -Verbose
    
    이 절차의 앞부분에서 중앙 관리 저장소 상태를 확인하기 위해 수행한 단계는 모든 서버에 적용되는 단계가 아니므로, 중앙 관리 저장소가 아직 완전히 장애 조치(failover)되지 않았기 때문에 이 cmdlet이 실패할 가능성이 있습니다. cmdlet이 실패하는 경우에는 표시되는 오류 메시지에 따라 중앙 관리 저장소를 수정하고 이 cmdlet을 다시 실행해야 합니다.
    
    다음 오류 메시지가 표시되는 경우에는 이 사이트의 에지 풀이 다음 홉으로 다른 풀을 사용하도록 변경한 후에 풀을 장애 조치(failover)해야 합니다. 자세한 내용은 이 항목 첫 부분의 절차를 참고하세요.
    
        Invoke-CsPoolFailOver : This Front-end pool "pool1.contoso.com" is specified in
        topology as the next hop for the Edge server. Failing over this pool may cause External
        access/Federation/Split-domain/XMPP features to stop working. Please use Topology Builder to
        change the Edge internal next hop setting to point to a different Front-end pool,  before you
        proceed.

