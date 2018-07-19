---
title: 'Lync Server 2013: 프런트 엔드 풀 ABC 장애 조치(failover) 절차'
TOCTitle: 프런트 엔드 풀 ABC 장애 조치(failover) 절차
ms:assetid: 67763ad3-6796-45eb-a486-901f21ac1a95
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ945635(v=OCS.15)
ms:contentKeyID: 52056860
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 프런트 엔드 풀 ABC 장애 조치(failover) 절차

 

_**마지막으로 수정된 항목:** 2014-05-22_

다음 단계에 따라 ABC 장애 조치(failover) 절차를 수행합니다. 이 절차에는 각 단계의 간략한 설명과 각 단계에 대해 실행할 명령 및 cmdlet이 포함되어 있습니다.

cmdlet을 실행하려면 관리자 권한으로 실행 명령을 사용하여 Lync Server 관리 셸을 엽니다.

## ABC 장애 조치(failover)를 수행하려면

1.  풀 A가 CMS(중앙 관리 서버)의 호스트인지 확인합니다.
    
      - 다음 cmdlet을 실행합니다.
        
            Get-CsService -CentralManagement
        
        활성 CMS의 ID 필드가 풀 A의 FQDN(정규화된 도메인 이름)을 가리키는 경우 이 절차의 2-3단계를 수행하여 중앙 관리 서버를 먼저 장애 조치(failover)할 수 있습니다. 그렇지 않은 경우에는 4단계로 건너뜁니다.

