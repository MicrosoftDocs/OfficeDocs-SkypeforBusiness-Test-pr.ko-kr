---
title: 기존 클라이언트 버전 정책 삭제
TOCTitle: 기존 클라이언트 버전 정책 삭제
ms:assetid: b88aaa25-97ff-4eb6-bd34-b97332cd6890
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ923064(v=OCS.15)
ms:contentKeyID: 52056924
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 기존 클라이언트 버전 정책 삭제

 

_**마지막으로 수정된 항목:** 2013-02-23_

이전에 구성된 클라이언트 버전 정책을 삭제하려는 경우 Lync Server 2013 제어판 또는 Lync Server 2013 관리 셸에서 삭제할 수 있습니다.

## Lync Server 제어판을 사용하여 클라이언트 버전 정책을 삭제하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 표시줄에서 **클라이언트**를 클릭하고 **클라이언트 버전 정책** 탐색 단추를 클릭합니다.

4.  **클라이언트 버전 정책** 페이지에서 삭제할 클라이언트 버전 정책을 선택하고 **편집**, **삭제**를 차례로 클릭합니다.

## Windows PowerShell cmdlet을 사용하여 클라이언트 버전 정책 삭제

**Remove-CsClientVersionPolicy** cmdlet을 사용하여 클라이언트 버전 정책을 삭제할 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 특정 클라이언트 버전 정책을 제거하려면

  - 이 명령은 Redmond 사이트에 적용된 클라이언트 버전 정책을 삭제합니다.
    
        Remove-CsClientVersionPolicy -Identity site:Redmond

## 사이트 범위에 적용된 모든 클라이언트 버전 정책을 제거하려면

  - 이 명령은 사이트 범위에 구성된 모든 클라이언트 버전 정책을 제거합니다.
    
        Get-CsClientVersionPolicy -Fiter "site:*" | Remove-CsClientVersionPolicy

## 특정 사용자 에이전트를 포함하지 않는 클라이언트 버전 정책을 제거하려면

  - 이 명령은 Windows Phone Lync(WPLync) 사용자 에이전트에 대한 규칙을 포함하지 않는 모든 클라이언트 버전 정책을 제거합니다.
    
        Get-CsClientVersionPolicy | Where-Object {$_.Rules -notmatch "UserAgent=WPLync" | Remove-CsClientVersionPolicy

자세한 내용은 [Remove-CsClientVersionPolicy](remove-csclientversionpolicy.md) cmdlet의 도움말 항목을 참조하십시오.

