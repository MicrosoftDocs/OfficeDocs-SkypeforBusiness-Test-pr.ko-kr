---
title: 주소록 서버 Cmdlet
TOCTitle: 주소록 서버 Cmdlet
ms:assetid: 33da45da-3c57-4d04-9679-f0e5a0cfd37e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg415643(v=OCS.15)
ms:contentKeyID: 49303253
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 주소록 서버 Cmdlet

 

_**마지막으로 수정된 항목:** 2012-06-26_

주소록 서버는 Active Directory 도메인 서비스와 Microsoft Lync Server 2013 간의 중계자입니다. 주소록 서버를 사용하면 Lync Server 2013에 저장된 사용자 정보와 Active Directory에 저장된 사용자 정보가 동기화됩니다. 이 작업은 주소록 파일을 사용자 데이터베이스에 저장된 정보와 주기적으로 동기화하는 방식으로 수행됩니다. 따라서 Lync Server에는 주소록 서버 관리를 위한 여러 cmdlet이 포함되어 있습니다.

## 주소록 서버 Cmdlet

Lync Server 제어판에서 주소록 서버 설정을 구성할 수는 없습니다. 주로 Windows PowerShell을 사용하여 이러한 설정을 관리합니다. 다음은 주소록 서버 관리에 직접적으로 관련된 cmdlet 목록입니다.

**주소록 서버**

  -   
    [Get-CsAddressBookConfiguration](get-csaddressbookconfiguration.md)

  -   
    [New-CsAddressBookConfiguration](new-csaddressbookconfiguration.md)

  -   
    [Remove-CsAddressBookConfiguration](remove-csaddressbookconfiguration.md)

  -   
    [Set-CsAddressBookConfiguration](set-csaddressbookconfiguration.md)

<!-- end list -->

  -   
    [Update-CsAddressBook](update-csaddressbook.md)

  -   
    [Debug-CsAddressBookReplication](debug-csaddressbookreplication.md)

<!-- end list -->

  -   
    [Test-CsAddressBookService](test-csaddressbookservice.md)

  -   
    [Test-CsAddressBookWebQuery](test-csaddressbookwebquery.md)

## 참고 항목

#### 기타 리소스

[Lync Server PowerShell 블로그](http://go.microsoft.com/fwlink/?linkid=203150%26clcid=0x412)

