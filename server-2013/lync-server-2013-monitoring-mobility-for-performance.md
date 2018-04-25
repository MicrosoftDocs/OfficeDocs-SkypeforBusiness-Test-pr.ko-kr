---
title: Lync Server 2013의 모바일 기능의 성능 모니터링
TOCTitle: Lync Server 2013의 모바일 기능의 성능 모니터링
ms:assetid: 9c831c63-9a7d-48ec-9118-f8a7e80ddd04
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh690033(v=OCS.15)
ms:contentKeyID: 49304521
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 모바일 기능의 성능 모니터링

 

_**마지막으로 수정된 항목:** 2013-02-14_

Lync Server Mobility Service를 사용하는 경우 프런트 엔드 서버 및 프런트 엔드 풀에 대한 부하가 증가합니다. Android 및 Nokia 장치와 같이 모바일 응용 프로그램을 최소화해도 서버에 대한 연결이 유지되는 모바일 장치의 경우에는 모바일 응용 프로그램을 최소화하면 서버에 대한 연결이 종료되는 장치에 비해 부하가 더 많이 발생합니다. 모바일 기능 사용량이 증가함에 따라 모바일 기능 성능을 모니터링하여 용량을 늘려야 하는 시기를 결정해야 합니다.

다음과 같은 다양한 제한이 모바일 성능에 영향을 줍니다.

  - 사용 가능한 메모리

  - 요청 큐 제한

  - 동시 연결 수

  - IIS 큐 길이

모바일 기능의 성능에 영향을 줄 수 있는 서버의 다른 제한으로는 최대 12개의 동시 로그인, 인증 및 세션 갱신/종료가 있습니다. 대부분의 배포에서는 이러한 최대값을 수정할 필요가 없습니다.

## 이 단원의 내용

  - [서버 메모리 용량 제한 모니터링](lync-server-2013-monitoring-for-server-memory-capacity-limits.md)

  - [Mobility Service 및 UCWA 사용 모니터링](lync-server-2013-monitoring-mobility-service-and-ucwa-usage.md)

  - [높은 성능을 위해 Mobility Service 구성](lync-server-2013-configuring-mobility-service-for-high-performance.md)

  - [IIS 요청 추적 로그 파일 모니터링](lync-server-2013-monitoring-iis-request-tracing-log-files.md)

  - [모바일 기능 성능 카운터](lync-server-2013-mobility-performance-counters.md)

