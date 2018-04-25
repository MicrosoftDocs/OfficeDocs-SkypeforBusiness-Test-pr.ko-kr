---
title: 익명의 사용자가 자동으로 모임에 입장하지 않도록 설정
TOCTitle: 익명의 사용자가 자동으로 모임에 입장하지 않도록 설정
ms:assetid: 23f120d2-4c39-4509-aa1f-4d186a525075
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362775(v=OCS.15)
ms:contentKeyID: 56270226
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 익명의 사용자가 자동으로 모임에 입장하지 않도록 설정

 

_**마지막으로 수정된 항목:** 2015-06-22_

익명 사용자의 온라인 모임 참가가 자동으로 허용되지 않도록 설정하려면 [Set-CsMeetingConfiguration](set-csmeetingconfiguration.md) cmdlet을 사용하고 AdmitAnonymousUsersByDefault 속성을 False($False)로 설정합니다.

    Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False

자동으로 허용되도록 설정하려면 AdmitAnonymousUsersByDefault 속성을 다시 True($True)로 설정합니다.

    Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True

## 참고 항목

#### 개념

[빠른 참조: Windows PowerShell을 사용하여 일반적인 Lync Online 관리 작업 수행](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

