---
title: 전화 접속 액세스 번호 마이그레이션
TOCTitle: 전화 접속 액세스 번호 마이그레이션
ms:assetid: e0dfaed2-64c7-45cb-aaa9-d6117a26625d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721909(v=OCS.15)
ms:contentKeyID: 49886017
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 전화 접속 액세스 번호 마이그레이션

 

_**마지막으로 수정된 항목:** 2012-10-19_

Lync Server 2010에서 Lync Server 2013으로 전화 접속 액세스 번호를 마이그레이션하려면 **Move-CsApplicationEndpoint** cmdlet을 실행하여 연락처 개체를 마이그레이션해야 합니다. Lync Server 2010과 Lync Server 2013이 동시 사용하는 동안에는 Lync Server 2013에서 만든 전화 접속 액세스 번호가 Lync Server 2010에서 만드는 전화 접속 액세스 번호와 비슷하게 작동합니다.

다음은 Lync Server 2010에서 만들었지만 Lync Server 2013으로 이동된 전화 접속 액세스 번호나 마이그레이션 이전, 도중 또는 이후에 Lync Server 2013에서 만든 전화 접속 액세스 번호의 특징입니다.

  - Office Communications Server 2007 R2 모임 초대와 전화 접속 액세스 번호 페이지에 표시되지 않습니다.

  - Lync Server 2010 모임 초대와 전화 접속 액세스 번호 페이지에 표시됩니다.

  - Lync Server 2013 모임 초대와 전화 접속 액세스 번호 페이지에 표시됩니다.

  - Office Communications Server 2007 R2 관리 도구에서 보거나 수정할 수 없습니다.

  - Lync Server 2010 제어판과 Lync Server 2010 관리 셸에서 보거나 수정할 수 있습니다.

  - Lync Server 2013 제어판과 Lync Server 2013 관리 셸에서 보거나 수정할 수 있습니다.

  - Priority 매개 변수와 함께 et-CsDialinConferencingAccessNumber cmdlet을 사용하여 지역 내에서 다시 순차화할 수 있습니다.

Lync Server 2010 풀을 해지하기 전에 Lync Server 2010 풀을 가리키는 전화 접속 액세스 번호의 마이그레이션을 마쳐야 합니다. 다음 절차에 설명된 대로 전화 접속 액세스 번호 마이그레이션을 완료하지 않으면 액세스 번호로의 수신 전화가 실패합니다.


> [!IMPORTANT]
> Lync Server 2010 풀을 해지하기 전에 이 절차를 수행해야 합니다.




> [!NOTE]
> 짧은 기간 동안 서비스 중단이 발생할 경우에 대비하여 네트워크 사용량이 낮을 때 전화 접속 액세스 번호를 이동하는 것이 좋습니다.



**전화 접속 액세스 번호를 식별하고 이동하려면**

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  각 전화 접속 액세스 번호를 Lync Server 2013에 호스팅된 풀로 이동하려면 명령줄에서 다음을 실행합니다.
    
        Move-CsApplicationEndpoint -Identity <SIP URI of the access number to be moved> -Target <FQDN of the pool to which the access number is moving>

3.  Lync Server 제어판을 엽니다.

4.  왼쪽 탐색 모음에서 **회의**를 클릭합니다.

5.  **전화 접속 액세스 번호** 탭을 클릭합니다.

6.  마이그레이션하려는 Lync Server 2010 풀에 대해 유지되는 전화 접속 액세스 번호가 없는지 확인합니다.
    

    > [!NOTE]
    > 모든 전화 접속 액세스 번호가 Lync Server 2013 풀을 가리키면 Lync Server 2010 풀을 해지할 수 있습니다.



**Lync Server 제어판을 사용하여 전화 접속 액세스 번호 마이그레이션 확인**

1.  **CsUserAdministrator** 역할이나 **CsAdministrator** 역할에 할당된 사용자 계정에서 내부 배포의 컴퓨터에 로그온합니다.

2.  Lync Server 제어판을 엽니다.

3.  왼쪽 탐색 모음에서 **회의**를 클릭합니다.

4.  **전화 접속 액세스 번호** 탭을 클릭합니다.

5.  모든 전화 접속 액세스 번호가 Lync Server 2013에 호스팅된 풀로 마이그레이션되었는지 확인합니다.

**Communications Server 관리 셸을 사용하여 전화 접속 액세스 번호 마이그레이션 확인**

1.  Lync Server 관리 셸을 엽니다.

2.  마이그레이션된 모든 전화 접속 회의 액세스 번호를 반환하려면 명령줄에서 다음을 실행합니다.
    
        Get-CsDialInConferencingAccessNumber -Filter {Pool -eq "<FQDN of the pool to which the access number is moved>"}

3.  모든 전화 접속 액세스 번호가 Lync Server 2013에 호스팅된 풀로 마이그레이션되었는지 확인합니다.

