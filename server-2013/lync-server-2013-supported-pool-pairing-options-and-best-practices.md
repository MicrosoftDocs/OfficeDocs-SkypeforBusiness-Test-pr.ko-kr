---
title: Lync Server 2013 지원되는 풀 연결 옵션 및 모범 사례
TOCTitle: 지원되는 풀 연결 옵션 및 모범 사례
ms:assetid: 142caf34-0f20-47f3-9d32-ce25ab622fad
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204697(v=OCS.15)
ms:contentKeyID: 49302892
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에 대한 지원되는 풀 연결 옵션 및 모범 사례

 

_**마지막으로 수정된 항목:** 2013-02-19_

쌍으로 지정된 프런트 엔드 풀을 포함할 두 데이터 센터 간의 거리에는 제한이 없습니다. 같은 지역에 있으며 고속 링크가 설정된 두 데이터 센터를 사용하는 것이 좋습니다. 단일 재해가 두 데이터 센터에서 동시에 발생하지 않도록 두 데이터 센터가 충분히 떨어져 있는 것이 가장 좋습니다.

두 데이터 센터가 서로 다른 지역에 있어도 되지만 이 경우 데이터 복제 대기 시간으로 인해 데이터 손실률이 높아질 수 있습니다.

쌍으로 지정할 풀을 계획할 때는 다음 쌍만 지원됨을 기억해야 합니다.

  - Enterprise Edition 풀은 다른 Enterprise Edition 풀과만 쌍으로 지정할 수 있습니다. Standard Edition 풀은 다른 Standard Edition 풀과만 쌍으로 지정할 수 있습니다.

  - 물리적 풀은 다른 물리적 풀과만 쌍으로 지정할 수 있습니다. 마찬가지로 가상 풀은 다른 가상 풀과만 쌍으로 지정할 수 있습니다.

토폴로지 작성기 또는 토폴로지 유효성 검사에서 이러한 권장 사항을 따르지 않는 방식으로 두 풀을 쌍으로 지정하는 작업을 차단할 수는 없습니다. 예를 들어 토폴로지 작성기에서는 Enterprise Edition 풀과 Standard Edition 풀의 쌍 지정을 허용합니다. 그러나 이러한 유형으로 쌍을 지정할 수는 없습니다.

쌍의 각 풀에는 재해 발생 시 두 풀의 모든 사용자 작업을 처리할 수 있는 용량이 있어야 합니다.

Enterprise Edition 풀을 쌍으로 지정하는 경우에는 백 엔드 서버에 대해 고가용성을 구현할 수도 있지만, Standard Edition 풀 쌍의 경우에는 재해 복구 조치만 사용 가능합니다.

