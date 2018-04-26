---
title: 'Lync Server 2013: 고가용성 및 재해 복구 지원'
TOCTitle: 고가용성 및 재해 복구 지원
ms:assetid: 47e77e85-c7c3-4ade-8db7-a34c71aeafd7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204866(v=OCS.15)
ms:contentKeyID: 49303510
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 고가용성 및 재해 복구 지원

 

_**마지막으로 수정된 항목:** 2012-09-25_

Lync Server 2013은 풀링을 통한 서버 중복성으로 고가용성을 제공합니다. 특정 서버 역할을 실행하는 서버가 실패할 경우 풀에서 동일 역할을 실행하는 다른 서버가 해당 서버의 부하를 맡습니다. 이러한 방식은 프런트 엔드 서버, 에지 서버, 중재 서버 및 디렉터에 적용됩니다. 서버 역할에 대한 자세한 내용은 [Lync Server 2013의 서버 역할](lync-server-2013-server-roles.md)을 참조하십시오.

Lync Server 2013에서는 또한 풀 연결을 설정하여 재해 복구 수단을 제공합니다. 이 토폴로지를 배포할 경우 프런트 엔드 풀의 쌍을 지정합니다. 이 연결 쌍의 각 풀은 별도의 데이터 센터에 위치하며, 지리적으로 별도의 영역에 존재합니다. 하나의 풀 또는 사이트가 다운될 경우 해당 풀의 사용자를 연결된 쌍의 다른 풀을 사용하도록 리디렉션하여 서비스 중단을 최소화할 수 있습니다.

Lync Server 2013에서는 또한 백 엔드 서버의 고가용성이 지원됩니다. 이것은 프런트 엔드 풀에 대해 2개의 백 엔드 서버를 배포하고 백 엔드 서버에서 실행되는 모든 Lync 데이터베이스의 동시 SQL Server 미러링을 설정하는 선택적인 토폴로지입니다.

풀 연결 및 백 엔드 서버 미러링에 대한 자세한 내용은 [Lync Server 2013의 고가용성 및 재해 복구 계획](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md)을 참조하십시오.

## 참고 항목

#### 개념

[Lync Server 2013의 서버 역할](lync-server-2013-server-roles.md)  
[Lync Server 2013의 고가용성 및 재해 복구 계획](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md)

