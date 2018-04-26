---
title: 'Lync Online: 차단된 도메인 목록에 도메인 추가'
TOCTitle: 차단된 도메인 목록에 도메인 추가
ms:assetid: ea6ebeea-3031-4c42-9a2c-88eaab790636
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362853(v=OCS.15)
ms:contentKeyID: 56270314
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Online에서 차단된 도메인 목록에 도메인 추가

 

_**마지막으로 수정된 항목:** 2015-06-22_

차단된 도메인 목록에 도메인을 추가하려면 다음과 같은 구문을 사용합니다.

    $x = New-CsEdgeDomainPattern "fabrikam.com"
    Set-CsTenantFederationConfiguration -BlockedDomains @{Add=$x}

여기서 볼 수 있듯이 이 명령을 사용하려면 두 단계를 거쳐야 합니다. 먼저 [New-CsEdgeDomainPattern](new-csedgedomainpattern.md)을 사용하여 차단 목록에 추가할 도메인을 나타내는 도메인 개체를 만듭니다. 그리고 나서 [Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md) cmdlet 및 Add 메서드를 사용하여 해당 도메인(이 예제의 경우 변수 $x에 저장된 도메인)을 목록에 추가합니다.

## 참고 항목

#### 개념

[빠른 참조: Windows PowerShell을 사용하여 일반적인 Lync Online 관리 작업 수행](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

