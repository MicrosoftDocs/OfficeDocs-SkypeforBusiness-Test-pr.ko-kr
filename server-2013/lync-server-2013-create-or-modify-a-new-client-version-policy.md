---
title: 새 클라이언트 버전 정책 만들기 또는 수정
TOCTitle: 새 클라이언트 버전 정책 만들기 또는 수정
ms:assetid: 4be6e449-aa82-4b46-abb1-d31281573a72
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ898476(v=OCS.15)
ms:contentKeyID: 52056834
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 새 클라이언트 버전 정책 만들기 또는 수정

 

_**마지막으로 수정된 항목:** 2013-02-23_

클라이언트 버전 정책을 사용하여 환경에서 지원되는 클라이언트 버전을 지정할 수 있습니다. 클라이언트 버전을 사용하면 여러 클라이언트 버전 지원과 관련된 비용을 줄일 수 있습니다. 또한 이전 버전 및 최신 버전의 클라이언트가 상호 작용하면 이전 버전 클라이언트를 기준으로 하여 사용 가능한 기능을 제한할 수 있으므로 전반적인 사용자 환경도 개선됩니다. Lync Server 2013 제어판 또는 Lync Server 2013 관리 셸에서 클라이언트 버전 정책을 만들거나 수정할 수 있습니다.

## Lync Server 제어판을 사용하여 클라이언트 버전 정책을 만들거나 수정하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 표시줄에서 **클라이언트**를 클릭합니다.
    

    > [!NOTE]
    > <STRONG>클라이언트 버전 정책</STRONG> 탭이 기본적으로 선택되어 있습니다.



4.  **클라이언트 버전 정책** 페이지에서 다음 중 하나를 수행합니다.
    
      - 클라이언트 버전 정책을 만들려면 **새로 만들기**를 클릭하고 **사이트 정책**, **풀 정책** 또는 **사용자 정책**을 선택한 후에 **확인**을 클릭합니다.
    
      - 전역 정책 또는 다른 기존 클라이언트 버전 정책을 수정하려면 해당 정책을 선택하고 **편집**, **세부 정보 표시**를 차례로 클릭합니다.

5.  **클라이언트 버전 정책 편집** 페이지에서 [새 클라이언트 버전 정책 규칙 만들기 또는 수정](lync-server-2013-create-or-modify-a-new-client-version-policy-rule.md)의 설명에 따라 규칙을 만들거나 수정합니다.

## Windows PowerShell cmdlet을 사용하여 클라이언트 버전 정책 만들기 또는 수정

**New-CsClientVersionPolicy** cmdlet을 사용하여 클라이언트 버전 정책을 만들고 **set-csclientversionpolicy** cmdlet을 사용하여 정책을 수정할 수 있습니다. 이러한 cmdlet은 Lync Server 2013 관리 셸Windows PowerShell 또는 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.의 원격 세션에서 실행할 수 있습니다.

## 새 사이트 범위 클라이언트 버전 정책을 만들려면

  - 다음 명령은 Redmond 사이트에 적용되는 새 클라이언트 버전 정책을 만듭니다. 추가 매개 변수가 지정되지 않으므로 새 정책은 기본 클라이언트 버전 설정을 사용합니다.
    
        New-CsClientVersionPolicy -Identity "site:Redmond"

## 새 사용자별 클라이언트 버전 정책을 만들려면

  - 사용자별 정책을 만들려면 다음과 같은 명령을 사용합니다.
    
        New-CsClientVersionPolicy -Identity "RedmondClientVersionPolicy"

자세한 내용은 [New-CsClientVersionPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsClientVersionPolicy) cmdlet 및 [set-csclientversionpolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsClientVersionPolicy) cmdlet의 도움말 항목을 참조하십시오.

