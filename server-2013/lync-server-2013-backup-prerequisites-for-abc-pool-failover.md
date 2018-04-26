---
title: ABC 풀 장애 조치(failover)를 위한 백업 필수 구성 요소
TOCTitle: ABC 풀 장애 조치(failover)를 위한 백업 필수 구성 요소
ms:assetid: 652046f5-6086-4592-902d-d5789581977d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ945634(v=OCS.15)
ms:contentKeyID: 52056868
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# ABC 풀 장애 조치(failover)를 위한 백업 필수 구성 요소

 

_**마지막으로 수정된 항목:** 2013-03-26_

ABC 풀 장애 조치(failover) 절차 사용 시의 이점을 최대한 활용하려면 재해와 장애 조치(failover) 전에 특정 백업을 수행해야 합니다.

  - **Export-CsLISConfiguration** cmdlet을 사용하여 풀 A에서 LIS(위치 정보 서비스) 구성 데이터를 정기적으로 백업해야 합니다.
    
        Export-csLisConfiguration -FileName <C:\LISExportPrimary.zip>

  - **Export-CsRgsConfiguration** cmdlet을 사용하여 풀 A에서 응답 그룹 구성 데이터를 정기적으로 백업해야 합니다.
    
        Export-CsRgsConfiguration -Source "service:ApplicationServer:<Pool A FQDN>" -FileName "C:\RgsExportPrimary.zip"
    
    일반적으로는 일별 백업을 수행하는 것이 좋지만 변경 내용이 많은 경우에는 백업을 더 자주 수행하도록 예약할 수 있습니다. 재해 시 손실될 수 있는 정보의 양은 백업의 빈도와 변경 내용의 양 및 변경 빈도에 따라 달라집니다.
    
    응답 그룹 응용 프로그램은 응용 프로그램 수준 설정 집합을 풀당 하나씩만 저장할 수 있습니다. **Get-CsRgsConfiguration** cmdlet을 통해 이러한 설정에 액세스할 수 있습니다. 이러한 설정에는 기본 대기 음악 구성, 기본 대기 음악 오디오 파일, 에이전트 다시 연결 유예 기간, 통화 컨텍스트 구성 등이 있습니다. **Import-CsRgsConfiguration** cmdlet에서 **ReplaceExistingSettings** 매개 변수를 사용하면 이러한 설정을 풀 간에 전송할 수 있지만 이 작업을 수행하면 대상 풀의 모든 응용 프로그램 수준 설정이 재정의됩니다.
    

    > [!TIP]
    > 응답 그룹 응용 프로그램을 구성하는 데 사용한 모든 원본 오디오 파일(모든 녹음 파일 또는 대기 음악 파일)의 백업 복사본을 별도의 위치에 보관합니다.

    
    사용자 지정한 대기 음악 파일을 풀에서 통화 대기용으로 업로드한 경우에는 해당 파일의 복사본도 다른 위치에 보관해야 합니다. 이러한 파일은 Lync Server 2013 재해 복구 프로세스의 일부분으로 백업되지 않으며 풀에 업로드한 파일이 손상되거나 지워지면 손실됩니다.
    
        Xcopy  <Source: Pool A CPS File Store Path>  <Destination>
        Example: Xcopy  "<Pool A File Store Path>\LyncFileStore\coX-ApplicationServer-X\AppServerFiles\CPS\"  "<Destination:  Backup location 1>"
    

    > [!NOTE]
    > 통화 대기 응용 프로그램은 설정 집합 및 사용자 지정된 대기 음악 오디오 파일을 풀당 하나씩만 저장할 수 있습니다. <STRONG>Get-CsCpsConfiguration</STRONG> cmdlet을 통해 이러한 설정에 액세스할 수 있습니다. 통화 대기용 재해 복구 메커니즘은 백업 풀의 통화 대기 응용 프로그램을 사용하므로 기본 풀의 설정은 재해 발생 시 백업되거나 보존되지 않습니다. 기본 풀이 손실되면 이러한 설정을 복구할 수 없으며 새 풀을 배포하여 기본 풀을 교체하면 통화 대기 설정 및 사용자 지정된 대기 음악 오디오 파일을 다시 구성해야 합니다.



  - 지정되지 않은 번호 음성 기능의 일부분으로 알림을 구성하는 경우에는 초기 구성 중에 사용한 원본 오디오 파일의 복사본을 다른 위치에 보관하는 것이 좋습니다. 이렇게 하지 않은 경우 오디오 파일을 가져온 서버나 풀의 파일 저장소에서 구성된 오디오 파일의 복사본을 가져올 수 있습니다. 이러한 파일은 Lync Server 2013 재해 복구 프로세스의 일부분으로 백업되지 않으며 풀에 업로드한 파일이 손상되거나 지워지면 손실됩니다. 지정되지 않은 번호 음성 기능을 구성하는 데 사용한 모든 오디오 파일을 서버 또는 풀의 파일 저장소에서 복사하려면 다음 명령을 사용합니다.
    
        Use: Xcopy  <Source: Pool A Announcement Service File Store Path>  <Destination>
        Example Usage:  Xcopy  "<Pool A File Store Path>\X-ApplicationServer-X\AppServerFiles\RGS\AS"  "<Destination: Backup location>"

  - 풀에 모니터링 및 보관 데이터베이스가 있는 경우에는 SQL Server 관리 도구를 사용하여 백업해야 합니다. ABC 장애 조치(failover) 절차에서 모니터링 및 보관 데이터베이스는 Lync Server 백업 서비스를 통해 백업되지 않으므로 풀 A에 배치된 경우 보존되지 않습니다.

