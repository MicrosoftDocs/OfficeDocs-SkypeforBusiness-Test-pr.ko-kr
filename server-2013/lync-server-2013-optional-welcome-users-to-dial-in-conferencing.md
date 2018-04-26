---
title: 'Lync Server 2013: (선택 사항) 사용자에게 전화 접속 회의 시작 메시지 보내기'
TOCTitle: (선택 사항) 사용자에게 전화 접속 회의 시작 메시지 보내기
ms:assetid: caa4fd61-f506-4c09-bb5b-1aa260d7a720
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398846(v=OCS.15)
ms:contentKeyID: 49305030
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# (선택 사항) Lync Server 2013에서 사용자에게 전화 접속 회의 시작 메시지 보내기

 

_**마지막으로 수정된 항목:** 2012-09-30_

전화 접속 회의를 구성하고 기능이 제대로 작동하는지 테스트한 후 사용자에 대한 초기 PIN(개인 식별 번호)을 설정하여 전화 접속 회의 설정 웹 페이지로 이동되는 링크 및 초기 PIN 등과 같은 기초 지침을 비롯하여 기능 사용 가능 여부를 사용자에게 알려줘야 합니다. 이 단계는 선택 사항입니다. 일반적으로 **Set-CsClientPin** cmdlet를 사용하여 PIN을 재설정하지만 정보가 포함된 환영 전자 메일을 보낼 경우 처음에 이 항목의 절차를 사용할 수 있습니다. 전자 메일을 보내지 않을 경우에는 대신 **Set-CsClientPin**을 사용할 수 있습니다.

**Set-CsPinSendCAWelcomeMail** 스크립트를 사용하여 PIN을 설정하고 한 명의 사용자에게 환영 전자 메일을 보낼 수 있습니다. 기본적으로 PIN이 이미 설정된 경우 스크립트에서 PIN을 재설정하지 않지만 **Force** 매개 변수를 사용하여 PIN을 강제로 재설정할 수 있습니다. 전자 메일 메시지는 SMTP(Simple Mail Transfer Protocol)를 사용하여 전송됩니다.

**Set-CsPinSendCAWelcomeMail** 스크립트를 반복적으로 실행하는 스크립트를 만들어 PIN을 설정하고 전자 메일을 여러 사용자에게 보낼 수 있습니다. 전자 메일 템플릿(즉, **CAWelcomeEmailTemplate.html** 파일)을 수정하여 인트라넷 페이지에 링크를 추가하거나 전자 메일 텍스트를 수정할 수 있습니다.

## 초기 PIN을 설정하고 환영 전자 메일을 보내려면

1.  RTCUniversalServerAdmins 그룹의 구성원으로 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  명령 프롬프트에서 다음을 실행합니다.
    
        Set-CsPinSendCAWelcomeMail -UserUri <user identifier>
        -From <email address of sender> [-Subject <subject for email message>]
        [-UserEmailAddress <destination email address>]
        [-Cc <email address of recipients who receive copy of email>]
        [-Bcc <email address of recipients who receive blind copies>]
        [-TemplatePath <path for email template>]
        [-SmtpServer] <SMTP server name>]
        [-BodyAsPlainText] [-UseSsl]
        [-Pin <new numeric PIN>] [-Force] `
        [-Credential <SMTP server credentials used to send email with the specified From address>]
    
    **SmtpServer**   기본적으로 스크립트에서 이 매개 변수에 대해 예약된 환경 변수인 **$PSEmailServer** 값을 사용합니다. **$PSEmailServer** 변수가 설정되지 않은 경우 이 매개 변수를 지정해야 합니다.
    
    **Credential**   기본적으로 스크립트에서 현재 사용자의 자격 증명을 사용합니다. 현재 사용자에게 지정된 보내는 사람 주소를 대신하여 전자 메일을 보낼 수 있는 사용 권한이 없는 경우 이 매개 변수를 지정해야 합니다. 일반적으로 전자 메일 주소를 보내는 사람 주소로 지정하지 않을 경우 이 매개 변수를 지정합니다.
    
    예를 들면 다음과 같습니다.
    
        Set-CsPinSendCAWelcomeMail -UserUri "bob@contoso.com"
        -From "marco@contoso.com"
    
    이 예에서는 새 PIN을 만들고 Marco가 Bob에게 환영 전자 메일을 보냅니다. 기본 템플릿의 전자 메일 텍스트가 사용되며 전자 메일 메시지가 HTML 형식으로 만들어집니다. 기본 제목은 "전화 접속 회의 시작"입니다.
    
    다른 예:
    
        Set-CsPinSendCAWelcomeMail -UserUri "bob@contoso.com"
        -From "marco@contoso.com" -Subject "Your new dial-in conferencing PIN"
        -Pin "383042650" -Force
        -Credential Admin@contoso.com -UseSsl
    
    이 예에서는 Bob에게 기존 PIN이 있는 경우에도 "383042650" 값으로 새 PIN을 재설정한 다음 Marco가 Bob에게 환영 전자 메일을 보냅니다 Credential 매개 변수가 지정되었으므로 이 명령을 실행하는 사용자에게 암호를 입력하라는 메시지가 표시됩니다. 이 전자 메일은 SSL(Secure Sockets Layer)을 사용하여 보내집니다.

