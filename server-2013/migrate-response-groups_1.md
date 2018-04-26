---
title: 응답 그룹 마이그레이션
TOCTitle: 응답 그룹 마이그레이션
ms:assetid: 5c07bf4b-ad8a-4b83-b970-7d933bb7c4ef
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204931(v=OCS.15)
ms:contentKeyID: 49303753
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 응답 그룹 마이그레이션

 

_**마지막으로 수정된 항목:** 2012-10-19_

사용자를 Lync Server 2013 풀로 이동한 후 응답 그룹을 마이그레이션할 수 있습니다. 응답 그룹을 마이그레이션할 때는 에이전트 그룹, 큐, 워크플로 및 오디오 파일을 복사하고, 응답 그룹 연락처 개체를 레거시 배포에서 Lync Server 2013 풀로 이동하는 작업이 포함됩니다. 레거시 응답 그룹을 마이그레이션한 후에는 응답 그룹에 대한 호출이 Lync Server 2013 풀의 응답 그룹 응용 프로그램에서 처리됩니다. 응답 그룹에 대한 호출은 더 이상 레거시 풀에서 처리되지 않습니다.


> [!NOTE]
> 모든 사용자를 Lync Server 2013 풀로 이동하기 전에 응답 그룹을 마이그레이션할 수 있지만 모든 사용자를 먼저 이동하는 것이 좋습니다. 특히 응답 그룹 에이전트인 사용자는 Lync Server 2013 풀로 이동될 때까지 새로운 기능을 완전하게 사용할 수 없습니다.



응답 그룹을 마이그레이션하기 전에 응답 그룹 응용 프로그램이 포함된 Lync Server 2013 풀을 배포해야 합니다. 응답 그룹 응용 프로그램은 Enterprise Voice를 배포할 때 기본적으로 설치되고 활성화됩니다. **Get-CsService–ApplicationServer** cmdlet을 실행하여 응답 그룹 응용 프로그램이 설치되었는지 확인할 수 있습니다.


> [!NOTE]
> 레거시 응답 그룹을 마이그레이션하기 전에 Lync Server 2013 풀에서 새로운 Lync Server 2013 응답 그룹을 만들 수 있습니다.



레거시 풀에서 Lync Server 2013으로 응답 그룹을 마이그레이션하려면 **Move-CsRgsConfiguration** cmdlet을 실행합니다. **Move-CsRgsConfiguration**을 실행하려면 먼저 WMI(Windows Management Instrumentation) Backward Compatibility 인터페이스 패키지를 설치해야 합니다. 이 응용 프로그램은 OCSWMIBC.msi를 실행하여 설치합니다. OCSWMIBC.msi는 설치 미디어의 Setup 폴더에 있습니다.


> [!IMPORTANT]
> 응답 그룹 마이그레이션 cmdlet은 전체 풀에 대한 응답 그룹 구성을 이동합니다. 마이그레이션할 특정 그룹, 큐 또는 워크플로를 선택할 수 없습니다.



응답 그룹을 마이그레이션한 후에는 공식 에이전트가 자신의 응답 그룹에서 로그인 및 로그아웃할 때 사용할 수 있는 URL을 업데이트하고 Lync Server 제어판 또는 Lync Server 관리 셸 cmdlet을 사용해서 모든 에이전트 그룹, 큐 및 워크플로가 성공적으로 이동되었는지 확인해야 합니다.


> [!WARNING]
> 응답 그룹을 마이그레이션할 때 Office Communications Server 2007 R2 응답 그룹은 이동되지 않습니다. Office Communications Server 2007 R2 응답 그룹은 제거하지 마십시오. Office Communications Server 2007 R2 응답 그룹을 제거할 경우 Lync Server 2013이 응답 그룹이 작동하지 않습니다.




> [!IMPORTANT]
> 풀을 해제하기 전까지는 이전 배포에서 어떠한 데이터도 제거하지 않는 것이 좋습니다. 또한 마이그레이션 직후 응답 그룹을 내보내는 것이 좋습니다. Office Communications Server 2007 R2 응답 그룹이 제거될 경우 백업에서 응답 그룹을 복원하여 Lync Server 2013 응답 그룹이 다시 실행되도록 만들 수 있습니다.



**Move-CsRgsConfiguration** cmdlet을 실행하면 에이전트 그룹, 큐, 워크플로 및 오디오 파일이 롤백 목적으로 레거시 풀에 보존됩니다. 하지만 레거시 풀로 롤백해야 하는 경우에는 **Move-CsApplicationEndpoint** cmdlet을 실행해서 연락처 개체를 다시 레거시 풀로 이동해야 합니다.


