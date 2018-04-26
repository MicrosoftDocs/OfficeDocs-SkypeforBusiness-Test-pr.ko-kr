---
title: 'Lync Server 2013: 위임'
TOCTitle: 위임
ms:assetid: 89e76e5c-3cfb-4504-8d0d-7509c8ba9815
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994045(v=OCS.15)
ms:contentKeyID: 52056888
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 위임

 

_**마지막으로 수정된 항목:** 2013-03-09_

Lync의 위임 기능은 다음과 같은 방식으로 위치 기반 라우팅의 영향을 받습니다.

  - 위치 기반 라우팅을 사용할 수 있는 대리인이 관리자를 대신해 전화를 걸 경우 통화에 권한을 부여하는 데 대리인의 음성 정책이 사용되며, 대리인의 음성 라우팅 정책이 통화를 라우팅하는 데 사용됩니다.

  - 관리자가 받는 수신 PSTN 통화의 경우 통화 전송 및 전달과 동시 연결 항목에 설명되어 있는 통화 전달 또는 동시 연결에 적용되는 동일한 규칙이 적용됩니다.

  - 관리자가 받는 수신 통화에 대해 대리인이 PSTN 끝점을 동시 연결 대상으로 설정한 경우 대리인의 PSTN 끝점으로 통화를 라우팅하는 데 수신 트렁크에 연결된 사이트의 음성 라우팅 정책이 사용됩니다.

  - 위임을 위해서는 일반적으로 관리자 및 관리자와 연결된 대리인이 같은 네트워크 사이트에 있는 것이 좋습니다.

## 참고 항목

#### 기타 리소스

[Lync Server 2013의 위치 기반 라우팅 시나리오](lync-server-2013-scenarios-for-location-based-routing.md)

