---
title: 중앙화된 로깅 서비스에 중지 사용
TOCTitle: 중앙화된 로깅 서비스에 중지 사용
ms:assetid: 09ac093e-8f30-4874-84b4-12548ac8c898
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ687964(v=OCS.15)
ms:contentKeyID: 49885641
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 중앙화된 로깅 서비스에 중지 사용

 

_**마지막으로 수정된 항목:** 2012-11-01_

Stop-CsClsLogging cmdlet을 사용하여 현재 실행 중인 로깅 세션을 중지할 수 있습니다. 일반적으로 로깅 세션을 중지해야 하는 상황은 많지 않습니다. 예를 들어 로깅을 먼저 중지하지 않고도 로그를 검색하고 구성을 변경할 수 있습니다. 두 시나리오(AlwaysOn 및 UserReplicator)를 실행 중인데 Authentication 관련 정보를 수집해야 하는 경우에는 전역, 사이트, 풀 또는 컴퓨터 범위에서 다른 시나리오 중 하나를 중지해야 Authentication 시나리오 실행을 시작할 수 있습니다. 자세한 내용은 [Stop-CsClsLogging](https://docs.microsoft.com/en-us/powershell/module/skype/Stop-CsClsLogging)을 참조하십시오.


> [!NOTE]
> 지정된 배포, 풀 또는 컴퓨터에서 실행할 수 있는 시나리오를 확인할 때는 <STRONG>컴퓨터당</STRONG> 두 개의 시나리오만 실행할 수 있음을 기억해야 합니다. 풀에서 활동을 로깅 중이라면 풀을 엔터티 하나로 간주해야 합니다. 대부분의 경우에는 풀의 각 컴퓨터에서 서로 다른 시나리오를 실행하지 않습니다. 데이터를 수집 중인 문제를 확인하여 전체 배포에서 지정된 컴퓨터에 가장 적합한 시나리오를 고려하는 것이 적절합니다. 예를 들어 UserReplicator 시나리오를 고려하는 경우 에지 서버 또는 에지 풀에서는 UserReplicator를 실행해도 거의 아무런 효과가 없습니다.<BR>문제와 영향의 범위를 파악한 후에는 각 컴퓨터와 풀에서 실행할 시나리오를 적절하게 선택해야 합니다. AlwaysOn 시나리오는 다양한 공급자에 대한 정보를 수집하므로 폭넓은 응용 프로그램에 적합하기는 하지만, 특정 시나리오는 특정 컴퓨터나 풀에서만 응용 프로그램과 관련하여 유용합니다. 또한 먼저 지정된 시나리오의 유용성을 파악하지 않고 로깅 세션을 임의로 시작할 때도 주의해야 합니다. 잘못된 시나리오를 사용하거나 작업에 적합한 시나리오를 사용하기는 하지만 잘못된 범위(전역/사이트/풀/컴퓨터)에서 시나리오를 적용하는 경우에는 시나리오를 전혀 실행하지 않은 것과 마찬가지로 부적절한 데이터가 제공될 수 있습니다.



Lync Server 관리 셸을 사용하여 중앙 로깅 서비스 기능을 제어하려면 CsAdministrator 또는 CsServerAdministrator RBAC(역할 기반 액세스 제어) 보안 그룹 또는 이러한 두 그룹 중 하나를 포함하는 사용자 지정 RBAC 역할의 구성원이어야 합니다. 이 cmdlet이 할당된 모든 RBAC 역할(직접 만든 사용자 지정 RBAC 역할 포함)의 목록을 반환하려면 Lync Server 관리 셸 또는 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Lync Server 2013 cmdlet"}

예를 들면 다음과 같습니다.

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsClsConfiguration"}

## 현재 실행 중인 중앙 로깅 서비스 세션을 중지하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  다음을 입력하여 중앙 로깅 서비스를 쿼리해 현재 실행 중인 시나리오를 확인합니다.
    
        Show-CsClsLogging
    
    ![Show-CsCl 호출 후의 Windows PowerShell 콘솔](images/JJ687964.eb190c32-529c-4277-a731-52c47d22d8fa(OCS.15).jpg "Show-CsCl 호출 후의 Windows PowerShell 콘솔")
    
    Show-CsClsLogging의 결과는 실행 중인 시나리오 및 시나리오가 실행되는 범위의 요약입니다. 자세한 내용은 [Show-CsClsLogging](https://docs.microsoft.com/en-us/powershell/module/skype/Show-CsClsLogging)을 참조하십시오.

3.  특정 시나리오를 사용하여 현재 실행 중인 로깅 세션을 중지하려면 다음을 입력합니다.
    
        Stop-CsClsLogging -Scenario <scenario name> -Computers <comma separated list of fully qualified computer names> -Pools <comma separated list of fully qualified pool names>
    
    예를 들면 다음과 같습니다.
    
        Stop-CsClsLogging -Scenario UserReplicator -Pools pool01.contoso.net
    
    이 명령은 pool01.contoso.net에서 UserReplicatior 시나리오를 사용한 로깅을 중지합니다.
    

    > [!NOTE]
    > UserReplicator 시나리오를 사용하여 이 로깅 세션 중에 작성되는 로그는 삭제되지 않습니다. Search-CsClsLogging 명령을 사용하면 로깅에 대해 검색을 계속 실행할 수 있습니다. 자세한 내용은 <A href="https://docs.microsoft.com/en-us/powershell/module/skype/Search-CsClsLogging">Search-CsClsLogging</A>을 참조하십시오.



Start-CsClsLogging의 보조 명령으로 작동하는 Stop-CsClsLogging cmdlet은 시나리오에 의해 정의된 로깅 세션을 종료하고 로깅 세션에서 작성된 로그를 보관합니다. 지정된 컴퓨터에서 한 번에 두 개의 시나리오를 실행할 수 있습니다. 한 시나리오를 중지하고 다른 시나리오를 사용하여 정보를 수집하는 방법은 대부분의 작업 문제 해결 중에 수행할 수 있는 일반적인 작업입니다.

## 참고 항목

#### 작업

[중앙화된 로깅 서비스에 시작을 사용하여 로그 캡처](lync-server-2013-using-start-for-the-centralized-logging-service-to-capture-logs.md)  

#### 개념

[중앙화된 로깅 서비스 개요](lync-server-2013-overview-of-the-centralized-logging-service.md)  

#### 기타 리소스

[Show-CsClsLogging](https://docs.microsoft.com/en-us/powershell/module/skype/Show-CsClsLogging)  
[Start-CsClsLogging](https://docs.microsoft.com/en-us/powershell/module/skype/Start-CsClsLogging)  
[Stop-CsClsLogging](https://docs.microsoft.com/en-us/powershell/module/skype/Stop-CsClsLogging)

