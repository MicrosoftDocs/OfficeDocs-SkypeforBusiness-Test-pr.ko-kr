---
title: 'Lync Server 2013: 큐 만들기 또는 수정'
TOCTitle: 큐 만들기 또는 수정
ms:assetid: b9d6366a-839f-4651-a01d-9254546cadeb
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205207(v=OCS.15)
ms:contentKeyID: 49304842
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 큐 만들기 또는 수정

 

_**마지막으로 수정된 항목:** 2013-02-23_

다음 절차를 사용하여 큐를 만들거나 수정할 수 있습니다.

## Lync Server 제어판을 사용하여 큐를 만들거나 수정하려면

1.  RTCUniversalServerAdmins 그룹의 구성원이나 응답 그룹을 지원하는 미리 정의된 관리 역할 중 하나의 구성원으로 로그온합니다.
    

    > [!NOTE]
    > 관리 워크플로의 위임된 응답 그룹 관리자 중 하나인 경우 응답 그룹 큐를 만들거나 수정하고 여러분이 관리하는 워크플로에 할당할 수 있습니다.



2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **응답 그룹** 을 클릭하고 **큐** 를 클릭합니다.

4.  **큐** 페이지에서 다음 중 하나를 수행합니다.
    
      - 새 큐를 만들려면 **새로 만들기** 를 클릭합니다. **서비스 선택** 에서 검색 필드에 큐를 추가할 **ApplicationServer** 서비스의 이름 일부나 전체를 입력합니다. 서비스 결과 목록에서 원하는 서비스를 클릭하고 **확인** 을 클릭합니다.
    
      - 기존 큐를 수정하려면 검색 필드에 큐의 이름을 모두 또는 일부분 입력합니다. 결과 큐 목록에서 원하는 큐를 클릭하고 **편집** 을 클릭한 다음 **자세한 정보 표시** 를 클릭합니다.

5.  **이름** 에 큐를 식별하는 이름을 입력합니다.

6.  **설명** 에 큐의 설명을 입력합니다.

7.  **그룹** 에서 큐를 할당할 그룹을 지정합니다. 다음 중 하나를 수행합니다.
    
      - 큐에 그룹을 추가하려면 **선택** 을 클릭하고 **그룹 선택** 검색 필드에 큐에 할당할 에이전트 그룹의 이름을 일부분 또는 모두 입력한 다음 **찾기** 를 클릭합니다.
    
      - 큐에서 그룹을 제거하려면 에이전트 그룹 목록에서 제거할 그룹을 클릭한 다음 **제거** 를 클릭합니다.
    
      - 에이전트가 검색되는 순서를 변경하려면 에이전트 그룹 목록에서 그룹을 클릭한 다음 위쪽 화살표 또는 아래쪽 화살표를 클릭합니다.
        

        > [!NOTE]
        > 서버는 큐에서 사용 가능한 에이전트를 검색할 때 그룹 순서를 사용합니다. 즉, 목록의 첫 번째 그룹이 먼저 검색되고 목록의 두 번째 그룹 등이 차례로 검색됩니다.



8.  에이전트가 전화를 받을 때까지 발신자가 대기하도록 할 최대 시간을 지정하려면 **큐 시간 초과 사용** 확인란을 선택하고 다음을 수행합니다.
    
    1.  **제한 시간(초)** 에서 에이전트가 전화를 받을 때까지 발신자가 대기하는 최대 시간(초)을 지정합니다.
    
    2.  **통화 작업** 에서 통화 시간이 초과되면 수행할 작업을 다음 중에서 선택합니다.
    
    <!-- end list -->
    
      - 제한 시간 이후에 전화를 끊으려면 **연결 끊기** 를 클릭합니다.
    
      - 통화를 음성 메일로 착신 전환하려면 **음성 메일로 착신 전환** 을 클릭한 다음 **SIP 주소** 필드에 음성 메일 주소를 sip: *\<사용자 이름\>* @ *\<도메인 이름\>* 형식으로 입력합니다(예: sip:bob@contoso.com).
    
      - 통화를 다른 전화 번호로 착신 전환하려면 **착신 전환 전화 번호** 를 클릭한 다음 **SIP 주소** 필드에 전화 번호를 sip: *\<번호\>* @ *\<도메인 이름\>* 형식으로 입력합니다(예: sip:+14255550121@contoso.com).
    
      - 통화를 다른 사용자에게 착신 전환하려면 **SIP 주소로 전달** 을 클릭한 다음 **SIP 주소** 필드에 해당 사용자의 URI를 sip: *\<사용자 이름\>* @ *\<도메인 이름\>* 형식으로 입력합니다.
    
      - 통화를 다른 큐로 착신 전환하려면 **다른 큐로 착신 전환** 을 클릭한 다음 사용할 큐를 찾습니다.

