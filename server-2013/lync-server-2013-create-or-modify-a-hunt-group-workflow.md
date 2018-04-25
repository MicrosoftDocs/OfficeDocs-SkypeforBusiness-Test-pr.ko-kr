---
title: 'Lync Server 2013: 헌트 그룹 워크플로 만들기 또는 수정'
TOCTitle: 헌트 그룹 워크플로 만들기 또는 수정
ms:assetid: dcb9effb-5d12-4dee-80fc-ab9654222d5a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205321(v=OCS.15)
ms:contentKeyID: 49305257
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 헌트 그룹 워크플로 만들기 또는 수정

 

_**마지막으로 수정된 항목:** 2013-09-11_

다음 방법 중 하나를 사용하여 헌트 그룹 워크플로를 만들거나 수정합니다.


> [!NOTE]
> Lync Server 관리 셸 또는 응답 그룹 구성 도구를 사용하여 헌트 그룹 워크플로를 만들거나 수정할 수 있습니다. Lync Server 제어판에서 응답 그룹 구성 도구에 액세스하거나 URL로 <STRONG>https://</STRONG> <EM>&lt;webPoolFqdn&gt;</EM> <STRONG>/RgsConfig</STRONG> 를 입력하여 웹 브라우저에서 웹 페이지를 직접 열어 이 도구에 액세스할 수 있습니다.



## 응답 그룹 구성 도구을 사용하여 헌트 그룹 워크플로를 만들거나 수정하려면

1.  RTCUniversalServerAdmins 그룹의 구성원이나 응답 그룹을 지원하는 미리 정의된 관리 역할 중 하나의 구성원으로 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **응답 그룹** 을 클릭하고 **워크플로** 를 클릭합니다.

4.  **워크플로** 페이지에서 **워크플로 만들기 또는 편집** 을 클릭합니다.

5.  **서비스 선택** 검색 필드에 만들거나 변경할 워크플로를 호스트하는 **ApplicationServer** 서비스의 이름 전부 또는 일부를 입력합니다. 서비스 결과 목록에서 원하는 서비스를 클릭하고 **확인** 을 클릭합니다.
    

    > [!NOTE]
    > 응답 그룹 구성 도구가 열립니다. 웹 브라우저에서 URL로 <STRONG>https://</STRONG> <EM>&lt;webPoolFqdn&gt;</EM> <STRONG>/RgsConfig</STRONG> 를 입력하여 응답 그룹 구성 도구를 직접 열 수도 있습니다.



6.  다음 중 하나를 수행합니다.
    
      - **새 워크플로 만들기** 의 헌트 그룹 옆에 있는 **만들기** 를 클릭합니다.
    
      - **기존 워크플로 관리** 에서 변경할 워크플로를 찾은 다음 **동작** 에서 **편집** 을 클릭합니다.

7.  사용자가 워크플로를 호출할 준비가 되면 **워크플로 활성화** 를 선택합니다.
    

    > [!NOTE]
    > 관리되는 워크플로를 만들어야 하는 경우 <STRONG>워크플로 활성화</STRONG> 를 선택해야 합니다. 활성화된 관리 워크플로를 저장한 후에는 해당 워크플로를 수정하고 비활성화할 수 있습니다.



8.  페더레이션 사용자가 그룹을 호출할 수 있도록 허용하려면 **페더레이션 사용** 확인란을 선택합니다. 페더레이션용으로 구성된 응답 그룹 응용 프로그램에 적용되는 외부 액세스 정책도 있어야 합니다.
    

    > [!NOTE]
    > 전역 외부 액세스 정책은 응답 그룹 응용 프로그램에 적용됩니다. Lync Server 제어판을 사용하거나 <STRONG>Set-CsExternalAccessPolicy</STRONG> cmdlet을 사용하여 EnableOutsideAccess 매개 변수를 True로 설정하는 방식으로 응답 그룹 페더레이션에 대한 글로벌 정책을 구성할 수 있습니다. 글로벌 정책 설정은 사이트나 사용자 정책이 할당되지 않은 모든 사용자에게 적용됩니다. 따라서 응답 그룹에 대해 이 설정을 변경하기 전에 페더레이션 설정이 조직의 요구 사항을 충족하는지 확인하십시오. 사용자에게 정책이 적용되는 방법에 대한 자세한 내용은 <A href="lync-server-2013-manage-external-access-policy-for-your-organization.md">Lync Server 2013에서 외부 액세스 정책 관리</A>를 참조하십시오. 페더레이션 설정에 대한 자세한 내용은 <A href="set-csexternalaccesspolicy.md">Set-CsExternalAccessPolicy</A>를 참조하십시오.

    

    > [!NOTE]
    > Lync Online에서 호스팅되는 사용자는 온-프레미스 배포에서 호스팅되는 응답 그룹으로 전화를 걸 수 없습니다. 이는 하이브리드 배포 및 온-프레미스 배포가 Lync Online 배포와 페더레이션된 경우에도 마찬가지입니다.



