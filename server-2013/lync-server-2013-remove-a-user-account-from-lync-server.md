---
title: Lync Server에서 사용자 계정 제거
TOCTitle: Lync Server에서 사용자 계정 제거
ms:assetid: 2f512aba-e358-45ae-af58-74312ee9c514
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688008(v=OCS.15)
ms:contentKeyID: 49885702
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server에서 사용자 계정 제거

 

_**마지막으로 수정된 항목:** 2013-02-22_

다음 절차에 따라 이전에 추가한 사용자 계정을 Lync Server 2013에서 제거할 수 있습니다.


> [!NOTE]
> 사용자를 제거하면 사용자 계정에 대해 구성한 모든 설정이 손실됩니다. 사용자 계정을 제거하는 대신 일시적으로 사용하지 않도록 설정하려면 <A href="lync-server-2013-disable-or-re-enable-user-account-for-lync-server.md">사용자 계정에서 Lync Server를 사용하거나 사용하지 않도록 설정</A> 항목을 참조하십시오.



## Lync Server에서 Lync Server 사용자 계정을 제거하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **사용자**를 클릭합니다.

4.  **사용자 검색** 상자에 사용하지 않도록 설정하거나 다시 사용하도록 설정할 사용자 계정의 표시 이름, 이름, 성, SAM(보안 계정 관리자) 계정 이름, SIP 주소 또는 줄 URI(Uniform Resource Identifier)를 모두 또는 첫 부분을 입력하고 **찾기**를 클릭합니다.

5.  표에서 제거할 사용자 계정을 클릭합니다.

6.  **동작** 메뉴에서 **Lync Server에서 제거**를 선택하면 대화 상자가 나타납니다.

7.  대화 상자에서 **확인**을 선택하여 사용자를 제거합니다.

## Lync Server PowerShell cmdlet을 사용하여 사용자 계정 제거

Disable-CsUser cmdlet을 사용하여 사용자 계정을 제거할 수도 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 사용자 계정 제거

  - 사용자 계정을 제거하려면 Disable-CsUser cmdlet을 사용합니다. 예를 들면 다음과 같습니다.
    
        Disable-CsUser -Identity "Ken Myer"
    
    이 명령을 실행한 후에는 계정 및 이전 설정을 다시 사용하도록 설정할 수 없습니다. 대신 Enable-CsUser cmdlet을 사용하여 Ken Myer에 대해 새 계정을 만들어야 합니다.

자세한 내용은 [Disable-CsUser](https://docs.microsoft.com/en-us/powershell/module/skype/Disable-CsUser) cmdlet에 대한 도움말 항목을 참조하십시오.

## 참고 항목

#### 작업

[사용자 계정에서 Lync Server를 사용하거나 사용하지 않도록 설정](lync-server-2013-disable-or-re-enable-user-account-for-lync-server.md)  

#### 기타 리소스

[Lync Server 2013에 사용자 사용 또는 사용 안 함](lync-server-2013-enabling-and-disabling-users-for-lync-server.md)

