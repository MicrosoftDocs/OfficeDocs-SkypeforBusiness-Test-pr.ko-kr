---
title: 내선 전화 번호에 대한 통화 대기 구성
TOCTitle: 내선 전화 번호에 대한 통화 대기 구성
ms:assetid: fbf97624-9587-42a6-b276-1b69c574a74d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg182611(v=OCS.15)
ms:contentKeyID: 49305617
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 내선 전화 번호에 대한 통화 대기 구성

 

_**마지막으로 수정된 항목:** 2012-09-10_

통화 대기 응용 프로그램에서는 통화 대기 파킹된 통화 번호 테이블의 내선 번호를 사용하여 통화를 대기합니다. 조직에서 대기 통화에 대해 예약하는 다양한 내선 번호로 통화 대기 파킹된 통화 번호 테이블을 구성해야 합니다. 이 내선 번호는 가상 내선 번호여야 합니다(즉 이 번호에 할당된 사용자나 전화가 없어야 함). 통화 대기 응용 프로그램이 배포 및 구성된 각 Lync Server 풀에는 하나 이상의 파킹된 통화 번호 범위가 포함될 수 있습니다. 파킹된 통화 번호 범위는 Lync Server 배포에서 전역적으로 고유해야 합니다.


> [!IMPORTANT]
> 통화 대기를 사용하려면 음성 정책에서 <STRONG>통화 대기 사용</STRONG> 확인란을 선택해야 합니다. 기본적으로 이 옵션은 선택되어 있지 않습니다.



## 이 단원의 내용

  - [Lync Server 2013에서 통화 대기 번호 범위 만들기 또는 수정](lync-server-2013-create-or-modify-a-call-park-orbit-range.md)

  - [Lync Server 2013에서 통화 대기 파킹된 통화 번호 범위 삭제](lync-server-2013-delete-a-call-park-orbit-range.md)

