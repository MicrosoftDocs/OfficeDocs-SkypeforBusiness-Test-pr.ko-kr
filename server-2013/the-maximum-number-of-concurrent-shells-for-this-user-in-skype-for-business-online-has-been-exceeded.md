---
title: 이 사용자에 대한 최대 동시 셸 개수가 초과했습니다
TOCTitle: 이 사용자에 대한 최대 동시 셸 개수가 초과했습니다
ms:assetid: b309efe8-a214-41ea-a345-93e6a36e0cb1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362837(v=OCS.15)
ms:contentKeyID: 56270291
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 이 사용자에 대한 최대 동시 셸 개수가 초과했습니다

 

_**마지막으로 수정된 항목:** 2015-06-22_

관리자마다 비즈니스용 Skype Online에 대한 동시 원격 연결이 최대 3개까지 허용됩니다. 3개의 원격 Windows PowerShell 연결을 실행 중인 경우 4번째 동시 연결에 대한 시도가 실패하고 다음과 같은 오류 메시지가 나타납니다.

    New-PSSession : [admin.vdomain.com] 다음 오류 메시지가 발생하여 admin.vdomain.com 원격 서버에 연결하지 못했습니다. WS-Management 서비스가 요청을 처리할 수 없습니다. 이 사용자의 최대 동시 셸 수가 초과되었습니다. 기존 셸을 닫거나 이 사용자의 할당량을 높이십시오. 자세한 내용은 about_Remote_Troubleshooting 도움말 항목을 참조하십시오.

이 문제를 해결하는 유일한 방법은 하나 이상의 이전 연결을 닫는 것입니다.비즈니스용 Skype Online 세션을 마쳤으면 **Remove-PSSession** cmdlet을 사용하여 세션을 종료하는 것이 좋습니다. 이렇게 하면 이 문제를 방지할 수 있습니다.

## 참고 항목

#### 개념

[Lync Online의 연결 문제 진단 및 해결](diagnosing-and-resolving-connection-problems-with-skype-for-business-online.md)

