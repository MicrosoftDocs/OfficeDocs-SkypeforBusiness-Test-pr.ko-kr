---
title: 차단 도메인 목록에서 도메인 제거
TOCTitle: 차단 도메인 목록에서 도메인 제거
ms:assetid: a11ea475-bb8b-44be-a5a5-4abb2fed42b8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362830(v=OCS.15)
ms:contentKeyID: 56270286
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 차단 도메인 목록에서 도메인 제거

 

_**마지막으로 수정된 항목:** 2015-06-22_

차단된 도메인 목록에서 도메인을 제거하기 위해서는 두 가지 단계를 거쳐야 합니다. 먼저 [New-CsEdgeDomainPattern](new-csedgedomainpattern.md) cmdlet을 사용하여 제거할 도메인에 대한 도메인 개체를 만들어야 합니다.

    $x = New-CsEdgeDomainPattern "fabrikam.com"

이 개체를 만든 후에 다음 구문을 사용하여 차단된 도메인 목록에서 도메인(이 예제에서는 변수 $x에 도메인이 저장됨)을 제거합니다.

    Set-CsTenantFederationConfiguration -BlockedDomains @{Remove=$x}

차단된 도메인 목록에서 도메인을 모두 제거하려면 BlockedDomains 속성 값을 null($Null)로 설정합니다.

    Set-CsTenantFederationConfiguration -BlockedDomains $Null

## 참고 항목

#### 개념

[빠른 참조: Windows PowerShell을 사용하여 일반적인 Lync Online 관리 작업 수행](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