9.  통화하는 동안 에이전트의 ID를 숨기려면 **에이전트 익명성 사용** 확인란을 선택합니다.
    

    > [!NOTE]
    > 통화가 연결된 후 에이전트 또는 발신자가 IM(인스턴트 메시징) 및 비디오를 추가할 수 있지만 IM 또는 비디오로 익명 통화를 시작할 수는 없습니다. 익명 에이전트는 통화를 보류하고, 전송(무조건 전송 및 협의 전송)하고, 대기시킨 후 재개할 수도 있습니다. 익명 통화는 회의, 응용 프로그램 공유 및 데스크톱 공유, 파일 전송, 화이트보드 및 데이터 공동 작업, 통화 기록을 지원하지 않습니다. Lync VDI 플러그 인을 사용하는 에이전트는 수신 통화를 익명으로 받을 수는 있지만 발신 전화를 익명으로 걸 수는 없습니다.



10. **전화를 받을 그룹의 주소를 입력하십시오** 에 워크플로 호출에 응답할 그룹의 기본 SIP URI(Uniform Resource Identifier) 주소를 입력합니다.
    

    > [!NOTE]
    > 워크플로의 기본 URI는 워크플로가 식별 및 참조되는 방식입니다. 입력하는 SIP URI는 Active Directory 도메인 서비스에서 연락처 개체로 만들어집니다. URI를 만들려면 개체가 Active Directory에서 고유해야 합니다.



11. **표시 이름** 에 워크플로에 대해 표시할 이름(예: 영업 응답 그룹)을 입력합니다.
    

    > [!NOTE]
    > "&lt;" 또는 "&gt;" 문자를 표시 이름에 포함하지 마십시오. <STRONG>RGS Presence Watcher</STRONG> 또는 <STRONG>RGS Presence Watcher</STRONG> 는 예약되어 있으므로 표시 이름으로 사용할 수 없습니다.



12. **전화 번호** 에 응답 그룹의 줄 URI(예: +14255550165)를 입력합니다.

13. **표시 이름** 에 응답 그룹에 대해 표시할 번호(예: +1 (425) 555-0165)를 입력합니다.

14. (선택 사항) **설명** 에 Lync 클라이언트의 연락처 카드에 표시할 워크플로에 대한 설명을 입력합니다.

15. **워크플로 유형** 에서 이 워크플로를 응답 그룹 관리자가 관리할 경우 **관리됨(Managed)** 을 선택합니다. 다음을 수행하여 응답 그룹 관리자를 워크플로에 할당합니다.
    
    1.  이 워크플로의 관리자 SIP URI를 입력하고 **추가** 를 클릭합니다.
    
    2.  워크플로에 추가할 다른 관리자의 SIP URI를 입력하고 **추가** 를 클릭합니다.
    

    > [!IMPORTANT]
    > 응답 그룹의 관리자로 지정된 모든 사용자에게 CsResponseGroupManager 역할이 할당되어야 합니다. 이 역할이 할당되지 않은 사용자는 응답 그룹을 관리할 수 없습니다.



16. **2단계 언어 선택** 에서 음성 인식 및 텍스트 음성 변환에 사용할 언어를 클릭합니다.

