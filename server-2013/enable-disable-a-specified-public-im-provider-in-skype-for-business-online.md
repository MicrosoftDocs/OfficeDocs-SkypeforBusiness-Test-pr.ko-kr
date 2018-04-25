---
title: 지정된 공용 메신저 공급자 설정/해제
TOCTitle: 지정된 공용 메신저 공급자 설정/해제
ms:assetid: 9d3e2607-01c0-4ae9-accc-39f03ce253bb
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362825(v=OCS.15)
ms:contentKeyID: 56270279
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 지정된 공용 메신저 공급자 설정/해제

 

_**마지막으로 수정된 항목:** 2015-06-22_

비즈니스용 Skype Online에서는 다음 공용 메신저 공급자 중 하나 이상의 사용자와 페더레이션을 설정할 수 있습니다.

  - Windows Live 인터넷 서비스 네트워크

  - Yahoo\!

  - AOL

이러한 공급자 중 하나 이상과 페더레이션을 허용하려면 [Set-CsTenantPublicProvider](set-cstenantpublicprovider.md) cmdlet을 사용하여 Provider 속성 값을 다음 값 중 하나 이상으로 설정합니다.

  - Windows Live

  - Yahoo

  - AOL

예를 들어 다음 명령은 Windows Live 및 AOL과 페더레이션을 설정합니다.

    Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider "AOL","WindowsLive"

공급자를 추가하거나 제거할 때마다 명령에 관련 페더레이션 공급자를 모두 포함해야 합니다. 예를 들어 Yahoo\!를 추가하려면 다음 명령을 실행합니다.

    Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider "Yahoo"

이 명령은 Yahoo\!를 유일한 페더레이션 공급자로 남겨 둡니다. 명령에서 유일하게 호출된 공급자이기 때문입니다. 3개의 공용 메신저 공급자 모두와 페더레이션을 설정하려면 3개 공급자를 모두 포함해야 합니다.

    Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider "Yahoo", "AOL","WindowsLive"

Set-CsTenantPublicProvider cmdlet을 호출할 때에는 Tenant 매개 변수를 포함해야 합니다. 그렇지 않으면 테넌트 ID를 입력하라는 메시지가 나타납니다. 다음 명령을 사용하면 비즈니스용 Skype Online 테넌트의 테넌트 ID를 반환할 수 있습니다.

    Get-CsTenant | Select-Object TenantID

또는 이 명령을 사용하여 변수에 테넌트 ID를 저장합니다.

    $tenantID = (Get-CsTenant | Select-Object TenantID)

그런 다음 Set-CsTenantPublicProvider를 호출할 때 해당 변수(이 예의 경우 $tenantID)를 사용할 수 있습니다.

    Set-CsTenantPublicProvider -Tenant $tenantID -Provider "Yahoo", "AOL","WindowsLive"

## 참고 항목

#### 개념

[빠른 참조: Windows PowerShell을 사용하여 일반적인 Lync Online 관리 작업 수행](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

