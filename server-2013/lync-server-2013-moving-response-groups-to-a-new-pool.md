---
title: 새 풀로 응답 그룹 이동
TOCTitle: 새 풀로 응답 그룹 이동
ms:assetid: da0db765-41e5-430b-b5a7-5418ec5ff2a7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205298(v=OCS.15)
ms:contentKeyID: 49305225
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 새 풀로 응답 그룹 이동

 

_**마지막으로 수정된 항목:** 2012-11-01_

FQDN(정규화된 도메인 이름)이 달라도 풀 간에 응답 그룹을 이동할 수 있는 새로운 cmdlet 지원이 Lync Server 2013에 도입되었습니다.

다음 절차의 단계에 따라 한 프런트 엔드 풀에서 다른 FQDN의 또 다른 프런트 엔드 풀로 응답 그룹을 이동합니다.


> [!NOTE]
> 동시 사용 환경에서는 Lync Server 2013프런트 엔드 풀 간에만 응답 그룹을 이동할 수 있습니다.



## 다른 FQDN의 풀로 응답 그룹을 이동하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  원본 풀에서 응답 그룹을 내보내고 명령줄에 다음을 입력합니다.
    
        Export-CsRgsConfiguration -Source "service:ApplicationServer:<source FQDN>" -FileName "<export file name>"
    
    예를 들면 다음과 같습니다.
    
        Export-CsRgsConfiguration -Source "service:ApplicationServer:source.contoso.com" -FileName "C:\RgsExportSource.zip"
    
    내보내기 중에 원본 풀에서 응답 그룹을 제거하려면 -RemoveExportedConfiguration 매개 변수를 포함합니다. 예를 들면 다음과 같습니다.
    
        Export-CsRgsConfiguration -Source ApplicationServer:source.contoso.com -FileName "C:\RgsExportSource.zip" -RemoveExportedConfiguration

3.  응답 그룹을 대상 풀로 가져오고 대상 풀을 새 소유자로 할당합니다. 명령줄에 다음을 입력합니다.
    
        Import-CsRgsConfiguration -Destination "service:ApplicationServer:<destination pool>" -FileName "<export file name>" -OverwriteOwner
    
    원본 풀에서 대상 풀로 응답 그룹 응용 프로그램 수준 설정을 복사하려는 경우 –ReplaceExistingSettings 매개 변수를 포함합니다. 풀당 응용 프로그램 수준 설정 집합을 한 개만 정의할 수 있습니다. 원본 풀에서 대상 풀로 응용 프로그램 수준 설정을 복사하는 경우 원본 풀의 설정이 대상 풀의 설정을 대체합니다. 원본 풀에서 응용 프로그램 수준 설정을 복사하지 않는 경우에는 대상 풀의 기존 설정이 가져온 응답 그룹에 적용됩니다.
    
    예를 들면 다음과 같습니다.
    
        Import-CsRgsConfiguration -Destination "service:ApplicationServer:destination.contoso.com" -FileName "C:\RgsExportSource.zip" -OverwriteOwner -ReplaceExistingSettings
    

    > [!NOTE]
    > 응용 프로그램 수준 설정에는 기본 대기 음악 구성, 기본 대기 음악 오디오 파일, 에이전트 되걸기 유예 기간 및 호출 컨텍스트 구성이 포함됩니다. 이러한 구성 설정을 보려면 <STRONG>Get-CsRgsConfiguration</STRONG> cmdlet을 실행합니다. 이 cmdlet에 대한 자세한 내용은 <A href="https://docs.microsoft.com/powershell/module/skype/Get-CsRgsConfiguration">Get-CsRgsConfiguration</A>을 참조하십시오.



4.  다음 절차에 따라 가져온 응답 그룹 구성을 표시하여 가져오기가 성공적으로 수행되었는지 확인합니다.
    
      - 모든 워크플로를 가져왔는지 확인합니다. 명령줄에 다음을 입력합니다.
        
            Get-CsRgsWorkflow -Identity "service:ApplicationServer:<destination pool FQDN>"
    
      - 모든 큐를 가져왔는지 확인합니다. 명령줄에 다음을 입력합니다.
        
            Get-CsRgsQueue -Identity "service:ApplicationServer:<destination pool FQDN>"
    
      - 모든 에이전트 그룹을 가져왔는지 확인합니다. 명령줄에 다음을 입력합니다.
        
            Get-CsRgsAgentGroup -Identity "service:ApplicationServer:<destination pool FQDN>"
    
      - 모든 업무 시간을 가져왔는지 확인합니다. 명령줄에 다음을 입력합니다.
        
            Get-CsRgsHoursOfBusiness -Identity "service:ApplicationServer:<destination pool FQDN>" 
    
      - 모든 휴일을 가져왔는지 확인합니다. 명령줄에 다음을 입력합니다.
        
            Get-CsRgsHolidaySet -Identity "service:ApplicationServer:<destination pool FQDN>" 

5.  응답 그룹 중 하나로 전화를 걸고 통화가 올바르게 처리되는지 확인하여 가져오기가 성공적으로 수행되었는지 확인합니다.

6.  공식 에이전트 그룹의 구성원인 에이전트에게 대상 풀의 에이전트 그룹에 로그인하도록 요청합니다.

7.  원본 풀에서 이전에 응답 그룹을 제거하지 않은 경우 응답 그룹을 원본 풀에서 제거합니다. 명령줄에 다음을 입력합니다.
    
        Export-CsRgsConfiguration -Source "service:ApplicationServer:<source pool FQDN> -RemoveExportedConfiguration -FileName "<temporary export file name>"
    
    예를 들면 다음과 같습니다.
    
        Export-CsRgsConfiguration -Source "service:ApplicationServer:source.contoso.com" -RemoveExportedConfiguration -FileName "C:\TempRGsConfiguration.zip"

