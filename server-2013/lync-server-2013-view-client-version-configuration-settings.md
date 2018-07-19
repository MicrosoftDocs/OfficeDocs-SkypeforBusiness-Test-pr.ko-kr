---
title: 클라이언트 버전 구성 설정 보기
TOCTitle: 클라이언트 버전 구성 설정 보기
ms:assetid: c72df4e6-a889-4cb6-86f7-8334d7774c6e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ923062(v=OCS.15)
ms:contentKeyID: 52056956
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 클라이언트 버전 구성 설정 보기

 

_**마지막으로 수정된 항목:** 2013-02-23_

클라이언트 버전 구성 설정은 클라이언트 버전 제어를 설정하거나 해제하는 데 사용됩니다. 전역 클라이언트 버전 구성은 Lync Server 2013과 함께 설치되며 전체 서버 배포에 대해 클라이언트 버전 제어를 사용하거나 사용하지 않도록 설정하는 데 사용됩니다. 전역 구성을 사용하도록 설정하면 포함되어 있는 모든 클라이언트 버전 정책이 사용자의 로그온 시도 시 적용됩니다. Lync Server 2013 제어판 또는 Lync Server 2013 관리 셸에서 클라이언트 버전 구성 설정을 확인할 수 있습니다.


> [!NOTE]
> 익명 사용자는 사용자, 사이트 또는 서비스와 연결되지 않으므로 전역 수준 정책에만 영향을 받습니다.



## Lync Server 제어판을 사용하여 클라이언트 버전 구성 설정을 보려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 표시줄에서 **클라이언트**를 클릭하고 **클라이언트 버전 구성** 탐색 단추를 클릭합니다.

4.  보려는 클라이언트 버전 구성의 이름을 두 번 클릭합니다.

## Windows PowerShell cmdlet을 사용하여 클라이언트 버전 구성 설정 보기

**Get-CsClientVersionConfiguration** cmdlet을 사용하여 클라이언트 버전 구성 설정을 볼 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 클라이언트 버전 구성 정보를 보려면

  - 모든 클라이언트 버전 구성 설정에 대한 정보를 보려면 Lync Server 관리 셸에 다음 명령을 입력한 후 Enter 키를 누릅니다.
    
        Get-CsClientVersionConfiguration
    
    그러면 다음과 같은 정보가 반환됩니다.
    
        Identity      : Global
        DefaultAction : Allow
        DefaultURL    :
        Enabled       : True

자세한 내용은 [Get-CsClientVersionConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsClientVersionConfiguration) cmdlet의 도움말 항목을 참조하십시오.

