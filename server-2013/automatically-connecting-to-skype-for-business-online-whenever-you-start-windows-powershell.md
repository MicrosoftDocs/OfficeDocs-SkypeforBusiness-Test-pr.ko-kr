---
title: Windows PowerShell을 시작할 때 자동으로 Lync Online에 연결
TOCTitle: Windows PowerShell을 시작할 때 자동으로 Lync Online에 연결
ms:assetid: 68f76c36-5dd6-48ea-b19a-d65593199e4c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362799(v=OCS.15)
ms:contentKeyID: 56270247
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Windows PowerShell을 시작할 때 자동으로 Lync Online에 연결

 

_**마지막으로 수정된 항목:** 2015-06-22_

비즈니스용 Skype Online 연결에 필요한 모든 명령을 기억할 수 없다면 바로 가기 파일을 두 번 클릭하고 비즈니스용 Skype Online 암호를 입력한 다음 비즈니스용 Skype Online에 연결할 수 있도록 구성하면 됩니다.

이렇게 하려면 먼저 메모장(또는 기타 텍스트 편집기)을 연 후에 다음 명령을 붙여 넣습니다. kenmyer@litwareinc.com은 사용자의 비즈니스용 Skype Online 계정 이름으로 대체합니다.

    $credential = Get-Credential "kenmyer@litwareinc.com"
    $session = New-CsOnlineSession -Credential $credential 
    Import-PSSession $session

.PS1 파일 확장자(예: C:\\Scripts\\LyncOnline.ps1)로 파일을 저장합니다.

파일을 저장하고 다음 절차를 완료하면 바탕 화면 바로 가기가 만들어집니다. 여기서 Windows PowerShell을 시작하여 스크립트를 실행할 수 있습니다.

1.  바탕 화면을 마우스 오른쪽 단추로 클릭하고 **새로 만들기**, **바로 가기**를 클릭합니다.

2.  **바로 가기 만들기** 마법사에서 **항목 위치 입력** 상자에 다음을 입력하고 **다음**을 클릭합니다. 방금 만든 스크립트 파일의 경로를 사용합니다.
    
        powershell.exe -noexit C:\Scripts\LyncOnline.ps1

3.  **바로 가기에 사용할 이름을 입력하십시오.** 상자에서 바로 가기 이름(예: **비즈니스용 Skype Online**)을 입력하고, **완료**를 클릭합니다.

4.  다음에 Windows PowerShell을 사용하여 비즈니스용 Skype Online을 관리하려면 이 새로 만든 바로 가기를 두 번 클릭하고 암호를 입력하면 됩니다. 연결 생성 및 새 원격 세션 설정에 이 스크립트를 사용할 수 있습니다.

일반적으로 이 새로운 세션은 변수 $session에 저장되지 않습니다. 대신, 주로 세션 ID 1을 부여받습니다. 세션 종료 시간에 도달하기 전까지는 사용자의 세션에는 아무런 영향을 주지 않습니다. 이를 위해 **Remove-PSSession** cmdlet을 호출할 때 해당 세션 ID를 참조하세요.

    Remove-PSSession 1

Windows PowerShell 프롬프트에서 이 명령을 실행하여 비즈니스용 Skype Online 세션에 부여된 ID를 확인할 수 있습니다.

    Get-PSSession

## 참고 항목

#### 개념

[Lync Online 관리를 위한 컴퓨터 구성](configuring-your-computer-for-skype-for-business-online-management.md)

