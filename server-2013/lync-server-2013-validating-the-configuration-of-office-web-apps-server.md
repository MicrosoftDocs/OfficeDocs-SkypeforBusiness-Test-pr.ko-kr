---
title: Lync Server 2013에서 Office Web Apps 서버 구성의 유효성 검사
TOCTitle: Office Web Apps 서버 구성의 유효성 검사
ms:assetid: f6e8ecbf-305d-4a13-92d0-b61dbd82b0ea
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205393(v=OCS.15)
ms:contentKeyID: 49305564
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 Office Web Apps 서버 구성의 유효성 검사

 

_**마지막으로 수정된 항목:** 2014-04-22_

Office Web Apps 서버가 토폴로지에 추가된 후 그리고 해당 토폴로지가 게시된 후에는 Lync Server 이벤트 로그에 두 가지 새로운 이벤트 로그가 표시되어야 합니다. 먼저, LS 데이터 MCU 이벤트(이벤트 ID 41034)가 추가되어야 합니다. 이 이벤트는 Office Web Apps 서버가 검색되었음을 보고합니다.

**웹 회의 서버 WAC가 검색되었으며 PowerPoint 콘텐츠를 사용할 수 있습니다.(Web Conferencing Server WAC is discovered, PowerPoint content is enabled.)**

또한 백 오피스 Office Web Apps 서버 URL을 보고하는 또 다른 LS 데이터 MCU 이벤트(이벤트 ID 41032)도 표시되어야 합니다. 예를 들면 다음과 같은 로그가 표시되어야 합니다.

**웹 회의 서버 WAC가 검색되었습니다.(Web Conferencing Server WAC discovery has succeeded.)**

**WAC 내부 발표자 페이지: https://atl-officewebapps-001.litwareinc.com/m/Presenter.aspx?a=0\&embed=**

**WAC 내부 참석자 페이지: https://atl-officewebapps-001.litwareinc.com/m/ParticipantFrame.aspx?a=0\&embed=true&=**

**WAC 외부 발표자 페이지: https://atl-officewebapps-001.litwareinc.com/m/Presenter.aspx?a=0\&embed**

**WAC 내부 참석자 페이지: https://atl-officewebapps-001.litwareinc.com/m/ParticipantFrame.aspx?a=0\&embed=true&**

이벤트 ID가 41033인 LS 데이터 MCU 이벤트가 표시되는 경우 이는 Office Web Apps 서버가 검색되지 않았음을 의미합니다. 이 경우에는 Microsoft Lync Server 2013에서 새로 구성된 Office Web Apps 서버를 검색하기 위해 필요한 만큼 검색 시도를 반복합니다. 검색 프로세스가 계속 실패할 경우에는 Office Web Apps 서버를 토폴로지 문서에서 제거하고 업데이트된 토폴로지를 게시한 다음 연결 문제가 해결된 후에 Office Web Apps 서버를 토폴로지에 다시 추가해 봅니다.

Office Web Apps 서버가 올바르게 구성된 것 같고 검색 프로세스에서 인식되었으면 Microsoft Lync 2013 클라이언트 간에 PowerPoint 프레젠테이션을 공유하여 Office Web Apps 서버가 예상대로 작동 중인지 확인할 수 있습니다. 사용자 A가 PowerPoint 프레젠테이션을 로드하고 표시할 수 있으며 사용자 B가 모임에 참가하고 해당 프레젠테이션을 볼 수 있는 경우에는 Office Web Apps 서버가 작동 중인 것입니다.

Office Web Apps 서버가 올바르게 구성된 것처럼 보이지만, PowerPoint 프레젠테이션을 공유하려 할 때 “서버 연결 문제로 인해 일부 공유 기능을 사용할 수 없습니다.”라는 오류 메시지를 나타날 수도 있습니다. 이러한 오류 메시지가 나타나면 새 Office Web Apps 서버와 연결된 프런트 엔드 서버를 다시 시작해야 합니다.

