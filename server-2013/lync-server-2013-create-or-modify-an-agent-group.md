---
title: 'Lync Server 2013: 에이전트 그룹 만들기 또는 수정'
TOCTitle: 에이전트 그룹 만들기 또는 수정
ms:assetid: f1461fff-51c1-4f4b-9311-8cba02c333fc
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205370(v=OCS.15)
ms:contentKeyID: 49305488
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 에이전트 그룹 만들기 또는 수정

 

_**마지막으로 수정된 항목:** 2014-02-07_

다음 절차 중 하나를 사용하여 에이전트 그룹을 만들거나 수정합니다.


> [!NOTE]
> 관리자(예: CsVoiceAdministrator)는 에이전트 그룹에 사용자를 할당하기 전에 사용자가 Enterprise Voice 및 Lync Server를 사용할 수 있도록 설정해야 합니다. 관리된 워크플로에 대한 위임된 응답 그룹 관리자 중 한 명이라면 자신이 관리하는 워크플로에서 에이전트 그룹을 만들고 에이전트 그룹을 사용할 수 있습니다.




> [!IMPORTANT]
> 사용자를 응답 그룹 에이전트로 할당할 경우 해당 사용자는 개인 정보 보호 모드를 사용하도록 설정한 경우 "RGS 현재 상태 감시자" 연락처를 검색하여 자신의 연락처 목록에 추가해야 합니다. 개인 정보 보호 모드를 사용하도록 설정했지만 연락처 목록에 "RGS 현재 상태 감시자"가 없는 에이전트는 응답 그룹에 대한 통화를 받을 수 없습니다. 개인 정보 보호 모드를 사용하도록 설정하지 않은 에이전트는 영향을 받지 않습니다.



## Lync Server 제어판을 사용하여 에이전트 그룹을 만들고 수정하려면

1.  RTCUniversalServerAdmins 그룹의 구성원이나 응답 그룹을 지원하는 미리 정의된 관리 역할 중 하나의 구성원으로 로그온합니다.
    

    > [!NOTE]
    > 관리된 워크플로에 대한 위임된 응답 그룹 관리자 중 한 명이라면 자신이 관리하는 워크플로에서 에이전트 그룹을 만들고 사용할 수 있습니다.



2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 표시줄에서 **응답 그룹** 을 클릭한 다음 **그룹** 을 클릭합니다.

4.  **그룹** 페이지에서 다음 중 하나를 수행합니다.
    
      - 새 에이전트 그룹을 만들려면 **새로 만들기** 를 클릭합니다. **서비스 선택** 검색 필드에 그룹을 추가할 참가 설정을 정의할 **ApplicationServer** 서비스의 이름 일부나 전체를 입력합니다. 서비스 결과 목록에서 원하는 서비스를 클릭하고 **확인** 을 클릭합니다.
    
      - 기존 에이전트 그룹을 수정하려면 검색 필드에 에이전트 그룹 이름의 일부나 전체를 입력합니다. 검색 결과 목록에서 원하는 그룹을 클릭하고 **편집** 을 클릭한 다음 **자세한 정보 표시** 를 클릭합니다.

5.  **이름** 에 에이전트 그룹의 식별 이름을 입력합니다.

6.  **설명** 에 그룹에 대한 설명을 입력합니다.

7.  **참가 정책** 에서 다음 중 하나를 선택하여 그룹의 로그인 동작을 설정합니다.
    
      - 그룹의 에이전트가 그룹에 로그인 및 로그아웃할 필요가 없도록 지정하려면 **비공식** 을 선택합니다. 이 경우 에이전트가 Lync Server 2013에 로그인하면 그룹에 자동으로 로그인됩니다.
    
      - 그룹의 에이전트가 그룹에 로그인 및 로그아웃해야 하도록 지정하려면 **공식** 을 선택합니다. 이 옵션을 선택하면 에이전트가 Lync에서 메뉴 항목을 클릭하여 Internet Explorer를 열고 그룹에 로그인 및 로그아웃할 수 있는 웹 페이지 콘솔을 표시해야 합니다.

