---
title: System Center 검색에 참여하도록 Lync Server 컴퓨터 구성
TOCTitle: System Center 검색에 참여하도록 Lync Server 컴퓨터 구성
ms:assetid: 2f9c9cb0-3120-4571-9cd2-657c2123fe21
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204776(v=OCS.15)
ms:contentKeyID: 49303193
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# System Center 검색에 참여하도록 Lync Server 컴퓨터 구성

 

_**마지막으로 수정된 항목:** 2012-10-20_

새 Lync Server 에이전트가 System Center Operations Manager의 검색 프로세스에 참가하도록 하려면 System Center Operations Manager 콘솔이 설치된 각 컴퓨터에서 다음 절차를 완료해야 합니다.

1.  **관리** 탭에서 **에이전트에서 관리**를 클릭합니다.

2.  컴퓨터의 이름을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다. **속성** 대화 상자의 **보안** 탭에서 **이 에이전트를 프록시로 허용하고 다른 컴퓨터에서 관리되는 개체 검색**을 선택하고 **확인**을 클릭합니다.

2단계를 완료한 후 상태 에이전트 서비스를 다시 부팅합니다. 서비스를 다시 부팅하면 새 컴퓨터 검색이 "강제 수행"됩니다. 서비스를 다시 부팅하지 않으면 System Center Operations Manager에서 새 컴퓨터를 검색할 때까지 최대 4시간이 걸릴 수 있습니다. 서비스가 다시 부팅되고 나면 해당 컴퓨터의 작업 관리자 이벤트 로그에 오류 이벤트가 기록되지 않는지 확인합니다.