17. 환영 메시지를 구성하려면 **3단계 환영 메시지 구성** 아래에서 **환영 메시지를 재생합니다** 확인란을 선택하고 다음 중 하나를 수행합니다.
    
      - 환영 메시지를 발신자에게 음성으로 변환되는 텍스트로 입력하려면 **텍스트 음성 변환 사용** 을 클릭한 다음 텍스트 상자에 환영 메시지를 입력합니다.
        

        > [!NOTE]
        > 입력하는 텍스트에 HTML 태그를 포함하지 마십시오. HTML 태그를 포함하면 오류 메시지가 나타납니다.

    
      - 시작 메시지에 웨이브(.wav) 또는 Windows Media 오디오(.wma) 파일 녹음을 사용하려면 **녹음 선택** 을 클릭합니다. 새 오디오 파일을 업로드하려면 **녹음** 링크를 클릭합니다. 새 브라우저 창에서 **찾아보기** 를 클릭하고 사용할 오디오 파일을 선택한 다음 **열기** 를 클릭합니다. **업로드** 를 클릭하여 오디오 파일을 로드합니다.
        

        > [!NOTE]
        > 모든 사용자 제공 오디오 파일은 특정 요구 사항을 충족해야 합니다. 지원되는 파일 형식에 대한 자세한 내용은 <A href="lync-server-2013-technical-requirements-for-response-group.md">Lync Server 2013의 응답 그룹에 대한 기술 요구 사항</A>을 참조하십시오.



18. **4단계 업무 시간 지정** 의 **표준 시간대** 에서 워크플로의 표준 시간대를 클릭합니다.
    

    > [!NOTE]
    > 표준 시간대는 워크플로의 발신자 및 에이전트가 거주하는 지역의 표준 시간대로서, 시작 및 종료 시간을 계산하는 데 사용됩니다. 예를 들어 북미 동부 표준 시간대를 사용하도록 워크플로가 구성되어 있고 오전 7시에 시작하여 오후 11시에 끝나도록 워크플로를 예약한 경우 시작 및 종료 시간은 각각 동부 표준시 7시와 동부 표준시 23시로 설정됩니다. 시간은 24시간 형식으로 입력해야 합니다.



19. 다음 중 하나를 수행하여 사용할 업무 시간 일정의 유형을 선택합니다.
    
      - 미리 정의된 업무 시간 일정을 사용하려면 **미리 설정된 일정 사용** 을 클릭한 다음 드롭다운 메뉴에서 사용할 일정을 선택합니다.
        

        > [!NOTE]
        > 이 옵션을 선택하려면 먼저 미리 설정된 일정이 하나 이상 정의해야 합니다. <STRONG>New-CSRgsHoursOfBusiness</STRONG> cmdlet을 사용하여 미리 설정된 일정을 정의할 수 있습니다. 자세한 내용은 <A href="lync-server-2013-optional-define-response-group-business-hours.md">(선택 사항) Lync Server 2013에서 응답 그룹 업무 시간 정의</A>를 참조하십시오.

        

        > [!NOTE]
        > 미리 설정된 일정을 선택한 경우 응답 그룹을 사용할 수 있는 요일 및 시간으로 <STRONG>요일</STRONG> , <STRONG>시작</STRONG> 및 <STRONG>종료</STRONG> 가 자동으로 채워집니다.

    
      - 이 워크플로에만 적용되는 사용자 지정 일정을 사용하려면 **사용자 지정 일정 사용** 을 클릭합니다.

20. 이 워크플로에 대한 사용자 지정 일정을 만들려면 응답 그룹을 사용할 수 있는 요일 확인란을 클릭합니다.

21. 사용자 지정 일정을 만드는 경우 응답 그룹을 사용할 수 있는 주의 각 요일에 대해 **시작** 및 **종료** 시간을 입력합니다.
    

    > [!NOTE]
    > <STRONG>시작</STRONG> 및 <STRONG>종료</STRONG> 시간은 24시간 형식이어야 합니다. 예를 들어 평일 오전 9시에서 오후 5시까지 근무하고 12시부터 점심 시간 동안 문을 닫는 경우 업무 시간은 <STRONG>시작</STRONG> 9:00, <STRONG>종료</STRONG> 12:00, <STRONG>시작</STRONG> 13:00 및 <STRONG>종료</STRONG> 17:00로 지정됩니다.



