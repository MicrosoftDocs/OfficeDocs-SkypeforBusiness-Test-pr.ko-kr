---
title: 클라이언트 버전 정책 규칙 보기
TOCTitle: 클라이언트 버전 정책 규칙 보기
ms:assetid: f3a0215f-f72f-4e9b-a07b-25858dc4203a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ923060(v=OCS.15)
ms:contentKeyID: 52056998
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 클라이언트 버전 정책 규칙 보기

 

_**마지막으로 수정된 항목:** 2013-02-23_

클라이언트 버전 정책은 클라이언트 버전 정책 규칙 집합으로 구성됩니다. 이러한 규칙은 사용자가 특정 클라이언트 및 클라이언트 버전을 사용하여 로그온을 시도할 때 수행할 동작을 정의합니다. Lync Server 2013 제어판 및 Lync Server 2013 관리 셸에서 클라이언트 버전 정책 규칙을 볼 수 있습니다.

## Lync Server 제어판을 사용하여 클라이언트 버전 정책 규칙을 보려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 표시줄에서 **클라이언트**를 클릭하고 **클라이언트 버전 정책** 탐색 단추를 클릭합니다.

4.  **클라이언트 버전 정책** 페이지에서 보려는 클라이언트 버전 정책을 두 번 클릭합니다.

5.  규칙이 **클라이언트 버전 정책 편집** 페이지에 나타납니다. 규칙의 세부 정보를 보려면 해당 규칙을 선택하고 **자세한 정보 표시**를 클릭합니다.

## Windows PowerShell cmdlet을 사용하여 클라이언트 버전 정책 규칙 보기

또한 Lync Server 관리 셸 및 **Get-CsClientVersionPolicyRule** cmdlet을 사용하여 클라이언트 버전 정책 규칙을 볼 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 클라이언트 버전 정책 규칙을 보려면

  - 클라이언트 버전 정책 규칙을 보려면 Lync Server 관리 셸에서 다음 명령을 입력하고 Enter 키를 누릅니다.
    
        Get-CsClientVersionPolicyRule
    
    그러면 구성된 각 규칙에 대해 다음과 같은 정보가 반환됩니다.
    
        Identity          : Global/2336c611-a243-4c5d-994b-eea8a524d0e4
        Priority          : 0
        RuleId            : 2336c611-a243-4c5d-994b-eea8a524d0e4
        Description       :
        Action            : Block
        ActionUrl         :
        MajorVersion      : 1
        MinorVersion      : 3
        BuildNumber       :
        QfeNumber         :
        UserAgent         : RTC
        UserAgentFullName :
        Enabled           : True
        CompareOp         : LEQ

자세한 내용은 [Get-CsClientVersionPolicyRule](get-csclientversionpolicyrule.md) cmdlet의 도움말 항목을 참조하십시오.

