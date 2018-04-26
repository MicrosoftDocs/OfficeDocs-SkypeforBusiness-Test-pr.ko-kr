---
title: 컴퓨터, 사이트, 전역 중앙 로깅 서비스 구성 관리
TOCTitle: 컴퓨터, 사이트, 전역 중앙 로깅 서비스 구성 관리
ms:assetid: 93b9a354-9aea-4b3a-a4fe-68a89f436196
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688138(v=OCS.15)
ms:contentKeyID: 49885877
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 컴퓨터, 사이트, 전역 중앙 로깅 서비스 구성 관리

 

_**마지막으로 수정된 항목:** 2014-02-04_

중앙 로깅 서비스는 단일 컴퓨터나 컴퓨터 풀을 포함하는 범위, 사이트 범위(즉, 배포에 컴퓨터 및 풀 컬렉션을 포함하는 Redmond 사이트와 같은 정의된 사이트) 또는 전역 범위(즉, 배포의 모든 컴퓨터 및 풀)로 실행할 수 있습니다.

Lync Server 관리 셸을 사용하여 중앙 로깅 서비스 범위를 구성하려면 CsAdministrator 또는 CsServerAdministrator RBAC(역할 기반 액세스 제어) 보안 그룹의 구성원이거나 이러한 두 그룹 중 하나를 포함하는 사용자 지정 RBAC 역할이 할당되어 있어야 합니다. 사용자가 직접 만든 사용자 지정 RBAC 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 가져오려면 Lync Server 관리 셸 또는 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "<Lync Server 2013 cmdlet>"}

예를 들면 다음과 같습니다.

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsClsConfiguration"}


> [!NOTE]
> Windows PowerShell은 CLSController.exe를 통해서는 제공되지 않는 많은 옵션과 추가 구성 옵션을 제공합니다. CLSController는 빠르고 간단한 방법으로 명령을 실행할 수 있도록 하지만 CLSController에 제공되는 명령 집합으로 한정됩니다. Windows PowerShell은 CLSController의 명령 프로세서로 사용할 수 있는 명령에 한정되지 않고 보다 광범위한 명령과 다양한 옵션을 제공합니다. 예를 들어 CLSController.exe는 -computers 및 -pools에 대한 범위 옵션을 제공하며 사용자가 수정할 수 없는 한정된 수의 시나리오를 갖는 반면, Windows PowerShell은 대부분의 명령에서 컴퓨터 또는 풀을 나타낼 수 있을 뿐만 아니라 새로운 시나리오를 정의할 때 사이트 범위나 전역 범위를 정의할 수 있습니다. Windows PowerShell의 이 강력한 기능 덕분에 사이트 범위 또는 전역 범위로 시나리오를 정의하지만 실제 로깅을 단일 컴퓨터 또는 풀로 제한할 수 있습니다.<BR>Windows PowerShell과 CLSController 간에는 실행할 수 있는 명령줄 명령에 근본적인 차이점이 있습니다. Windows PowerShell을 사용하면 다양한 방법으로 시나리오를 구성하고 정의하는 것은 물론, 이러한 시나리오를 문제 해결 시나리오에서 의미 있게 재사용할 수 있습니다. CLSController를 사용하면 빠르고 효율적으로 명령을 실행하고 결과를 얻을 수 있지만 CLSController의 명령 집합은 명령줄에서 사용할 수 있는 소수의 명령으로 한정됩니다. Windows PowerShell cmdlet과 달리, CLSController는 새로운 시나리오를 정의할 수 없고, 사이트 또는 전역 수준으로 범위를 관리할 수 없고, 필요에 맞게 구성할 수 없는 한정된 명령 집합을 갖는 등 수많은 제한 사항이 있습니다. CLSController는 빠른 실행의 이점을 제공하는 한편, Windows PowerShell은 CLSController를 통해 가능한 수준을 넘어 중앙 로깅 서비스 기능을 확장합니다.



단일 컴퓨터 범위는 [Search-CsClsLogging](search-csclslogging.md), [Show-CsClsLogging](show-csclslogging.md), [Start-CsClsLogging](start-csclslogging.md), [Stop-CsClsLogging](stop-csclslogging.md), [Sync-CsClsLogging](sync-csclslogging.md), [Update-CsClsLogging](update-csclslogging.md) 명령을 실행할 때 –Computers 매개 변수를 사용하여 정의할 수 있습니다. -Computers 매개 변수에는 대상 컴퓨터 FQDN(정규화된 도메인 이름)의 쉼표로 구분된 목록이 허용됩니다.


