---
title: 테넌트에 연결하는 기능이 해제됨
TOCTitle: 테넌트에 연결하는 기능이 해제됨
ms:assetid: 7365d31b-173e-4339-b0a3-98ab73a9558f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362820(v=OCS.15)
ms:contentKeyID: 56270258
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 테넌트에 연결하는 기능이 해제됨

 

_**마지막으로 수정된 항목:** 2015-06-22_

Windows PowerShell을 사용하여 비즈니스용 Skype Online을 관리하려면 Windows PowerShell 정책의 EnableRemotePowerShellAccess 속성이 True로 설정되어야 합니다. 그렇지 않은 경우 연결은 실패하고, 다음과 같은 오류 메시지가 나타납니다.

    New-PSSession : [admin.vdomain.com] 다음 오류 메시지가 발생하여 admin.vdomain.com 원격 서버에서 데이터를 처리하지 못했습니다. 원격 PowerShell 세션을 사용하여 이 테넌트에 연결하는 기능이 사용하지 않도록 설정되었습니다. Lync 도움말에서 이 테넌트에 대한 테넌트 Powershell 정책을 확인하세요. 자세한 내용은 about_Remote_Troubleshooting 도움말 항목을 참조하십시오..

다음과 같은 오류 메시지가 표시되면 Office 365 고객 지원 서비스에 연락하여 원격 Windows PowerShell 액세스를 사용하도록 설정해야 합니다.

## 참고 항목

#### 개념

[Lync Online의 연결 문제 진단 및 해결](diagnosing-and-resolving-connection-problems-with-skype-for-business-online.md)