8.  **알림 시간(초)** 에 사용 가능한 다음 에이전트에 통화를 전달하기 전에 현재 에이전트에 신호음을 울릴 시간(초)을 지정합니다(기본값은 20초).
    

    > [!IMPORTANT]
    > 에이전트 알림 시간 설정은 180초를 초과할 수 없습니다. 에이전트 알림 시간이 180초를 초과하면 SIP 트랜잭션 타이머가 최대 대기 시간에 도달하므로 클라이언트 응용 프로그램에서 통화를 거부합니다.



9.  **라우팅 방법** 에서 그룹의 에이전트에 통화가 라우팅되는 방법을 다음과 같이 지정합니다.
    
      - 새 통화를 유휴 시간이 가장 길었던 에이전트( Lync Server에서 현재 상태가 **대화 가능** 또는 **대화 불가능** 으로 가장 오래 유지된 에이전트)에게 먼저 제공하려면 **최장 유휴 시간** 을 클릭합니다.
    
      - 대화 가능한 모든 에이전트에 동시에 새 통화를 제공하려면 **병렬** 을 클릭합니다. 통화를 수락하는 첫 번째 에이전트에 통화가 전송됩니다.
    
      - 각 에이전트에 차례로 새 통화를 제공하려면 **라운드 로빈** 을 클릭합니다.
    
      - 항상 **에이전트** 목록에 나열된 순서대로 에이전트에 새 통화를 제공하려면 **직렬** 을 클릭합니다.
    
      - 현재 상태에 관계 없이 Lync Server 2013과 응답 그룹 응용 프로그램에 동시에 로그인한 모든 에이전트에 새 통화를 제공하려면 **Attendant** 를 클릭합니다. 에이전트로 구성된 Lync 2010 Attendant 사용자는 대기 중인 모든 통화를 보고 순서에 상관없이 대기 중인 통화에 응답할 수 있습니다. 이 경우 통화를 수락한 첫 번째 에이전트에 통화가 전송되고 그 후에는 다른 Lync 2010 Attendant 사용자에게 통화가 더 이상 표시되지 않습니다.

10. **에이전트** 에서 에이전트 목록을 만들려는 방법을 지정합니다.
    
      - 사용자 지정 에이전트 목록을 사용하려면 **사용자 지정 에이전트 그룹 정의** 를 클릭하고 다음 중 하나를 수행합니다.
        
          - 에이전트 그룹에 사용자를 추가하려면 **선택** 을 클릭하고 **에이전트 선택** 검색 필드에 이 그룹에 추가할 사용자의 전체 이름 또는 일부 이름을 입력한 다음 **찾기** 를 클릭합니다. 결과 에이전트 목록에서 사용자를 클릭한 다음 **확인** 을 클릭합니다.
        
          - 에이전트 그룹에서 사용자를 제거하려면 에이전트 목록에서 제거할 사용자를 클릭한 다음 **제거** 를 클릭합니다.
        
          - 라운드 로빈 라우팅 또는 직렬 라우팅을 사용하는 그룹에서 통화가 제공되는 에이전트의 순서를 변경하려면 에이전트 목록에서 사용자를 클릭한 다음 위쪽 또는 아래쪽 화살표를 클릭합니다.
    
      - Microsoft Exchange Server 메일 그룹을 에이전트 그룹으로 사용하려면 **기존 전자 메일 그룹 사용** 을 클릭하고 **메일 그룹 주소** 에 메일 그룹의 전자 메일 주소를 입력합니다(예: NetworkSupport@contoso.com).
        
        전자 메일 그룹을 사용하는 경우 다음과 같은 제약 조건이 적용됩니다.
        
          - 에이전트 그룹에 대해 메일 그룹을 여러 개 선택할 수는 없습니다. 각 그룹이 하나의 메일 그룹만 지원합니다.
        
          - 메일 그룹에 하나 이상의 메일 그룹이 포함되어 있는 경우 중첩된 메일 그룹의 구성원은 에이전트 목록에 추가되지 않습니다.
        
          - 직렬 또는 라운드 로빈 라우팅을 선택하면 서버에서 라우팅 방법 및 에이전트가 메일 그룹에 나열된 순서에 따라 수신 전화를 적절한 에이전트에 제공합니다.
        
          - 메일 그룹에 Lync Server 2010을 사용할 수 있지만 Enterprise Voice를 사용할 수 없는 사용자가 포함되어 있으면 에이전트 그룹에 작동하지 않는 에이전트로 추가됩니다. 메일 그룹의 모든 구성원이 사용자 계정에 대해 Enterprise Voice를 사용할 수 있는지 확인하세요.
        

        > [!IMPORTANT]
        > 전자 메일 그룹을 사용하는 경우 숨겨진 구성원 또는 숨겨진 목록이 응답 그룹 관리자 또는 사용자에게 표시될 수 있습니다.

        
        숨겨진 구성원 또는 숨겨진 목록은 다음과 같이 표시될 수 있습니다.
        
          - 응답 그룹 관리자가 에이전트 목록에 메일 그룹을 할당할 수 있도록 메일 그룹이 구성된 경우 사용자는 그룹에 전화를 걸어 구성원을 찾을 수 있습니다.
        
          - Exchange 전체 주소 목록에서 숨겨지도록 메일 그룹이 구성된 경우 응답 그룹 관리자가 해당 메일 그룹을 볼 수 있으며 응답 그룹 프로세스에 적절한 사용자 권한이 있는 경우 에이전트 목록에 해당 메일 그룹을 할당할 수 있습니다. 이는 관리자에게 적절한 사용자 권한이 없는 경우에도 마찬가지입니다.

