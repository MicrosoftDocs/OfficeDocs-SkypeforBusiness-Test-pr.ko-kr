---
title: Windows PowerShell을 사용하여 Lync Online에 연결
TOCTitle: Windows PowerShell을 사용하여 Lync Online에 연결
ms:assetid: 6167dad9-9628-4fdb-bed1-bdb3f7108e64
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362795(v=OCS.15)
ms:contentKeyID: 56270242
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Windows PowerShell을 사용하여 Lync Online에 연결

 

_**마지막으로 수정된 항목:** 2015-06-22_

필수 구성 요소 소프트웨어를 설치했다면 Windows PowerShell을 사용하여 비즈니스용 Skype Online을 관리할 수 있습니다. 관리 작업을 수행하려면 먼저 Windows PowerShell의 표준 인스턴스를 열어야 합니다. Windows PowerShell(Lync Server 관리 셸과 유사함)의 특수 인스턴스를 열 필요가 없으며, 제어판 앱 또는 기타 특수한 유형의 응용 프로그램을 열 필요도 없습니다. 비즈니스용 Skype Online 관리는 Windows PowerShell의 원격 세션을 사용하여 수행되기 때문입니다. 다음과 같은 원리입니다.

1.  Windows PowerShell의 정규 세션을 사용하여 비즈니스용 Skype Online에 연결합니다. 원격 연결 중에 사용자는 로컬 컴퓨터에서 작업하며 Windows PowerShell의 로컬 복사본을 사용하지만 원격 시스템(비즈니스용 Skype Online)에서 발견한 개체를 관리합니다.

2.  비즈니스용 Skype Online 관리에 필요한 모든 cmdlet, 스크립트, 기타 항목은 컴퓨터에 다운로드됩니다. 이 항목은 메모리에 보관되며 비즈니스용 Skype Online에서 설정된 원격 세션에서만 사용할 수 있습니다. 이는 반드시 기억해 두어야 할 사항입니다. 비즈니스용 Skype Online에 원격 연결을 수행한 경우 비즈니스용 Skype Online cmdlet(예: [Get-CsTenant](get-cstenant.md))은 사용자 컴퓨터의 메모리에 복사됩니다. 사용자는 원격 세션에서 이 cmdlet을 실행할 수 있습니다. 이 cmdlet은 원격 세션에서만 사용할 수 있습니다. 예를 들어 Windows PowerShell의 두 번째 세션을 시작한 경우 이 세션에서는 비즈니스용 Skype Online에 연결할 수 없습니다. **Get-CsTenant** cmdlet을 해당 세션에서 실행하려는 경우 다음 메시지가 표시됩니다.
    
        Get-CsTenant : The term 'Get-CsTenant' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
    
    **Get-CsTenant** cmdlet(또는 기타 비즈니스용 Skype Online cmdlet)을 하드 디스크에서 검색하는 경우 검색 결과가 나오지 않습니다. 이는 원격 세션을 만들 때 하드 디스크에는 아무 것도 저장되지 않기 때문입니다.

3.  원격 세션을 닫으면 다운로드된 항목이 컴퓨터 메모리에서 삭제됩니다. 예를 들어 **Get-CsTenant** cmdlet을 사용하여 Windows PowerShell의 원격 세션을 시작한 다음 해당 세션을 닫을 수 있습니다. Windows PowerShell을 다시 시작하는 경우 **Get-CsTenant** cmdlet은 더 이상 사용할 수 없습니다. **Get-CsTenant** cmdlet에 액세스하려면 비즈니스용 Skype Online.에 다시 연결해야 합니다.


> [!NOTE]
> 하이브리드 배포를 사용 중인 경우 <A href="using-windows-powershell-in-a-hybrid-deployment-with-skype-for-business-online.md">하이브리드 배포에서 Windows PowerShell 사용</A> 문서에 간략히 설명된 절차를 따라야 합니다.



비즈니스용 Skype Online에 대한 원격 연결을 만들려면 로컬 컴퓨터에서 Windows PowerShell의 새 세션을 시작합니다. Windows 7, Windows Server 2008 R2, Windows Server 2012 또는 Windows Server 2012 R2를 사용하는 경우 다음을 실행합니다.

  - **시작**, **모든 프로그램**, **보조프로그램**, **Windows PowerShell**, **Windows PowerShell**을 차례로 클릭합니다.

Windows 8 또는 8.1을 사용하는 경우 다음을 실행합니다.

  - 아이콘 모음에 액세스하여 **검색**, **Windows PowerShell**을 클릭합니다. Windows 키와 C를 동시에 누르면 터치 스크린 여부에 관계없이 Windows 8 또는 8.1 컴퓨터의 아이콘 모음에 빠르게 액세스할 수 있습니다.

