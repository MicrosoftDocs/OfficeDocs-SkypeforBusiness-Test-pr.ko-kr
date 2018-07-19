---
title: 중앙 로깅 서비스에 대한 공급자 구성
TOCTitle: 중앙 로깅 서비스에 대한 공급자 구성
ms:assetid: 6a197ecf-b56b-45e0-8e7c-f532ec5164ff
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688082(v=OCS.15)
ms:contentKeyID: 49885796
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 중앙 로깅 서비스에 대한 공급자 구성

 

_**마지막으로 수정된 항목:** 2014-03-19_

중앙 로깅 서비스에서 *공급자*는 가장 중요하게 파악해야 하는 개념 및 구성입니다. *공급자*는 Lync Server 추적 모델에서 Lync Server 서버 역할 구성 요소에 직접적으로 매핑됩니다. 공급자는 추적되는 Lync Server 2013의 구성 요소, 수집할 메시지 유형(예: 심각, 오류 또는 경고), 플래그(예: TF\_Connection 또는 TF\_Diag)를 정의합니다. 공급자는 각 Lync Server 서버 역할에서 추적 가능한 구성 요소입니다. 공급자를 사용하여 구성 요소에 대한 추적 수준 및 유형을 정의합니다(예: S4, SIPStack, IM 및 현재 상태). 정의된 공급자는 특정 문제 조건을 해결하기 위해 지정된 논리적 컬렉션에 대한 모든 공급자를 그룹화하는 시나리오에서 사용됩니다.

Lync Server 관리 셸을 사용하여 중앙 로깅 서비스 함수를 실행하려면 CsAdministrator 또는 CsServerAdministrator RBAC(역할 기반 액세스 제어) 보안 그룹 또는 이러한 두 그룹 중 하나를 포함하는 사용자 지정 RBAC 역할의 구성원이어야 합니다. 이 cmdlet이 지정된 모든 RBAC(역할 기반 액세스 제어) 목록을 반환하려면(사용자가 직접 만든 사용자 지정 RBAC 역할 포함) Lync Server 관리 셸 또는 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Lync Server 2013 cmdlet"}

예:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsClsConfiguration"}

이 항목의 남은 부분에서는 공급자를 정의하고, 문제 해결을 최적화하기 위해 공급자 및 공급자 정의에 포함되는 항목을 수정하는 방법에 대해 집중적으로 설명합니다. 중앙 로깅 서비스 명령은 두 가지 방법으로 실행할 수 있습니다. 기본적으로 C:\\Program Files\\Common Files\\Microsoft Lync Server 2013\\CLSAgent 디렉터리에 있는 CLSController.exe를 사용하거나 Lync Server 관리 셸을 사용해서 Windows PowerShell 명령을 실행할 수 있습니다. 중요한 차이점은, CLSController.exe를 명령줄에서 사용할 경우 공급자가 이미 정의되었고 변경할 수 없는 상태에서 선택할 수 있는 시나리오가 제한되어 있지만, Windows PowerShell을 사용할 경우에는 로깅 세션에서 사용할 새 공급자를 정의하고 공급자가 수집하는 항목 및 데이터 수집 수준 등 공급자 만들기를 완벽하게 제어할 수 있다는 것입니다.


> [!IMPORTANT]
> 앞에서 설명한 것처럼 공급자는 매우 강력합니다. 하지만 시나리오는 공급자가 제공하는 구성 요소에 대한 추적을 설정하고 실행하는 데 필요한 모든 정보를 포함하기 때문에 보다 강력합니다. 공급자 컬렉션을 포함하는 시나리오에서 명령줄에서 한 번에 수백 개의 명령을 실행하는 것과 수백 개의 명령을 포함하는 배치 파일을 실행해서 많은 정보를 수집하는 것에 대한 느슨한 비교일 수 있습니다.<BR>공급자를 세부적으로 조사할 필요가 없도록 중앙 로깅 서비스에서는 이미 정의된 여러 개의 시나리오를 제공합니다. 제공된 시나리오에는 발생 가능한 다양한 문제들이 포함되어 있습니다. 드문 경우지만 공급자를 만들고 정의해서 이를 시나리오에 지정해야 할 수도 있습니다. 새 공급자와 시나리오를 만들기 위한 필요성을 조사하기 전에 먼저 이러한 각 시나리오를 충분히 살펴보는 것이 좋습니다. 공급자 만들기에 대한 정보도 사용자가 추적 정보 수집을 위해 공급자 요소를 사용하는 시나리오에 익숙해질 수 있도록 여기에서 제공되지만 공급자 자체에 대한 세부 정보는 여기에서 다뤄지지 않습니다.