> [!TIP]
> 또한 -Pools와 로깅 명령을 실행할 풀의 쉼표로 구분된 목록을 정의할 수도 있습니다.



사이트 범위와 전역 범위는 **New-**, **Set-** 및 **Remove-**중앙 로깅 서비스 cmdlet에서 정의됩니다. 다음 예에서는 사이트 범위와 전역 범위를 설정하는 방법을 보여 줍니다.


> [!IMPORTANT]
> 예로 든 명령들에는 다른 섹션에서 설명하는 매개 변수와 개념이 포함되어 있을 수 있습니다. 이러한 명령은 <STRONG>-Identity</STRONG> 매개 변수를 사용하여 범위를 정의하는 방법을 보여 주기 위한 것이며, 다른 매개 변수들은 예제 명령을 완성하고 그러한 범위를 지정하는 방법을 보여 주기 위해 사용됩니다. <STRONG>Set-CsClsConfiguration</STRONG> cmdlet에 대한 자세한 내용은 작업 설명서에서 <A href="set-csclsconfiguration.md">Set-CsClsConfiguration</A>을 참조하십시오.



## 현재 중앙 로깅 서비스 구성을 검색하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  명령줄 프롬프트에 다음 명령을 입력합니다.
    
        Get-CsClsConfiguration

새로운 구성을 만들거나 기존 구성을 업데이트하려면 **New-CsClsConfiguration** 및 **Set-CsClsConfiguration** cmdlet을 사용합니다.

**Get-CsClsConfiguration**을 실행하면 다음 스크린샷과 유사한 정보가 표시됩니다. 이 경우, 현재 배포에 기본 전역 구성이 있지만 사이트 구성이 정의되지 않았습니다.

![Get-CsClsConfiguration의 샘플 출력.](images/JJ688029.23f98ddc-fc48-499a-b6c5-752611f2a0b0(OCS.15).jpg "Get-CsClsConfiguration의 샘플 출력.")

## 컴퓨터 로컬 저장소에서 현재 중앙 로깅 서비스 구성을 검색하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  명령줄 프롬프트에 다음 명령을 입력합니다.
    
        Get-CsClsConfiguration -LocalStore

**Get-CsClsConfiguration**에서 아무 매개 변수도 지정하지 않는 첫 번째 예를 사용하면 명령이 중앙 관리 저장소의 데이터를 참조합니다. -LocalStore 매개 변수를 지정하면 명령이 중앙 관리 저장소가 아닌 컴퓨터 로컬 저장소를 참조합니다.

## 현재 정의된 시나리오 목록을 검색하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  명령줄 프롬프트에 다음 명령을 입력합니다.
    
        Get-CsClsConfiguration -Identity <scope and name> | Select-Object -ExpandProperty Scenarios
    
    예를 들어 전역 범위로 정의된 시나리오를 검색하려면 다음과 같이 합니다.
    
        Get-CsClsConfiguration -Identity "global" | Select-Object -ExpandProperty Scenarios

**Get-CsClsConfiguration** cmdlet은 항상 지정된 범위의 구성에 포함된 시나리오를 표시합니다. 대부분의 경우 시나리오가 모두 표시되지 않고 잘려서 표시됩니다. 여기에 사용된 명령은 모든 시나리오와 사용된 공급자, 설정 및 플래그에 대한 일부 정보를 표시합니다.

## Windows PowerShell을 사용하여 중앙 로깅 서비스의 전역 범위를 업데이트하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  명령줄 프롬프트에 다음 명령을 입력합니다.
    
        Set-CsClsConfiguration -Identity <scope> -EtlFileRolloverSizeMB <size for logging file in megabytes>
    
    예를 들면 다음과 같습니다.
    
        Set-CsClsConfiguration -Identity "global" -EtlFileRolloverSizeMB 40

이 명령을 실행하면 배포에 포함된 각 컴퓨터와 풀의 CLSAgent에서 추적 파일 롤오버 크기 값이 40메가바이트로 설정됩니다. 이 명령은 모든 사이트의 컴퓨터와 풀에 영향을 미쳐 각각의 구성된 추적 로그 롤오버 값이 40메가바이트로 설정됩니다.

