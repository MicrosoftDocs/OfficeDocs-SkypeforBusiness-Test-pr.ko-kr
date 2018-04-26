---
title: 'Lync Server 2013: Kerberos 인증 계정 암호 설정'
TOCTitle: Kerberos 인증 계정 암호 설정
ms:assetid: b435f88e-4a77-4be7-b7e5-c17484303b74
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412870(v=OCS.15)
ms:contentKeyID: 49304773
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 Kerberos 인증 계정 암호 설정

 

_**마지막으로 수정된 항목:** 2010-11-03_

Kerberos 인증 계정에 대한 컴퓨터 개체를 만들고 나면 계정에 대한 암호를 설정할 수 있으며, Windows PowerShell cmdlet을 실행하여 특정 서버에서 Kerberos 계정 암호를 설정할 수 있습니다. Kerberos 인증을 위해 만든 개체에 대한 암호를 설정할 수 있습니다. 이 암호는 알려진 값으로 설정할 수 있지만 기본적으로는 임의로 암호가 설정됩니다. 이 암호는 계정을 사용하는 모든 Kerberos 인증 원본에 사용할 수 있습니다. Windows PowerShell cmdlet을 사용하여 Kerberos 계정 암호를 설정하고 관리할 수 있습니다.


> [!NOTE]
> Kerberos 계정 개체는 컴퓨터 개체이지만 참조된 Windows PowerShell cmdlet에서 작업 시 UserAccount 매개 변수가 사용됩니다. 이는 오류 상황이 아니며 Kerberos 계정 만들기 및 유지 관리에서 사용할 경우 예상된 cmdlet 동작입니다.



## 이 단원의 내용

  - [Lync Server 2013에서 서버에 대한 Kerberos 인증 계정 암호 설정](lync-server-2013-set-a-kerberos-authentication-account-password-on-a-server.md)

  - [Lync Server 2013에서 IIS에 Kerberos 인증 계정 암호 동기화](lync-server-2013-synchronize-a-kerberos-authentication-account-password-to-iis.md)

