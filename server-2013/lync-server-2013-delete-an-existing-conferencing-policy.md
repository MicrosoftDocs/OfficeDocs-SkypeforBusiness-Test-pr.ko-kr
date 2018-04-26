---
title: 기존 회의 정책 삭제
TOCTitle: 기존 회의 정책 삭제
ms:assetid: 709ed771-790f-4bf1-a4de-b37ca5168688
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688089(v=OCS.15)
ms:contentKeyID: 49885806
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 기존 회의 정책 삭제

 

_**마지막으로 수정된 항목:** 2013-02-23_

사용자 수준 또는 사이트 수준 회의 정책을 삭제하려면 다음 단계를 수행합니다.


> [!NOTE]
> 전역 회의 정책은 삭제할 수 없습니다.



## 사이트 또는 사용자 회의 정책을 삭제하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **회의**를 클릭하고 **회의 정책**을 클릭합니다.

4.  회의 정책 목록에서 삭제하려는 사이트 또는 사용자 정책을 클릭하고, 편집을 클릭한 후 삭제를 클릭합니다.

## Lync Server 관리 셸 Cmdlet을 사용하여 회의 정책 제거

Lync Server 관리 셸 및 **Remove-CsConferencingPolicy** cmdlet을 사용하여 트렁크 구성 설정을 삭제할 수도 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 지정된 회의 정책을 제거하려면

  - 다음 명령은 ID RedmondConferencingPolicy가 포함된 회의 정책을 제거합니다.
    
        Remove-CsConferencingPolicy -Identity "RedmondConferencingPolicy"

## 사용자별 범위에 적용된 모든 회의 정책을 제거하려면

  - 다음 명령은 사용자별 범위에 구성된 모든 회의 정책을 제거합니다.
    
        Get-CsConferencingPolicy -Filter "tag:*" | Remove-CsConferencingPolicy

## 외부 사용자의 기록을 허용하는 모든 회의 정책을 제거하려면

  - 다음 명령은 외부 사용자가 회의를 기록하도록 허용하는 모든 회의 정책을 삭제합니다.
    
        Get-CsConferencingPolicy | Where-Object {$_.AllowExternalUsersToRecordMeetings -eq $True} | Remove-CsConferencingPolicy

자세한 내용은 [Remove-CsConferencingPolicy](remove-csconferencingpolicy.md)를 참조하십시오.