[중앙화된 로깅 서비스 개요](lync-server-2013-overview-of-the-centralized-logging-service.md)에서 소개된, 시나리오에 사용하기 위한 공급자 정의의 핵심 요소는 다음과 같습니다.

  - **공급자**   OCSLogger에 익숙한 경우, 공급자는 추적 엔진이 로그를 수집해야 하는 대상을 OCSLogger에 지정하기 위해 선택하는 구성 요소입니다. 공급자는 OCSLogger에서 동일한 이름의 구성 요소이며, 많은 경우에 OCSLogger의 구성 요소와 동일한 이름을 포함합니다. OCSLogger에 익숙하지 않은 경우 공급자는 중앙 로깅 서비스가 로그를 수집할 서버 역할 관련 구성 요소입니다. 중앙 로깅 서비스의 경우 CLSAgent는 중앙 로깅 서비스에서 사용자가 공급자 구성에 정의하는 구성 요소의 추적을 수행하는 아키텍처적인 부분입니다.

  - **로깅 수준**   OCSLogger는 수집된 데이터에 대한 다양한 세부 정보 수준을 선택할 수 있는 옵션을 제공합니다. 이 기능은 중앙 로깅 서비스 및 시나리오의 핵심 부분이며, **Type** 매개 변수에 의해 정의됩니다. 다음 중에서 선택할 수 있습니다.
    
      - **All**   정의된 공급자에 대한 로그에 심각, 오류, 경고 및 정보 유형의 추적 메시지를 수집합니다.
    
      - **Fatal**   정의된 공급자에 대한 심각한 실패를 나타내는 추적 메시지만 수집합니다.
    
      - **Error**   정의된 공급자에 대한 오류를 나타내는 추적 메시지만 수집합니다.
    
      - **Warning**   심각 및 오류 메시지를 포함하여 정의된 공급자에 대한 경고를 나타내는 추적 메시지만 수집합니다.
    
      - **Info**   심각, 오류 및 경고 메시지를 포함하여 정의된 공급자에 대한 정보 메시지를 나타내는 추적 메시지만 수집합니다.
    
      - **Verbose**   정의된 공급자에 대한 심각, 오류, 경고 및 정보 유형의 모든 추적 메시지를 수집합니다.

  - **Flags**   OCSLogger는 사용자가 추적 파일에서 검색할 수 있는 정보 유형을 정의하는 각 공급자에 대한 플래그를 선택할 수 있는 옵션을 제공합니다. 공급자에 따라 다음과 같은 플래그를 선택할 수 있습니다.
    
      - **TF\_Connection**   연결 관련 로그 항목을 제공합니다. 이러한 로그에는 특정 구성 요소에 대해 설정된 연결에 대한 정보가 포함됩니다. 여기에는 또한 중요한 네트워크 수준 정보(즉, 연결 개념이 없는 구성 요소)도 포함됩니다.
    
      - **TF\_Security**   보안과 관련된 모든 이벤트/로그 항목을 제공합니다. 예를 들어 SipStack의 경우 도메인 유효성 검사 실패 및 클라이언트 인증/권한 부여 실패와 같은 보안 이벤트가 있습니다.
    
      - **TF\_Diag**   구성 요소를 진단하거나 문제를 해결하는 데 사용할 수 있는 진단 이벤트를 제공합니다. 예를 들어 SipStack의 경우 인증서 실패 또는 DNS 경고/오류가 있습니다.
    
      - **TF\_Protocol**   SIP 및 CCCP 메시지와 같은 프로토콜 메시지를 제공합니다.
    
      - **TF\_Component**   공급자의 일부로 지정된 구성 요소에 대해 로깅을 사용하도록 설정합니다.
    
      - **All**   공급자에 대해 사용할 수 있는 모든 사용 가능한 플래그를 설정합니다.

## 기존 중앙 로깅 서비스 시나리오 공급자에 대한 정보를 검토하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  기존 공급자의 구성을 검토하려면 다음을 입력합니다.
    
        Get-CsClsScenario -Identity <scope and scenario name>
    
    예를 들어 전역 회의 참석자에 대한 정보를 검토하려면 다음을 입력합니다.
    
        Get-CsClsScenario -Identity "global/CAA"
    
    이 명령은 연결된 플래그, 설정 및 구성 요소를 포함하는 공급자 목록을 표시합니다. 표시된 정보가 충분하지 않거나 목록이 기본 Windows PowerShell 목록 형식에 대해 너무 긴 경우, 다른 출력 방법을 정의하여 추가 정보를 표시할 수 있습니다. 이를 위해서는 다음을 입력합니다.
    
        Get-CsClsScenario -Identity "global/CAA" | Select-Object -ExpandProperty Provider
    
    이 명령의 출력에는 각 공급자가 표시되며, 각 공급자는 공급자 이름, 로깅 유형, 로깅 수준, 플래그, GUID 및 역할이 별도의 줄에 하나씩 5줄 형식으로 표시됩니다.

## 새 중앙 로깅 서비스 시나리오 공급자를 정의하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  시나리오 공급자는 추적할 구성 요소, 사용할 플래그 및 수집할 세부 정보 수준으로 구성됩니다. 이를 위해서는 다음을 입력합니다.
    
        $<variableName> = New-CsClsProvider -Name <provider component> -Type <log type> -Level <log level detail type> -Flags <provider trace log flags>
    
    예를 들어 Lyss 공급자에서 수집할 항목 및 세부 정보 수준을 정의하는 추적 공급자 정의는 다음과 비슷하게 표시됩니다.
    
        $LyssProvider = New-CsClsProvider -Name "Lyss" -Type "WPP" -Level "Info" -Flags "All"