22. 근무하지 않는 동안 메시지를 재생하려면 **응답 그룹의 업무 시간이 지났을 때 메시지를 재생합니다** 확인란을 선택하고 다음 중 하나를 수행하여 메시지를 지정합니다.
    
      - 메시지를 발신자에게 음성으로 변환되는 텍스트로 입력하려면 **텍스트 음성 변환 사용** 을 클릭한 다음 텍스트 상자에 메시지를 입력합니다.
        

        > [!NOTE]
        > 입력하는 텍스트에 HTML 태그를 포함하지 마십시오. HTML 태그를 포함하면 오류 메시지가 나타납니다.

    
      - 메시지에 대한 오디오 파일 녹음을 사용하려면 **녹음 선택** 을 클릭합니다. 새 오디오 파일을 업로드하려면 **녹음** 링크를 클릭합니다. 새 브라우저 창에서 **찾아보기** 를 클릭하고 사용할 파일을 선택한 다음 **열기** 를 클릭합니다. **업로드** 를 클릭하여 오디오 파일을 로드합니다.
        

        > [!NOTE]
        > 모든 사용자 제공 오디오 파일은 특정 요구 사항을 충족해야 합니다. 지원되는 오디오 파일 형식에 대한 자세한 내용은 <A href="lync-server-2013-technical-requirements-for-response-group.md">Lync Server 2013의 응답 그룹에 대한 기술 요구 사항</A>을 참조하십시오.



23. 메시지가 재생된 후에 발신자를 처리할 방법을 지정합니다(메시지가 구성된 경우).
    
      - 통화 연결을 끊으려면 **전화 끊기** 를 클릭합니다.
    
      - 통화를 음성 사서함으로 착신 전환하려면 **음성 사서함으로 착신 전환** 을 클릭하고 음성 메일 주소를 입력합니다. 음성 메일 주소 형식은 *\<사용자 이름\>* @ *\<도메인 이름\>* (예: bob@contoso.com)입니다.
    
      - 통화를 다른 사용자에게 착신 전환하려면 **SIP URI로 착신 전환** 을 클릭하고 사용자 주소를 입력합니다. 사용자 주소의 형식은 *\<사용자 이름\>* @ *\<도메인 이름\>* 입니다.
    
      - 통화를 다른 전화 번호로 착신 전환하려면 **전화 번호로 착신 전환** 을 클릭하고 전화 번호를 입력합니다. 전화 번호의 형식은 *\<번호\>* @ *\<도메인 이름\>* (예: +14255550121@contoso.com)입니다. 도메인 이름은 발신자를 올바른 대상으로 라우팅하는 데 사용됩니다.

24. **5단계 휴일 지정** 아래에서 응답 그룹이 근무하지 않는 요일을 정의하는 하나 이상의 휴일 집합에 대한 확인란을 클릭합니다.
    

    > [!NOTE]
    > 워크플로를 구성하기 전에 휴일 및 휴일 집합을 정의해야 합니다. <STRONG>New-CsRgsHoliday</STRONG> 및 <STRONG>New-CsRgsHolidaySet</STRONG> cmdlet를 사용하여 휴일 및 휴일 집합을 정의할 수 있습니다. 자세한 내용은 <A href="lync-server-2013-optional-define-response-group-holiday-sets.md">(선택 사항) Lync Server 2013에서 응답 그룹 휴일 집합 정의</A>를 참조하십시오.



25. 휴일에 메시지를 재생하려면 **휴일에 메시지를 재생합니다** 확인란을 선택하고 다음 중 하나를 수행하여 재생할 메시지를 지정합니다.
    
      - 메시지를 발신자에게 음성으로 변환되는 텍스트로 입력하려면 **텍스트 음성 변환 사용** 을 클릭한 다음 텍스트 상자에 메시지를 입력합니다.
        

        > [!NOTE]
        > 입력하는 텍스트에 HTML 태그를 포함하지 마십시오. HTML 태그를 포함하면 오류 메시지가 나타납니다.

    
      - 메시지에 대한 오디오 파일 녹음을 사용하려면 **녹음 선택** 을 클릭합니다. 새 오디오 파일을 업로드하려면 **녹음** 링크를 클릭합니다. 새 브라우저 창에서 **찾아보기** 를 클릭하고 사용할 파일을 선택한 다음 **열기** 를 클릭합니다. **업로드** 를 클릭하여 오디오 파일을 로드합니다.
        

        > [!NOTE]
        > 모든 사용자 제공 오디오 파일은 특정 요구 사항을 충족해야 합니다. 지원되는 오디오 파일 형식에 대한 자세한 내용은 <A href="lync-server-2013-technical-requirements-for-response-group.md">Lync Server 2013의 응답 그룹에 대한 기술 요구 사항</A>을 참조하십시오.



