---
title: 이 테넌트를 관리할 권한이 없는 사용자
TOCTitle: 이 테넌트를 관리할 권한이 없는 사용자
ms:assetid: 714ccf81-9451-4585-b62d-979f2a606315
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362812(v=OCS.15)
ms:contentKeyID: 56270257
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 이 테넌트를 관리할 권한이 없는 사용자

 

_**마지막으로 수정된 항목:** 2015-06-22_

사용자가 테넌트 관리자 그룹의 구성원이 아닌 이상 비즈니스용 Skype Online으로 원격 Windows PowerShell 연결을 할 수 없습니다. 구성원이 아닌 경우 연결 시도는 실패하고, 다음과 같은 오류 메시지가 나타납니다.

    New-PSSession : [admin.vdomain.com] 다음 오류 메시지가 발생하여 admin.vdomain.com 원격 서버에서 데이터를 처리하지 못했습니다. 'user@foo.com' 사용자가 이 테넌트를 관리할 권한을 가지고 있지 않습니다. 사용자를 알맞은 RBAC 역할에 할당하여 권한을 부여할 수 있습니다. 자세한 내용은 about_Remote_Troubleshooting 도움말 항목을 참조하십시오..

테넌트 관리자 그룹의 구성원이거나 구성원이라고 생각하는 경우에는 Office 365 고객 지원 서비스에 문의하세요.

## 참고 항목

#### 개념

[Lync Online의 연결 문제 진단 및 해결](diagnosing-and-resolving-connection-problems-with-skype-for-business-online.md)

