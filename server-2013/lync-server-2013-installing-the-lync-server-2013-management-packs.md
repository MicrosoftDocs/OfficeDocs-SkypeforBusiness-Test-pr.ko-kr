---
title: Lync Server 2013 관리 팩 설치
TOCTitle: Lync Server 2013 관리 팩 설치
ms:assetid: b800d4ab-fdc8-4c72-a76a-b78932779fe3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205202(v=OCS.15)
ms:contentKeyID: 49304821
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 관리 팩 설치

 

_**마지막으로 수정된 항목:** 2012-10-22_

System Center Operations Manager 자체에는 Windows 운영 체제의 일부분만 모니터링하는 기능이 있습니다. 그러나 System Center Operations Manager에서 모니터링할 수 있는 항목과 그러한 항목이 모니터링되는 방식 및 알림이 트리거/보고되는 방식 등을 제어하는 소프트웨어인 관리 팩을 설치하여 System Center Operations Manager의 기능을 확장할 수 있습니다. Microsoft Lync Server 2013에는 다음과 같은 기능을 제공하는 두 가지 System Center Operations Manager 관리 팩이 포함되어 있습니다.

  - 구성 요소 및 사용자 관리 팩(Microsoft.LS.2013.Monitoring.ComponentAndUser.mp)은 이벤트 로그에 기록되거나, 성능 카운터에 의해 등록되거나, CDR(통화 정보 기록) 또는 QoE(체감 품질) 데이터베이스에 로깅되는 Lync Server 문제를 추적합니다. 중요한 문제의 경우 전자 메일, 인스턴트 메시지 또는 SMS(Short Message Service) 메시징을 통해 관리자에게 즉시 알리도록 System Center Operations Manager를 구성할 수 있습니다. SMS는 모바일 장치 간에 텍스트 메시지를 보내는 데 사용되는 기술입니다.
    

    > [!NOTE]
    > Operations Manager 알림을 구성하는 방법에 대한 자세한 내용은 TechNet 라이브러리에 있는 알림 구성(<A class=uri href="http://go.microsoft.com/fwlink/?linkid=268785%26clcid=0x412">http://go.microsoft.com/fwlink/?linkid=268785&amp;clcid=0x412</A>)을 참조하십시오.



  - 모니터링 활성화 팩(Microsoft.LS.2013.Monitoring.ActiveMonitoring.mp)은 시스템으로의 로그온, 인스턴트 메시지 교환, PSTN(공중 전화망)에 있는 전화로 전화 걸기를 비롯하여 주요 Lync Server 구성 요소를 사전에 모니터링합니다. 이러한 테스트는 Lync Server 가상 트랜잭션 cmdlet을 사용하여 수행됩니다. 예를 들어 **Test-CsIM** cmdlet은 한 쌍의 테스트 사용자 간의 인스턴트 메시징 대화를 시뮬레이션하는 데 사용됩니다. 이 시뮬레이션된 메시징 대화가 실패할 경우 알림이 생성됩니다.

Lync Server 2013에 포함된 이 두 가지 관리 팩에는 Microsoft Lync Server 2010에 사용된 관리 팩에 비해 다수의 향상된 기능이 들어 있습니다. 예를 들어 Lync Server 2013 구성 요소 관리 팩의 기능은 Lync Server 자체의 모니터링으로만 한정되지 않습니다. 구성 요소 관리 팩은 Lync Server에 대한 이벤트 로그 및 성능 카운터를 모니터링할 뿐만 아니라 다음과 같은 중요한 항목에 대한 성능을 추적하고 알림을 생성할 수 있습니다.

  - **IIS(인터넷 정보 서비스)**   IIS가 오프라인 상태가 되면 알림이 생성됩니다. Lync Server 웹 서비스에서 IIS를 사용하므로 이것은 중요합니다.

  - **프로세스 사용량**   사용 가능한 메모리를 비롯한 시스템 리소스가 부족해지기 시작하면 알림이 생성됩니다. 이러한 알림은 시스템 사용량이 많은 원인이 Lync Server에 있지 않은 경우에도 생성됩니다.

  - **컴퓨터 오류 이벤트**   서버의 실행 가능성을 위협하는 하드웨어 또는 소프트웨어 문제가 발생할 경우 알림이 생성됩니다. 예를 들어 서버에서 하드웨어 디스크 오류가 발생할 위험이 있는 경우 Lync Server 관리자가 알림을 받게 됩니다.

또한 이러한 새로운 관리 팩은 향상된 보고 기능을 제공합니다. Lync Server 2013에 대한 새로운 보고서에는 다음이 포함됩니다.

  - **종단 간 시나리오 가용성 보고서**   이 보고서에서는 등록 또는 현재 상태와 같은 주요 Lync Server 서비스의 가용성/가동 시간에 대한 자세한 정보를 보여 줍니다.

  - **용량 보고서**   이 보고서에서는 성능 카운터 정보를 사용하여 메모리 가용성 및 프로세서 사용량과 같은 시스템 구성 요소의 추세를 보여 줍니다.

  - **구성 요소 보고서**   이 보고서에서는 주요 알림 생성 요인을 Lync Server 구성 요소별로 그룹화하여 보여 줍니다.

Lync Server 2013용 관리 팩은 통화 안정성(통화 정보 기록을 사용하여 측정된 메트릭)과 QoE 상태(체감 품질을 사용하여 측정된 메트릭)에 대한 알림을 자동으로 보고합니다. 통화 정보 기록을 사용하도록 설정한 경우 System Center Operations Manager 콘솔에서 다음 절차를 완료하여 통화 안정성 알림을 검토할 수 있습니다.

  - **모니터링**, **Microsoft Lync Server 2013 상태**, **통화 안정성 및 미디어 품질**을 차례로 확장한 후 **통화 안정성**을 클릭합니다.

체감 품질 알림을 보려면 System Center Operations Manager 콘솔에서 다음 절차를 완료합니다.

  - **모니터링**, **Microsoft Lync Server 2013 상태**, **통화 안정성 및 미디어 품질**, **미디어 품질**을 차례로 확장합니다.

이제 Lync Server 2013용 관리 팩에서는 Microsoft Lync Server 2010에 사용된 중앙 검색 메커니즘 대신 컴퓨터 수준 검색을 사용합니다. 즉, 각 System Center 에이전트가 기본적으로 자체를 검색하여 자신의 존재를 중앙 관리 서버에 보고합니다. 컴퓨터 수준 검색을 사용하면 System Center 인프라 관리가 간소화되며 다양한 버전의 Lync Server 관리 팩(예: Lync Server 2010용 관리 팩과 Lync Server 2013용 관리 팩)을 함께 사용할 수 있습니다.

