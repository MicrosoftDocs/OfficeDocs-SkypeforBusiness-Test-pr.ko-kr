---
title: 기존 모임 구성 설정 모음 삭제
TOCTitle: 기존 모임 구성 설정 모음 삭제
ms:assetid: 92ff8a91-05c5-4047-a533-5dff12f22299
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688136(v=OCS.15)
ms:contentKeyID: 49885873
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 기존 모임 구성 설정 모음 삭제

 

_**마지막으로 수정된 항목:** 2013-02-23_

사이트 구성 또는 사용자 구성은 삭제할 수 있습니다. 전역 정책은 제거할 수 없습니다. 전역 구성을 삭제하는 경우 자동으로 구성이 기본값으로 다시 설정됩니다.

## 사이트 또는 사용자 모임 구성을 삭제하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 표시줄에서 **회의**, **모임 구성**을 차례로 클릭합니다.

4.  모임 구성 목록에서 삭제할 사이트 또는 풀 구성을 클릭하고 편집을 클릭한 다음 삭제를 클릭합니다.

## Lync Server PowerShell cmdlet을 사용하여 모임 구성 설정 제거

Windows PowerShell 및 Remove-CsMeetingConfiguration cmdlet을 사용하여 모임 설정을 삭제할 수도 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 모임 구성 설정의 지정된 컬렉션 제거

  - 다음 명령은 Redmond 사이트에 적용된 모임 구성 설정을 제거합니다.
    
        Remove-CsMeetingConfiguration -Identity "site:Redmond"

## 사이트 범위에 적용된 모든 모임 구성 설정 제거

  - 다음 명령은 사이트 범위에 적용된 모든 모임 구성 설정을 제거합니다.
    
        Get-CsMeetingConfiguration -Filter "site:*" | Remove-CsMeetingConfiguration

## 기본적으로 익명 사용자를 승인하는 모든 모임 구성 설정 제거

  - 그리고 다음 명령은 기본적으로 익명 사용자가 승인되도록 허용하는 모든 설정을 제거합니다.
    
        Get-CsMeetingConfiguration | Where-Object {$_.AdmitAnonymousUsersByDefault -eq $True} | Remove-CsMeetingConfiguration

자세한 내용은 [Remove-CsMeetingConfiguration](remove-csmeetingconfiguration.md) cmdlet에 대한 도움말 항목을 참조하십시오.

