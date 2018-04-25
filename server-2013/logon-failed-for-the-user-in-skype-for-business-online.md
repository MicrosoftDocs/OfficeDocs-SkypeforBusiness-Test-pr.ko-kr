---
title: 사용자 로그인 실패
TOCTitle: 사용자 로그인 실패
ms:assetid: 006020cd-34d0-4a78-b5b4-e382d95ef04d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn329053(v=OCS.15)
ms:contentKeyID: 56270207
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 사용자 로그인 실패

 

_**마지막으로 수정된 항목:** 2015-06-22_

비즈니스용 Skype Online에 원격으로 연결하려면 유효한 비즈니스용 Skype Online 사용자 계정의 사용자 이름과 암호를 제공해야 합니다. 유효한 정보를 제공하지 않은 경우 로그온에 실패하고 다음과 유사한 오류 메시지가 표시됩니다.

    Get-CsWebTicket : 'kenmyer@litwareinc.com' 사용자로 로그온하지 못했습니다. 올바른 사용자 이름 및 암호를 사용하여 새 PSCredential 개체를 만드십시오..

유효한 사용자 계정을 사용하고 있고 보유한 암호가 올바른 경우에는 다시 로그온을 시도합니다. 다시 시도해도 실패하는 경우 동일한 자격 증명을 사용하여 <https://login.microsoftonline.com/>에 로그온합니다. 여기서도 로그온할 수 없는 경우 Office 365 고객 지원 서비스에 문의하세요.

## 참고 항목

#### 개념

[Lync Online의 연결 문제 진단 및 해결](diagnosing-and-resolving-connection-problems-with-skype-for-business-online.md)

