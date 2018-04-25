---
title: System Center 검색에 참여하도록 감시자 노드 구성
TOCTitle: System Center 검색에 참여하도록 감시자 노드 구성
ms:assetid: 15c5dcfd-603b-47ea-af1b-8714c2ec08af
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204704(v=OCS.15)
ms:contentKeyID: 49302919
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# System Center 검색에 참여하도록 감시자 노드 구성

 

_**마지막으로 수정된 항목:** 2012-10-22_

감시자 노드가 System Center Operations Manager의 검색 프로세스에 참가하도록 하려면 System Center Operations Manager 콘솔이 설치된 컴퓨터에서 다음 절차를 완료해야 합니다.

1.  **관리** 탭에서 **에이전트에서 관리**를 클릭합니다.

2.  감시자 노드 컴퓨터의 이름을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다. **속성** 대화 상자의 **보안** 탭에서 **이 에이전트를 프록시로 허용하고 다른 컴퓨터에서 관리되는 개체 검색**을 선택하고 **확인**을 클릭합니다.

감시자 노드가 프록시로 작동하도록 구성한 후 감시자 노드 컴퓨터를 다시 부팅합니다. 컴퓨터가 다시 부팅되고 나면 해당 컴퓨터의 Operations Manager 이벤트 로그에 오류 이벤트가 기록되지 않는지 확인합니다. 컴퓨터를 15분 정도 실행한 후 Operations Manager 콘솔을 사용하여 Lync Server 컴퓨터가 **Lync** 범주 아래에 나열되는지 확인합니다.

