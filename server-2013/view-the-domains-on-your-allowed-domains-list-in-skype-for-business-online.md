---
title: 허용 도메인 목록의 도메인 보기
TOCTitle: 허용 도메인 목록의 도메인 보기
ms:assetid: 13bceaba-5c4f-431f-864f-9e374cafa986
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362772(v=OCS.15)
ms:contentKeyID: 56270216
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 허용 도메인 목록의 도메인 보기

 

_**마지막으로 수정된 항목:** 2015-06-22_

허용 도메인 목록에 있는 모든 도메인을 보려면 [Get-CsTenantFederationConfiguration](get-cstenantfederationconfiguration.md) 및 다음 구문을 사용하세요.

    Get-CsTenantFederationConfiguration | Select-Object -ExpandProperty AllowedDomains | Select-Object AllowedDomain

## 참고 항목

#### 개념

[빠른 참조: Windows PowerShell을 사용하여 일반적인 Lync Online 관리 작업 수행](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

