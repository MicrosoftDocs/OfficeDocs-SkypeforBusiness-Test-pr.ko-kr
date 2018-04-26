---
title: 'Lync Online: Windows PowerShell 3.0 다운로드 및 설치'
TOCTitle: Windows PowerShell 3.0 다운로드 및 설치
ms:assetid: 39ae065d-02d7-4ce3-9e6f-6ad550a1777e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362783(v=OCS.15)
ms:contentKeyID: 56270225
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Online에서 Windows PowerShell 3.0 다운로드 및 설치

 

_**마지막으로 수정된 항목:** 2015-06-22_

Windows Server 2012, Windows Server 2012 R2, Windows 8 또는 Windows 8.1을 사용하는 경우 Windows PowerShell 3.0이 이미 있을 것입니다. 이 응용 프로그램은 해당 운영 체제에서 미리 설치하여 제공되기 때문입니다.

Windows 7 또는 Windows Server 2008 R2를 실행하는 경우 Windows PowerShell 3.0도 실행 중일 수 있습니다. 하지만 3.0 버전 대신 원래 해당 운영 체제에서 제공되는 2.0 버전을 실행 중일 수도 있습니다. 사용 중인 Windows PowerShell의 버전을 확인하려면 Windows 7 또는 Windows Server 2008 R2 컴퓨터에서 다음을 실행합니다.

1.  **시작**, 모든 프로그램, **보조프로그램**, **Windows PowerShell**을 차례로 클릭한 다음 **Windows PowerShell**을 클릭합니다.

2.  Windows PowerShell 콘솔에 다음 명령을 입력한 다음 Enter 키를 누릅니다.
    
        Get-Host | Select-Object Version

3.  그러면 콘솔 창에 다음과 같은 정보가 표시됩니다.
    
        Version
        -------
        3.0

