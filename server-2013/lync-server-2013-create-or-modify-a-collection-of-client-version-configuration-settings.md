---
title: 클라이언트 버전 구성 설정 모음 만들기 또는 수정
TOCTitle: 클라이언트 버전 구성 설정 모음 만들기 또는 수정
ms:assetid: 4e6faffd-a36f-40f1-8734-78d84b7df921
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ898477(v=OCS.15)
ms:contentKeyID: 52056837
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 클라이언트 버전 구성 설정 모음 만들기 또는 수정

 

_**마지막으로 수정된 항목:** 2013-02-23_

클라이언트 버전 구성 설정은 클라이언트 버전 제어를 설정하거나 해제하는 데 사용됩니다. 전역 클라이언트 버전 구성은 Lync Server와 함께 설치되며 전체 서버 배포에 대해 클라이언트 버전 제어를 사용하거나 사용하지 않도록 설정하는 데 사용됩니다. 개별 사이트에 대해 클라이언트 버전 구성 설정을 구성할 수도 있습니다. Lync Server 2013 제어판 또는 Lync Server 2013 관리 셸에서 클라이언트 버전 구성 설정을 만들거나 수정할 수 있습니다.


> [!NOTE]
> 익명 사용자는 사용자, 사이트 또는 서비스와 연결되지 않으므로 전역 수준 정책에만 영향을 받습니다.



## Lync Server 제어판을 사용하여 클라이언트 버전 구성 설정을 만들거나 수정하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 표시줄에서 **클라이언트**를 클릭하고 **클라이언트 버전 구성** 탐색 단추를 클릭합니다.

4.  **클라이언트 버전 구성** 페이지에서 다음을 수행합니다.
    
      - 새 구성을 만들려면 **새로 만들기**를 클릭하고 사이트를 선택한 다음 **확인**을 클릭하여 설정을 업데이트합니다.
    
      - 구성을 수정하려면 해당 구성을 선택하고 **편집**, **세부 정보 표시**를 차례로 클릭한 후에 설정을 변경합니다.

## Windows PowerShell cmdlet을 사용하여 클라이언트 버전 구성 설정 만들기 또는 수정

**New-CsClientVersionConfiguration** cmdlet을 사용하여 클라이언트 버전 구성 설정을 만들고 **Set-CsClientVersionConfiguration** cmdlet을 사용하여 설정을 수정할 수 있습니다. 이러한 cmdlet은 Lync Server 2013 관리 셸Windows PowerShell 또는 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.의 원격 세션에서 실행할 수 있습니다.

## 클라이언트 버전 구성 설정의 새 컬렉션을 만들려면

  - 다음 명령은 Redmond 사이트에 적용되는 클라이언트 버전 구성 설정 컬렉션을 새로 만듭니다. 이 예제에서는 Redmond 사이트에 대해 클라이언트 버전이 사용하지 않도록 설정됩니다.
    
        New-CsClientVersionConfiguration -Identity "site:Redmond" -Enabled $False

## 사이트에 대해 클라이언트 버전을 사용하도록 설정하려면

  - 다음 명령은 Redmond 사이트에 대한 클라이언트 버전을 사용하도록 설정합니다.
    
        Set-CsClientVersionConfiguration -Identity "site:Redmond" -Enabled $True

## 조직 전체에서 클라이언트 버전을 사용하지 않도록 설정하려면

  - 이 예에서는 조직에서 사용 중인 모든 클라이언트 버전 구성 설정에 대해 클라이언트 버전이 사용하지 않도록 설정됩니다.
    
        Get-CsClientVersionConfiguration | Set-CsClientVersionConfiguration  -Enabled $False

자세한 내용은 [New-CsClientVersionConfiguration](new-csclientversionconfiguration.md) 및 [Set-CsClientVersionConfiguration](set-csclientversionconfiguration.md) cmdlet의 도움말 항목을 참조하십시오.

