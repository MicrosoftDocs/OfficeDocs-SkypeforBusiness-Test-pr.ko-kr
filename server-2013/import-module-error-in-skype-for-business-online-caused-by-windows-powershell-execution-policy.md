---
title: Windows PowerShell 실행 정책으로 인해 발생한 Import-Module 오류
TOCTitle: Windows PowerShell 실행 정책으로 인해 발생한 Import-Module 오류
ms:assetid: 4bc093ca-fd30-44c9-a0a3-16f78698df2b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362786(v=OCS.15)
ms:contentKeyID: 56270229
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Windows PowerShell 실행 정책으로 인해 발생한 Import-Module 오류

 

_**마지막으로 수정된 항목:** 2015-06-22_

Windows PowerShell 실행 정책은 Windows PowerShell 콘솔로 로드할 수 있는 구성 파일과 이 콘솔에서 사용자가 실행할 수 있는 스크립트를 결정하는 데 도움을 줍니다. 적어도, 실행 정책이 RemoteSigned로 설정되지 않으면 비즈니스용 Skype Online 커넥터 모듈을 가져올 수 없습니다. 설정되지 않은 상태에서 해당 모듈을 가져오려고 하면 다음과 같은 오류 메시지가 표시됩니다.

    Import-Module : 이 시스템에서 실행 중인 스크립트를 사용할 수 없으므로 C:\Program Files\Common Files\Microsoft Lync Server 2013\Modules\LyncOnlineConnector\LyncOnlineConnectorStartup.psm1 파일을 로드할 수 없습니다. 자세한 내용은 about_Execution_Policies(http://go.microsoft.com/fwlink/?LinkID=135170)를 참고하십시오.

이 문제를 해결하려면 관리자로서 Windows PowerShell을 시작한 다음 다음 명령을 실행합니다.

    Set-ExecutionPolicy RemoteSigned

실행 정책에 대한 자세한 내용은 [http://go.microsoft.com/fwlink/?LinkID=135170](http://go.microsoft.com/fwlink/?linkid=135170)의 도움말 항목을 참고하세요.

## 참고 항목

#### 개념

[Lync Online의 연결 문제 진단 및 해결](diagnosing-and-resolving-connection-problems-with-skype-for-business-online.md)

