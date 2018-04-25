---
title: 'Lync Server 2013: IPv6에 대한 마이그레이션 및 동시 사용 고려 사항'
TOCTitle: IPv6에 대한 마이그레이션 및 동시 사용 고려 사항
ms:assetid: 8c769c4f-c8a9-4cbf-9080-beee3be9848a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205068(v=OCS.15)
ms:contentKeyID: 49304322
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 IPv6에 대한 마이그레이션 및 동시 사용 고려 사항

 

_**마지막으로 수정된 항목:** 2012-06-14_

IP 버전 6(IPv6)는 Lync Server 2010 또는 Office Communications Server에서 지원되지 않습니다. 파일럿 목적으로 Lync Server 2010 및 Lync Server 2013 이중 스택 동시 사용을 테스트할 수 있습니다. 풀에 대해 IPv6(이중 스택 네트워크)를 사용하도록 설정하려면 먼저 지정된 중앙 사이트에 대한 모든 풀을 Lync Server 2013으로 업그레이드하는 것이 좋습니다. IPv6 전용의 풀을 구성해야 할 경우에는 랩 환경에서 테스트 목적으로 IPv6 전용 풀을 설정하는 것이 좋습니다.

마이그레이션 및 동시 사용 중에는 다음과 같은 시나리오가 지원됩니다.

  - 이중 스택 모드의 Lync Server 2013과 동시 사용되는 IPv4 모드의 Lync Server 2013, Lync Server 2010 및 Office Communications Server 2007 R2 풀

  - IPv6 전용 풀이 격리된 상태인 경우 IPv6 전용 모드의 Lync Server 2013 풀

