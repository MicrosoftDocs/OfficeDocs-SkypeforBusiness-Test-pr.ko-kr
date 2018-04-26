---
title: 동시 사용 고려 사항
TOCTitle: 동시 사용 고려 사항
ms:assetid: 9d1a3c0f-492a-4e37-bc2f-63509e328785
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205131(v=OCS.15)
ms:contentKeyID: 49304529
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 동시 사용 고려 사항

 

_**마지막으로 수정된 항목:** 2012-10-06_

마이그레이션 후에는 Lync Server 2013, 영구 채팅 서버 풀만 있게 되며, 레거시 배포는 해제할 수 있습니다.

마이그레션이 완료된 후 현재 그룹 채팅 서버 배포를 완전히 해제하기 전에 다음과 같은 배포가 있을 수 있습니다.

  - Lync Server 2013, 영구 채팅 서버 풀 - Lync Server 2013 풀에 속해 있어야 합니다.

  - Lync Server 2010, 그룹 채팅 풀 - Lync Server 2010 풀에 속해 있어야 합니다.

  - Office Communications Server 2007 R2그룹 채팅 풀 - Office Communications Server 2007 R2 풀에 속해 있어야 합니다.

이러한 배포는 함께 있을 수 있지만, 한 배포의 범주, 대화방 및 추가 기능이 다른 배포의 범주, 대화방 및 추가 기능과 상호 작용하지 않습니다.

Office Communications Server 2007 R2, Lync Server 2010, 그룹 채팅 또는 Lync Server 2013의 경우 수동 구성을 사용하여 레거시 클라이언트( 그룹 채팅 클라이언트)를 한 번에 한 풀에 연결할 수 있습니다.

Lync 2013(클라이언트)은 Lync Server 2013, 영구 채팅 서버 풀과만 상호 작용할 수 있으며, 레거시 그룹 채팅 서버 풀과는 상호 작용할 수 없습니다. Lync 2013(클라이언트)에서 영구 채팅을 사용하려면 사용자가 Lync 2013에 속해 있고 이를 사용할 수 있도록 정책에 설정되어 있어야 합니다.

