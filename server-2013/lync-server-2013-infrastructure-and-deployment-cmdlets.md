---
title: 인프라 및 배포 Cmdlet
TOCTitle: 인프라 및 배포 Cmdlet
ms:assetid: 0a6e872a-9f70-4f23-a4a5-8820dbf55370
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398153(v=OCS.15)
ms:contentKeyID: 49302758
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 인프라 및 배포 Cmdlet

 

_**마지막으로 수정된 항목:** 2012-10-09_

Microsoft Lync Server 2013에 포함된 인프라 및 배포 cmdlet은 제품 초기 설치 및 배포 시에 유용할 수 있습니다. Lync Server를 배포한 후에는 이러한 cmdlet을 사용하여 구성 요소가 정상적으로 작동하는지 확인하고, 복제 설정을 관리하고, Lync Server 토폴로지/정책/구성 설정을 백업 및 복원하는 등의 작업을 수행할 수 있습니다.

## 인프라 및 배포 Cmdlet

대부분의 인프라 및 배포는 관리자가 직접 호출해야 하는 경우가 거의 없습니다. 설치 프로그램 또는 토폴로지 작성기를 실행하면 이러한 cmdlet이 자동으로 호출되기 때문입니다. 단, 한 가지 중요한 예외는 **Export-CsConfiguration** cmdlet입니다. 이 cmdlet은 Lync Server 토폴로지, 정책 및 구성 설정의 백업 복사본을 만드는 데 사용할 수 있습니다. 그러나 필요한 경우에는 Lync Server 관리 셸 또는 스크립트에서도 인프라 및 배포 cmdlet을 실행할 수 있습니다. 스크립트를 사용하면 특정 작업을 자동화할 수 있습니다. 다음은 인프라 및 배포에 직접적으로 관련된 cmdlet 목록입니다.

**[Active Directory Cmdlet](lync-server-2013-active-directory-cmdlets.md)**

  -   
    [Disable-CsAdDomain](disable-csaddomain.md)

  -   
    [Enable-CsAdDomain](enable-csaddomain.md)

  -   
    [Get-CsAdDomain](get-csaddomain.md)

  -   
    [Disable-CsAdForest](disable-csadforest.md)

  -   
    [Enable-CsAdForest](enable-csadforest.md)

  -   
    [Get-CsAdForest](get-csadforest.md)

  -   
    [Get-CsAdServerSchema](get-csadserverschema.md)

  -   
    [Install-CsAdServerSchema](install-csadserverschema.md)

**[복제 Cmdlet](lync-server-2013-replication-cmdlets.md)**

  -   
    [Debug-CsInterPoolReplication](debug-csinterpoolreplication.md)

  -   
    [Invoke-CsManagementStoreReplication](invoke-csmanagementstorereplication.md)

  -   
    [Get-CsManagementStoreReplicationStatus](get-csmanagementstorereplicationstatus.md)

  -   
    [Enable-CsReplica](enable-csreplica.md)

  -   
    [Test-CsReplica](test-csreplica.md)

  -   
    [Get-CsUserReplicatorConfiguration](get-csuserreplicatorconfiguration.md)

  -   
    [New-CsUserReplicatorConfiguration](new-csuserreplicatorconfiguration.md)

  -   
    [Remove-CsUserReplicatorConfiguration](remove-csuserreplicatorconfiguration.md)

  -   
    [Set-CsUserReplicatorConfiguration](set-csuserreplicatorconfiguration.md)

**[토폴로지 Cmdlet](lync-server-2013-topology-cmdlets.md)**

  -   
    [Get-CsPool](get-cspool.md)

  -   
    [Get-CsSite](get-cssite.md)

  -   
    [Set-CsSite](set-cssite.md)

  -   
    [Enable-CsTopology](enable-cstopology.md)

  -   
    [Get-CsTopology](get-cstopology.md)

  -   
    [Publish-CsTopology](publish-cstopology.md)

  -   
    [Test-CsTopology](test-cstopology.md)

  -   
    [Export-CsConfiguration](export-csconfiguration.md)

  -   
    [Import-CsConfiguration](import-csconfiguration.md)

  -   
    [Get-CsServerVersion](get-csserverversion.md)

  -   
    [Disable-CsComputer](disable-cscomputer.md)

  -   
    [Enable-CsComputer](enable-cscomputer.md)

  -   
    [Get-CsComputer](get-cscomputer.md)

  -   
    [Test-CsComputer](test-cscomputer.md)

  -   
    [Get-CsNetworkInterface](get-csnetworkinterface.md)

**[백업 및 고가용성 Cmdlet](lync-server-2013-backup-and-high-availability-cmdlets.md)**

  - [Get-CsBackupServiceConfiguration](get-csbackupserviceconfiguration.md)

  - [Remove-CsBackupServiceConfiguration](remove-csbackupserviceconfiguration.md)

  - [Set-CsBackupServiceConfiguration](set-csbackupserviceconfiguration.md)

  - [Get-CsBackupServiceStatus](get-csbackupservicestatus.md)

  - [Invoke-CsBackupServiceSync](invoke-csbackupservicesync.md)

  - [Debug-CsIntraPoolReplication](debug-csintrapoolreplication.md)

  - [Backup-CsPool](backup-cspool.md)

  - [Get-CsPoolBackupRelationship](get-cspoolbackuprelationship.md)

  - [Get-CsPoolFabricState](get-cspoolfabricstate.md)

  - [Invoke-CsPoolFailBack](invoke-cspoolfailback.md)

  - [Invoke-CsPoolFailOver](invoke-cspoolfailover.md)

  - [Get-CsPoolUpgradeReadinessState](get-cspoolupgradereadinessstate.md)

  - [Invoke-CsStorageServiceFlush](invoke-csstorageserviceflush.md)

  - [Sync-CsUserData](sync-csuserdata.md)

  - [Remove-CsUserStoreBackupData](remove-csuserstorebackupdata.md)

## 참고 항목

#### 기타 리소스

[Lync Server PowerShell 블로그](http://go.microsoft.com/fwlink/?linkid=203150%26clcid=0x412)