26. 메시지가 재생된 후에 발신자를 처리할 방법을 지정합니다(메시지가 구성된 경우).
    
      - 통화 연결을 끊으려면 **전화 끊기** 를 클릭합니다.
    
      - 통화를 음성 사서함으로 착신 전환하려면 **음성 사서함으로 착신 전환** 을 클릭하고 음성 메일 주소를 입력합니다. 음성 메일 주소 형식은 *\<사용자 이름\>* @ *\<도메인 이름\>* (예: bob@contoso.com)입니다.
    
      - 통화를 다른 사용자에게 착신 전환하려면 **SIP URI로 착신 전환** 을 클릭하고 사용자 주소를 입력합니다. 사용자 주소의 형식은 *\<사용자 이름\>* @ *\<도메인 이름\>* 입니다.
    
      - 통화를 다른 전화 번호로 착신 전환하려면 **전화 번호로 착신 전환** 을 클릭하고 전화 번호를 입력합니다. 전화 번호의 형식은 *\<번호\>* @ *\<도메인 이름\>* (예: +14255550121@contoso.com)입니다. 도메인 이름은 발신자를 올바른 대상으로 라우팅하는 데 사용됩니다.

27. **6단계 큐 구성** 의 **전화를 받을 큐 선택** 에서 에이전트가 사용 가능할 때까지 발신자를 대기 상태로 둘 큐를 선택합니다.

28. **7단계 대기 음악 구성** 에서 다음 중 하나를 수행하여 에이전트를 기다리는 동안 발신자에게 들려줄 음악을 선택합니다.
    
      - 기본 대기 음악 녹음을 사용하려면 **기본값 사용** 을 클릭합니다.
    
      - 대기 음악에 오디오 파일 녹음을 사용하려면 **음악 파일 선택** 을 클릭합니다. 새 오디오 파일을 업로드하려면 **음악 파일** 링크를 클릭합니다. 새 브라우저 창에서 **찾아보기** 를 클릭하고 사용할 파일을 선택한 다음 **열기** 를 클릭합니다. **업로드** 를 클릭하여 오디오 파일을 로드합니다.
        

        > [!NOTE]
        > 모든 사용자 제공 오디오 파일은 특정 요구 사항을 충족해야 합니다. 지원되는 오디오 파일 형식에 대한 자세한 내용은 <A href="lync-server-2013-technical-requirements-for-response-group.md">Lync Server 2013의 응답 그룹에 대한 기술 요구 사항</A>을 참조하십시오.



29. **배포** 를 클릭합니다.

## Windows PowerShell을 사용하여 헌트 그룹 워크플로를 만들거나 수정하려면

1.  RTCUniversalServerAdmins 그룹의 구성원이나 응답 그룹을 지원하는 미리 정의된 관리 역할 중 하나의 구성원으로 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  시작 메시지로 재생할 프롬프트를 작성하여 변수에 저장합니다. 명령줄에서 다음을 실행합니다.
    
        $promptWM = New-CsRgsPrompt -TextToSpeechPrompt "<text for TTS prompt>"
    
    예를 들면 다음과 같습니다.
    
        $promptWM = New-CsRgsPrompt -TextToSpeechPrompt "Welcome to Contoso. Please wait for an available agent."
    

    > [!NOTE]
    > 프롬프트로 오디오 파일을 사용하려면 <STRONG>Import-CsRgsAudioFile</STRONG> cmdlet을 사용합니다. 자세한 내용은 <A href="import-csrgsaudiofile.md">Import-CsRgsAudioFile</A>을 참조하십시오.



4.  통화가 이동될 해당 큐 또는 질문의 ID를 가져옵니다. 명령줄에서 다음을 실행합니다.
    
        $qid = (Get-CsRgsQueue -Name "Help Desk").Identity
    
    큐 만들기에 대한 자세한 내용은 [New-CsRgsQueue](new-csrgsqueue.md)를 참조하십시오.