9.  큐에 보관할 최대 통화 수를 지정하려면 **큐 오버플로 사용** 확인란을 선택하고 다음을 수행합니다.
    
    1.  **최대 통화 수** 에서 큐에 보관할 최대 통화 수를 선택합니다.
    
    2.  **착신 전환** 에서 큐가 가득 차면 착신 전환할 통화를 **가장 최근 통화** 또는 **가장 오래된 통화** 중에서 선택합니다.
    
    3.  **통화 작업** 에서 오버플로 임계값에 도달하면 수행할 작업을 다음 중에서 선택합니다.
    
    <!-- end list -->
    
      - 제한 시간 이후에 전화를 끊으려면 **연결 끊기** 를 클릭합니다.
    
      - 통화를 음성 메일로 착신 전환하려면 **음성 메일로 착신 전환** 을 클릭한 다음 **SIP 주소** 필드에 음성 메일 주소를 sip: *\<사용자 이름\>* @ *\<도메인 이름\>* 형식으로 입력합니다(예: sip:bob@contoso.com).
    
      - 통화를 다른 전화 번호로 착신 전환하려면 **착신 전환 전화 번호** 를 클릭한 다음 **SIP 주소** 필드에 전화 번호를 sip: *\<번호\>* @ *\<도메인 이름\>* 형식으로 입력합니다(예: sip:+14255550121@contoso.com).
    
      - 통화를 다른 사용자에게 착신 전환하려면 **SIP 주소로 전달** 을 클릭한 다음 **SIP 주소** 필드에 해당 사용자의 URI를 sip: *\<사용자 이름\>* @ *\<도메인 이름\>* 형식으로 입력합니다.
    
      - 통화를 다른 큐로 착신 전환하려면 **다른 큐로 착신 전환** 을 클릭한 다음 사용할 큐를 찾습니다.

10. **커밋** 을 클릭합니다.

## Windows PowerShell을 사용하여 큐를 만들거나 수정하려면

1.  RTCUniversalServerAdmins 그룹의 구성원이나 응답 그룹을 지원하는 미리 정의된 관리 역할 중 하나의 구성원으로 로그온합니다.
    

    > [!NOTE]
    > 관리 워크플로의 위임된 응답 그룹 관리자 중 하나인 경우 에이전트 그룹을 만들 에이전트 그룹을 큐에 할당할 수 있습니다.



2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  명령줄에서 다음을 실행하여 큐 시간 초과 임계값에 도달하면 재생할 음성 안내를 만들고 변수에 저장합니다.
    
        $promptTO = New-CsRgsPrompt -TextToSpeechPrompt "<text for TTS prompt>"
    
    예를 들면 다음과 같습니다.
    
        "All agents are currently busy. Please call back later."
    

    > [!NOTE]
    > 프롬프트로 오디오 파일을 사용하려면 <STRONG>Import-CsRgsAudioFile</STRONG> cmdlet을 사용합니다. 자세한 내용은 <A href="import-csrgsaudiofile.md">Import-CsRgsAudioFile</A>을 참조하십시오.