11. **커밋** 을 클릭합니다.

## Windows PowerShell을 사용하여 에이전트 그룹을 만들고 수정하려면

1.  RTCUniversalServerAdmins 그룹의 구성원이나 응답 그룹을 지원하는 미리 정의된 관리 역할 중 하나의 구성원으로 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  새 에이전트 그룹을 만들려면 **New-CsRgsAgentGroup**을 사용하고 기존 에이전트 그룹을 수정하려면 **Set-CsRgsAgentGroup**을 사용합니다. 명령줄에서 다음을 실행합니다.
    
        New-CsRgsAgentGroup -Name "<agent group name>" -Parent $serviceId [-Description "<agent group description>"] -[AgentAlertTime <# seconds until call is routed to next agent>] [-ParticipationPolicy <Formal | Informal>] [-RoutingMethod <method for routing calls>] [-AgentsByUri("<first agent's SIP address>","<second agent's SIP address>")];
    
    예를 들면 다음과 같습니다.
    
        New-CsRgsAgentGroup -Name "Help Desk" -Parent "service:ApplicationServer:atl-cs-001.contoso.com"  -Description "Contoso Help Desk" -AgentAlertTime 20 -ParticipationPolicy Formal -RoutingMethod RoundRobin -AgentsByUri("sip:mindy@contoso.com","sip:bob@contoso.com")
    

    > [!IMPORTANT]
    > 에이전트 알림 시간 설정은 180초를 초과할 수 없습니다. 에이전트 알림 시간이 180초 이상이면 SIP 트랜잭션 타이머가 최대 대기 시간에 도달하므로 클라이언트 응용 프로그램에서 통화를 거부합니다.



4.  에이전트 그룹이 실행되었는지 확인합니다. 다음을 실행합니다.
    
        Get-CsRgsAgentGroup -Name "Help Desk"

## 참고 항목

#### 작업

[Lync Server 2013에서 에이전트 그룹 삭제](lync-server-2013-delete-an-agent-group.md)  

#### 기타 리소스

[Lync Server 2013에서 응답 그룹 에이전트 그룹 관리](lync-server-2013-managing-response-group-agent-groups.md)  
[Get-CsService](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsService)  
[New-CsRgsAgentGroup](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsRgsAgentGroup)  
[Set-CsRgsAgentGroup](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsRgsAgentGroup)  
[Get-CsRgsAgentGroup](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsRgsAgentGroup)

