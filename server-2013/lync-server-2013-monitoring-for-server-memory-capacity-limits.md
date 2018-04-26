---
title: 서버 메모리 용량 제한 모니터링
TOCTitle: 서버 메모리 용량 제한 모니터링
ms:assetid: 1697ea71-6fcf-480d-b4e9-cd79f94d247e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh689982(v=OCS.15)
ms:contentKeyID: 49302925
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 서버 메모리 용량 제한 모니터링

 

_**마지막으로 수정된 항목:** 2013-02-16_

    Some information in this topic pertains to Cumulative Updates for Lync Server 2013: February 2013.


> [!WARNING]
> 용량 계획에 대해 설명하는 이 항목의 정보는 Lync 2010 Mobile 클라이언트 및 Mobility Service(Mcx)에만 해당됩니다. Lync 2013 모바일 클라이언트에서 사용하는 UCWA(통합 통신 웹 API)에 대한 용량 계획은 Lync Server 2013, 계획 도구에서 제공됩니다.



두 모바일 기능 성능 카운터를 통해 현재 사용량을 파악하고 Lync Server 2013 Mobility Service(Mcx)를 위한 용량을 계획할 수 있을 뿐 아니라 UCWA의 메모리 사용량을 모니터링할 수 있습니다. UCWA의 경우 카운터는 **LS:WEB – UCWA** 범주에 있습니다. Mobility Service(Mcx)의 경우 카운터는 **LS:WEB - Mobile Communication Service** 범주에 있습니다. 모니터링할 카운터는 다음과 같습니다.

  - **Currently Active Session Count with Active Presence Subscriptions**: UCWA 또는 Mobility Service(Mcx)를 통해 등록되었으며 활성 현재 상태 구독을 포함하는 현재 끝점 수(항상 연결된 모바일 사용자의 수)

  - **Currently Active Session Count**: UCWA 또는 Mobility Service를 통해 등록된 현재 끝점 수

시간의 경과에 따른 **Currently Active Session Count with Active Presence Subscriptions**와 **Currently Active Session Count**의 차이가 작은 경우에는 대부분의 모바일 장치 사용자가 Android 또는 Nokia 모바일 장치와 같은 항상 연결되는 장치를 사용하는 것입니다(Mcx의 경우에만 해당). 항상 연결된 상태의 UCWA 장치로는 Lync 2013 모바일 클라이언트를 실행하는 Apple 및 Android 장치가 포함됩니다. 반면 **Currently Active Session Count**가 **Currently Active Session Count with Active Presence Subscriptions**보다 훨씬 큰 경우에는 Apple iOS 장치나 Windows Phone 등의 백그라운드 끝점 장치 사용자가 더 많은 것입니다(Mcx). 이러한 장치로 등록되는 Lync 2013 모바일 클라이언트는 Windows Phone뿐입니다.

예상 사용량, 용량 계획 결과 및 지속적인 Mobility Service/기타 프런트 엔드 서버 카운터 모니터링을 토대로 **Currently Active Session Count with Active Presence Subscriptions** 및 **Currently Active Session Count** 성능 카운터에 제한을 설정해야 합니다. 이렇게 설정한 제한을 통해 서버 용량을 평가하고 용량이 초과되면 경고를 표시할 수 있습니다.

적절한 제한을 결정하려면 먼저 프런트 엔드 서버에서 Mobility Service에 사용 가능한 메모리의 양을 확인해야 합니다. 카운터를 모니터링한 후 다음 수식에 따라 추가 용량을 계획해야 하는 시기를 결정합니다.

Mcx Mobility Service에 사용되는 총 메모리(MB) = 164 + (400 + 134) / 1024 \* **Currently Active Session Count with Active Presence Subscriptions** + 400 / 1024 \*(**Currently Active Session Count** – **Currently Active Session Count with Active Presence Subscriptions**)


> [!IMPORTANT]
> Microsoft Lync Server 2010 Capacity Calculator는 계획자가 CPU, 메모리, 하드 드라이브를 비롯하여 서버에 대한 요구 사항을 결정하는 데 사용할 수 있는 모든 수식으로 채워져 있는 스프레드시트입니다. 이 스프레드시트와 관련 문서는 <A class=uri href="http://go.microsoft.com/fwlink/?linkid=212657">http://go.microsoft.com/fwlink/?linkid=212657</A>에서 다운로드할 수 있습니다.



프런트 엔드 서버는 장애 조치(failover) 상황에서 Mobility Service를 지원하기 위해 충분한 메모리를 사용할 수 있어야 합니다. **Memory\\Available Mbytes** 카운터나 앞서 설명한 수식을 사용하여 프런트 엔드 서버에서 현재 사용 가능한 메모리를 모니터링해 Mobility Service에서 사용할 것으로 예상되는 메모리 양을 계획할 수도 있습니다.

예상 모바일 기능 사용자 수를 계획할 때 프런트 엔드 서버에서 사용 가능한 메모리가 1,500MB보다 적으면 Mobility Service를 지원하기 위해 하드웨어를 더 추가해야 합니다. 자세한 내용은 작업 설명서에서 [Lync Server 2013의 모바일 기능의 성능 모니터링](lync-server-2013-monitoring-mobility-for-performance.md)을 참조하십시오.

## 참고 항목

#### 기타 리소스

[Lync Server 2013의 모바일 기능의 성능 모니터링](lync-server-2013-monitoring-mobility-for-performance.md)

