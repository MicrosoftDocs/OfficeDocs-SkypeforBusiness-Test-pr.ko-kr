---
title: 이 테넌트에 대한 최대 동시 셸 개수가 초과했습니다
TOCTitle: 이 테넌트에 대한 최대 동시 셸 개수가 초과했습니다
ms:assetid: a4c91ffa-fdcc-414c-b941-a0d36c906825
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362832(v=OCS.15)
ms:contentKeyID: 56270287
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 이 테넌트에 대한 최대 동시 셸 개수가 초과했습니다

 

_**마지막으로 수정된 항목:** 2015-06-22_

관리자마다 비즈니스용 Skype Online 테넌트에 대해 최대 3개의 동시 연결이 허용되지만 하나의 테넌트에 대해 허용되는 동시 연결은 9개 이하로 제한됩니다. 예를 들어 3명의 관리자가 있는 경우, 각 관리자가 3개의 열려 있는 세션을 가질 수 있습니다. 4번째 관리자가 연결을 시도하는 경우(이에 따라 총 동시 연결 수가 10이 됨) 다음 오류 메시지와 함께 실패합니다.

    New-PSSession : [admin.vdomain.com] 다음 오류 메시지가 발생하여 admin.vdomain.com 원격 서버에 연결하지 못했습니다. WS-Management 서비스가 요청을 처리할 수 없습니다. 이 테넌트의 최대 동시 셸 수가 초과되었습니다. 기존 셸을 닫거나 이 테넌트의 할당량을 높이십시오. 자세한 내용은 about_Remote_Troubleshooting 도움말 항목을 참조하십시오..

이 문제를 해결하는 유일한 방법은 하나 이상의 이전 연결을 닫는 것입니다. 비즈니스용 Skype Online 세션을 마쳤으면 **Remove-PSSession** cmdlet을 사용하여 해당 세션을 종료하는 것이 좋습니다. 이렇게 하면 이 문제를 방지할 수 있습니다.

## 참고 항목

#### 개념

[빠른 참조: Windows PowerShell을 사용하여 일반적인 Lync Online 관리 작업 수행](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

