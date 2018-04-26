---
title: 차단 도메인 목록의 도메인 보기
TOCTitle: 차단 도메인 목록의 도메인 보기
ms:assetid: 67c65dbf-1a68-4c77-aabd-bed5001b4267
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362797(v=OCS.15)
ms:contentKeyID: 56270249
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 차단 도메인 목록의 도메인 보기

 

_**마지막으로 수정된 항목:** 2015-06-22_

차단된 도메인 목록의 모든 도메인을 보려면 [Get-CsTenantFederationConfiguration](get-cstenantfederationconfiguration.md) cmdlet을 호출합니다. 그런 다음, 반환된 데이터를 **Select-Object** cmdlet에 보냅니다.

    Get-CsTenantFederationConfiguration | Select-Object -ExpandProperty BlockedDomains

## 참고 항목

#### 개념

[빠른 참조: Windows PowerShell을 사용하여 일반적인 Lync Online 관리 작업 수행](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

