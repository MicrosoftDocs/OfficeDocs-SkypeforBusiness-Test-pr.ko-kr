---
title: Mobility Service 및 UCWA 사용 모니터링
TOCTitle: Mobility Service 및 UCWA 사용 모니터링
ms:assetid: 8389b37a-ca3e-4047-8b51-85bc07da87e8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh690025(v=OCS.15)
ms:contentKeyID: 49304235
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Mobility Service 및 UCWA 사용 모니터링

 

_**마지막으로 수정된 항목:** 2013-02-14_

Lync Server Mobility Service(Mcx) 및 UCWA(통합 통신 웹 API)에서 사용하는 CPU 및 메모리를 지속적으로 모니터링해야 합니다. 사용량을 모니터링하려면 다음 방법을 사용하면 됩니다.

**UCWA(통합 통신 웹 API)의 경우:**

  - IIS(인터넷 정보 서비스) 관리자의 **LyncUcwa** 작업자 프로세스. **작업자 프로세스** 창에서 **CPU %** 및 **전용 바이트(KB)**(메모리) 열을 확인합니다.

  - **CPU** 및 **프로세서** 성능 카운터

대부분의 배포에서 UCWA CPU 사용량은 평균 15% 미만이어야 하며 메모리 사용량은 [서버 메모리 용량 제한 모니터링](lync-server-2013-monitoring-for-server-memory-capacity-limits.md)에서 설명하는 제한 내로 유지되어야 합니다.

CPU 및 메모리 사용량 카운터 외에 다음 성능 카운터를 사용하여 서버가 너무 많은 요청으로 인해 오버로드되었는지를 확인할 수 있습니다.

  - 서버의 대기 중인 웹 요청 수를 나타내는 **LS:WEB – Throttling and Authentication\\WEB – Total Requests in Processing**. 이 카운터의 값이 10,000에 도달하면 후속 요청은 실패하며 "503 - 서비스를 사용할 수 없음" 오류 메시지가 표시됩니다.

  - **ASP.NET\\Requests Queued**(항상 0이어야 함)


> [!NOTE]
> 이 값에 도달하거나 값을 초과하는 경우에는 용량 계획을 다시 확인하여 웹 서비스를 호스트하는 컴퓨터의 올바른 CPU 크기와 코어 및 메모리 수를 다시 계산해야 합니다.



**Mobility Service(Mcx)의 경우:**

  - IIS(인터넷 정보 서비스) 관리자의 **CSIntMcxAppPool** 및 **CSExtMcxAppPool** 작업자 프로세스. **작업자 프로세스** 창에서 **CPU %** 및 **전용 바이트(KB)**(메모리) 열을 확인합니다.

  - **CPU** 및 **프로세서** 성능 카운터

대부분의 배포에서 Mobility Service CPU 사용량은 평균 15% 미만이어야 하며 메모리 사용량은 [서버 메모리 용량 제한 모니터링](lync-server-2013-monitoring-for-server-memory-capacity-limits.md)에서 설명하는 제한 내로 유지되어야 합니다.

CPU 및 메모리 사용량 카운터 외에 다음 ASP.NET 성능 카운터를 사용하여 서버가 너무 많은 요청으로 인해 오버로드되었는지를 확인할 수 있습니다.

  - 서버의 대기 중인 웹 요청 수를 나타내는 **ASP.NET v2.0.50727\\Requests Current**. 이 카운터의 값이 5,000에 도달하면 후속 요청은 실패하며 "503 - 서비스를 사용할 수 없음" 오류 메시지가 표시됩니다.

  - **ASP.NET\\Requests Queued**(항상 0이어야 함)


> [!NOTE]
> 이 값에 도달하거나 값을 초과하는 경우에는 용량 계획을 다시 확인하여 웹 서비스를 호스트하는 컴퓨터의 올바른 CPU 크기와 코어 및 메모리 수를 다시 계산해야 합니다.



## 참고 항목

#### 개념

[서버 메모리 용량 제한 모니터링](lync-server-2013-monitoring-for-server-memory-capacity-limits.md)

