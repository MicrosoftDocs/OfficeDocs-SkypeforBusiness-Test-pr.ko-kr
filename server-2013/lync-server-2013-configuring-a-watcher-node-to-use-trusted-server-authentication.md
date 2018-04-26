---
title: 트러스트된 서버 인증을 사용하도록 감시자 노드 구성
TOCTitle: 트러스트된 서버 인증을 사용하도록 감시자 노드 구성
ms:assetid: 42d879ac-aa90-4ed6-b5e2-1e208711672a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204852(v=OCS.15)
ms:contentKeyID: 49303461
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 트러스트된 서버 인증을 사용하도록 감시자 노드 구성

 

_**마지막으로 수정된 항목:** 2012-10-22_

감시자 노드 컴퓨터가 경계 네트워크 내에 있을 경우 신뢰할 수 있는 서버 인증을 사용하면 여러 사용자 계정 암호 대신 단일 인증서를 유지 관리하여 관리 부담을 크게 줄일 수 있습니다.

신뢰할 수 있는 서버 인증 구성의 첫 번째 단계는 감시자 노드 컴퓨터를 호스팅하기 위한 신뢰할 수 있는 응용 프로그램 풀을 만드는 것입니다. 신뢰할 수 있는 응용 프로그램 풀을 만든 후에는 해당 감시자 노드의 가상 트랜잭션이 신뢰할 수 있는 응용 프로그램으로 실행되도록 구성해야 합니다.


> [!NOTE]
> 신뢰할 수 있는 응용 프로그램은 A trusted application is an application that is given trusted status to run as part of Lync Server 2013의 일부로 실행되도록 신뢰 상태가 제공되었지만 제품의 기본 제공 부분이 아닌 응용 프로그램입니다. 신뢰 상태란 응용 프로그램이 실행될 때마다 응용 프로그램에 인증을 요청하지 않는 상태를 의미합니다.



신뢰할 수 있는 응용 프로그램 풀을 만들려면 Lync Server 2013 관리 셸을 열고 다음과 비슷한 명령을 실행합니다.

    New-CsTrustedApplicationPool -Identity atl-watcher-001.litwareinc.com -Registrar atl-cs-001.litwareinc.com -ThrottleAsServer $True -TreatAsAuthenticated $True -OutboundOnly $False -RequiresReplication $True -ComputerFqdn atl-watcher-001.litwareinc.com -Site Redmond


> [!NOTE]
> 위 명령에 사용된 매개 변수에 대한 자세한 내용을 보려면 Lync Server 관리 셸 프롬프트에 다음을 입력합니다.<BR>Get-Help New-CsTrustedApplicationPool -Full | more



신뢰할 수 있는 응용 프로그램 풀을 만든 후에는 가상 트랜잭션을 신뢰할 수 있는 응용 프로그램으로 실행하도록 감시자 노드 컴퓨터를 구성합니다. 이 작업은 **New-CsTrustedApplication** cmdlet 및 다음과 비슷한 명령을 사용하여 수행됩니다.

    New-CsTrustedApplication -ApplicationId STWatcherNode -TrustedApplicationPoolFqdn atl-watcher-001.litwareinc.com -Port 5061

앞의 명령이 완료되고 신뢰할 수 있는 응용 프로그램이 만들어지면 Enable-CsTopology를 실행하여 변경 내용이 적용되었는지 확인합니다.

    Enable-CsTopology

Enable-CsTopology를 실행한 후에는 컴퓨터를 다시 시작하는 것이 좋습니다.

신뢰할 수 있는 새 응용 프로그램이 만들어졌는지 확인하려면 Lync Server 관리 셸 프롬프트에 다음을 입력합니다.

    Get-CsTrustedApplication -Identity "atl-watcher-001.litwareinc.com/urn:application:STWatcherNode"

## 감시자 노드에서 기본 인증서 구성

각 감시자 노드에는 Lync Server 배포 마법사를 사용하여 지정된 기본 인증서가 있어야 합니다.

**기본 인증서를 지정하려면**

1.  **시작**, **모든 프로그램**, **Lync Server**를 차례로 클릭한 후 **Lync Server 배포 마법사**를 클릭합니다.

2.  Lync Server 배포 마법사에서 **Lync Server 시스템 설치 또는 업데이트**를 클릭한 후 **인증서 요청, 설치 또는 지정** 제목 아래에서 **실행**을 클릭합니다.
    

    > [!NOTE]
    > <STRONG>실행</STRONG> 단추가 해제된 경우 <STRONG>로컬 구성 저장소 설치</STRONG> 아래에서 먼저 <STRONG>실행</STRONG>을 클릭해야 할 수 있습니다.



3.  다음 중 하나를 수행합니다.
    
      - 기본 인증서로 사용할 수 있는 인증서가 이미 있으면 인증서 마법사에서 **기본값**을 클릭하고 **지정**을 클릭합니다. 인증서 지정 마법사의 단계에 따라 해당 인증서를 지정합니다.
    
      - 기본 인증서를 사용하도록 인증서를 요청해야 할 경우 **요청**을 클릭한 후 인증서 요청 마법사의 단계에 따라 해당 인증서를 요청합니다. 웹 서버 인증서에 대한 기본값을 사용하면 기본 인증서로 지정할 수 있는 인증서가 표시됩니다.

## 감시자 노드 설치 및 구성

감시자 노드 컴퓨터를 다시 시작하고 인증서를 구성한 후에는 Watchernode.msi 파일을 실행해야 합니다. Operations Manager 에이전트 파일 및 Lync Server 2013 핵심 구성 요소가 모두 설치된 컴퓨터에서 Watchernode.msi를 실행해야 합니다.

**감시자 노드를 설치 및 구성하려면**

1.  **시작**, **모든 프로그램**, **Lync Server**를 차례로 클릭한 후 **Lync Server 관리 셸**을 클릭하여 Lync Server 관리 셸을 엽니다.

2.  Lync Server 관리 셸에서 다음 명령을 입력한 후 Enter 키를 누릅니다(Watchernode.msi 복사본이 있는 실제 경로 지정).
    
        C:\Tools\Watchernode.msi Authentication=TrustedServer
    

    > [!NOTE]
    > 또한 명령 창에서 Watchernode.msi를 실행할 수도 있습니다. 명령 창을 열려면 <STRONG>시작</STRONG>을 클릭하고 <STRONG>명령 프롬프트</STRONG>를 마우스 오른쪽 단추로 클릭한 후 <STRONG>관리자로 실행</STRONG>을 클릭합니다. 명령 창이 열리면 앞의 명령과 동일하게 입력합니다.



앞의 명령 Authentication=TrustedServer에서 이름/값 쌍은 대/소문자를 구분합니다. 표시된 것과 정확히 동일하게 입력해야 합니다. 다음 명령은 대/소문자가 올바르지 않기 때문에 실패합니다.

C:\\Tools\\Watchernode.msi authentication=trustedserver

경계 네트워크 내에 있는 컴퓨터에서만 TrustedServer 모드를 사용할 수 있습니다. 감시자 노드가 TrustedServer 모드로 실행될 때는 관리자가 컴퓨터에 테스트 사용자 암호를 유지 관리할 필요가 없습니다.

