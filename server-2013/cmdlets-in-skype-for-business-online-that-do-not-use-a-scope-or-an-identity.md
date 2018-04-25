---
title: 범위 또는 ID를 사용하지 않는 cmdlet
TOCTitle: 범위 또는 ID를 사용하지 않는 cmdlet
ms:assetid: 9c50c732-3c64-4b6a-96fd-8f528eb739ce
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362824(v=OCS.15)
ms:contentKeyID: 56270278
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 범위 또는 ID를 사용하지 않는 cmdlet

 

_**마지막으로 수정된 항목:** 2015-06-22_

허용 목록과 차단 목록(사용자가 어떤 외부 조직과 통신할 수 있는지 결정하는 목록)을 수정할 때 사용되는 cmdlet은 범위 또는 Identity를 사용하지 않습니다. 실제로 **New-CsEdgeAllowAllKnownDomains** cmdlet에는 매개 변수가 하나도 없습니다. 범위 또는 Identity를 사용하지 않는 cmdlet은 다음과 같습니다.

  - [New-CsEdgeAllowAllKnownDomains](new-csedgeallowallknowndomains.md)

  - [New-CsEdgeAllowList](new-csedgeallowlist.md)

  - [New-CsEdgeDomainPattern](new-csedgedomainpattern.md)

**New-CsEdgeAllowList** cmdlet 및 **New-CsEdgeDomainPattern** cmdlet을 사용할 때에는 Domain 매개 변수를 포함해야 합니다. 예를 들면 다음과 같습니다.

    $x = New-CsEdgeDomainPattern -Domain "fabrikam.com"

## 참고 항목

#### 개념

[ID, 범위, 테넌트](identities-scopes-and-tenants-in-skype-for-business-online.md)  
[Lync Online Cmdlet](the-skype-for-business-online-cmdlets.md)