Windows PowerShell 콘솔이 표시되면 Windows PowerShell 자격 증명 개체를 만들어야 합니다. 자격 증명 개체는 사용자 이름과 암호를 안전하게 비즈니스용 Skype Online로 전달하는 데 사용됩니다. 자격 증명 개체를 만들려면 Windows PowerShell 프롬프트에서 다음 명령을 입력한 뒤 ENTER 키를 누릅니다.

    $credential = Get-Credential


> [!NOTE]
> 이 예에서 사용자 이름 및 암호는 $credential 변수에 저장됩니다. Windows PowerShell의 변수 명명 규칙을 준수하는 경우 사용자는 이 변수의 이름을 원하는 대로 지정할 수 있습니다. 하지만 사용자와 암호를 저장하려면 일부 유형의 변수를 사용해야 합니다. 그렇지 않으면 자격 증명 개체는 만들어지는 즉시 사라지게 됩니다.



ENTER 키를 누르고 **Windows PowerShell 자격 증명** 대화 상자를 확인합니다.

![Windows PowerShell 로그인 자격 증명](images/Dn362795.0f04e0a1-c9d6-4341-a0bb-ef721c4815fd(OCS.15).png "Windows PowerShell 로그인 자격 증명")

**사용자 이름** 상자에 비즈니스용 Skype Online 사용자 이름을 입력합니다. **암호** 상자에는 비즈니스용 Skype Online 암호(암호는 마스킹되어 화면에 표시되지 않음)를 입력합니다. 예를 들어 사용자 이름이 kenmyer@litwareinc.com이고 암호가 p@ssw0rd\!인 경우 대화 상자는 다음과 같이 표시됩니다.

![Windows PowerShell 자격 증명 로그인](images/Dn362795.85977a0e-b14a-4aec-a45e-8548e9c9f691(OCS.15).png "Windows PowerShell 자격 증명 로그인")

자격 증명 개체를 만들려면 **확인**을 클릭합니다. 개체가 만들어졌는지 확인하려면 변수 이름을 Windows PowerShell 프롬프트에 입력하고 ENTER 키를 누릅니다.

    $credential

Windows PowerShell에서 다음과 유사한 형식의 메시지가 표시됩니다.

    UserName                            Password
    --------                            --------
    kenmyer@litwareinc.com              System.Security.SecureString


> [!NOTE]
> <STRONG>Get-Credential</STRONG> cmdlet은 사용자가 입력하는 모든 자격 증명을 수락하며 유효한 사용자 이름과 암호를 입력했는지 확인하지 않는다는 점에 유의하세요. 그러한 유효성 검사는 비즈니스용 Skype Online에 로그인을 시도하는 경우에만 발생합니다.



자격 증명 개체를 만든 후에는 비즈니스용 Skype Online에 연결할 수 있는 새 원격 Windows PowerShell 세션을 만들 수 있습니다. 이를 수행하려면 다음 명령을 Windows PowerShell 프롬프트에 입력하고 ENTER 키를 누릅니다.

    $session = New-CsOnlineSession -Credential $credential


> [!NOTE]
> $session은 정보를 보유하는 데 사용하는 변수입니다. 이 경우 비즈니스용 Skype Online 연결에 대한 정보가 이에 해당합니다. 마찬가지로, Windows PowerShell 변수 명명 지침(이름에 공백 또는 문장 부호를 포함할 수 없음 등)을 준수하는 한 변수를 원하는 이름으로 지정할 수 있습니다.



명령을 정확히 입력했는지 확인하세요(변수 이름에 예외가 있을 수 있습니다). 사용자의 비즈니스용 Skype Online 도메인 이름과는 무관합니다. 도메인 이름과는 관계없이 **New-CsOnlineSession** cmdlet을 통해 Office 365에 연결되며 제공된 자격 증명을 사용하여 로그인됩니다. 연결 및 인증이 완료되면 제공된 자격 증명에 따라 적절한 URI로 자동 리디렉션됩니다.

연결에 성공하면 Windows PowerShell 콘솔에서 다음과 비슷한 메시지가 표시됩니다.

    VERBOSE: Determining domain to admin
    VERBOSE: AdminDomain = litwareinc.com
    VERBOSE: Discovering PowerShell endpoint URI
    VERBOSE: TargetUri = https://webdir0d.litwareinc.com/OcsPowerShellLiveId
    VERBOSE: Requesting authentication token
    VERBOSE: Success
    VERBOSE: Initializing remote session
    VERBOSE: Success
    Id Name       ComputerName    State        ConfigurationName     Availability -- ----       ------------    -----        -----------------     ------------
    2 Session2    litwarein...    Opened       Microsoft.PowerShell  Available

