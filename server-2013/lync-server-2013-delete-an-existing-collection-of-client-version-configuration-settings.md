---
title: 기존 클라이언트 버전 구성 설정 모음 삭제
TOCTitle: 기존 클라이언트 버전 구성 설정 모음 삭제
ms:assetid: 70bf1216-d0d2-45ce-881f-b8edadf3cec7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ898480(v=OCS.15)
ms:contentKeyID: 52056875
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 기존 클라이언트 버전 구성 설정 모음 삭제

 

_**마지막으로 수정된 항목:** 2013-02-23_

이전에 사이트에 대해 구성된 클라이언트 구성 설정을 제거하려는 경우 Lync Server 2013 제어판 또는 Lync Server 2013 관리 셸에서 해당 설정을 제거할 수 있습니다.

## Lync Server 제어판을 사용하여 클라이언트 구성 설정을 제거하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 표시줄에서 **클라이언트**를 클릭하고 **클라이언트 버전 구성** 탐색 단추를 클릭합니다.

4.  사이트를 선택하고 **편집**, **삭제**, **확인**을 차례로 클릭합니다.

## Windows PowerShell cmdlet을 사용하여 클라이언트 버전 구성 설정 제거

**Remove-CsClientVersionConfiguration** cmdlet을 사용하여 클라이언트 버전 구성 설정을 삭제할 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 클라이언트 버전 구성 설정의 지정된 컬렉션을 제거하려면

  - 다음 명령은 Redmond 사이트에 적용된 클라이언트 버전 구성 설정을 제거합니다.
    
        Remove-CsClientVersionConfiguration -Identity "site:Redmond"

## 사이트 범위에 적용된 모든 클라이언트 버전 구성 설정을 제거하려면

  - 이 명령은 사이트 범위에 구성된 모든 클라이언트 버전 구성 설정을 제거합니다.
    
        Get-CsClientVersionConfiguration -Filter site:* | Remove-CsClientVersionConfiguration

## DefaultAction 속성의 값에 따라 모든 클라이언트 버전 구성 설정을 제거하려면

  - 이 명령은 기본 작업이 "Block"으로 설정된 모든 클라이언트 버전 구성 설정을 제거합니다.
    
        Get-CsClientVersionConfiguration | Where-Object {$_.DefaultAction -eq "Block" | Remove-CsClientVersionConfiguration

자세한 내용은 [Remove-CsClientVersionConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsClientVersionConfiguration) cmdlet의 도움말 항목을 참조하십시오.

