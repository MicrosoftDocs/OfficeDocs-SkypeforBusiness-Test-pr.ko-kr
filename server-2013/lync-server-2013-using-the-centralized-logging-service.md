---
title: 중앙화된 로깅 서비스 사용
TOCTitle: 중앙화된 로깅 서비스 사용
ms:assetid: 7b05aaef-f0ea-4649-ba8a-02e68b0cdf23
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688101(v=OCS.15)
ms:contentKeyID: 49885828
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 중앙화된 로깅 서비스 사용

 

_**마지막으로 수정된 항목:** 2012-11-01_

중앙 로깅 서비스는 Lync Server 2013의 새로운 기능이며, 이전 릴리스에서 제공되었던 **OCSLogger** 및 **OCSTracer** 도구를 대신해서 보다 향상된 기능을 제공합니다. 중앙 로깅 서비스를 사용하면 다음과 같은 작업을 수행할 수 있습니다.

  - 단일 위치 및 명령을 사용해서 하나 이상의 컴퓨터 또는 풀에서 로그인을 시작합니다.

  - 단일 위치 및 명령을 사용해서 하나 이상의 컴퓨터 또는 풀에서 로그인을 중지합니다.

  - 단일 위치 및 명령으로 하나 이상의 컴퓨터 및 풀에서 로그를 검색합니다. 모든 컴퓨터에서 캡처되고 저장된 전체 로그 집계를 반환하거나 특정 데이터만 캡처하도록 조정된 결과를 반환하도록 검색 명령을 조정할 수 있습니다.

  - 다음과 같이 로깅 세션을 구성합니다.
    
      - **시나리오**를 정의하거나 기본 시나리오를 사용합니다. 중앙 로깅 서비스에서 *시나리오*는 범위(전역 또는 사이트), 시나리오 목적을 식별하기 위한 시나리오 이름 및 하나 이상의 공급자로 구성됩니다. 한 컴퓨터에서 언제라도 두 개의 시나리오를 실행할 수 있습니다.
    
      - 기존 *공급자*를 사용하거나 새 공급자를 만듭니다. *공급자*는 로깅 세션이 수집하는 항목, 세부 정보 수준, 추적할 구성 요소 및 적용할 플래그를 정의합니다.
        

        > [!TIP]
        > OCSLogger에 익숙한 경우 <EM>공급자</EM>는 <STRONG>구성 요소</STRONG>(예: S4, SIPStack), <STRONG>로깅 유형</STRONG>(예: WPP, EventLog 또는 IIS 로그 파일), <STRONG>추적 수준</STRONG>(예: 모두, 상세, 디버그) 및 <STRONG>플래그</STRONG>(예: TF_COMPONENT, TF_DIAG)를 나타내는 총체적 표현을 의미합니다. 이러한 항목은 공급자(Windows PowerShell 변수)로 정의되어 중앙 로깅 서비스 명령에 전달됩니다.

    
      - 로그를 수집하려는 컴퓨터 및 풀을 구성합니다.
    
      - **사이트**(해당 사이트의 컴퓨터에서만 로깅 캡처 실행) 또는 **전역**(배포에 포함된 모든 컴퓨터에서 로깅 캡처 실행) 옵션 중에서 로깅 세션의 범위를 정의합니다.

중앙 로깅 서비스는 매우 강력한 도구이며 대규모나 소규모 모두 문제 해결에 필요한 거의 모든 요구 사항을 충족시킬 수 있습니다. 근본 원인 분석부터 성능 문제까지 중앙 로깅 서비스는 관리자에게 중요한 도구로 활용될 수 있습니다. 모든 예제는 Lync Server 관리 셸을 사용하여 표시됩니다. 여기에는 **CLSController.exe**라는 중앙 로깅 서비스용 명령줄 구성 요소가 있습니다. 도움말은 도구 자체를 통해 명령줄 도구로 제공됩니다. 하지만 명령줄에서 실행할 수 있는 기능은 제한적으로 제공됩니다. Lync Server 관리 셸을 사용하면 이보다 많은 기능을 활용할 수 있으며, 기능 집합을 보다 다양하게 구성할 수 있습니다. 중앙 로깅 서비스를 사용할 때는 항상 Lync Server 관리 셸을 먼저 고려하고 활용해야 합니다.

이 섹션의 항목에서는 중앙 로깅 서비스를 사용하는 방법에 대해 설명하고 여러 기능을 사용하는 방법에 대한 예를 제공합니다.

## 이 단원의 내용

  - [중앙화된 로깅 서비스 개요](lync-server-2013-overview-of-the-centralized-logging-service.md)

  - [PowerShell로 중앙화된 로깅 서비스 구성 설정 관리](lync-server-2013-managing-the-centralized-logging-service-configuration-settings.md)

  - [중앙화된 로깅 서비스 구성 설정 이해](lync-server-2013-understanding-centralized-logging-service-configuration-settings.md)

  - [중앙화된 로깅 서비스에 시작을 사용하여 로그 캡처](lync-server-2013-using-start-for-the-centralized-logging-service-to-capture-logs.md)

  - [중앙화된 로깅 서비스에 중지 사용](lync-server-2013-using-stop-for-the-centralized-logging-service.md)

  - [중앙화된 로깅 서비스에서 만든 로그 캡처에 검색 사용](lync-server-2013-using-search-on-capture-logs-created-by-the-centralized-logging-service.md)

  - [중앙화된 로깅 서비스의 로그 캡처 읽기](lync-server-2013-reading-capture-logs-from-the-centralized-logging-service.md)

