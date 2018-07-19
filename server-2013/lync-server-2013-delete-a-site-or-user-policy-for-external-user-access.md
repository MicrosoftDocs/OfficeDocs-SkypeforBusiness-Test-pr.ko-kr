---
title: 'Lync Server 2013: 외부 사용자 액세스에 대한 사이트 또는 사용자 정책 삭제'
TOCTitle: 외부 사용자 액세스에 대한 사이트 또는 사용자 정책 삭제
ms:assetid: 6d907507-825b-4354-9c03-337a459f72de
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg521013(v=OCS.15)
ms:contentKeyID: 49303963
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 외부 사용자 액세스에 대한 사이트 또는 사용자 정책 삭제

 

_**마지막으로 수정된 항목:** 2013-02-22_

**외부 액세스 정책** 페이지의 Lync Server 제어판에 나열된 사이트 또는 사용자 정책을 삭제할 수 있습니다. 글로벌 정책을 삭제해도 실제로 정책이 삭제되지 않으며, 기본 설정으로만 재설정하기 때문에 외부 사용자 액세스 옵션에 대한 지원이 포함되지 않습니다. 글로벌 정책 재설정에 대한 자세한 내용은 [Lync Server 2013에서 외부 사용자 액세스에 대한 전역 정책 다시 설정](lync-server-2013-reset-the-global-policy-for-external-user-access.md)을 참조하십시오.

## 외부 사용자 액세스에 대한 사이트 또는 사용자 정책을 삭제하려면

1.  RTCUniversalServerAdmins 그룹의 구성원(또는 이와 동일한 사용자 권한을 가진 사용자 계정) 또는 CsAdministrator 역할이 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  **외부 사용자 액세스** 를 클릭한 다음 **외부 액세스 정책** 을 클릭합니다.

4.  **외부 액세스 정책** 탭에서 삭제할 사이트 또는 사용자 정책, **편집** 을 차례로 클릭한 다음 **삭제** 를 클릭합니다.

5.  삭제를 확인하는 메시지가 표시되면 **확인** 을 클릭합니다.

## Windows PowerShell cmdlet을 사용하여 PIN 정책 제거

외부 액세스 정책은 Windows PowerShell 및 Remove-CsExternalAccessPolicy cmdlet을 사용하여 삭제할 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 특정 외부 액세스 정책을 제거하려면

  - 이 명령은 Redmond 사이트에 적용된 외부 액세스 정책을 제거합니다.
    
        Remove-CsExternalAccessPolicy -Identity "site:Redmond"

## 사용자별 범위에 적용된 모든 외부 액세스 정책을 제거하려면

  - 이 명령은 사용자별 범위에 구성된 모든 외부 액세스 정책을 제거합니다.
    
        Get-CsExternalAccessPolicy -Filter "tag:*" | Remove-CsExternalAccessPolicy

## 외부 사용자 액세스가 해제된 모든 외부 액세스 정책을 제거하려면

  - 이 명령은 외부 사용자 액세스가 해제된 모든 외부 액세스 정책을 삭제합니다.
    
        Get-CsExternalAccessPolicy | Where-Object {$_.EnableOutsideAccess -eq $False} | Remove-CsExternalAccessPolicy

자세한 내용은 [Remove-CsExternalAccessPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsExternalAccessPolicy) cmdlet 관련 도움말 항목을 참고하세요.

