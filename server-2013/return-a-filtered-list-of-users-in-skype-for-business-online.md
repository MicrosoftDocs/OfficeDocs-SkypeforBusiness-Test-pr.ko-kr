---
title: 필터링된 사용자 목록 반환
TOCTitle: 필터링된 사용자 목록 반환
ms:assetid: f2c4d13b-8601-4192-8b94-e9a57969da11
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362858(v=OCS.15)
ms:contentKeyID: 56270315
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 필터링된 사용자 목록 반환

 

_**마지막으로 수정된 항목:** 2015-06-22_

[Get-CsOnlineUser](get-csonlineuser.md) cmdlet 및 LdapFilter 또는 Filter 매개 변수를 사용하면 대상 사용자 집합에 대한 정보를 손쉽게 반환할 수 있습니다. 예를 들어 다음 명령은 재무 부서에서 일하는 모든 사용자를 반환합니다.

    Get-CsOnlineUser -LdapFilter "department=Finance"

## 참고 항목

#### 개념

[빠른 참조: Windows PowerShell을 사용하여 일반적인 Lync Online 관리 작업 수행](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

