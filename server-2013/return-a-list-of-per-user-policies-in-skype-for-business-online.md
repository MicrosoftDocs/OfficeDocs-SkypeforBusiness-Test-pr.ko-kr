---
title: 사용자별 정책 목록 반환
TOCTitle: 사용자별 정책 목록 반환
ms:assetid: e95a2755-3501-40cc-a704-5ecd01839d76
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362856(v=OCS.15)
ms:contentKeyID: 56270308
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 사용자별 정책 목록 반환

 

_**마지막으로 수정된 항목:** 2015-06-22_

사용 가능한 사용자별 정책 목록을 반환하려면 먼저 적절한 **Get-Cs** cmdlet을 선택합니다. 예를 들어 사용자별 음성 정책을 반환하려는 경우에는 [Get-CsVoicePolicy](get-csvoicepolicy.md) cmdlet을 선택합니다. 그리고 나서 다음 구문을 사용하여 각 사용자별 정책에 대한 ID를 반환합니다.

    Get-CsVoicePolicy -Filter "tag:*" | Select-Object Identity

사용권 계약 및 국가/지역 제한이 서로 다르기 때문에 특정 회의 정책, 외부 액세스 정책 또는 모바일 정책을 특정 사용자에게 할당하지 못할 수도 있습니다. 지정된 사용자(예: kenmyer@litwareinc.com)에게 실제로 할당할 수 있는 사용자별 정책을 확인하려면 다음 명령 중 하나와 ApplicableTo 매개 변수를 적절하게 사용합니다.

    Get-CsConferencingPolicy -ApplicableTo "kenmyer@litwareinc.com"
    Get-CsExternalAccessPolicy -ApplicableTo "kenmyer@litwareinc.com"
    Get-CsMobilityPolicy -ApplicableTo "kenmyer@litwareinc.com"

앞의 구문은 실제로 Ken Myer에게 할당할 수 있는 사용자별 정책만 반환합니다.

## 참고 항목

#### 개념

[빠른 참조: Windows PowerShell을 사용하여 일반적인 Lync Online 관리 작업 수행](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

