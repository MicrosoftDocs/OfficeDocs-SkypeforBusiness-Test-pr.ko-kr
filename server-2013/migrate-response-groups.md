---
title: 응답 그룹 마이그레이션
TOCTitle: 응답 그룹 마이그레이션
ms:assetid: 43741ae7-c871-4573-b660-f2f5febc0856
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204854(v=OCS.15)
ms:contentKeyID: 49303466
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 응답 그룹 마이그레이션

 

_**마지막으로 수정된 항목:** 2013-09-23_

사용자를 Lync Server 2013 풀로 이동한 후 응답 그룹을 마이그레이션할 수 있습니다. 응답 그룹을 마이그레이션할 때는 에이전트 그룹, 큐, 워크플로, 오디오 파일을 복사하고, 응답 그룹 연락처 개체를 레거시 배포에서 Lync Server 2013 풀로 이동하는 작업이 포함됩니다. 레거시 응답 그룹을 마이그레이션한 후에는 응답 그룹에 대한 호출이 Lync Server 2013 풀의 응답 그룹 응용 프로그램에서 처리됩니다. 응답 그룹에 대한 호출은 더 이상 레거시 풀에서 처리되지 않습니다.


> [!NOTE]
> 모든 사용자를 Lync Server 2013 풀로 이동하기 전에 응답 그룹을 마이그레이션할 수 있지만 모든 사용자를 먼저 이동하는 것이 좋습니다. 특히 응답 그룹 에이전트인 사용자는 Lync Server 2013 풀로 이동될 때까지 새로운 기능을 완전하게 사용할 수 없습니다.



응답 그룹을 마이그레이션하기 전에 응답 그룹 응용 프로그램이 포함된 Lync Server 2013 풀을 배포해야 합니다. 응답 그룹 응용 프로그램은 Enterprise Voice를 배포할 때 기본적으로 설치되고 활성화됩니다. **Get-CsService –ApplicationServer** cmdlet을 실행하여 응답 그룹 응용 프로그램이 설치되었는지 확인할 수 있습니다.


> [!NOTE]
> 레거시 응답 그룹을 마이그레이션하기 전에 Lync Server 2013 풀에서 새로운 Lync Server 2013 응답 그룹을 만들 수 있습니다.



레거시 풀에서 Lync Server 2013으로 응답 그룹을 마이그레이션하려면 **Move-CsRgsConfiguration** cmdlet을 실행합니다.


> [!IMPORTANT]
> 응답 그룹 마이그레이션 cmdlet은 전체 풀에 대한 응답 그룹 구성을 이동합니다. 마이그레이션할 특정 그룹, 큐 또는 워크플로를 선택할 수 없습니다.



응답 그룹을 마이그레이션한 후에는 Lync Server 제어판 또는 Lync Server 관리 셸 cmdlet을 사용해서 모든 에이전트 그룹, 큐 및 워크플로가 성공적으로 이동되었는지 확인해야 합니다.

응답 그룹을 마이그레이션할 때 Lync Server 2010 응답 그룹은 제거되지 않습니다. 마이그레이션 후 Lync Server 제어판 또는 Lync Server 관리 셸을 사용하여 응답 그룹을 관리할 때는 Lync Server 2010 응답 그룹과 Lync Server 2013 응답 그룹을 모두 볼 수 있습니다. 업데이트는 Lync Server 2013 응답 그룹에만 적용해야 합니다. Lync Server 2010 응답 그룹은 롤백 목적으로만 보존됩니다.


> [!WARNING]
> 마이그레이션이 완료되고 새 응답 그룹이 만들어진 후에는 Lync Server 제어판 및 Lync Server 관리 셸에 Lync Server 2010 및 Lync Server 2013 버전의 각 응답 그룹이 표시됩니다. Lync Server 제어판 또는 Lync Server 관리 셸을 사용하여 Lync Server 2010 응답 그룹을 제거하지 않도록 합니다. 응답 그룹을 제거하면 마이그레이션하는 동안 만들어진 해당 응답 그룹이 작동하지 않습니다. Lync Server 2010 풀을 해제하면 Lync Server 2010 응답 그룹이 제거됩니다.




