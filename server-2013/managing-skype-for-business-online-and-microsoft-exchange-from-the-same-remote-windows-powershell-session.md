---
title: 동일한 원격 Windows PowerShell 세션에서 Lync Online 및 Microsoft Exchange 관리
TOCTitle: 동일한 원격 Windows PowerShell 세션에서 Lync Online 및 Microsoft Exchange 관리
ms:assetid: 4eb4b5f0-f407-46bd-a2ac-a7ccbc387d51
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362787(v=OCS.15)
ms:contentKeyID: 56270232
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 동일한 원격 Windows PowerShell 세션에서 Lync Online 및 Microsoft Exchange 관리

 

_**마지막으로 수정된 항목:** 2015-06-22_

Office 365를 구독하면 비즈니스용 Skype Online에 대한 액세스 권한뿐 아니라 Exchange Online에 대한 액세스 권한도 부여됩니다. Windows PowerShell의 원격 세션을 사용하여 비즈니스용 Skype Online을 관리할 수 있습니다. 또한 Windows PowerShell의 원격 세션을 사용하여 Exchange를 관리할 수도 있습니다. 하지만 비즈니스용 Skype Online과 Exchange Online은 동일한 URI를 공유하지도, 동일한 연결 방법을 사용하지도 않습니다. 즉, 별도의 세션을 사용하여 비즈니스용 Skype Online과 Exchange를 관리해야 합니다. 단일 Windows PowerShell 원격 세션을 사용하여 두 제품 모두를 관리할 수 있는 방법이 있을까요?

아시다시피 Windows PowerShell의 동일한 인스턴스에서 두 제품 모두를 관리할 수 있고, 이중 관리 세션 설정은 매우 간편합니다. 먼저 Windows PowerShell을 시작하고 늘 하던 방식대로 비즈니스용 Skype Online에 연결합니다. 자격 증명 개체를 만든 다음 비즈니스용 Skype Online에 연결하는 새로운 세션을 만듭니다.

    $credential = Get-Credential "kenmyer@litwareinc.com"
    $lyncSession = New-CsOnlineSession -Credential $credential

그런 다음 비슷한 프로세스를 사용하여 Exchange Online에 연결합니다. 새 자격 증명 개체는 만들지 않아도 됩니다. 비즈니스용 Skype Online에 로그온할 때 사용한 것과 동일한 개체($credential)를 계속해서 사용할 수 있습니다.

    $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $credential -Authentication "Basic" -AllowRedirection

Exchange Online에 연결할 때는 Office 365 URI와 관계없이 항상 https://outlook.office365.com/powershell-liveid/ URI를 사용해야 합니다. 인증을 받은 후에는 적절한 URI로 자동 리디렉션됩니다. 따라서 AllowRedirection 매개 변수를 포함하는 것이 특히 중요합니다. 이 매개 변수를 생략하면 인증은 되지만 리디렉션은 실패하고 Exchange Online으로 연결할 수 없습니다.

    New-PSSession : [ps.outlook.com] The WinRM service cannot process the request because the request needs to be sent to a different machine. Use the redirect information to send the request to a new machine.  Redirect location reported: https://pod51043psh.outlook.com/powershell-liveid?PSVersion=3.0 . To automatically connect to the redirected URI, verify  MaximumConnectionRedirectionCount" property of session preference variable "PSSessionOption" and use "AllowRedirection" parameter on the cmdlet.

이제 컴퓨터에서 두 개의 개별 세션이 실행됩니다. 이를 확인하려면 Windows PowerShell 프롬프트에 다음 명령을 입력합니다.

    Get-PSSession

화면에 다음과 비슷한 정보가 표시되어야 합니다.

    Id Name      ComputerName  State   ConfigurationName     Availability
    -- ----      ------------  -----   -----------------     ------------
     1 Session1  pod510w43...  Opened  Microsoft.PowerShell     Available
     2 Session2  up02921vd...  Opened  Microsoft.Exchange       Available

이제 Windows PowerShell의 로컬 세션으로 가져올 수 있는 원격 세션 쌍이 있습니다. 로컬 세션으로 가져오려면 다음 두 명령을 실행합니다.

    Import-PSSession $lyncSession
    Import-PSSession $exchangeSession

이제 비즈니스용 Skype Online 및 Exchange Online cmdlet을 둘 다 사용할 수 있습니다. 다음 명령을 실행하여 사용자 정보가 반환되는지 확인합니다.

    Get-CsOnlineUser -ResultSize 1

그런 다음 Exchange 명령을 실행하여 사서함 정보가 반환되는지 확인합니다.

    Get-Mailbox -ResultSize 1

관리 세션을 종료하려면 원격 세션을 모두 닫았는지 확인합니다.

    Remove-PSSession $lyncSession
    Remove-PSSession $exchangeSession

## 참고 항목

#### 개념

[Lync Online 관리를 위한 컴퓨터 구성](configuring-your-computer-for-skype-for-business-online-management.md)

