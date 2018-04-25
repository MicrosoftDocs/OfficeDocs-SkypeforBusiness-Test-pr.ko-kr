---
title: 이전에 사용자에게 할당된 사용자별 정책 할당 취소
TOCTitle: 이전에 사용자에게 할당된 사용자별 정책 할당 취소
ms:assetid: bdba1d22-28e4-4203-a109-a3fb408783d3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362840(v=OCS.15)
ms:contentKeyID: 56270297
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 이전에 사용자에게 할당된 사용자별 정책 할당 취소

 

_**마지막으로 수정된 항목:** 2015-06-22_

사용자에게 이전에 할당한 사용자별 정책을 할당 취소하려면 해당 **Grant-Cs** cmdlet(예: 음성 정책의 할당을 취소하려면 [Grant-CsVoicePolicy](grant-csvoicepolicy.md) cmdlet)을 다시 실행하고 PolicyName 매개 변수를 null 값($Null)으로 설정합니다.

    Grant-CsVoicePolicy -Identity "Ken Myer" -PolicyName $Null

모든 사용자의 음성 정책 할당을 취소하려면 다음 명령을 사용합니다.

    Get-CsOnlineUser | Grant-CsVoicePolicy -PolicyName $Null

사용자의 정책 할당을 취소하면 해당 사용자가 전역 정책에 의해 관리됩니다.

## 참고 항목

#### 개념

[빠른 참조: Windows PowerShell을 사용하여 일반적인 Lync Online 관리 작업 수행](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

