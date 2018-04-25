---
title: 'Lync Server 2013: 전화 접속 회의에 대한 다이얼 플랜 구성'
TOCTitle: 전화 접속 회의에 대한 다이얼 플랜 구성
ms:assetid: a3e0958e-384f-43e5-b4c9-686b6ecac7ed
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412768(v=OCS.15)
ms:contentKeyID: 49304598
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 전화 접속 회의에 대한 다이얼 플랜 구성

 

_**마지막으로 수정된 항목:** 2013-02-25_

전화 접속 회의를 배포할 경우 전화 접속 액세스 전화 번호를 라우팅하기 위해 하나 이상의 다이얼 플랜을 만들거나 수정해야 합니다. 각 다이얼 플랜의 하나 이상의 정규화 규칙이 전화 내선 번호를 E.164 형식의 완전한 전화 번호로 변환하는지 확인합니다. 전화 접속 회의의 사용자는 PIN(개인 식별 번호) 및 전화 번호를 입력하여 인증된 엔터프라이즈 사용자로 전화 회의에 참가합니다. 사용자들이 전화 내선 번호를 입력할 때 사용자를 인증할 수 있도록 내선 번호를 완전한 전화 번호로 변환하는 정규화 규칙이 필요합니다.

전화 접속 회의에 대해 다이얼 플랜을 설정하려면 다음을 수행합니다.

  - Enterprise Voice 배포 여부에 상관없이 전역 다이얼 플랜을 수정하여 전화 접속 회의 지역을 추가하고 정규화 규칙이 전화 접속 액세스 번호를 정확하게 변환할 수 있도록 합니다. 자세한 내용은 [Lync Server 2013에서 다이얼 플랜 수정](lync-server-2013-modify-a-dial-plan.md)을 참고하세요.

  - Enterprise Voice를 배포하지 않은 경우에는 전화 접속 회의 액세스 번호에 대해 다이얼 플랜을 만듭니다. 이 경우 전화 접속 회의 지역을 포함해야 합니다. 자세한 내용은 [Lync Server 2013에서 다이얼 플랜 만들기](lync-server-2013-create-a-dial-plan.md)를 참조하십시오.

  - Enterprise Voice를 배포한 경우 필요에 따라 Enterprise Voice 다이얼 플랜을 수정하여 지역을 포함하고 전화 접속 액세스 번호에 적합한 정규화 규칙을 사용합니다. 자세한 내용은 [Lync Server 2013에서 다이얼 플랜 수정](lync-server-2013-modify-a-dial-plan.md)을 참조하십시오. 전화 접속 액세스 번호에만 사용되는 전용 다이얼 플랜을 만들 수도 있습니다. 자세한 내용은 [Lync Server 2013에서 다이얼 플랜 만들기](lync-server-2013-create-a-dial-plan.md)를 참조하십시오.

지역을 계획하는 방법에 대한 자세한 내용은 계획 설명서에서 [Lync Server 2013의 전화 접속 회의 요구 사항](lync-server-2013-dial-in-conferencing-requirements.md)을 참조하십시오.

## 이 단원의 내용

  - [Lync Server 2013에서 다이얼 플랜 정보 보기](lync-server-2013-view-dial-plan-information.md)

  - [Lync Server 2013에서 다이얼 플랜 만들기](lync-server-2013-create-a-dial-plan.md)

  - [Lync Server 2013에서 다이얼 플랜 수정](lync-server-2013-modify-a-dial-plan.md)

  - [Lync Server 2013에서 정규화 규칙 정의](lync-server-2013-defining-normalization-rules.md)

