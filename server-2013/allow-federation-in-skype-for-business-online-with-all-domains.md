---
title: 모든 도메인과 페더레이션 허용
TOCTitle: 모든 도메인과 페더레이션 허용
ms:assetid: d26f1057-a76c-447a-9efe-72efdce4c15e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362855(v=OCS.15)
ms:contentKeyID: 56270306
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 모든 도메인과 페더레이션 허용

 

_**마지막으로 수정된 항목:** 2015-06-22_

사용자가 도메인에 상관없이 다른 사용자와 통신할 수 있도록 하려면 다음 두 가지 작업을 실행해야 합니다. 먼저 [New-CsEdgeAllowAllKnownDomains](new-csedgeallowallknowndomains.md) cmdlet을 사용하여 AllowAllKnownDomains 개체의 인스턴스를 만듭니다.

    $x = New-CsEdgeAllowAllKnownDomains

그런 다음 [Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md) cmdlet을 호출하고 AllowedDomains 속성 값을 AllowAllKnownDomains 개체를 포함하는 변수(이 예제의 경우 $x)로 설정합니다.

    Set-CsTenantFederationConfiguration -AllowedDomains $x

## 참고 항목

#### 개념

[빠른 참조: Windows PowerShell을 사용하여 일반적인 Lync Online 관리 작업 수행](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

