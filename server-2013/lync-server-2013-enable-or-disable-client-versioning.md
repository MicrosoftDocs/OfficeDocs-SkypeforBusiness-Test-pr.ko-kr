---
title: 클라이언트 버전을 사용하거나 사용하지 않도록 설정
TOCTitle: 클라이언트 버전을 사용하거나 사용하지 않도록 설정
ms:assetid: 33a98cb9-a979-4bb6-afb2-512f601d7ac5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ898475(v=OCS.15)
ms:contentKeyID: 52056818
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 클라이언트 버전을 사용하거나 사용하지 않도록 설정

 

_**마지막으로 수정된 항목:** 2013-02-23_

클라이언트 버전 구성 설정은 전역적으로 또는 특정 사이트에 대해 클라이언트 버전 제어를 설정하거나 해제하는 데 사용됩니다. 전역 클라이언트 버전 구성은 Lync Server 2013과 함께 설치되며 전체 서버 배포에 대해 클라이언트 버전 제어를 사용하거나 사용하지 않도록 설정하는 데 사용됩니다. 전역 구성을 사용하도록 설정하면 포함되어 있는 모든 클라이언트 버전 정책이 사용자의 로그온 시도 시 적용됩니다. 클라이언트 버전 제어를 수행하지 않으려면 전역 클라이언트 버전 구성을 사용하지 않도록 설정하면 됩니다. Lync Server 2013 제어판 또는 Lync Server 2013 관리 셸에서 클라이언트 버전을 사용하거나 사용하지 않도록 설정할 수 있습니다.


> [!NOTE]
> 익명 사용자는 사용자, 사이트 또는 서비스와 연결되지 않으므로 전역 수준 정책에만 영향을 받습니다.



## Lync Server 제어판을 사용하여 클라이언트 버전을 사용하거나 사용하지 않도록 설정하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 표시줄에서 **클라이언트**를 클릭하고 **클라이언트 버전 구성** 탐색 단추를 클릭합니다.

4.  다음을 수행합니다.
    
      - 클라이언트 버전을 전역적으로 사용하거나 사용하지 않도록 설정하려면 **전역** 구성을 두 번 클릭하고 설정을 수정합니다.
    
      - 특정 사이트에 대해 클라이언트 버전을 사용하거나 사용하지 않도록 설정하려면 **새로 만들기**를 클릭하고 사이트를 선택한 다음 **확인**을 클릭하고 사이트의 설정을 수정합니다.

## Windows PowerShell cmdlet을 사용하여 클라이언트 버전을 사용하거나 사용하지 않도록 설정

**Set-CsClientVersionConfiguration** cmdlet을 사용하여 클라이언트 버전을 사용하거나 사용하지 않도록 설정할 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 클라이언트 버전을 사용하도록 설정하려면

  - **Enabled** 속성을 True($True)로 설정하여 클라이언트 버전을 사용하도록 설정할 수 있습니다.
    
        Set-CsClientVersionConfiguration -Identity "site:Redmond" -Enabled $True

## 클라이언트 버전을 사용하지 않도록 설정하려면

  - **Enabled** 속성을 False($False)로 설정하여 클라이언트 버전을 사용하지 않도록 설정할 수 있습니다.
    
        Set-CsClientVersionConfiguration -Identity "site:Redmond" -Enabled $True

자세한 내용은 [Set-CsClientVersionConfiguration](set-csclientversionconfiguration.md) cmdlet의 도움말 항목을 참조하십시오.

