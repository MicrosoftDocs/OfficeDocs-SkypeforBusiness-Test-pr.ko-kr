---
title: Lync Server 2013 관리 팩 가져오기
TOCTitle: Lync Server 2013 관리 팩 가져오기
ms:assetid: 846287e1-660f-453f-bdba-b2137b5f0ea1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205052(v=OCS.15)
ms:contentKeyID: 49304245
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 관리 팩 가져오기

 

_**마지막으로 수정된 항목:** 2012-10-22_

System Center Operations Manager가 모니터링할 수 있는 항목, 이러한 항목의 모니터링 방법 및 알림을 트리거하고 보고하는 방법을 기술하는 소프트웨어인 관리 팩을 설치하면 System Center Operations Manager의 기능을 확장할 수 있습니다. Lync Server 2013에는 다음 기능을 제공하는 두 가지 System Center Operations Manager 관리 팩이 포함됩니다.

  - 구성 요소 및 사용자 관리 팩(Microsoft.LS.2013.Monitoring.ComponentAndUser.mp)은 이벤트 로그에 기록되었거나, 성능 카운터로 등록되었거나, CDR(통화 정보 기록) 또는 QoE(체감 품질) 데이터베이스에 기록된 Lync Server 문제를 추적합니다. 중요한 문제의 경우 전자 메일, 인스턴트 메시지 또는 SMS(Short Message Service) 메시징을 통해 관리자에게 즉시 알리도록 System Center Operations Manager를 구성할 수 있습니다. SMS는 모바일 장치 간에 문자 메시지를 전송하기 위해 사용되는 기술입니다.
    

    > [!NOTE]
    > Operations Manager 알림 구성에 대한 자세한 내용은 TechNet 라이브러리에서 알림 구성(<A class=uri href="http://go.microsoft.com/fwlink/?linkid=268785%26clcid=0x412">http://go.microsoft.com/fwlink/?linkid=268785&amp;clcid=0x412</A>)을 참조하십시오.



  - 모니터링 활성화 관리 팩(Microsoft.LS.2013.Monitoring.ActiveMonitoring.mp)은 시스템에 로그인, 인스턴트 메시지 교환 또는 PSTN(공중 전화망)에 있는 전화에 연결하기 등 핵심 Lync Server 구성 요소를 사전적으로 테스트합니다. 이러한 테스트는 Lync Server 가상 트랜잭션 cmdlet을 사용해서 수행됩니다. 예를 들어 **Test-CsIM** cmdlet을 사용해서 테스트 사용자의 쌍 간에 IM(인스턴트 메시징) 대화를 시뮬레이션할 수 있습니다. 시뮬레이션된 메시징 대화가 실패하면 알림이 생성됩니다.

관리 팩을 가져와야 합니다. 관리 팩을 가져오지 않으면 Operations Manager를 사용해서 Lync Server 이벤트를 모니터링하거나 Lync Server 가상 트랜잭션을 실행할 수 없습니다.

구성 요소 및 사용자 관리 팩은 Lync Server 2013을 모니터링하는 데에만 사용됩니다. Lync Server 2013과 Lync Server 2010이 모두 설치된 동시 사용 시나리오의 경우 Lync Server 2010 컴퓨터를 위해 Lync Server 2010 관리 팩을 계속 사용해야 합니다.


> [!NOTE]
> Lync Server 2010용 관리 팩에는 Lync Server 2010 모니터링 관리 팩과 Lync Server 2010 그룹 채팅 모니터링 관리 팩이 포함됩니다.



다음 도구 중 하나를 사용해서 관리 팩을 가져올 수 있습니다.

  - **System Center Operations Manager**   이 방법을 사용하면 Operations Manager를 사용해서 Lync Server에 대한 모니터링을 추가합니다.

  - **Operations Manager 셸**   Operations Manager 셸을 사용하면 관리 팩을 직접 가져오거나 System Center Operations Manager 콘솔을 사용해서 관리 팩을 직접 가져올 때 발생하는 문제를 해결할 수 있습니다.

## System Center Operations Manager를 사용해서 관리 팩 가져오기

1.  Microsoft.LS.2013.Monitoring.ActiveMonitoring.mp 및 Microsoft.LS.2013.Monitoring.ComponentAndUser.mp 파일을 다운로드합니다.

2.  System Center Operations Manager에서 **관리**를 클릭합니다.

3.  **관리** 창에서 **관리 팩**을 마우스 오른쪽 단추로 클릭한 후 **관리 팩 가져오기**를 클릭합니다.

4.  **관리 팩 선택** 대화 상자에서 **추가**를 클릭한 후 **디스크에서 추가**를 클릭합니다.

5.  Operations Manager가 Lync Server 관리 팩에 대한 종속성이 있는지 확인하기 위해 온라인으로 전환할 수 없도록 방지하려면 **온라인 카탈로그 연결** 대화 상자에서 **취소**를 클릭합니다. System Center Operations Manager 2012를 사용하는 경우 **아니요**를 클릭합니다.

6.  **가져올 관리 팩 선택** 대화 상자에서 **Microsoft.LS.2013.Monitoring.ActiveMonitoring.mp** 및 **Microsoft.LS.2013.Monitoring.ComponentAndUser.mp** 파일을 찾아서 선택한 후 **열기**를 클릭합니다. 대화 상자에서 여러 파일을 선택하려면 첫 번째 파일을 클릭하고, Ctrl 키를 누른 상태에서 두 번째 파일을 클릭합니다.

7.  **관리 팩 선택** 대화 상자에서 **설치**를 클릭합니다. 오류 메시지가 표시되고 설치가 실패하면 일반적으로 관리 팩 파일이 Windows 사용자 계정 컨트롤에서 보호되는 폴더에 있기 때문일 수 있습니다. 이 경우 파일을 다른 폴더에 복사한 후 가져오기 및 설치 프로세스를 다시 시작합니다.

8.  **관리 팩 선택** 대화 상자에서 **닫기**를 클릭합니다. 가져오기 및 설치 프로세스는 완료하는 데 몇 분 정도 걸릴 수 있습니다.

## Operations Manager 셸을 사용하여 관리 팩 가져오기

일반적으로는 Operations Manager를 사용해서 관리 팩을 가져오는 것이 더 쉽습니다. 하지만 오류가 발생하고 가져오기가 실패하면 콘솔이 적절한 오류 보고서를 제공하지 않을 수 있습니다. 비교적 Operations Manager 셸이 보다 자세한 정보를 제공합니다. Operations Manager를 사용 중이고 관리 팩을 가져오는 데 문제가 발생하면 Operations Manager 셸을 사용하여 팩을 가져와보십시오. Operations Manager 셸은 가져오기가 실패한 이유를 확인하는 데 도움이 될 수 있는 보다 자세한 정보를 제공합니다.

System Center Operations Manager 2007 R2를 사용하는 경우에는 다음 절차를 완료합니다.

1.  **시작**, **모든 프로그램**, **System Center Operations Manager 2007 R2**를 차례로 클릭한 후 **Operations Manager 셸**을 클릭합니다.

2.  Operations Manager 셸에서 Microsoft.LS.2013.Monitoring.ActiveMonitoring.mp 파일의 복사본에 대한 실제 경로를 사용해서 명령 프롬프트에 다음 명령을 입력한 후 Enter 키를 누릅니다.
    
        MPImport.exe D:\MP\Microsoft.LS.2013.Monitoring.ActiveMonitoring.mp

3.  첫 번째 관리 팩을 가져온 후 Microsoft.LS.2013.Monitoring.ComponentAndUser.mp 파일의 복사본에 대한 경로를 사용해서 프로세스를 반복합니다.
    
        MPImport.exe D:\MP\Microsoft.LS.2013.Monitoring.ComponentAndUser.mp

4.  Operations Manager 셸을 닫습니다.

System Center Operations Manager 2012를 사용하는 경우에는 아래 절차를 대신 수행합니다.

1.  **시작**, **모든 프로그램**, **Microsoft System Center 2012**, **Operations Manager**를 차례로 클릭한 후 **Operations Manager 셸**을 클릭합니다.

2.  Operations Manager 셸에서 Microsoft.LS.2013.Monitoring.ActiveMonitoring.mp 파일의 복사본에 대한 실제 경로를 사용해서 명령 프롬프트에 다음 명령을 입력한 후 Enter 키를 누릅니다.
    
        Import-SCOMManagementPack -FullName "D:\MP\ Microsoft.LS.2013.Monitoring.ActiveMonitoring.mp"

3.  첫 번째 관리 팩을 가져온 후 Microsoft.LS.2013.Monitoring.ComponentAndUser.mp 파일의 복사본에 대한 경로를 사용해서 프로세스를 반복합니다.
    
        Import-SCOMManagementPack -FullName "D:\MP\ Microsoft.LS.2013.Monitoring.ComponentAndUser.mp"