> [!IMPORTANT]
> 풀을 해제하기 전까지는 이전 배포에서 어떠한 데이터도 제거하지 않는 것이 좋습니다. 또한 마이그레이션 직후 응답 그룹을 내보내는 것이 좋습니다. Lync Server 2010 응답 그룹이 제거될 경우 백업에서 응답 그룹을 복원하여 Lync Server 2013 응답 그룹이 다시 실행되도록 만들 수 있습니다.



Lync Server 2013에는 **워크플로 유형** 이라고 부르는 새로운 응답 그룹 기능이 도입되었습니다. **워크플로 유형** 은 **관리됨** 또는 **관리되지 않음** 일 수 있습니다. 모든 응답 그룹은 **워크플로 유형** 이 **관리되지 않음** 상태로 마이그레이션되고 관리자 목록은 비어 있습니다.

**Move-CsRgsConfiguration** cmdlet을 실행하면 에이전트 그룹, 큐, 워크플로 및 오디오 파일이 롤백 목적으로 레거시 풀에 보존됩니다. 하지만 레거시 풀로 롤백해야 하는 경우에는 **Move-CsApplicationEndpoint** cmdlet을 실행해서 연락처 개체를 다시 레거시 풀로 이동해야 합니다.

다음 응답 그룹 구성 마이그레이션 절차에서는 레거시 풀과 Lync Server 2013 풀 사이에 일 대 일 관계가 있는 것으로 가정합니다. 마이그레이션 및 배포 중에 풀을 통합하거나 분할할 계획인 경우 어느 레거시 풀을 어느 Lync Server 2013 풀에 매핑할지를 계획해야 합니다.

## 응답 그룹 구성을 마이그레이션하려면

1.  RTCUniversalServerAdmins 그룹의 구성원이거나 이와 동등한 관리자 권한 및 사용 권한을 가진 계정을 사용하여 컴퓨터에 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  다음을 실행합니다.
    
        Move-CsRgsConfiguration -Source <source pool FQDN> -Destination <destination pool FQDN>
    
    예를 들면 다음과 같습니다.
    
        Move-CsRgsConfiguration -Source lync-old.contoso.net -Destination lync-new.contoso.net

4.  응답 그룹 및 에이전트를 Lync Server 2013 풀로 마이그레이션한 후 에이전트가 로그인 및 로그아웃을 위해 사용하는 URL은 Lync Server 2013 URL이며 **도구** 메뉴에서 사용할 수 있습니다. 에이전트가 책갈피와 같은 모든 참조를 새 URL로 업데이트하도록 알립니다.

## Lync Server 제어판을 사용하여 응답 그룹 마이그레이션을 확인하려면

1.  RTCUniversalReadOnlyAdmins 그룹의 구성원이거나 최소한 CsViewOnlyAdministrator 역할의 구성원인 계정을 사용하여 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 창에서 **응답 그룹** 을 클릭합니다.

4.  **워크플로** 탭에서 Lync Server 2010 환경의 모든 워크플로가 목록에 포함되었는지 확인합니다.

5.  **큐** 탭을 클릭하고 Lync Server 2010 환경의 모든 큐가 목록에 포함되었는지 확인합니다.

6.  **그룹** 탭을 클릭하고 Lync Server 2010 환경의 모든 에이전트 그룹이 목록에 포함되었는지 확인합니다.

## Lync Server 관리 셸을 사용하여 응답 그룹 마이그레이션을 확인하려면

1.  RTCUniversalReadOnlyAdmins 그룹의 구성원이거나 최소한 CsViewOnlyAdministrator 역할의 구성원인 계정을 사용하여 컴퓨터에 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.
    
    다음 cmdlet에 대한 자세한 내용을 보려면 다음을 실행합니다.
    
        Get-Help <cmdlet name> -Detailed

3.  다음을 실행합니다.
    
        Get-CsRgsAgentGroup

4.  Lync Server 2010 환경의 모든 에이전트 그룹이 목록에 포함되었는지 확인합니다.

5.  다음을 실행합니다.
    
        Get-CsRgsQueue

6.  Lync Server 2010 환경의 모든 큐가 목록에 포함되었는지 확인합니다.

7.  다음을 실행합니다.
    
        Get-CsRgsWorkflow

8.  Lync Server 2010 환경의 모든 워크플로가 목록에 포함되었는지 확인합니다.