5.  업무 시간 동안 워크플로를 열 때 수행할 기본 동작을 정의하여 변수에 저장합니다. 명령줄에서 다음을 실행합니다.
    
        $actionWM = New-CsRgsCallAction -Prompt <saved prompt from previous step> -Action <action to be taken> -QueueID $qid
    

    > [!NOTE]
    > 헌트 그룹 워크플로의 경우 기본적으로 통화를 큐로 이동해야 합니다. 이 매개 변수는 활성 워크플로에 필요합니다. 비활성 워크플로에는 필요하지 않습니다.

    
    예를 들면 다음과 같습니다.
    
        $actionWM = New-CsRgsCallAction -Prompt $promptWM -Action TransferToQueue -QueueID $qid.Identity

6.  업무 시간과 휴일을 정의하려는 경우 워크플로를 만들거나 수정하기 전에 정의해야 합니다. 자세한 내용은 [(선택 사항) Lync Server 2013에서 응답 그룹 업무 시간 정의](lync-server-2013-optional-define-response-group-business-hours.md)와 [(선택 사항) Lync Server 2013에서 응답 그룹 휴일 집합 정의](lync-server-2013-optional-define-response-group-holiday-sets.md)를 참조하십시오.

7.  업무 시간 외나 휴일에 받는 통화에 대한 프롬프트를 만들려면 **New-CsRgsPrompt** cmdlet을 사용하여 프롬프트를 정의하고 **New-CsRgsCallAction**를 사용하여 프롬프트 후에 수행될 동작을 정의합니다. 자세한 내용은 [New-CsRgsPrompt](new-csrgsprompt.md)와 [New-CsRgsCallAction](new-csrgscallaction.md)을 참조하십시오.

8.  Lync Server 응답 그룹 서비스에 대한 서비스 이름을 검색하여 변수에 할당합니다. 명령줄에 다음을 실행합니다.
    
        $serviceId="service:"+(Get-CSService | ?{$_.Applications -like "*RGS*"}).ServiceId;

9.  워크플로를 만들거나 수정합니다. 워크플로를 만들려면 **New-CsRgsWorkflow**를 사용하고, 워크플로를 수정하려면 **Set-CsRgsWorkflow**를 사용합니다. 명령줄에 다음을 입력합니다.
    
        $workflowHG = New-CsRgsWorkflow -Parent <service ID for the Response Group service> -Name "<hunt group name>" [-Description "<hunt group description>"] -PrimaryUri "<SIP address for the workflow>" [-LineUri "<Phone number for the workflow>"] [-DisplayNumber "<Phone number displayed in Lync>"] [-Active <$true | $false>] [-Anonymous <$true | $false>] [-DefaultAction <variable from preceding step>] [-EnabledForFederation <$true | $false>] [-Managed <$true | $false>] [-MangersByUri <SIP addresses for Response Group Managers who can manage the workflow>]
    
    예를 들면 다음과 같습니다.
    
        $workflowHG = New-CsRgsWorkflow -Parent $serviceID -Name "Human Resources" -Description "Human Resources workflow" -PrimaryUri "sip:humanresources@contoso.com" -LineUri "TEL:+14255551219" -DisplayNumber "555-1219" -Active $true -Anonymous $true -DefaultAction $actionWM -EnabledForFederation $false -Managed $true -ManagersByUri "sip:bob@contoso.com", "mindy@contoso.com"
    

    > [!IMPORTANT]
    > 워크플로의 관리자로 지정된 모든 사용자에게 CsResponseGroupManager 역할을 할당해야 합니다.

    

    > [!NOTE]
    > 선택적 추가 매개 변수에 대한 자세한 내용은 <A href="new-csrgsworkflow.md">New-CsRgsWorkflow</A> 또는 <A href="set-csrgsworkflow.md">Set-CsRgsWorkflow</A>를 참조하십시오.



## 참고 항목

#### 작업

[(선택 사항) Lync Server 2013에서 응답 그룹 휴일 집합 정의](lync-server-2013-optional-define-response-group-holiday-sets.md)  

#### 개념

[(선택 사항) Lync Server 2013에서 응답 그룹 업무 시간 정의](lync-server-2013-optional-define-response-group-business-hours.md)  

#### 기타 리소스

[New-CsRgsWorkflow](new-csrgsworkflow.md)  
[Set-CsRgsWorkflow](set-csrgsworkflow.md)  
[New-CsRgsPrompt](new-csrgsprompt.md)  
[New-CsRgsCallAction](new-csrgscallaction.md)

