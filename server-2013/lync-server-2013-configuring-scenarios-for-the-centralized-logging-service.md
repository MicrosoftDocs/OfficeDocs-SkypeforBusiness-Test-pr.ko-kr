---
title: 중앙 로깅 서비스에 대한 시나리오 구성
TOCTitle: 중앙 로깅 서비스에 대한 시나리오 구성
ms:assetid: 6c3bf826-e7fd-4002-95dc-01020641ef01
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688085(v=OCS.15)
ms:contentKeyID: 49885802
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 중앙 로깅 서비스에 대한 시나리오 구성

 

_**마지막으로 수정된 항목:** 2014-02-05_

시나리오는 범위(즉, 전역, 사이트, 풀 또는 컴퓨터)를 정의하고 중앙 로깅 서비스에서 사용할 공급자를 정의합니다. 시나리오를 사용하면 공급자에 대한 추적을 사용하거나 사용하지 않도록 설정할 수 있습니다(예: S4, SIPStack, IM, 현재 상태). 시나리오를 구성하면 지정된 논리적 컬렉션에 대해 특정 문제 조건을 해결하는 모든 공급자를 그룹화할 수 있습니다. 문제 해결 및 로깅 요구를 충족하기 위해 시나리오를 수정해야 하는 것으로 확인되는 경우 Lync Server 2013 디버그 도구는 *Edit-CsClsScenario*라는 이름의 함수를 포함하는 *ClsController.psm1*이라는 Windows PowerShell 모듈을 제공합니다. 이 모듈의 목적은 명명된 시나리오의 속성을 편집하는 것입니다. 이 항목에서는 이 모듈의 작동 방법에 대한 예를 보여 줍니다. Lync Server 2013 디버그 도구는 [http://go.microsoft.com/fwlink/?LinkId=285257](http://go.microsoft.com/fwlink/?linkid=285257) 링크에서 다운로드할 수 있습니다.


> [!IMPORTANT]
> 지정된 모든 범위(사이트, 전역, 풀 또는 컴퓨터)에 대해 항상 최대 2개의 시나리오를 실행할 수 있습니다. 현재 실행 중인 시나리오를 확인하려면 Windows PowerShell 및 <A href="get-csclsscenario.md">Get-CsClsScenario</A>를 사용합니다. Windows PowerShell 및 <A href="set-csclsscenario.md">Set-CsClsScenario</A>를 사용하면 실행 중인 시나리오를 동적으로 변경할 수 있습니다. 로깅 세션 중 실행 중인 시나리오를 수정하여 공급자로부터 수집 중인 데이터를 조정하거나 세부적으로 조정할 수 있습니다.



Lync Server 관리 셸을 사용하여 중앙 로깅 서비스 함수를 실행하려면 CsAdministrator 또는 CsServerAdministrator RBAC(역할 기반 액세스 제어) 보안 그룹 또는 이러한 두 그룹 중 하나를 포함하는 사용자 지정 RBAC 역할의 구성원이어야 합니다. 이 cmdlet이 지정된 모든 RBAC 목록을 반환하려면(사용자가 직접 만든 사용자 지정 RBAC 역할 포함) Lync Server 관리 셸 또는 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Lync Server 2013 cmdlet"}

예:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsClsConfiguration"}

이 항목의 남은 부분에서는 시나리오를 정의하고, 시나리오를 수정하고, 실행 중인 시나리오를 검색하고, 시나리오를 제거하고, 문제 해결을 최적화하기 위해 시나리오에 포함되는 내용을 지정하는 방법에 대해 자세히 설명합니다. 중앙 로깅 서비스 명령을 실행하는 방법은 두 가지입니다. 기본적으로 C:\\Program Files\\Common Files\\Microsoft Lync Server 2013\\CLSAgent 디렉터리에 있는 CLSController.exe를 사용하거나 Lync Server 관리 셸을 사용해서 Windows PowerShell 명령을 실행할 수 있습니다. 중요한 차이점은 명령줄에서 CLSController.exe를 사용할 경우 사용 가능한 시나리오를 선택하는 데 제한이 있다는 점입니다. Windows PowerShell을 사용할 경우에는 로깅 세션에 사용할 새 시나리오를 정의할 수 있습니다.

[중앙화된 로깅 서비스 개요](lync-server-2013-overview-of-the-centralized-logging-service.md)에 소개된 대로 시나리오의 요소는 다음과 같습니다.

  - **공급자**   OCSLogger에 익숙한 경우, 공급자는 추적 엔진이 로그를 수집해야 하는 대상을 OCSLogger에 지정하기 위해 선택하는 구성 요소입니다. 공급자는 OCSLogger에서 동일한 이름의 구성 요소이며, 많은 경우에 OCSLogger의 구성 요소와 동일한 이름을 포함합니다. OCSLogger에 익숙하지 않은 경우 공급자는 중앙 로깅 서비스가 로그를 수집할 서버 역할 관련 구성 요소입니다. 공급자 구성에 대한 자세한 내용은 [중앙 로깅 서비스에 대한 공급자 구성](lync-server-2013-configuring-providers-for-centralized-logging-service.md)을 참조하십시오.

  - **Identity**   - Identity 매개 변수는 시나리오의 범위 및 이름을 설정합니다. 예를 들어 "global"이라는 범주를 설정하고 시나리오를 "LyssServiceScenario"로 식별할 수 있습니다. 두 가지를 조합하면 Identity(예: "global/LyssServiceScenario")가 정의됩니다.
    
    선택적으로 -Name 및 -Parent 매개 변수를 사용할 수 있습니다. Name 매개 변수는 시나리오를 고유하게 식별하기 위해 정의합니다. Name을 사용할 경우에는 Parent도 사용해서 전역 또는 사이트에 시나리오를 추가해야 합니다.
    

    > [!IMPORTANT]
    > Name 및 Parent 매개 변수를 사용할 경우에는 <STRONG>-Identity</STRONG> 매개 변수를 사용할 수 없습니다.



## New-CsClsScenario cmdlet을 사용하여 새 시나리오를 만들려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  로깅 세션에 대한 새 시나리오를 만들려면 [New-CsClsProvider](new-csclsprovider.md)를 사용하고 시나리오의 이름을 정의합니다(즉, 고유하게 식별하기 위한 방법). WPP(Windows Software Tracing Preprocessor의 약어이며 기본값임), EventLog(Windows 이벤트 로그 형식) 또는 IISLog(IIS 로그 파일 형식을 기반으로 하는 ASCII 형식 파일) 중에서 로깅 형식 유형을 선택합니다. 그런 다음 수준(이 항목의 로깅 수준 아래에 정의됨) 및 플래그(이 항목의 플래그 아래에 정의됨)를 정의합니다.
    
    이 예제 시나리오에서는 예제 공급자 변수로 LyssProvider를 사용합니다.
    
    정의된 옵션을 사용하여 시나리오를 만들려면 다음을 입력합니다.
    
        New-CsClsScenario -Identity <scope>/<unique scenario name> -Provider <provider variable>
    
    예:
    
        New-CsClsScenario -Identity "site:Redmond/LyssServiceScenario" -Provider $LyssProvider
    
    \-Name 및 -Parent를 사용한 대체 형식:
    
        New-CsClsScenario -Name "LyssServiceScenario" -Parent "site:Redmond" -Provider $LyssProvider

## New-CsClsScenario cmdlet을 사용하여 다중 공급자가 포함된 새 시나리오를 만들려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  범위당 시나리오는 2개로 제한됩니다. 하지만 공급자 집합 수는 제한이 없습니다. 이 예에서는 3개의 공급자를 만들었고 현재 정의 중인 시나리오에 이 세 개를 모두 지정한다고 가정합니다. 공급자 변수 이름은 LyssProvider, ABServerProvider 및 SIPStackProvider입니다. 여러 개의 공급자를 정의해서 시나리오에 지정하려면 Lync Server 관리 셸 또는 Windows PowerShell 명령 프롬프트에서 다음을 입력합니다.
    
        New-CsClsScenario -Identity "site:Redmond/CollectDataScenario" -Provider @{Add=$LyssProvider, $ABServerProvider,  $SIPStackProvider}
    

    > [!NOTE]
    > Windows PowerShell에 표시된 것처럼 <CODE>@{&lt;variable&gt;=&lt;value1&gt;, &lt;value2&gt;, &lt;value&gt;...}</CODE>를 사용하여 값의 해시 테이블을 만드는 방식을 <EM>스플랫(splat)</EM>이라고 합니다. Windows PowerShell의 스플랫에 대한 자세한 내용은 <A class=uri href="http://go.microsoft.com/fwlink/?linkid=267760%26clcid=0x412">http://go.microsoft.com/fwlink/?linkid=267760&amp;clcid=0x412</A>를 참조하십시오.



## Set-CsClsScenario cmdlet을 사용하여 기존 시나리오를 수정하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  시나리오는 범위당 두 개로 제한됩니다. 로깅 캡처 세션이 진행 중일 때에도 언제든지 실행 중인 시나리오를 변경할 수 있습니다. 실행 중인 시나리오를 다시 정의할 경우에는 현재 로깅 세션에서 제거된 시나리오 사용을 중지하고 새 시나리오를 사용합니다. 하지만 제거된 시나리오에서 캡처된 로깅 정보는 캡처된 로그에 유지됩니다. 새 시나리오를 정의하려면 다음을 수행합니다(이미 정의된 공급자 이름 "S4Provider"를 추가한다고 가정).
    
        Set-CsClsScenario -Identity <name of scope and scenario defined by New-CsClsScenario> -Provider @{Add=<new provider to add>}
    
    예:
    
        Set-CsClsScenario -Identity "site:Redmond/LyssServiceScenario" -Provider @{Add=$S4Provider}
    
    공급자를 바꾸려면, 현재 집합을 바꾸기 위한 쉼표로 구분된 공급자 목록 또는 단일 공급자를 정의합니다. 여러 공급자들 중 하나만 바꾸려면 새 공급자와 함께 현재 공급자를 추가하여 새 공급자와 기존 공급자가 모두 포함된 새로운 공급자 집합을 만듭니다. 모든 공급자를 새로운 집합으로 바꾸려면 다음을 입력합니다.
    
        Set-CsClsScenario -Identity <name of scope and scenario defined by New-CsClsScenario> -Provider @{Replace=<providers to replace existing provider set>}
    
    예를 들어 $LyssProvider, $ABServerProvider 및 $SIPStackProvider로 구성된 현재 집합을 $LyssServiceProvider로 바꾸려면
    
        Set-CsClsScenario -Identity "site:Redmond/LyssServiceScenario" -Provider @{Replace=$LyssServiceProvider}
    
    $LyssProvider, $ABServerProvider 및 $SIPStackProvider로 구성된 현재 집합 중에서 $LyssProvider 공급자만 $LyssServiceProvider로 바꾸려면 다음을 입력합니다.
    
        Set-CsClsScenario -Identity "site:Redmond/LyssServiceScenario" -Provider @{Replace=$LyssServiceProvider, $ABServerProvider, $SIPStackProvider}

## Remove-CsClsScenario cmdlet을 사용하여 기존 시나리오를 제거하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  이전에 정의된 시나리오를 제거하려면 다음을 입력합니다.
    
        Remove-CsClsScenario -Identity <name of scope and scenario>
    
    예를 들어 정의된 시나리오 site:Redmond/LyssServiceScenario를 제거하려면
    
        Remove-CsClsScenario -Identity "site:Redmond/LyssServiceScenario"

**Remove-CsClsScenario** cmdlet은 지정된 시나리오를 제거하지만 캡처되었던 추적은 로그에서 계속해서 검색에 사용할 수 있습니다.

## ClsController.psm1 모듈을 사용하여 Edit-CsClsScenario cmdlet을 로드하거나 언로드하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.
    

    > [!IMPORTANT]
    > ClsController.psm1 모듈은 별도의 웹 다운로드로 제공됩니다. 이 모듈은 Lync Server 2013 디버깅 도구에 포함됩니다. 기본적으로 디버깅 도구는 C:\Program Files\Lync Server 2013\Debugging Tools 디렉터리에 설치됩니다.



2.  Windows PowerShell에서 다음을 입력합니다.
    
        Import-Module "C:\Program Files\Lync Server 2013\Debugging Tools\ClsController.psm1"
    

    > [!TIP]
    > 모듈을 성공적으로 로드하면 Windows PowerShell 명령 프롬프트가 표시됩니다. 모듈이 로드되었고 Edit-CsClsScenario를 사용할 수 있는지 확인하려면 <CODE>Get-Help Edit-CsClsScenario</CODE>를 입력합니다. EditCsClsScenario에 대한 구문의 기본적인 이해가 필요합니다.



3.  모듈을 언로드하려면 다음을 입력합니다.
    
        Remove-Module ClsController
    

    > [!TIP]
    > 모듈을 성공적으로 언로드하면 Windows PowerShell 명령 프롬프트가 표시됩니다. 모듈이 언로드되었는지 확인하려면 <CODE>Get-Help Edit-CsClsScenario</CODE>를 입력합니다. Windows PowerShell이 cmdlet의 도움말을 찾으려고 시도하지만 실패합니다.



## Edit-ClsController 모듈을 사용하여 시나리오에서 기존 공급자를 제거하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  AlwaysOn 시나리오에서 공급자를 제거하려면 다음을 입력합니다.
    
        Edit-CsClsScenario -ScenarioName <string of the scenario to edit> -ProviderName <string of the provider to remove> -Remove
    
    예:
    
        Edit-CsClsScenario -ScenarioName AlwaysOn -ProviderName ChatServer -Remove
    
    ScenarioName 및 ProviderName 매개 변수는 위치 매개 변수입니다(즉, 명령줄에서 예상된 위치에 정의해야 함). cmdlet 이름을 1번 위치라고 할 때 시나리오 이름이 2번 위치에 있고 공급자가 3번 위치에 있으면 매개 변수 이름을 명시적으로 정의할 필요가 없습니다. 이 정보에 따라 이전 명령을 다시 작성하면 다음과 같이 입력할 수 있습니다.
    
        Edit-CsClsScenario AlwaysOn ChatServer -Remove
    
    매개 변수 값의 위치 기반 배치는 -Scenario 및 -Provider에만 적용됩니다. 다른 모든 매개 변수는 명시적으로 정의해야 합니다.

## Edit-ClsController 모듈을 사용하여 시나리오에 공급자를 추가하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  AlwaysOn 시나리오에 공급자를 추가하려면 다음을 입력합니다.
    
        Edit-CsClsScenario -ScenarioName <string of the scenario to edit> -ProviderName <string of the provider to add> -Level <string of type level> -Flags <string of type flags>
    
    예:
    
        Edit-CsClsScenario -ScenarioName AlwaysOn -ProviderName ChatServer -Level Info -Flags TF_COMPONENT
    
    \-Loglevel의 유형은 심각, 오류, 경고, 정보, 상세, 디버그 또는 모두 중 하나일 수 있습니다. -Flags는 TF\_COMPONENT, TF\_DIAG 등 공급자가 지원하는 모든 플래그일 수 있습니다. -Flags는 값이 ALL일 수도 있습니다.
    
    cmdlet의 위치 기능을 사용하여 이전 예제를 입력할 수도 있습니다. 예를 들어 AlwaysOn 시나리오에 ChatServer 공급자를 추가하려면 다음을 입력합니다.
    
        Edit-CsClsScenario AlwaysOn ChatServer -Level Info -Flags ALL

