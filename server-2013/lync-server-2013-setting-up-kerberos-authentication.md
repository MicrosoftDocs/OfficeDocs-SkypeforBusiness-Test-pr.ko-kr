---
title: 'Lync Server 2013: Kerberos 인증 설정'
TOCTitle: Kerberos 인증 설정
ms:assetid: dd8009ef-6265-4cc0-b2c7-e474cd1f4b09
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398976(v=OCS.15)
ms:contentKeyID: 49305248
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 Kerberos 인증 설정

 

_**마지막으로 수정된 항목:** 2013-02-21_

Lync Server 2013은 웹 서비스에 대해 NTLM 및 Kerberos 인증을 지원합니다. Office Communications Server 2007 및 Office Communications Server 2007 R2에서는 사용자 계정으로 기본 RTCComponentService 및 RTCService를 사용하여 웹 서비스 응용 프로그램 풀을 실행하므로 SPN(서비스 사용자 이름)을 사용자 계정에 할당하고 인증 사용자로 사용할 수 있었습니다. Lync Server에서는 NetworkService를 사용하여 웹 서비스를 실행하며 NetworkService에는 SPN을 할당할 수 없습니다.

Active Directory 개체에 SPN을 보유하지 못하는 문제를 해결하기 위해 Lync Server 제어판에서는 컴퓨터 계정 개체를 사용하여 SPN을 보유합니다. 컴퓨터 계정 개체는 SPN을 보유할 수 있으며, 이전 버전에서 사용자 계정 사용 시 문제가 되었던 암호 만료가 적용되지 않습니다.

Windows PowerShell cmdlet를 사용하여 Kerberos 인증을 제공하도록 컴퓨터 개체를 구성합니다.

## 이 단원의 내용

  - [Lync Server 2013의 Kerberos 인증을 사용하기 위한 필수 구성 요소](lync-server-2013-prerequisites-for-enabling-kerberos-authentication.md)

  - [Lync Server 2013에서 Kerberos 인증 계정 만들기](lync-server-2013-create-a-kerberos-authentication-account.md)

  - [Lync Server 2013에서 사이트에 Kerberos 인증 계정 할당](lync-server-2013-assign-a-kerberos-authentication-account-to-a-site.md)

  - [Lync Server 2013에서 Kerberos 인증 계정 암호 설정](lync-server-2013-setting-up-kerberos-authentication-account-passwords.md)

  - [Lync Server 2013에서 다른 사이트에 Kerberos 인증 추가](lync-server-2013-add-kerberos-authentication-to-other-sites.md)

  - [Lync Server 2013의 사이트에서 Kerberos 인증 제거](lync-server-2013-remove-kerberos-authentication-from-a-site.md)

  - [Lync Server 2013에서 Kerberos 인증 상태 및 할당 테스트 및 보고](lync-server-2013-testing-and-reporting-the-status-and-assignment-of-kerberos-authentication.md)

