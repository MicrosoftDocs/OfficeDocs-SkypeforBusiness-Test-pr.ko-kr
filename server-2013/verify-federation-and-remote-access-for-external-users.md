---
title: 외부 사용자에 대한 페더레이션 및 원격 액세스 확인
TOCTitle: 외부 사용자에 대한 페더레이션 및 원격 액세스 확인
ms:assetid: a383fefb-c428-4462-93fd-15ba540fa867
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688163(v=OCS.15)
ms:contentKeyID: 49885915
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 외부 사용자에 대한 페더레이션 및 원격 액세스 확인

 

_**마지막으로 수정된 항목:** 2012-09-18_

페더레이션 경로를 Lync Server 2013에지 서버로 전환한 후에는 페더레이션이 올바르게 수행되는지 확인하기 위해 몇 가지 기능 테스트를 수행해야 합니다. 외부 사용자 액세스를 위한 테스트에는 다음 중 일부 또는 모두를 포함하여 조직에서 지원하는 각각의 외부 사용자 유형이 포함됩니다.

## 외부 사용자 및 외부 액세스 연결 테스트

  - 하나 이상의 페더레이션 도메인의 사용자, Lync Server 2013의 내부 사용자 및 Lync Server 2010의 사용자. IM(인스턴트 메시징), 현재 상태, A/V(오디오/비디오) 및 데스크톱 공유를 테스트합니다.

  - 조직에서 Lync Server 2013의 사용자 및 Lync Server 2010의 사용자와의 통신을 지원하고 프로비저닝이 완료된 각 공용 IM 서비스 공급자의 사용자.

  - 익명 사용자가 회의에 참가할 수 있는지 확인합니다.

  - Lync Server 2010의 사용자 및 Lync Server 2010의 사용자와 원격 사용자 액세스를 사용하여(VPN 없이 인트라넷 외부에서 Lync Server 2013에 로그인) Lync Server 2010에 호스팅된 사용자. IM, 현재 상태, A/V 및 데스크톱 공유를 테스트합니다.

  - Lync Server 2013의 사용자 및 Lync Server 2010의 사용자와 원격 사용자 액세스를 사용하여(VPN 없이 인트라넷 외부에서 Lync Server 2013에 로그인) Lync Server 2013에 호스팅된 사용자. 메신저, 현재 상태, A/V 및 데스크톱 공유를 테스트합니다.

