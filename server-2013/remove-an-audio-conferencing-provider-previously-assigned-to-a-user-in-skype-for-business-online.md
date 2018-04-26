---
title: 이전에 사용자에게 할당된 오디오 회의 공급자 제거
TOCTitle: 이전에 사용자에게 할당된 오디오 회의 공급자 제거
ms:assetid: 85d59e6c-d646-4908-9767-adb48763f6de
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362808(v=OCS.15)
ms:contentKeyID: 56270273
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 이전에 사용자에게 할당된 오디오 회의 공급자 제거

 

_**마지막으로 수정된 항목:** 2015-06-22_

사용자에게 할당된 모든 오디오 회의 공급자를 제거하려면 매개 변수 없이 [Remove-CsUserAcp](remove-csuseracp.md) cmdlet을 실행합니다. 이때 해당되는 사용자를 나타내는 Identity 매개 변수는 예외입니다.

    Remove-CsUserAcp -Identity "Ken Myer"

사용자에게 여러 오디오 회의 공급자가 할당되어 있는 경우에는 Name 매개 변수와 제거할 공급자의 이름을 포함해 하나의 공급자를 제거할 수 있습니다.

    Remove-CsUserAcp -Identity "Ken Myer" -Name "Contoso ACP"

## 참고 항목

#### 개념

[빠른 참조: Windows PowerShell을 사용하여 일반적인 Lync Online 관리 작업 수행](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

