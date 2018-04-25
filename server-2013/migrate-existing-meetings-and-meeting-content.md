---
title: 기존 모임 및 모임 콘텐츠 마이그레이션
TOCTitle: 기존 모임 및 모임 콘텐츠 마이그레이션
ms:assetid: 30516731-2ae1-4a6d-a7e1-d3f05778c954
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688011(v=OCS.15)
ms:contentKeyID: 49885708
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 기존 모임 및 모임 콘텐츠 마이그레이션

 

_**마지막으로 수정된 항목:** 2013-02-22_

사용자 계정을 Lync Server 2010에서 Lync Server 2013 서버로 이동하면 사용자 계정과 함께 다음과 같은 정보가 이동됩니다.

  - **사용자가 이미 예약한 모임**. 회의 디렉터리 및 회의 데이터 이동이 포함됩니다.

  - **사용자의 개인 ID 번호(PIN)**. 사용자의 현재 PIN은 만료되거나 사용자가 새 PIN을 요청할 때까지 계속 작동합니다.

다음과 같은 사용자 계정 정보는 새 서버로 이동하지 않습니다.

  - **모임 콘텐츠**. PowerPoint, 화이트보드, 첨부 파일, 설문 데이터 등 모임 중에 공유되는 콘텐츠를 이동하려면 **Move-CsUser** cmdlet의 일부분으로 **-MoveConferenceData** 매개 변수를 사용합니다.

