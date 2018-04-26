---
title: 'Lync Server 2013: 바이러스 백신 검사 제외'
TOCTitle: Lync Server 2013을 위한 바이러스 백신 검사 제외
ms:assetid: 71e1f1cc-2d16-4111-9864-9276bf24dfe0
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn440138(v=OCS.15)
ms:contentKeyID: 59602775
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013을 위한 바이러스 백신 검사 제외

 

_**마지막으로 수정된 항목:** 2015-02-26_

바이러스 검사 프로그램이 Lync Server 2013의 작동을 방해하지 않도록 하려면 각 Lync Server 2013 서버의 특정 프로세스 및 디렉터리 또는 바이러스 검사 프로그램을 실행하는 서버 역할을 제외해야 합니다. 다음 프로세스 및 디렉터리는 제외해야 합니다.


> [!NOTE]
> 아래 나열된 폴더 및 파일 위치는 Lync Server 2013의 기본 위치입니다. 기본 위치를 사용하지 않는 경우, 이 항목에서 명시된 기본 위치 대신 조직에서 지정한 위치를 제외합니다.



  - Lync Server 2013 프로세스:
    
      - ABServer.exe
    
      - AcpMcuSvc.exe
    
      - ASMCUSvc.exe
    
      - AVMCUSvc.exe
    
      - ChannelService.exe
    
      - ClsAgent.exe
    
      - ComplianceService.exe
    
      - DataMCUSvc.exe
    
      - DataProxy.exe
    
      - FileTransferAgent.exe
    
      - IMMCUSvc.exe
    
      - LysSvc.exe
    
      - MasterReplicatorAgent.exe
    
      - MediaRelaySvc.exe
    
      - MediationServerSvc.exe
    
      - MRASSvc.exe
    
      - OcsAppServerHost.exe
    
      - ReplicaReplicatorAgent.exe
    
      - ReplicationApp.exe
    
      - RtcHost.exe
    
      - RTCSrv.exe
    
      - XmppProxy.exe
    
      - XmppTGW.exe

  - Windows Fabric 호스트 서비스 프로세스:
    
      - Fabric.exe
    
      - FabricDCA.exe
    
      - FabricHost.exe

  - IIS 프로세스:
    
      - %systemroot%\\system32\\inetsrv\\w3wp.exe
    
      - %systemroot%\\SysWOW64\\inetsrv\\w3wp.exe

  - SQL Server 백 엔드 프로세스:
    
      - %ProgramFiles%\\Microsoft SQL Server\\MSSQL11.MSSQLSERVER\\MSSQL\\Binn\\SQLServr.exe
    
      - %ProgramFiles%\\Microsoft SQL Server\\MSRS11.MSSQLSERVER\\Reporting Services\\ReportServer\\Bin\\ReportingServicesService.exe
    
      - %ProgramFiles%\\Microsoft SQL Server\\MSAS11.MSSQLSERVER\\OLAP\\Bin\\MSMDSrv.exe

  - SQL Server 프런트 엔드 프로세스:
    
      - %ProgramFiles%\\Microsoft SQL Server\\MSSQL11.LYNCLOCAL\\MSMQL\\Binn\\SQLServr.exe
    
      - %ProgramFiles%\\Microsoft SQL Server\\MSSQL11.RTCLOCAL\\MSMQL\\Binn\\SQLServr.exe

  - 디렉터리 및 파일:
    
      - %systemroot%\\System32\\LogFiles
    
      - %systemroot%\\SysWow64\\LogFiles
    
      - %systemroot%\\Microsoft.NET\\assembly\\GAC\_MSIL
    
      - %programfiles%\\Microsoft Lync Server 2013
    
      - %programfiles%\\Common Files\\Microsoft Lync Server 2013\\Watcher Node
    
      - %programfiles%\\Common Files\\Microsoft Lync Server 2013
    
      - %SystemDrive%\\RtcReplicaRoot
    
      - 토폴로지 작성기에 지정된 파일 공유 저장소. 파일 저장소는 토폴로지 작성기에 지정되어 있습니다.
    
      - 백 엔드 데이터베이스, 사용자 저장소, 보관 저장소, 모니터링 저장소, 응용 프로그램 저장소에 대한 데이터 및 로그 파일을 비롯한 SQL Server 데이터 및 로그 파일. 데이터베이스 및 로그 파일은 토폴로지 작성기에 지정되어 있을 수 있습니다. 기본 이름을 포함한 각 데이터베이스의 데이터 및 로그 파일에 대한 자세한 내용은 배포 설명서의 [Lync Server 2013에 대한 SQL Server 데이터 및 로그 파일 배치](lync-server-2013-sql-server-data-and-log-file-placement.md)를 참고하세요.
    
      - 프런트 엔드 데이터베이스, Lync 저장소, RtcDatabase 저장소에 대한 데이터 및 로그 파일을 비롯한 SQL Server 데이터 및 로그 파일. 일반적으로 %localdrive%\\CSData에 위치합니다.