\-Level은 심각, 오류, 경고 및 정보 메시지를 수집합니다. 사용되는 플래그는 Lyss 공급자에 대해 정의된 모든 항목이며 TF\_Connection, TF\_Diag 및 TF\_Protocol을 포함합니다.

$LyssProvider 변수를 정의한 후에는 **New-CsClsScenario** cmdlet에서 사용하여 Lyss 공급자에서 추적을 수집할 수 있습니다. 공급자를 만들고 새 시나리오에 지정하는 작업을 완료하려면 다음을 입력합니다.

    New-CsClsScenario -Identity "site:Redmond/RedmondLyssInfo" -Provider $LyssProvider

$LyssProvider는 **New-CsClsProvider**로 만들어진 정의된 시나리오가 포함된 변수입니다.

## 기존 중앙 로깅 서비스 시나리오 공급자를 변경하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  기존 공급자의 구성을 업데이트하거나 변경하려면 다음을 입력합니다.
    
        $LyssProvider = New-CsClsProvider -Name "Lyss" -Type "WPP" -Level "Debug" -Flags "TF_Connection, TF_Diag"
    
    그런 후 다음을 입력하여 시나리오를 업데이트해서 공급자를 지정합니다.
    
        Set-CsClsScenario -Identity "site:Redmond/RedmondLyssInfo" -Provider $LyssProvider

이 명령의 최종 결과로 site:Redmond/RedmondLyssInfo 시나리오는 여기에 지정된 공급자에 대한 플래그 및 수준을 업데이트합니다. 새 시나리오는 Get-CsClsScenario를 사용해서 볼 수 있습니다. 자세한 내용은 [Get-CsClsScenario](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsClsScenario)를 참조하십시오.


> [!WARNING]
> <STRONG>New-ClsCsProvider</STRONG>는 플래그가 유효한지 여부를 확인하지 않습니다. 플래그 철자(예: TF_DIAG 또는 TF_CONNECTION)가 올바른지 확인하십시오. 플래그 철자가 잘못된 경우 공급자가 예상된 로그 정보를 반환할 수 없습니다.



이 시나리오에 공급자를 추가하려면 다음을 입력합니다.

    Set-CsClsScenario -Identity "site:Redmond/RedmondLyssInfo" -Provider @{Add=$ABSProvider, $CASProvider, S4Provider}

여기서 Add 지시문으로 정의된 각 공급자는 이미 **New-CsClsProvider** 프로세스를 사용하여 정의되어 있습니다.

## 시나리오 공급자를 제거하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  제공된 cmdlet을 사용하면 기존 공급자를 업데이트하고 새 공급자를 만들 수 있습니다. 공급자를 제거하려면 **Set-CsClsScenario**의 Provider 매개 변수에 대해 Replace 지시문을 사용해야 합니다. 공급자를 완전히 제거하는 유일한 방법은 동일한 이름으로 다시 정의된 공급자로 바꾸고 Update 지시문을 사용하는 것입니다. 예를 들어, LyssProvider 공급자는 로그 유형이 WPP로 정의되어 있으며, 로그 수준은 Debug이고, 플래그 집합은 TF\_CONNECTION 및 TF\_DIAG입니다. 플래그를 "All"로 변경해야 합니다. 공급자를 변경하려면 다음을 입력합니다.
    
        $LyssProvider = New-CsClsProvider -Name "Lyss" -Type "WPP" -Level "Debug" -Flags "All"
    
        Set-CsClsScenario -Identity "site:Redmond/RedmondLyssInfo" -Provider @{Replace=$LyssProvider}

3.  시나리오 및 시나리오와 연결된 공급자를 완전히 제거하려면 다음을 입력합니다.
    
        Remove-CsClsScenario -Identity <scope and name of scenario>
    
    예:
    
        Remove-CsClsScenario -Identity "site:Redmond/RedmondLyssInfo"
    

    > [!WARNING]
    > <STRONG>Remove-CsClsScenario</STRONG> cmdlet은 사용자에게 확인 메시지를 프롬프트하지 않습니다. 시나리오는 시나리오에 연결된 공급자와 함께 삭제됩니다. 처음에 시나리오를 만들 때 사용한 명령을 다시 실행하면 시나리오를 다시 만들 수 있습니다. 제거된 시나리오 또는 공급자를 복구할 수 있는 절차는 없습니다.



**Remove-CsClsScenario** cmdlet을 사용하여 시나리오를 제거할 때는 해당 범위에서 시나리오가 완전히 제거됩니다. 이전에 만든 시나리오 및 시나리오에 속하는 공급자를 사용하려면 새 공급자를 만들고 이를 새 시나리오에 지정해야 합니다.

## 참고 항목

#### 기타 리소스

[Get-CsClsScenario](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsClsScenario)  
[New-CsClsScenario](new-csclsscenario.md)  
[Remove-CsClsScenario](remove-csclsscenario.md)  
[Set-CsClsScenario](set-csclsscenario.md)  
[New-CsClsProvider](new-csclsprovider.md)

