---
title: 사용자 계정에서 Lync Server를 사용하거나 사용하지 않도록 설정
TOCTitle: 사용자 계정에서 Lync Server를 사용하거나 사용하지 않도록 설정
ms:assetid: 12497d00-f665-4a97-be68-854c5a8be4fc
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg429696(v=OCS.15)
ms:contentKeyID: 49302864
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 사용자 계정에서 Lync Server를 사용하거나 사용하지 않도록 설정

 

_**마지막으로 수정된 항목:** 2013-02-22_

다음 절차에 따라 사용자 계정에 대해 구성한 Lync Server 설정은 그대로 유지하면서 Lync Server 2013에서 이전에 사용하도록 설정한 사용자 계정을 사용하지 않도록 설정할 수 있습니다. Lync Server 사용자 계정 설정은 그대로 유지되므로, 사용자 계정을 다시 구성하지 않아도 이전에 사용하도록 설정한 사용자 계정을 다시 사용하도록 설정할 수 있습니다.

## Lync Server에 대해 이전에 사용하도록 설정한 사용자 계정을 사용하지 않도록 설정하거나 다시 사용하도록 설정하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **사용자**를 클릭합니다.

4.  **사용자 검색** 상자에 사용하지 않도록 설정하거나 다시 사용하도록 설정할 사용자 계정의 표시 이름, 이름, 성, SAM(보안 계정 관리자) 계정 이름, SIP 주소 또는 줄 URI(Uniform Resource Identifier)를 모두 또는 첫 부분을 입력하고 **찾기**를 클릭합니다.

5.  표에서 사용하지 않도록 설정하거나 다시 사용하도록 설정할 사용자 계정을 클릭합니다.

6.  **동작** 메뉴에서 다음 중 하나를 수행합니다.
    
      - Lync Server 2013에 대해 사용자 계정을 일시적으로 사용하지 않도록 설정하려면 **Lync Server에 일시적으로 사용 안 함**을 클릭합니다.
    
      - Lync Server 2013에 대해 사용자 계정을 사용하도록 설정하려면 **Lync Server에 다시 사용**을 클릭합니다.

## Windows PowerShell cmdlet을 사용하여 사용자 계정을 사용하지 않도록 설정 및 다시 사용하도록 설정

**Set-CsUser** cmdlet을 사용하면 사용자 계정을 일시적으로 사용하지 않도록 설정했다가 나중에 다시 사용하도록 설정할 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 사용자 계정을 사용하지 않도록 설정

  - 사용자 계정을 일시적으로 사용하지 않도록 설정하려면 Enabled 속성의 값을 False($False)로 설정합니다. 예를 들면 다음과 같습니다.
    
        Set-CsUser -Identity "Ken Myer" -Enabled $False

## 사용자 계정을 다시 사용하도록 설정

  - 사용하지 않도록 설정된 사용자 계정을 다시 사용하도록 설정하려면 Enabled 속성의 값을 True($True)로 설정합니다. 예를 들면 다음과 같습니다.
    
        Set-CsUser -Identity "Ken Myer" -Enabled $True

자세한 내용은 [Set-CsUser](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsUser) cmdlet에 대한 도움말 항목을 참조하십시오.

## 참고 항목

#### 작업

[Lync Server에 사용자 계정 추가 및 사용](lync-server-2013-add-and-enable-user-account-for-lync-server.md)  

#### 기타 리소스

[Lync Server 2013에 사용자 사용 또는 사용 안 함](lync-server-2013-enabling-and-disabling-users-for-lync-server.md)

