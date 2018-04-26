---
title: PIN 정책 삭제
TOCTitle: PIN 정책 삭제
ms:assetid: 7c378927-2e41-418e-9721-327021bd2e45
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg521020(v=OCS.15)
ms:contentKeyID: 49304151
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# PIN 정책 삭제

 

_**마지막으로 수정된 항목:** 2013-02-23_

PIN(개인 식별 번호) 정책을 삭제하려면 다음 단계를 수행합니다.


> [!NOTE]
> 전역 PIN 정책은 삭제할 수 없습니다.



## Lync Server 2013 제어판에서 PIN 정책을 삭제하려면

1.  RTCUniversalServerAdmins 그룹의 구성원인 사용자 계정(또는 이와 동일한 사용자 권한을 가진 사용자 계정)이나 CsServerAdministrator 또는 CsAdministrator 역할이 할당된 사용자 계정에서 Lync Server 2013을 배포한 네트워크에 있는 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **보안**을 클릭하고 **PIN 정책**을 클릭합니다.

4.  **PIN 정책** 페이지의 검색 필드에 삭제할 정책의 이름 전부 또는 일부를 입력합니다.

5.  정책 목록에서 원하는 정책을 클릭하고 **편집**을 클릭한 다음 **삭제**를 클릭합니다.

6.  **확인**을 클릭합니다.

## Lync Server 관리 셸 및 Cmdlet을 사용해서 PIN 정책 제거

Windows PowerShell 및 Remove-CsPinPolicy cmdlet을 사용해서 PIN 정책을 삭제할 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 특정 PIN 정책 제거

  - 이 명령은 ID RedmondPinPolicy가 포함된 PIN 정책을 제거합니다.
    
        Remove-CsPinPolicy -Identity "RedmondPinPolicy"

## 사이트 범위에 적용된 모든 PIN 정책 제거

  - 이 명령은 사이트 범위에 구성된 모든 PIN 정책을 제거합니다.
    
        Get-CsPinPolicy -Filter "site:*" | Remove-CsPinPolicy

## 공통 패턴 사용을 허용하는 모든 PIN 정책 제거

  - 그리고 이 명령은 공통 패턴 사용을 허용하는 모든 PIN 정책을 제거합니다.
    
        et-CsPinPolicy | Where-Object {$_.AllowCommonPatterns -eq $True} | Remove-CsPinPolicy

자세한 내용은 [Remove-CsPinPolicy](remove-cspinpolicy.md) cmdlet의 도움말 항목을 참조하십시오.