Windows PowerShell을 사용하여 비즈니스용 Skype Online을 관리할 준비가 되었습니까? 아직 준비 되지 않았습니다. **New-CsOnlineSession** cmdlet을 사용하여 비즈니스용 Skype Online에 연결하면 사용자의 새 세션이 만들어집니다. 그러면 사용자는 Windows PowerShell 콘솔로 새 세션을 가져와야 합니다. 이렇게 하려면 다음 명령을 실행합니다.

    Import-PSSession $session

ENTER 키를 누르면 Windows PowerShell 콘솔에서 다음과 유사한 진행률이 표시됩니다.

    Creating implicit remoting module . . .
         Getting command information from remote session . . . 16 commands  
              received
         [oooooooooooooooo
         00:00:33 remaining

현재 Windows PowerShell이 비즈니스용 Skype Online 관리에 필요한 cmdlet과 기타 항목을 다운로드하고 있습니다. 다운로드를 마치면 Windows PowerShell 콘솔에서 다음과 유사한 정보가 표시됩니다.

    ModuleType Name                 ExportedCommands
    ---------- ----                 ----------------
    Script     tmp_5astd3uh.m5v     {Disable-CsMeetingRoom, Enable-Cs ...}

현재 Windows PowerShell을 사용하여 비즈니스용 Skype Online을 관리할 준비가 되었습니다. 다운로드가 성공했는지 확인하고 비즈니스용 Skype Online cmdlet 사용 가능 여부를 보려면 모든 비즈니스용 Skype Online cmdlet을 포함하는 임시 Windows PowerShell 모듈의 이름을 먼저 결정해야 합니다. 이를 위해 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

    Get-Module

다음과 유사한 정보가 화면에 표시됩니다.

    ModuleType Name                 ExportedCommands
    ---------- ----                 ----------------
    Manifest   Microsoft.PowerS...  {Add-Computer, Add-Content, A...}
    Script     tmp_5astd3uh.m5v     {Disable-CsMeetingRoom, Enabl...}

ModuleType Script가 있는 모듈은 비즈니스용 Skype Online cmdlet을 포함하는 모듈입니다. 해당 cmdlet 목록을 반환하려면 Script 모듈을 모듈 이름으로 사용하여 **Get-Command** cmdlet을 실행합니다.

    Get-Command -Module tmp_5astd3uh.m5v

그러면 Windows PowerShell에서는 모든 비즈니스용 Skype Online cmdlet 목록이 표시됩니다.

관리 작업을 완료하면 Windows PowerShell 콘솔을 닫기 전에 항상 다음 명령을 실행해야 합니다.

    Remove-PSSession $session

**Remove-PSSession** cmdlet은 비즈니스용 Skype Online과의 연결을 해제하고 원격 세션을 닫습니다. **Import-PSSession** cmdlet을 실행하여 세션을 다시 불러 오려고 하면 다음과 같은 오류 메시지가 표시됩니다.

    Import-PSSession : State of runspace is not valid for this operation.

이 메시지는 비즈니스용 Skype Online에 다시 연결하려면 새 세션을 만들어야 한다는 것을 알려줍니다.

Windows PowerShell 콘솔을 닫기 전에 세션을 제거하지 못했거나 콘솔이 예기치 않게 종료되더라도 나쁜 일이 발생하지는 않습니다. 15분 동안 작업이 없으면 세션은 저절로 연결 해제됩니다. 기본적으로 각 비즈니스용 Skype Online 관리자는 비즈니스용 Skype Online으로 동시에 세 개의 연결만 가능합니다. 세션을 제거하지 않고 Windows PowerShell 콘솔을 닫은 경우, 종료된 세션은 사용하지 않더라도 하나의 연결로 간주되며, 이는 시간 초과로 세션이 제거될 때까지 지속됩니다. 예를 들어, 비즈니스용 Skype Online 세션을 매번 제거하지 않고 Windows PowerShell 콘솔을 세 번 열고 닫은 경우, Windows PowerShell을 열어 네 번째 연결을 시도하는 경우 명령은 중지되며 연결이 이루어지지 않습니다.


> [!NOTE]
> 연결을 시도하는 중에 Windows PowerShell이 중지될 경우 Ctrl+C 키를 눌러 중지된 명령을 종료해야 합니다.



개별 관리자는 비즈니스용 Skype Online 테넌트에 대해 동시에 세 개까지 연결할 수 있지만, 조직의 경우에는 동시에 아홉 개까지 연결할 수 있습니다. 이는 비즈니스용 Skype Online에 대해 관리자 세 명이 세 개씩 동시에 연결하거나 아홉 명의 관리자가 하나씩 연결할 수 있다는 의미입니다. 한 명의 관리자가 세 개 이상의 활성 세션을 가질 수 없다는 점에 유의하세요.

## 참고 항목

#### 개념

[Lync Online 관리를 위한 컴퓨터 구성](configuring-your-computer-for-skype-for-business-online-management.md)

