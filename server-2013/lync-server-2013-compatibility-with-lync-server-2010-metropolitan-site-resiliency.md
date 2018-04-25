---
title: Lync Server 2010 대도시 사이트 복구와 Lync Server 2013의 호환성
TOCTitle: Lync Server 2010 대도시 사이트 복구
ms:assetid: 18673ff6-b664-4a57-a89b-cbda8b129e6a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204715(v=OCS.15)
ms:contentKeyID: 49302942
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2010 대도시 사이트 복구

 

_**마지막으로 수정된 항목:** 2014-03-19_

Lync Server 2010용으로 지원되었던 도시 사이트 탄성 솔루션은 Lync Server 2013에는 지원되지 않습니다. 이 솔루션은 같은 도시 지역의 두 데이터 센터에서 단일 프런트 엔드 풀을 제공했습니다.

도시 사이트 탄성 솔루션은 전체 데이터 센터의 손실이 발생한 경우 복구 목적으로 만들어졌습니다. 풀이 두 개의 데이터 센터에 걸쳐 있는 경우 일반적으로 프런트 엔드의 절반을 하나의 데이터 센터에 배치하고 나머지 반을 두 번째 데이터 센터에 배치합니다. 전체 데이터 센터가 손실될 경우 프런트 엔드 서버의 반을 잃게 되는 셈입니다. 이로 인해 Lync Server 2013에서 프런트 엔드 풀의 새로운 분산 시스템 모델에 문제가 발생할 수 있습니다. 자세한 내용은 [Lync Server 2013 의 프런트 엔드 서버, 메신저 및 현재 상태에 대한 토폴로지 및 구성 요소](lync-server-2013-topologies-and-components-for-front-end-servers-instant-messaging-and-presence.md)를 참고하세요.