2.  다음 cmdlet을 사용하여 재해 복구 모드에서 CMS를 풀 B로 장애 조치(failover)합니다.
    
        Invoke-CsManagementServerFailover -BackupSqlServerFqdn <Pool B BE FQDN> -BackupSqlInstanceName <Pool B BE instance name> [-BackupMirrorSqlServerFqdn <Pool B Mirror BE FQDN> -BackupMirrorSqlInstanceName <Pool B Mirror BE Instance name>] -Force -Verbose
    
    이 작업을 수행한 후에는 탄성을 개선하기 위해 CMS를 풀 B에서 쌍을 이루는 기존의 다른 풀로 이동하는 것이 좋습니다. 자세한 내용은 [Move-CsManagementServer](https://docs.microsoft.com/en-us/powershell/module/skype/Move-CsManagementServer)를 참조하십시오.

3.  풀 A에 CMS가 포함되어 있으면 LIS 구성을 풀 A에서 풀 B의 LIS 데이터베이스(Lis.mdf)로 가져옵니다. 이 작업은 LIS 데이터를 정기적으로 백업한 경우에만 수행할 수 있습니다. LIS 구성을 가져오려면 다음 cmdlet을 실행합니다.
    
        Import-CsLisConfiguration -FileName <String> 
        Publish-CsLisConfiguration

4.  백업된 Lync Server 응답 그룹 서비스 워크플로를 풀 A에서 풀 B로 가져옵니다.
    

    > [!NOTE]
    > 현재 <STRONG>Import-CsRgsConfiguration</STRONG> cmdlet을 사용하려면 풀 A의 대기열 및 워크플로 이름이 풀 B의 대기열 및 워크플로 이름과 달라야 합니다. 이들 이름이 다르지 않으면 <STRONG>Import-CsRgsConfiguration</STRONG> cmdlet 실행 시 오류가 발생하며 <STRONG>Import-CsRgsConfiguration</STRONG> cmdlet을 계속 실행하기 전에 풀 B에서 대기열 및 워크플로 이름을 바꿔야 합니다.

    
    응답 그룹 구성을 풀 A에서 풀 B로 가져올 때는 두 가지 옵션을 사용할 수 있습니다. 풀 B의 응용 프로그램 수준 설정을 풀 A의 응용 프로그램 수준 설정으로 덮어쓸지 여부에 따라 사용하는 옵션이 달라집니다.
    
      - 풀 B 설정을 덮어쓰려면 **ReplaceExistingSettings** 옵션을 포함하여 **Import-CsRgsConfiguration** cmdlet을 실행합니다.
        
            Import-CsRgsConfiguration -Destination "service:ApplicationServer:<Pool B FQDN>" -FileName "C:\RgsExportPrimary.zip"  -ReplaceExistingRgsSettings
    
      - 풀 B 설정을 덮어쓰지 않으려면 **ReplaceExistingSettings** 옵션을 포함하지 않고 **Import-CsRgsConfiguration** cmdlet을 사용합니다.
        
            Import-CsRgsConfiguration -Destination "service:ApplicationServer:<Pool B FQDN>" -FileName "C:\RgsExportPrimary.zip"
    

    > [!WARNING]
    > 백업 풀(풀 B)의 응용 프로그램 수준 설정을 기본 풀(풀 A)의 설정으로 덮어쓰지 않는 경우에는 풀 A가 손실되면 풀 A의 응용 프로그램 수준 설정도 손실됩니다. 응답 그룹 응용 프로그램은 풀당 응용 프로그램 수준 설정 집합을 하나만 저장할 수 있기 때문입니다. 풀 C를 배포하여 풀 A를 대체할 때는 기본 대기 음악 오디오 파일을 비롯하여 응용 프로그램 수준 설정을 다시 구성해야 합니다.



5.  다음 cmdlet을 실행해 가져온 응답 그룹을 표시하여 응답 그룹 구성 가져오기가 정상적으로 수행되었는지 확인합니다. 가져온 응답 그룹은 아직 풀 A의 소유입니다.
    
        Get-CsRgsWorkflow -Identity "service:ApplicationServer:<Pool B FQDN>" -Owner "service:ApplicationServer:<Pool A FQDN>"
        
        Get-CsRgsQueue -Identity "service:ApplicationServer:<Pool B FQDN>" -Owner "service:ApplicationServer:<Pool A FQDN>"
        
        Get-CsRgsAgentGroup -Identity "service:ApplicationServer:<Pool B FQDN>" -Owner "service:ApplicationServer:<Pool A FQDN>"

6.  지정되지 않은 번호의 경우 선택한 알림 서비스로 "알림"을 사용 중인 지정되지 않은 번호 범위를 풀 A에서 풀 B로 이동합니다. 이렇게 하려면 다음을 수행합니다.
    
      - 풀 A에서 배포한 모든 알림을 풀 B에서 다시 만듭니다. 풀 A에서 알림을 배포할 때 오디오 파일을 사용한 경우 풀 B에서 알림을 다시 만들려면 이러한 파일이 필요합니다. 풀 B에서 알림을 다시 만들려면 풀 B를 상위 서비스로 지정하여 **New-CsAnnouncement** cmdlet을 사용합니다.
    
      - 풀 A의 알림이 대상으로 설정된 모든 지정되지 않은 번호 범위의 대상을 풀 B에 새로 배포한 알림으로 다시 설정합니다. 이렇게 하려면 풀 A의 알림이 대상으로 설정된 모든 지정되지 않은 번호 범위에 대해 다음 cmdlet을 실행합니다.
        
            Set-CsUnassignedNumber -Identity "<Range Name>" -AnnouncementService "<Pool B FQDN>" -AnnouncementName "<New Announcement in pool B>"
    

    > [!NOTE]
    > 선택한 알림 서비스로 "Exchange UM"을 사용하는 지정되지 않은 번호 범위에 대해서는 이 단계를 수행할 필요가 없습니다.



7.  다음 cmdlet을 실행하여 DR(재해 복구) 모드에서 풀 A를 풀 B로 장애 조치(failover)합니다.
    
        Invoke-CsPoolFailover -PoolFqdn <Pool A FQDN> -DisasterMode

8.  풀 C를 작성합니다. 단, 아직 풀 C에서 서비스를 시작하지는 마십시오.
    
    이 단계는 5단계 및 6단계와 동시에 수행할 수 있습니다.

9.  다음 cmdlet을 실행하여 풀 A의 사용자를 풀 C로 강제 이동합니다.
    
        Get-csuser -Filter {RegistrarPool -eq "<Pool A FQDN>"} | Move-CsUser -Target <Pool C FQDN> -Force
    
    이때 풀 A의 사용자에 대해 서비스가 중단됩니다. 이 서비스 중단 상태는 16단계까지 계속되며 그 이후에는 풀 C에서 서비스가 시작됩니다.

10. 다음 cmdlet을 실행하여 풀 A의 전화 회의 디렉터리를 풀 C로 강제 이동합니다.
    
        Move-CsConferenceDirectory -Identity <Conference Directory ID of Pool A> -TargetPool <Pool C FQDN> -Force

11. 다음 cmdlet을 실행하여 CAA(전화 회의 자동 전화 교환) 대화 상대 개체를 풀 A에서 풀 C로 강제 이동합니다.
    
        Move-csApplicationEndpoint -Identity "<Pool A CAA Uri>" -targetApplicationPool <Pool C FQDN> -force

12. 전화 회의 콘텐츠를 풀 B에서 풀 C로 복사합니다.

13. 다음 cmdlet을 실행하여 풀 B에서 사용자 데이터를 내보낸 후 풀 C로 해당 사용자 데이터를 가져옵니다.
    
        Export-CsUserData -PoolFqdn <Pool B Fqdn> -FileName <String>
        Import-CsUserData -PoolFqdn <Pool C Fqdn> -FileName <String>

14. 백업한 통화 대기 응용 프로그램 데이터를 풀 A에서 풀 C로 복원하고 풀 A의 통화 대기 번호 범위를 풀 C에 할당합니다.
    
      - Lync Server 제어판 또는 Lync Server 관리 셸을 통해 풀 A의 통화 대기 번호 범위를 풀 C로 다시 할당할 수 있습니다. Lync Server 관리 셸의 경우 풀 A에 할당된 모든 통화 대기 번호 범위에 대해 다음 cmdlet을 실행합니다. Identity 매개 변수는 풀 A에 속한 통화 대기 번호 범위를 참조합니다.
        
            Set-CsCallParkOrbit -Identity "<Call Park Orbit Identity>" -CallParkService "service:ApplicationServer:<Pool C FQDN>"
    
      - 풀 A의 통화 대기에 대해 사용자 지정된 대기 음악을 구성한 경우 풀 C에서 통화 대기 사용자 지정된 대기 음악 파일을 복원합니다.
        
            Xcopy <Source> <Destination: Pool C CPS File Store Path>
        
        예를 들면 다음과 같습니다.
        
            Xcopy "Source Path" "<Pool C File Store Path>\OcsFileStore\coX-ApplicationServer-X\AppServerFiles\CPS\"
    
      - 마지막으로 **Set-CsCpsConfiguration** cmdlet을 사용하여 풀 C에서 통화 대기 설정을 다시 구성합니다. 통화 대기 응용 프로그램은 설정 집합과 사용자 지정된 대기 음악 오디오 파일을 풀당 하나씩만 저장할 수 있으며 이러한 설정은 재해 발생 시 백업되거나 보존되지 않습니다.

15. 영구 채팅의 다음 홉 풀이 풀 A를 가리키는 경우 토폴로지를 변경한 다음 변경 내용을 게시하여 다음 홉 서버가 풀 C를 가리키도록 합니다.
    
      - 토폴로지 작성기에서 영구 채팅 풀이 다음 홉으로 풀 C를 가리키도록 변경합니다. 이렇게 하려면 영구 채팅 풀을 마우스 오른쪽 단추로 클릭한 후에 **일반** 탭을 클릭하고 **다음 홉 풀** 에 풀 C의 이름을 입력합니다.
    
      - 다음 cmdlet을 실행하여 풀 C에서 서비스를 시작합니다.
        
            Start-csWindowsService
    
    이제 원래 풀 A에 있었던 사용자에게 발생했던 서비스 중단 상태가 종료됩니다.

16. 다음 cmdlet을 실행하여 풀 B에서 풀 A의 소유인 Lync Server 응답 그룹 서비스 워크플로를 풀 C로 가져올 수 있도록 내보냅니다.
    
        Export-CsRgsConfiguration -Source "service:ApplicationServer:<Pool B FQDN>" -Owner "service:ApplicationServer:<Pool A FQDN>" -FileName "C:\RgsExportPrimaryUpdated.zip" 

17. Lync Server 응답 그룹 서비스 워크플로를 풀 B에서 풀 C로 가져옵니다.
    
    응답 그룹 구성을 풀 B에서 풀 C로 가져올 때는 두 가지 옵션을 사용할 수 있습니다. 풀 C의 응용 프로그램 수준 설정을 풀 B의 응용 프로그램 수준 설정으로 덮어쓸지 여부에 따라 사용하는 옵션이 달라집니다.
    
      - 풀 C 설정을 덮어쓰려면 **ReplaceExistingSettings** 옵션을 포함하여 **Import-CsRgsConfiguration** cmdlet을 실행합니다.
        
            Import-CsRgsConfiguration -Destination "service:ApplicationServer:<Pool C FQDN>" -FileName "C:\RgsExportPrimary.zip"  -ReplaceExistingRgsSettings
    
      - 풀 C 설정을 덮어쓰지 않으려면 **ReplaceExistingSettings** 옵션을 포함하지 않고 **Import-CsRgsConfiguration** cmdlet을 사용합니다.
        
            Import-CsRgsConfiguration -Destination "service:ApplicationServer:<Pool B FQDN>" -FileName "C:\RgsExportPrimary.zip"
    

    > [!WARNING]
    > 풀 C의 응용 프로그램 수준 설정을 백업 풀(풀 B)의 설정으로 덮어쓰지 않는 경우에는 풀 B의 응용 프로그램 수준 설정이 손실됩니다. 응답 그룹 응용 프로그램은 풀당 응용 프로그램 수준 설정 집합을 하나만 저장할 수 있기 때문입니다.



18. 다음 cmdlet을 실행해 풀 C로 가져온 응답 그룹을 표시하여 응답 그룹 구성 가져오기가 정상적으로 수행되었는지 확인합니다.
    
        Get-CsRgsWorkflow -Identity "service:ApplicationServer:<Pool C FQDN>" -ShowAll
         Get-CsRgsQueue -Identity "service:ApplicationServer:<Pool C FQDN>" -ShowAll
        Get-CsRgsAgentGroup -Identity "service:ApplicationServer:<Pool C FQDN>" -ShowAll

19. 가져온 구성이 풀 C에서 확인되면 기본 풀이 소유한 응답 그룹을 풀 B에서 제거합니다. 이렇게 하면 응답 그룹의 가동 중지 시간을 최소화할 수 있습니다.
    
    이 단계를 수행하면 내보낸 구성을 사용하여 새 파일이 만들어진 다음 풀 B에서 해당 파일이 제거됩니다.
    
        Export-CsRgsConfiguration -Source "service:ApplicationServer:<Pool B FQDN>" -Owner "service:ApplicationServer:<Pool A FQDN>" -FileName "C:\RgsExportPrimaryUpdated.zip" -RemoveExportedConfiguration

20. 풀 A에서 풀 B로 이동한 지정되지 않은 번호 범위를 풀 C로 이동합니다.
    
      - 풀 A에서 풀 B에 다시 만든 모든 알림을 풀 C에서 다시 만듭니다. 이동할 알림을 배포할 때 오디오 파일을 사용한 경우 풀 C에서 알림을 다시 만들려면 이러한 파일이 필요합니다. 풀 C에서 알림을 다시 만들려면 풀 C를 상위 서비스로 지정하여 **New-CsAnnouncement** cmdlet을 사용합니다.
    
      - 풀 A에서 풀 B로 대상을 다시 설정한 모든 지정되지 않은 번호 범위에 대해 대상을 풀 C로 다시 설정합니다. 이렇게 하려면 대상을 다시 설정해야 하는 모든 지정되지 않은 번호 범위에 대해 다음 cmdlet을 실행합니다.
        
            Set-CsUnassignedNumber -Identity "<Range Name>" -AnnouncementService "<Pool C FQDN>" -AnnouncementName "<New Announcement in pool C>"
    
      - (선택 사항) 풀 C에서 다시 만든 알림을 풀 B에서 더 이상 사용하지 않는 경우 풀 B에서 제거합니다. 알림을 제거하려면 **Remove-CsAnnouncement** cmdlet을 사용합니다.
        

        > [!NOTE]
        > 알림 서비스로 "Exchange UM"을 사용하는 지정되지 않은 번호 범위에 대해서는 이 단계를 수행할 필요가 없습니다.



21. 다음 cmdlet을 실행하여 풀 B에서 풀 A의 사용자 데이터를 정리합니다.
    
        Remove-CsUserStoreBackupData -PoolFqdn <Pool B FQDN> -Verbose

22. 토폴로지 작성기에서 다음을 수행합니다.
    
      - 풀 A와 풀 B의 연결을 해제합니다. 그런 후에 토폴로지에서 풀 A를 제거하고 토폴로지를 게시합니다. 이렇게 하려면 다음을 수행합니다.
        
          - 토폴로지 작성기에서 풀 B를 마우스 오른쪽 단추로 클릭하고 **속성 편집** 을 클릭합니다.
        
          - 왼쪽 창에서 **탄성** 을 클릭합니다.
        
          - **연결된 백업 풀** 아래의 상자에서 풀 C를 선택합니다. 처음에는 연결된 백업 풀 선택 상자에 풀 A가 표시됩니다. 이전에 풀 B가 이 풀에 연결되었기 때문입니다.
        
          - **자동 음성 장애 조치(failover) 및 장애 복구(failback)** 를 선택하고 **확인** 을 클릭합니다.
            
            이 풀의 세부 정보를 표시하면 이제 연결된 풀이 오른쪽 창의 **탄성** 아래에 표시됩니다.
        
          - 콘솔 트리에서 풀 A를 마우스 오른쪽 단추로 클릭하고 삭제를 클릭합니다.
        
          - 토폴로지를 게시합니다.

23. 풀 C에서 부트스트래핑 응용 프로그램을 실행하여 백업 서비스 응용 프로그램을 설치한 후에 풀 C의 로컬 컴퓨터에 있는 배포 폴더에서 다음을 실행하여 백업 서비스 응용 프로그램을 시작합니다.
    
        Run "%SYSTEMROOT%\Program Files\Microsoft Lync Server 2013\Deployment\Bootstrapper.exe"
        Start-CsWindowsService -name LyncBackup

24. 다음 cmdlet을 실행하여 풀 B에서 백업 서비스 응용 프로그램을 다시 시작합니다.
    
        Stop-CsWindowsService -name LyncBackup
        Start-CsWindowsService -name LyncBackup

25. 풀 C가 SE(Standard Edition) 풀이고 풀 B에 CMS가 있는 경우 다음 cmdlet을 실행하여 풀 C에 CMS 데이터베이스를 수동으로 설치합니다.
    
        Install-CsDatabase -CentralManagementDatabase -SqlServerFqdn <Pool C FQDN> -SqlInstanceName rtc

26. 백업 서비스를 호출하여 풀 B와 C를 쌍으로 연결하기 전에 생성된 이전 회의 콘텐츠를 풀 B에서 풀 C로 동기화하고, 풀 C를 시작한 후 풀 B와 C를 쌍으로 연결하기 전에 생성된 새 회의 콘텐츠를 풀 C에서 풀 B로 동기화합니다. 이렇게 하려면 다음 cmdlet을 실행합니다.
    
        Invoke-CsBackupServiceSync -PoolFqdn <Pool C FQDN>
        Invoke-CsBackupServiceSync -PoolFqdn <Pool B FQDN>

27. 풀 A와 연결된 각 SBA(Survivable Branch Appliance) X에 대해 다음을 수행합니다.
    
      - 다음 cmdlet을 실행하여 SBA X를 종료합니다.
        
            Stop-CsWindowsService
    
      - SBA X에 있는 사용자 목록이 포함된 파일을 만듭니다. 30단계에서 사용자를 SBA X로 다시 이동할 때 이 목록이 필요합니다. 이렇게 하려면 다음 cmdlet을 실행합니다.
        
            Get-CsUser -Filter {RegistrarPool -eq "<SBA X FQDN>"} | Export-Csv d:\sbaxusers.txt
    
      - 다음 cmdlet을 실행하여 SBA X에 있는 사용자를 풀 C로 강제 이동합니다.
        
            Get-CsUser -Filter {RegistrarPool -eq "<SBA X FQDN>"} | Move-CsUser -Target <Pool C FQDN> -Force -Verbose
    
      - 먼저 다음 cmdlet을 실행하여 이러한 사용자의 데이터를 업데이트합니다.
        
            Convert-csUserData -InputFile <Data file exported from PoolB> -OutputFile c:\Logs\ExportedUserData.xml -TargetVersionLync2010 
            $a=get-csuser -Filter {RegistrarPool -eq "FQDN of SBA X"} | select SipAddress
            foreach($x in $a) {$x.SipAddress.Substring(4) >> users.txt}
        
        그런 후에 다음 스크립트를 실행합니다.
        
            $users=gc c:\logs\users.txt
            foreach ($user in $users)
            {
            Update-CsUserData -FileName c:\logs\exportedUserDAta.xml -UserFilter $user - 
            }
        

        > [!NOTE]
        > 풀 A에 연결된 SBA에 있는 사용자에 대해 사용자를 풀 C로 이동할 때까지 서비스가 중단됩니다.



28. 토폴로지 작성기에서 이전에 풀 A와 연결한 각 SBA X에 대해 다음을 수행합니다.
    
      - 연결을 풀 C로 변경합니다. 이렇게 하려면 분기 사이트를 클릭하고 SBA(Survivable Branch Appliance) 또는 서버 노드를 확장한 후에 **SBA(Survivable Branch Appliance)** 를 클릭합니다. 그런 다음 해당 SBA(Survivable Branch Appliance)가 풀 C로 연결할 **프런트 엔드 풀, 사용자 서비스 풀** 을 선택하고 **다음** 을 클릭합니다.
    
      - 토폴로지를 게시합니다. 이렇게 하려면 콘솔 트리에서 새 **SBA(Survivable Branch Appliance)** 를 마우스 오른쪽 단추로 클릭하고 **토폴로지** , **게시** 를 차례로 클릭합니다.

29. 이제 풀 C에 연결된 각 SBA X에 대해 다음을 수행합니다.
    
      - SBA(Survivable Branch Appliance)에서 다음 cmdlet을 실행하여 SBA X를 시작합니다.
        
            Start-CsWindowsService
    
      - 다음 cmdlet을 실행하여 원래 풀 C의 SBA X에 있었던 사용자를 SBA X로 이동합니다.
        
            Import-Csv d:\sbaxusers.txt | Move-CsUser -Target <SBA X FQDN> -Force