4.  명령줄에서 다음을 실행하여 큐 시간 초과 임계값에 도달하면 수행할 동작을 정의하고 변수에 저장합니다.
    
        $actionTO = New-CsRgsCallAction -Prompt <saved prompt from previous step> -Action <action to be taken>
    

    > [!NOTE]
    > 가능한 동작 및 구문에 대한 자세한 내용은 <A href="new-csrgscallaction.md">New-CsRgsCallAction</A>을 참조하십시오.

    
    예를 들면 다음과 같습니다.
    
        $action = New-CsRgsCallAction -Prompt $promptTO -Action Terminate

5.  명령줄에서 다음을 실행하여 큐 오버플로 임계값에 도달하면 재생할 음성 안내를 만들고 변수에 저장합니다.
    
        $promptOV = New-CsRgsPrompt -TextToSpeechPrompt "<text for TTS prompt>"
    
    예를 들면 다음과 같습니다.
    
        $promptOV = New-CsRgsPrompt -TextToSpeechPrompt "Too many calls are waiting. Please call back later."
    

    > [!NOTE]
    > 프롬프트로 오디오 파일을 사용하려면 <STRONG>Import-CsRgsAudioFile</STRONG> cmdlet을 사용합니다. 자세한 내용은 <A href="import-csrgsaudiofile.md">Import-CsRgsAudioFile</A>을 참조하십시오.



6.  명령줄에서 다음을 실행하여 큐 오버플로 임계값에 도달하면 수행할 동작을 정의하고 변수에 저장합니다.
    
        $actionOV = New-CsRgsCallAction -Prompt <saved prompt from previous step> -Action <action to be taken>
    

    > [!NOTE]
    > 가능한 동작 및 구문에 대한 자세한 내용은 <A href="new-csrgscallaction.md">New-CsRgsCallAction</A>을 참조하십시오.

    
    예를 들면 다음과 같습니다.
    
        $action = New-CsRgsCallAction -Prompt $promptOV -Action Terminate

7.  응답 그룹 서비스에 대한 서비스 이름을 검색하여 변수에 할당합니다. 명령줄에서 다음을 실행합니다.
    
        $serviceId="service:"+(Get-CSService | ?{$_.Applications -Like "*RGS*"}).ServiceId;

8.  명령줄에서 다음을 실행하여 큐에 할당할 에이전트 그룹의 ID를 얻습니다.
    
        $agid = (Get-CsRgsAgentGroup -Name "Help Desk").Identity;
    

    > [!NOTE]
    > 에이전트 그룹을 만드는 방법에 대한 자세한 내용은 <A href="new-csrgsagentgroup.md">New-CsRgsAgentGroup</A>을 참조하십시오.



9.  명령줄에서 다음을 실행하여 큐를 만듭니다.
    
        $q = New-CsRgsQueue -Parent <saved service ID from previous step> -Name "<name of queue>" [-Description "<description for queue>"] [-TimeoutThreshold <# seconds before call times out>] [-TimeoutAction <saved timeout action>] [-OverflowThreshold <# calls queue can hold>] [-OverflowCandidate <call to be acted on when overflow threshold met>] [-OverflowAction <saved overflow action>] [-AgentGroupIDList(<agent group identity>)];
    
    예를 들면 다음과 같습니다.
    
        $q = New-CsRgsQueue -Parent $serviceId -Name "Help Desk" -Description "Contoso Help Desk" -TimeoutThreshold 300 -TimeoutAction $actionTO -OverflowThreshold 10 -OverflowCandidate NewestCall -OverflowAction $actionOV -AgentGroupIDList($agid.Identity;

10. 다음을 실행하여 큐가 만들어졌는지 확인합니다.
    
        Get-CsRgsQueue -Name "Help Desk"

## 참고 항목

#### 기타 리소스

[New-CsRgsQueue](new-csrgsqueue.md)  
[Set-CsRgsQueue](set-csrgsqueue.md)  
[New-CsRgsPrompt](new-csrgsprompt.md)  
[New-CsRgsCallAction](new-csrgscallaction.md)  
[Get-CsRgsQueue](get-csrgsqueue.md)  
[Import-CsRgsAudioFile](import-csrgsaudiofile.md)  
[Remove-CsRgsQueue](remove-csrgsqueue.md)

