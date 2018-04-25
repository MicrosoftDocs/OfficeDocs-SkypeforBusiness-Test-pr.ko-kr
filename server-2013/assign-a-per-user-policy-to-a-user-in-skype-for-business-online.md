---
title: 사용자에게 사용자별 정책 할당
TOCTitle: 사용자에게 사용자별 정책 할당
ms:assetid: 37e07da7-6391-4d6d-a428-c70272897039
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362779(v=OCS.15)
ms:contentKeyID: 56270224
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 사용자에게 사용자별 정책 할당

 

_**마지막으로 수정된 항목:** 2015-06-22_

사용자에게 사용자별 정책을 할당하려면 먼저 적절한 **Grant-Cs** cmdlet을 선택해야 합니다. 예를 들어 사용자별 음성 정책을 할당하려면 [Grant-CsVoicePolicy](grant-csvoicepolicy.md)를 선택합니다. 정책을 할당 받는 사용자의 ID와 할당하는 정책의 이름을 모두 지정하고 cmdlet을 실행합니다.

    Grant-CsVoicePolicy -Identity "Ken Myer" -PolicyName "RedmondVoicePolicy"

모든 사용자에게 동일한 정책을 할당하려면 다음 구문을 사용합니다.

    Get-CsOnlineUser | Grant-CsVoicePolicy -PolicyName "RedmondVoicePolicy"

라이선스 계약 및 국가/지역 제한이 서로 다르므로 특정 회의 정책, 외부 액세스 정책 또는 모바일 정책을 특정 사용자에게 할당하지 못할 수도 있습니다. 지정된 사용자(예: kenmyer@litwareinc.com)에게 실제로 할당할 수 있는 사용자별 정책을 확인하려면 필요에 따라 다음 명령 중 하나(및 ApplicableTo 매개 변수)를 사용합니다.

    Get-CsConferencingPolicy -ApplicableTo "kenmyer@litwareinc.com"
    Get-CsExternalAccessPolicy -ApplicableTo "kenmyer@litwareinc.com"
    Get-CsMobilityPolicy -ApplicableTo "kenmyer@litwareinc.com"

위의 구문은 실제로 Ken Myer에게 할당할 수 있는 사용자별 정책만 반환합니다.

## 참고 항목

#### 개념

[빠른 참조: Windows PowerShell을 사용하여 일반적인 Lync Online 관리 작업 수행](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