> [!IMPORTANT]
> 풀을 해제하기 전까지는 레거시 풀에서 응답 그룹 데이터를 삭제하지 않는 것이 좋습니다.



응답 그룹 구성 마이그레이션 절차에서는 레거시 풀과 Lync Server 2013 풀 사이에 일 대 일 관계가 있는 것으로 가정합니다. 마이그레이션 및 배포 중에 풀을 통합하거나 분할할 계획인 경우 어느 레거시 풀을 어느 Lync Server 2013 풀에 매핑할지를 계획해야 합니다.

## 응답 그룹 구성을 마이그레이션하려면

1.  설치 미디어의 Setup 폴더에서 OCSWMIBC.msi를 찾고 설치합니다.

2.  RTCUniversalServerAdmins 그룹의 구성원이거나 이와 동등한 관리자 권한 및 사용 권한을 가진 계정을 사용하여 컴퓨터에 로그온합니다.

3.  Lync Server 관리 셸를 엽니다.

4.  명령줄에 다음을 입력합니다.
    
        Move-CsRgsConfiguration -Source <source pool FQDN> -Destination <destination pool FQDN>
    
    예를 들면 다음과 같습니다.
    
        Move-CsRgsConfiguration -Source pool01.contoso.net -Destination pool02.contoso.net

5.  Office Communications Server 2007 R2 환경에 Microsoft Office Communicator 2007 R2에 대한 응답 그룹 탭을 배포한 경우 Office Communicator 2007 R2 tabs.xml 파일에서 해당 탭을 제거합니다.
    

    > [!NOTE]
    > 공식 에이전트는 호출을 수신하기 전에 응답 그룹 탭을 사용하여 응답 그룹에 로그인했습니다. 응답 그룹 탭을 배포한 경우 배포 당시 Office Communicator 2007 R2 tabs.xml 파일의 위치를 선택했습니다.



6.  에이전트가 응답 그룹에서 로그인 및 로그아웃하는 데 필요한 업데이트된 URL을 사용자에게 제공합니다.
    

    > [!NOTE]
    > URL은 일반적으로 https://webpoolFQDN/RgsClients/Tab.aspx이며, 여기서 <EM>webpoolFQDN</EM> 은 바로 전에 Lync Server 2013으로 마이그레이션한 풀과 연결된 웹 풀의 FQDN(정규화된 도메인 이름)입니다.

    

    > [!NOTE]
    > 사용자가 Lync 2013으로 업그레이드한 후에는 Lync의 <STRONG>도구</STRONG> 메뉴에서 URL을 사용할 수 있으므로 이 단계가 필요하지 않습니다.



## Lync Server 제어판을 사용하여 응답 그룹 마이그레이션을 확인하려면

1.  Lync Server 제어판를 엽니다.

2.  왼쪽 탐색 창에서 **응답 그룹** 을 클릭합니다.

3.  **워크플로** 탭에서 Office Communications Server 2007 R2 환경의 모든 워크플로가 목록에 포함되었는지 확인합니다.

4.  **큐** 탭을 클릭하고 Office Communications Server 2007 R2 환경의 모든 큐가 목록에 포함되었는지 확인합니다.

5.  **그룹** 탭을 클릭하고 Office Communications Server 2007 R2 환경의 모든 에이전트 그룹이 목록에 포함되었는지 확인합니다.

## Cmdlet을 사용하여 응답 그룹 마이그레이션을 확인하려면

1.  Lync Server 관리 셸를 엽니다.
    
    다음 cmdlet에 대한 자세한 내용을 보려면 다음을 실행합니다.
    
        Get-Help <cmdlet name> -Detailed

2.  명령줄에 다음을 입력합니다.
    
        Get-CsRgsAgentGroup

3.  Office Communications Server 2007 R2 환경의 모든 에이전트 그룹이 목록에 포함되었는지 확인합니다.

4.  명령줄에 다음을 입력합니다.
    
        Get-CsRgsQueue

5.  Office Communications Server 2007 R2 환경의 모든 큐가 목록에 포함되었는지 확인합니다.

6.  명령줄에 다음을 입력합니다.
    
        Get-CsRgsWorkflow

7.  Office Communications Server 2007 R2 환경의 모든 워크플로가 목록에 포함되었는지 확인합니다.

