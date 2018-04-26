---
title: Live ID 서버 연결 실패
TOCTitle: Live ID 서버 연결 실패
ms:assetid: 701af721-dd6a-4f48-96f9-94e89c644201
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362811(v=OCS.15)
ms:contentKeyID: 56270255
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Live ID 서버 연결 실패

 

_**마지막으로 수정된 항목:** 2015-06-22_

다음과 같은 오류 메시지와 함께 연결 시도가 실패하는 이유는 일반적으로 세 가지입니다.

    Get-CsWebTicket : Live ID 서버에 연결하지 못했습니다. 프록시가 설정되어 있는지 또는 컴퓨터의 네트워크가 Live ID 서버에 연결되어 있는지 확인하세요.

Microsoft Online 서비스 로그인 도우미가 실행되지 않는 경우 이러한 오류가 종종 발생합니다. Windows PowerShell 프롬프트에서 다음 명령을 실행하여 이 서비스의 상태를 확인할 수 있습니다.

    Get-Service "msoidsvc"

서비스가 실행되지 않는 경우 다음 명령을 사용하여 서비스를 시작합니다.

    Start-Service "msoidsvc"

서비스가 실행 중인 경우 사용자의 컴퓨터와 Microsoft Live ID 인증 서버 간에 네트워크 연결 문제가 있을 수 있습니다. 이를 확인하려면 Internet Explorer를 열고 <https://login.microsoftonline.com/>으로 이동합니다. 여기서 Office 365에 로그인을 시도합니다. 로그인에 실패하면 네트워크 연결 문제일 수 있습니다.

드물게 Microsoft Live ID 인증 서버의 연결 URI가 잘못된 값으로 구성되었을 수 있습니다. 로그인 도우미가 실행되고 있고 네트워크 연결 문제가 없다면 이것이 이유일 수 있습니다. 이러한 경우 Office 365 고객 지원 서비스에 문의하세요.

## 참고 항목

#### 개념

[Lync Online의 연결 문제 진단 및 해결](diagnosing-and-resolving-connection-problems-with-skype-for-business-online.md)