## Windows PowerShell을 사용하여 중앙 로깅 서비스의 사이트 범위를 업데이트하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  명령줄 프롬프트에 다음 명령을 입력합니다.
    
        Set-CsClsConfiguration -Identity <scope/site name> -EtlFileRolloverSizeMB <size for logging file in megabytes> -EtlFileFolder <default location %TEMP%\Tracing>
    
    예를 들면 다음과 같습니다.
    
        Set-CsClsConfiguration -Identity "site/Redmond" -EtlFileRolloverSizeMB 40 -EtlFileFolder "C:\LogFiles\Tracing" 
    

    > [!NOTE]
    > 이 예에 나와 있듯이 로그 파일의 기본 위치는 %TEMP%\Tracing입니다. 그러나 실제로 파일을 기록하는 것은 CLSAgent이고 CSLAgent는 네트워크 서비스로 실행되므로 %TEMP% 변수는 %WINDIR%\ServiceProfiles\NetworkService\AppData\Local로 확장됩니다.



이 명령을 실행하면 Redmond 사이트에 포함된 각 컴퓨터와 풀의 CLSAgent에서 추적 파일 롤오버 크기 값이 40메가바이트로 설정됩니다. 다른 사이트의 컴퓨터와 풀은 이 명령의 영향을 받지 않으며 기본적으로 정의되어 있거나(20메가바이트) 로깅 세션을 시작할 때 정의되어 현재 구성된 추적 로그 롤오버 값을 계속 사용합니다.

## 새로운 중앙 로깅 서비스 구성을 만들려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  명령줄 프롬프트에 다음 명령을 입력합니다.
    
        New-CsClsConfiguration -Identity <scope and name> [CsClsConfiguration options for this site]
    

    > [!NOTE]
    > New-CsClsConfiguration을 사용하면 다수의 선택적 구성 설정에 액세스할 수 있습니다. 구성 옵션에 대한 자세한 내용은 <A href="get-csclsconfiguration.md">Get-CsClsConfiguration</A> 및 <A href="lync-server-2013-understanding-centralized-logging-service-configuration-settings.md">중앙화된 로깅 서비스 구성 설정 이해</A>를 참조하십시오.

    
    예를 들어 캐시 파일의 네트워크 폴더, 로그 파일의 롤오버 기간 및 로그 파일의 롤오버 크기를 정의하는 새로운 구성을 만들려면 다음 명령을 입력합니다.
    
        New-CsClsConfiguration -Identity "site:Redmond" -CacheFileNetworkFolder "\\fs01.contoso.net\filestore\logfiles" -EtlFileRolloverMinutes 120 -EtlFileRolloverSizeMB 40

새로운 구성을 만드는 것과 중앙 로깅 서비스의 새로운 속성을 정의하는 방식을 신중하게 계획해야 합니다. 구성을 변경할 때에는 주의를 기울여야 하며 변경 후에 문제 시나리오를 올바르게 로깅할 수 있을지 확인해야 합니다. 적절한 크기와 롤오버 기간으로 로그를 더욱 효과적으로 관리하여 문제 발생 시 문제를 손쉽게 해결할 수 있도록 구성을 변경해야 합니다.

## 기존 중앙 로깅 서비스 구성을 제거하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  명령줄 프롬프트에 다음 명령을 입력합니다.
    
        Remove-CsClsConfiguration -Identity <scope and name>
    
    예를 들어 로그 파일 롤오버 기간과 롤오버 로그 파일 크기를 늘리고 로그 파일 캐시 위치를 네트워크 공유로 설정하기 위해 기존에 만든 중앙 로깅 서비스 구성을 제거하려면 다음과 같이 합니다.
    
        Remove-CsClsConfiguration -Identity "site:Redmond"
    

    > [!NOTE]
    > 이것은 "새로운 중앙 로깅 서비스 구성을 만들려면" 절차에서 만든 새로운 구성입니다.



사이트 수준 구성을 제거하는 경우 사이트에 전역 설정이 사용됩니다.

## 참고 항목

#### 개념

[중앙화된 로깅 서비스 개요](lync-server-2013-overview-of-the-centralized-logging-service.md)  

#### 기타 리소스

[PowerShell로 중앙화된 로깅 서비스 구성 설정 관리](lync-server-2013-managing-the-centralized-logging-service-configuration-settings.md)  
[Set-CsClsConfiguration](set-csclsconfiguration.md)  
[Get-CsClsConfiguration](get-csclsconfiguration.md)  
[New-CsClsConfiguration](new-csclsconfiguration.md)  
[Remove-CsClsConfiguration](remove-csclsconfiguration.md)

