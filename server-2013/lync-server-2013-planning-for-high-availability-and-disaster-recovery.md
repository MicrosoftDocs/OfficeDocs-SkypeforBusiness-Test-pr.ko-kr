---
title: 'Lync Server 2013: 고가용성 및 재해 복구 계획'
TOCTitle: 고가용성 및 재해 복구 계획
ms:assetid: 15a72073-0336-45dd-b2a0-35e7522c6000
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204703(v=OCS.15)
ms:contentKeyID: 49302908
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 고가용성 및 재해 복구 계획

 

_**마지막으로 수정된 항목:** 2013-10-31_

Lync Server 2010에서와 마찬가지로, Lync Server 2013에서도 대부분의 서버 역할에 대한 기본적인 고가용성 스키마는 풀링을 통한 서버 중복성을 기반으로 합니다. 특정 서버 역할을 실행하는 서버에서 오류가 발생하면 같은 역할을 실행하는 풀의 다른 서버가 해당 서버의 부하를 대신 처리합니다. 이는 프런트 엔드 서버, 에지 서버, 중재 서버 및 디렉터에 적용됩니다.

Lync Server 2013에는 단일 풀 또는 사이트 전체가 다운되어도 서비스를 계속 제공할 수 있도록 서버를 두 개의 데이터 센터에 지리적으로 분산시키는 기능이 도입되어 프런트 엔드 풀에 대한 새로운 재해 복구 방법이 추가적으로 제공됩니다.

또한 Lync Server 2013에서는 백 엔드 데이터베이스에 대한 동기 SQL 미러링도 지원되므로 백 엔드 서버 고가용성이 향상됩니다.

이 섹션에서는 이와 같은 주요 고가용성 및 재해 복구 기능에 대해 설명하고, 다른 서버 역할의 고가용성 및 재해 복구를 위해 수행할 수 있는 단계에 대해서도 다룹니다.

## 이 섹션의 내용

  - [Lync Server 2013의 프런트 엔드 풀 재해 복구](lync-server-2013-front-end-pool-disaster-recovery.md)

  - [Lync Server 2013의 에지 서버 재해 복구](lync-server-2013-edge-server-disaster-recovery.md)

  - [Lync Server 2013 의 Enterprise Voice 복구 계획](lync-server-2013-planning-for-enterprise-voice-resiliency.md)

  - [Lync Server 2013의 재해 복구를 위한 통화 관리 기능](lync-server-2013-call-management-features-for-disaster-recovery.md)

  - [Lync Server 2013에서 고가용성 및 재해 복구를 위한 영구 채팅 서버 구성](lync-server-2013-configuring-persistent-chat-server-for-high-availability-and-disaster-recovery.md)

  - [Lync Server 2010 대도시 사이트 복구](lync-server-2013-compatibility-with-lync-server-2010-metropolitan-site-resiliency.md)