반환된 버전 번호가 3.0인 경우 Windows PowerShell 3.0을 실행 중인 것입니다. 반환된 버전 번호가 3.0이 아닌 경우에는 Windows PowerShell 3.0을 설치해야 합니다. [Microsoft 다운로드 센터](http://www.microsoft.com/en-us/download/details.aspx?id=34595)에서 Windows PowerShell 3.0이 포함된 Windows Management Framework 3.0을 다운로드할 수 있습니다.

Windows PowerShell 3.0이 설치되어 있는지 확인한 후에는 원격 스크립트를 실행할 수 있도록 Windows PowerShell이 구성되어 있는지 확인해야 합니다. 이 작업을 수행하려면 관리자로 Windows PowerShell을 시작합니다. Windows 7, Windows Server 2008 R2, Windows Server 2012 또는 Windows Server 2012 R2의 경우 다음을 수행하세요.

1.  **시작**, **모든 프로그램**, **보조프로그램**, **Windows PowerShell**을 차례로 클릭하고 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.

2.  **사용자 계정 컨트롤** 대화 상자가 나타나면 **예**를 클릭하여 관리자 자격 증명으로 Windows PowerShell을 실행할지 확인합니다.

Windows 8을 실행하는 경우에는 대신 다음 절차를 완료합니다.

1.  아이콘 모음에 액세스하고 **검색**을 클릭한 다음 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭합니다. 터치 스크린이든 터치 스크린이 아니든 모든 Windows 8 컴퓨터에서 Windows 키를 누른 상태에서 C 키를 눌러 아이콘 모음에 빠르게 액세스할 수 있습니다.

2.  화면 아래쪽의 도구 모음에서 **관리자 권한으로 실행**을 클릭합니다.

3.  **사용자 계정 컨트롤** 대화 상자가 나타나면 **예**를 클릭하여 관리자 자격 증명으로 Windows PowerShell을 실행할지 확인합니다.

Windows PowerShell이 실행된 후에는 원격 스크립트 실행을 허용하도록 실행 정책을 변경해야 합니다. Windows PowerShell 콘솔에 다음 명령을 입력하고 Enter 키를 누릅니다.

    Set-ExecutionPolicy RemoteSigned -Force


> [!NOTE]
> 위의 명령을 실행하면 다음 오류 메시지가 표시될 수도 있습니다.<BR>Set-ExecutionPolicy: 레지스트리 키 'HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Micrsoft.PowerShell'에 대한 액세스가 거부되었습니다.<BR>이 오류 메시지는 일반적으로 관리자 자격 증명으로 Windows PowerShell을 실행하지 않은 경우에 발생합니다. Windows PowerShell 세션을 닫고 관리자로 새로운 세션을 시작합니다.



실행 정책이 올바르게 구성되었는지 확인하려면 Windows PowerShell 프롬프트에 다음을 입력한 다음 Enter 키를 누릅니다.

    Get-ExecutionPolicy

다음 값이 반환되면 모든 항목이 올바르게 구성된 것입니다.

    RemoteSigned

현재 Windows PowerShell 3.0을 실행하고 있지 않은 경우 Microsoft 다운로드 센터에서 Windows Management Framework 3.0도 다운로드하고 설치해야 합니다. 이는 Windows PowerShell 3.0 및 WinRM(Windows Remote Management) 3.0을 포함하는 설치 패키지입니다. Windows 7을 실행 중이며 아직 Windows PowerShell 3.0으로 업데이트하지 않은 경우 이 설치 패키지가 필요할 수도 있습니다. Windows Server 2012, Windows Server 2012 R2, Windows 8 또는 Windows 8.1을 실행 중이라면 Windows PowerShell 3.0을 설치하지 않아도 됩니다. Windows PowerShell 3.0은 해당 운영 체제에서 미리 설치하여 제공됩니다.

Windows Management Framework 3.0을 설치하기 전에 다음을 수행합니다.

  - 올바른 버전의 설치 패키지를 다운로드했는지 확인합니다. 64비트 버전의 Windows 7을 실행 중이라면 Windows6.1-KB2506143-x64.msu 파일을 다운로드합니다. 32비트 버전의 Windows 7을 실행 중이라면 Windows6.1-KB2506143-x86.msu 파일을 다운로드합니다.

  - 컴퓨터에서 Windows 7을 실행 중인 경우 Windows 7 서비스 팩 1을 설치했는지 확인합니다.

실행 중인 Windows의 버전을 모르는 경우 또는 Windows 7 서비스 팩 1 설치 여부를 모르는 경우에는 **시작**을 클릭하고 **컴퓨터**를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다. 이 정보는 시스템 대화 상자에 나타납니다.

![설정을 보여 주는 시스템 대화 상자](images/Dn362783.30bff2e8-2862-4dd7-828f-43732f4b9314(OCS.15).png "설정을 보여 주는 시스템 대화 상자")

Windows Management Framework 3.0을 설치하려면 다음 절차를 완료합니다.

1.  .MSU 설치 파일( **Windows6.1-KB2506143-x64.msu** 또는 **Windows6.1-KB2506143-x86.msu**)을 두 번 클릭합니다.

2.  업데이트 다운로드 및 설치 마법사의 **이 사용 약관 읽기(1/1)** 페이지에서 **동의함**을 클릭합니다.

3.  설치가 완료되면 **지금 다시 시작**을 클릭하여 컴퓨터를 다시 시작합니다.

컴퓨터가 다시 부팅되고 나면 Windows PowerShell을 시작할 수 있고 관리자 자격 증명으로 이 프로그램을 실행할 수 있는지 확인합니다. 이를 위해서는 다음을 수행합니다.

1.  **시작**, **모든 프로그램**, **보조프로그램**, **Windows PowerShell**을 차례로 클릭하고 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 클릭합니다.

2.  사용자 계정 컨트롤 대화 상자가 나타나면 **예**를 클릭하여 관리자 자격 증명으로 Windows PowerShell을 실행할지 확인합니다.

Windows PowerShell 콘솔이 나타나면 WinRM 서비스가 실행되고 올바르게 구성되었는지 확인합니다. 서비스가 실행되고 있는지 확인하려면 Windows PowerShell 프롬프트에 다음 명령을 입력한 다음 Enter 키를 누릅니다.

    Get-Service winrm

그러면 WinRM 서비스 정보가 화면에 표시됩니다.

    Status   Name               DisplayName
    ------   ----               -----------
    Running  winrm              Windows Remote Management (WS-Manag...

서비스의 Status가 "Running"이 아닌 경우 다음 명령을 입력한 다음 Enter 키를 눌러 WinRM 서비스를 시작합니다.

    Start-Service winrm

서비스가 시작되면 다음 명령을 실행하여 WinRM에서 기본 인증을 사용하고 있는지 확인합니다.

    winrm set winrm/config/client/auth '@{Basic="True"}'

화면에 다음과 같은 정보가 표시됩니다.

    Auth
        Basic = true
        Digest = true
        Kerberos = true
        Negotiate = true
        Certificate = true
        CredSSP = false

기본 인증이 true로 설정된 경우에는 Windows PowerShell을 사용하여 비즈니스용 Skype Online에 연결할 수 있습니다.

