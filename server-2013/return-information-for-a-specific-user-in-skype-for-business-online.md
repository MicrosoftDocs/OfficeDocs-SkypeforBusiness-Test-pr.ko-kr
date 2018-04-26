---
title: 특정 사용자에 대한 정보 반환
TOCTitle: 특정 사용자에 대한 정보 반환
ms:assetid: 6c8c2190-8e62-4f92-bbe9-4f692bd7ebf5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362803(v=OCS.15)
ms:contentKeyID: 56270253
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 특정 사용자에 대한 정보 반환

 

_**마지막으로 수정된 항목:** 2015-06-22_

[Get-CsOnlineUser](get-csonlineuser.md) cmdlet을 호출할 때 여러 가지 방법으로 특정 사용자 계정을 참조할 수 있습니다. 사용자의 Active Directory 도메인 서비스 표시 이름을 사용할 수 있습니다.

    Get-CsOnlineUser -Identity "Ken Myer"

SIP 주소를 사용할 수 있습니다.

    Get-CsOnlineUser -Identity "sip:kenmyer@litwareinc.com"

사용자의 사용자 계정 이름(UPN)을 사용할 수 있습니다.

    Get-CsOnlineUser -Identity "kenmyer@litwareinc.com"

## 참고 항목

#### 개념

[빠른 참조: Windows PowerShell을 사용하여 일반적인 Lync Online 관리 작업 수행](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

