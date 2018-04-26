---
title: Lync Online 커넥터 모듈 다운로드 및 설치
TOCTitle: Lync Online 커넥터 모듈 다운로드 및 설치
ms:assetid: a0c87219-b642-4201-85d4-a85c2163d1eb
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362829(v=OCS.15)
ms:contentKeyID: 56270280
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Online 커넥터 모듈 다운로드 및 설치

 

_**마지막으로 수정된 항목:** 2015-06-22_

비즈니스용 Skype Online Connector 모듈에는 비즈니스용 Skype Online에 연결하는 원격 Windows PowerShell 세션을 만들 수 있는 **New-CsOnlineSession** cmdlet이 포함되어 있습니다. 64비트 컴퓨터에서만 지원되는 이 모듈(자세한 내용은 [Lync Online 관리를 위한 컴퓨터 구성](configuring-your-computer-for-skype-for-business-online-management.md) 참고)은 Microsoft 다운로드 센터([http://go.microsoft.com/fwlink/?LinkId=294688](http://go.microsoft.com/fwlink/?linkid=294688))에서 다운로드할 수 있습니다. LyncOnlinePowershell.exe 파일을 다운로드한 후 다음 절차를 완료합니다.

1.  **LyncOnlinePowershell.exe** 파일을 두 번 클릭합니다.

2.  비즈니스용 Skype Online 테넌트 PowerShell 설치 마법사의 **Microsoft Software License Terms** 페이지에서 **I accept the terms in the License Agreement**을 선택한 다음 **Install**를 클릭합니다. **User Account Control** 대화 상자가 나타나면 **Yes**를 클릭하여 설치를 계속합니다.

3.  **Completed the Microsoft Lync Online, Tenant PowerShell Setup** 페이지에서 **Finish**을 클릭합니다.

설치 프로그램이 비즈니스용 Skype Online Connector 모듈(및 **New-CsOnlineSession** cmdlet)을 사용자의 로컬 컴퓨터로 복사합니다. 모듈에 액세스하려면 관리자 자격 증명으로 Windows PowerShell 세션을 시작하고 다음 명령을 실행합니다.

    Import-Module LyncOnlineConnector

Windows PowerShell을 시작할 때마다 이 명령을 입력하지 않아도 되도록 Windows PowerShell 프로필에 명령을 추가할 수 있습니다. 이렇게 하려면 Windows PowerShell 메시지가 나타날 때 다음 명령을 입력하고 Enter 키를 누릅니다.

    notepad.exe $profile

메모장이 나타나고 프로필에 이미 명령이 있는 경우 명령 맨 아래에 다음 줄을 추가합니다.

    Import-Module LyncOnlineConnector

파일을 저장합니다. 다음에 Windows PowerShell을 시작하면 비즈니스용 Skype Online Connector 모듈을 자동으로 가져옵니다. 관리자 자격 증명으로 Windows PowerShell을 실행하지 않으면 오류 메시지가 나타나고 모듈이 로드되지 않으므로 유의하세요.

LyncOnlinePowershell.exe는 비즈니스용 Skype Online Connector 모듈 설치 외에도 두 개의 추가 구성 요소인 .NET Framework 4.5와 Microsoft Visual C++ 2012 재배포 가능(x64) 패키지(버전 11.0.50727)를 설치합니다. .NET Framework 4.5는 Windows PowerShell을 비롯한 .NET 응용 프로그램을 만들고 실행하는 데 사용되는 인프라를 제공합니다. Visual C++ 재배포 가능 패키지는 Microsoft Visual Studio 2012가 설치되어 있지 않은 컴퓨터를 위해 Visual C++ 런타임 구성 요소를 설치합니다.

## 참고 항목

#### 개념

[Lync Online 관리를 위한 컴퓨터 구성](configuring-your-computer-for-skype-for-business-online-management.md)

