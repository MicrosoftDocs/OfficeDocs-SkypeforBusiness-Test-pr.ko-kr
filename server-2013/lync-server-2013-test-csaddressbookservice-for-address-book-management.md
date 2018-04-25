---
title: 주소록 관리용 Test-CsAddressBookService
TOCTitle: 주소록 관리용 Test-CsAddressBookService
ms:assetid: b88cea74-41fd-4c0e-9284-7135bff27a27
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg429720(v=OCS.15)
ms:contentKeyID: 49304829
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 주소록 관리용 Test-CsAddressBookService

 

_**마지막으로 수정된 항목:** 2012-11-01_

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 Test-CsAddressBookService cmdlet을 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 가져오려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Test-CsAddressBookService"}

Lync Server 2013에는 특정 기능이 제대로 작동하는지 확인하기 위해 가상 명령을 시작하는 여러 cmdlet이 있습니다. Test-CsAddressBookService는 정의된 사용자가 주소록 웹 서비스에서 로컬 파일을 연결하고 요청할 수 있는지 확인합니다.

예:

    Test-CsAddressBookService -TargetFqdn atl-cs-001.contoso.com -UserCredential contoso\bob -UserSipAddress "sip:bob@contoso.com"

## 참고 항목

#### 기타 리소스

[Test-CsAddressBookService](test-csaddressbookservice.md)

