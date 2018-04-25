---
title: Lync Server 2013 응답 그룹 재해 복구 절차
TOCTitle: 응답 그룹 재해 복구 절차
ms:assetid: b49577b7-0ca3-4f20-b614-f3a2a0046b58
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205186(v=OCS.15)
ms:contentKeyID: 49304781
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 응답 그룹 재해 복구 절차

 

_**마지막으로 수정된 항목:** 2012-11-01_

재해 복구의 장애 조치(failover) 단계에서 응답 그룹은 여러 풀, 즉 주 풀(사용할 수 없음)과 백업 풀에 있게 됩니다. 두 풀의 응답 그룹은 이름과 소유자(주 풀)가 같지만 부모는 다릅니다. 이 시간 동안 응답 그룹 cmdlet은 평소와 약간 다르게 작동합니다. 다음 절차에 나온 매개 변수를 사용해야 합니다. 장애 조치 단계에서 cmdlet이 작동하는 방식에 대한 자세한 내용은 NextHop 블로그 문서 "Lync Server 2013: 재해 복구 과정의 응답 그룹 복구"( [http://go.microsoft.com/fwlink/?linkid=263957\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=263957%26clcid=0x412))를 참조하십시오. 이 블로그 문서의 내용은 릴리스된 버전의 Lync Server 2013에도 적용됩니다.

Lync Server 응답 그룹 서비스의 재해 복구를 준비하고 수행하려면 다음 절차의 단계를 따르십시오.

## 응답 그룹의 장애 조치(failover) 및 장애 복구(failback)를 수행하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  명령줄에 다음을 입력하여 일상적인 백업을 수행합니다.
    
        Export-CsRgsConfiguration -Source "service:ApplicationServer:<primary pool FQDN>" -FileName "<backup path and file name>"
    
    예를 들면 다음과 같습니다.
    
        Export-CsRgsConfiguration -Source "service:ApplicationServer:primary.contoso.com" -FileName "C:\RgsExportPrimary.zip"

3.  중단 시 백업 풀로 장애 조치를 수행한 후에 응답 그룹을 백업 풀로 가져옵니다. 명령줄에 다음을 입력합니다.
    
        Import-CsRgsConfiguration -Destination "service:ApplicationServer:<backup pool FQDN>" -FileName "<backup path and file name>"
    
    백업 풀의 응용 프로그램 수준 설정을 주 풀의 설정으로 바꾸려면 -ReplaceExistingSettings 매개 변수를 포함시킵니다. 예를 들면 다음과 같습니다.
    
        Import-CsRgsConfiguration -Destination "service:ApplicationServer:backup.contoso.com" -FileName "C:\RgsExportPrimary.zip" -ReplaceExistingSettings
    

    > [!WARNING]
    > 백업 풀의 설정을 바꾸지 않은 상태에서 주 풀을 복구할 수 없는 경우 주 풀 설정이 손실됩니다. 자세한 내용은 <A href="lync-server-2013-planning-for-response-group-disaster-recovery.md">Lync Server 2013의 응답 그룹 재해 복구 계획</A>을 참조하십시오.



4.  가져온 응답 그룹을 표시하여 가져오기가 성공했는지 확인합니다. 가져온 응답 그룹은 여전히 주 풀에서 소유합니다. 다음을 수행합니다.
    
      - 주 풀에서 소유하고 있는 백업 풀의 모든 워크플로를 표시하고 모든 주 풀 워크플로가 포함되어 있는지 확인합니다. 명령줄에 다음을 입력합니다.
        
            Get-CsRgsWorkflow -Identity "service:ApplicationServer:<backup pool FQDN>" -Owner "service:ApplicationServer"<primary pool FQDN>
        
        예를 들면 다음과 같습니다.
        
            Get-CsRgsWorkflow -Identity "service:ApplicationServer:backup.contoso.com" -Owner "service:ApplicationServer:primary.contoso.com"
    
      - 주 풀에서 소유하고 있는 백업 풀의 모든 큐를 표시하고 모든 주 풀 큐가 포함되어 있는지 확인합니다. 명령줄에 다음을 입력합니다.
        
            Get-CsRgsQueue -Identity "service:ApplicationServer:<backup pool FQDN>" -Owner "service:ApplicationServer"<primary pool FQDN>
        
        예를 들면 다음과 같습니다.
        
            Get-CsRgsQueue -Identity "service:ApplicationServer:backup.contoso.com" -Owner "service:ApplicationServer"primary.contoso.com"
    
      - 주 풀에서 소유하고 있는 백업 풀의 모든 에이전트 그룹을 표시하고 모든 주 풀 에이전트 그룹이 포함되어 있는지 확인합니다. 명령줄에 다음을 입력합니다.
        
            Get-CsRgsAgentGroup -Identity "service:ApplicationServer:<backup pool FQDN>" -Owner "service:ApplicationServer"<primary pool FQDN>
        
        예를 들면 다음과 같습니다.
        
            Get-CsRgsAgentGroup -Identity "service:ApplicationServer:backup.contoso.com" -Owner "service:ApplicationServer"primary.contoso.com"
    
      - 주 풀에서 소유하고 있는 백업 풀의 모든 업무 시간을 표시하고 모든 주 풀 업무 시간이 포함되어 있는지 확인합니다. 명령줄에 다음을 입력합니다.
        
            Get-CsRgsHoursOfBusiness -Identity "service:ApplicationServer:<backup pool FQDN>" -Owner "service:ApplicationServer"<primary pool FQDN>
        
        예를 들면 다음과 같습니다.
        
            Get-CsRgsHoursOfBusiness -Identity "service:ApplicationServer:backup.contoso.com" -Owner "service:ApplicationServer"primary.contoso.com"
    
      - 주 풀에서 소유하고 있는 백업 풀의 모든 휴일 집합을 표시하고 모든 주 풀 휴일 집합이 포함되어 있는지 확인합니다. 명령줄에 다음을 입력합니다.
        
            Get-CsRgsHolidaySet -Identity "service:ApplicationServer:<backup pool FQDN>" -Owner "service:ApplicationServer"<primary pool FQDN>
        
        예를 들면 다음과 같습니다.
        
            Get-CsRgsHolidaySet -Identity "service:ApplicationServer:backup.contoso.com" -Owner "service:ApplicationServer"primary.contoso.com"
    
    또는 -Owner 매개 변수 대신에 -ShowAll 매개 변수를 사용하여 주 풀에서 소유하고 있는 응답 그룹과 백업 그룹에서 소유하고 있는 응답 그룹을 포함한 백업 풀의 모든 응답 그룹을 표시할 수 있습니다. 예를 들면 다음과 같습니다.
    
        Get-CsRgsWorkflow -Identity "service:ApplicationServer:<backup pool FQDN>" -ShowAll
    

    > [!IMPORTANT]
    > -ShowAll 매개 변수 또는 -Owner 매개 변수를 사용해야 합니다. 이러한 매개 변수 중의 하나를 사용하지 않을 경우 백업 풀로 가져온 응답 그룹이 cmdlet에서 반환되는 결과에 나열되지 않습니다.



5.  가져온 응답 그룹에 전화를 걸고 통화가 올바르게 처리되는지 확인하여 가져오기가 성공했는지 확인합니다.

6.  공식 응답 그룹의 구성원인 에이전트에게 백업 풀의 해당 에이전트 그룹에 로그인하도록 요청합니다.

7.  가져온 응답 그룹을 평소와 같이 관리하고 수정합니다.
    

    > [!IMPORTANT]
    > 응답 그룹이 백업 풀에 있는 동안에는 Lync Server 관리 셸을 사용하여 관리해야 합니다. 백업 풀로 가져온 응답 그룹을 관리하는 데에는 Lync Server 제어판을 사용할 수 없습니다.



8.  주 풀이 복원되고 장애 복구가 완료되었으면 백업 풀로 가져온 주 풀 응답 그룹을 내보냅니다. 명령줄에 다음을 입력합니다.
    
        Export-CsRgsConfiguration -Source ApplicationServer:<backup pool FQDN> -Owner ApplicationServer:<primary pool FQDN> -FileName "<backup path and file name>"

9.  명령줄에 다음을 입력하여 응답 그룹을 주 풀로 다시 가져옵니다.
    
        Import-CsRgsConfiguration -Destination "service:ApplicationServer:<primary pool FQDN>" -OverwriteOwner -FileName "<exported path and file name>"
    
    예를 들면 다음과 같습니다.
    
        Import-CsRgsConfiguration -Destination "service:ApplicationServer:primary.contoso.com" -OverwriteOwner -FileName "C:\RgsExportPrimaryUpdated.zip"
    

    > [!NOTE]
    > 복구 시 동일하거나 다른 FQDN(정규화된 도메인 이름)을 사용하여 풀을 다시 만드는 경우 -OverwriteOwner 매개 변수를 사용해야 합니다. 일반적으로 응답 그룹을 주 풀로 다시 가져올 때는 -OverwriteOwner 매개 변수를 항상 사용할 수 있습니다.

    
    주 풀을 대체하도록 동일하거나 다른 FQDN(정규화된 도메인 이름)을 사용하여 새 풀을 배포하고 백업 풀의 응용 프로그램 수준 설정을 새 풀에 사용하려는 경우 -ReplaceExistingSettings 매개 변수를 포함시킵니다. 명령줄에 다음을 입력합니다.
    
        Import-CsRgsConfiguration -Destination "service:ApplicationServer:<new primary pool FQDN>" -OverwriteOwner -FileName "<exported path and file name>" -ReplaceExistingSettings
    
    예를 들면 다음과 같습니다.
    
        Import-CsRgsConfiguration -Destination "service:ApplicationServer:newprimary.contoso.com" -OverwriteOwner -FileName "C:\RgsExportPrimaryUpdated.zip" -ReplaceExistingSettings
    

    > [!IMPORTANT]
    > 새 풀의 응용 프로그램 수준 설정 및 기본 대기 음악 오디오 파일을 백업 풀의 설정으로 바꾸지 않을 경우 새 풀에서 기본 응용 프로그램 수준 설정이 사용됩니다.



10. 가져온 응답 그룹 구성을 표시하여 주 풀로 다시 가져오기가 성공했는지 확인합니다. 다음을 수행합니다.
    
      - 주 풀의 모든 워크플로를 표시하고 가져온 모든 워크플로가 포함되어 있는지 확인합니다. 명령줄에 다음을 입력합니다.
        
            Get-CsRgsWorkflow -Identity "service:ApplicationServer:<primary pool FQDN>" -ShowAll
        
        예를 들면 다음과 같습니다.
        
            Get-CsRgsWorkflow -Identity "service:ApplicationServer: primary.contoso.com" -ShowAll
    
      - 주 풀의 모든 큐를 표시하고 가져온 모든 큐가 포함되어 있는지 확인합니다. 명령줄에 다음을 입력합니다.
        
            Get-CsRgsQueue -Identity "service:ApplicationServer:<primary pool FQDN>" -ShowAll
        
        예를 들면 다음과 같습니다.
        
            Get-CsRgsQueue -Identity "service:ApplicationServer:primary.contoso.com" -ShowAll
    
      - 주 풀의 모든 에이전트 그룹을 표시하고 가져온 모든 에이전트 그룹이 포함되어 있는지 확인합니다. 명령줄에 다음을 입력합니다.
        
            Get-CsRgsAgentGroup -Identity "service:ApplicationServer: <primary pool FQDN>" -ShowAll
        
        예를 들면 다음과 같습니다.
        
            Get-CsRgsAgentGroup -Identity "service:ApplicationServer:primary.contoso.com" -ShowAll
    
      - 주 풀의 모든 업무 시간을 표시하고 가져온 모든 업무 시간이 포함되어 있는지 확인합니다. 명령줄에 다음을 입력합니다.
        
            Get-CsRgsHoursOfBusiness -Identity "service:ApplicationServer:<primary pool FQDN>" -ShowAll
        
        예를 들면 다음과 같습니다.
        
            Get-CsRgsHoursOfBusiness -Identity "service:ApplicationServer:primary.contoso.com" -ShowAll
    
      - 주 풀의 모든 휴일 집합을 표시하고 가져온 모든 휴일 집합이 포함되어 있는지 확인합니다. 명령줄에 다음을 입력합니다.
        
            Get-CsRgsHolidaySet -Identity "service:ApplicationServer:<primary pool FQDN>" -ShowAll
        
        예를 들면 다음과 같습니다.
        
            Get-CsRgsHolidaySet -Identity "service:ApplicationServer:primary.contoso.com" -ShowAll

11. 가져온 응답 그룹에 전화를 걸고 통화가 올바르게 처리되는지 확인하여 가져오기가 성공했는지 확인합니다.

12. 필요에 따라 주 풀에서 소유한 응답 그룹을 백업 풀에서 제거합니다. 명령줄에 다음을 입력합니다.
    
        Export-CsRgsConfiguration -Source "service:ApplicationServer:<backup pool FQDN>" -Owner "service:ApplicationServer:<primary pool FQDN>" -FileName "<backup path and file name>" -RemoveExportedConfiguration
    
    예를 들면 다음과 같습니다.
    
        Export-CsRgsConfiguration -Source "service:ApplicationServer:backup.contoso.com" -Owner "service:ApplicationServer:primary.contoso.com" -FileName "C:\RgsExportPrimaryUpdated.zip" -RemoveExportedConfiguration
    

    > [!NOTE]
    > 이 단계를 수행하면 내보낸 구성으로 새 파일이 만들어진 후 백업 풀에서 제거됩니다.


