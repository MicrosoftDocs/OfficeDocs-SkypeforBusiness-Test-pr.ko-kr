---
title: 'Lync Online: 허용 도메인 목록에 도메인 추가'
TOCTitle: 허용 도메인 목록에 도메인 추가
ms:assetid: 7b7f76c8-3047-40be-a938-8ac2868a6bc8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362818(v=OCS.15)
ms:contentKeyID: 56270267
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Online에서 허용 도메인 목록에 도메인 추가

 

_**마지막으로 수정된 항목:** 2015-06-22_

첫 번째 도메인을 허용 도메인 목록에 추가하는 과정은 3단계 프로세스로 구성됩니다. 먼저 [New-CsEdgeDomainPattern](new-csedgedomainpattern.md) cmdlet을 사용하여 추가할 도메인의 도메인 개체를 만듭니다.

    $x = New-CsEdgeDomainPattern -Domain "fabrikam.com"

그런 다음 [New-CsEdgeAllowList](new-csedgeallowlist.md) cmdlet을 사용하여 도메인 개체를 포함하는 새 허용 목록을 만듭니다.

    $newAllowList = New-CsEdgeAllowList -AllowedDomain $x

마지막으로, [Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md) cmdlet을 사용하여 새 허용 목록을 비즈니스용 Skype Online에 씁니다.

    Set-CsTenantFederationConfiguration -AllowedDomains $newAllowList

## 참고 항목

#### 개념

[빠른 참조: Windows PowerShell을 사용하여 일반적인 Lync Online 관리 작업 수행](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

