---
title: 'Lync Server 2013: IIS 보호'
TOCTitle: Lync Server 2013에서 IIS 보호
ms:assetid: a67171a6-6703-4e09-abb3-35d335bb674e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn518332(v=OCS.15)
ms:contentKeyID: 60504742
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 IIS 보호

 

_**마지막으로 수정된 항목:** 2013-12-05_

Microsoft Office Communications Server 2007 및 Microsoft Office Communications Server 2007 R2에서 IIS(Internet Information Services)는 표준 사용자 계정으로 실행되었으며 이로 인해 문제가 발생할 수 있었습니다. 즉, 해당 암호가 만료된 경우 웹 서비스가 손실될 수 있었으며, 이 문제는 진단하기 어려운 경우가 많았습니다. 암호 만료 문제를 방지하기 위해 Microsoft Lync Server 2013에서 실제로 존재하지 않는 컴퓨터에 대해 컴퓨터 계정을 만들 수 있습니다. 이 계정은 IIS를 실행하는 사이트의 모든 컴퓨터에 대해 인증 사용자 역할을 할 수 있습니다. 이러한 계정은 Kerberos 인증 프로토콜을 사용하므로 Kerberos 계정이라고 하며, 새 인증 프로세스를 Kerberos 웹 인증이라고 합니다. 이를 통해 단일 계정으로 모든 IIS 서버를 관리할 수 있습니다.

이 인증 주체로 서버를 실행하려면 먼저 New-CsKerberosAccount cmdlet을 사용하여 컴퓨터 계정을 만들어야 합니다. 그러면 이 계정이 하나 이상의 사이트에 할당됩니다. 계정이 할당된 후에는 Enable-CsTopology cmdlet을 실행하여 계정과 Lync Server 2013 사이트 간의 연결을 활성화합니다. 이렇게 하면 필요한 SPN(서비스 사용자 이름)이 AD DS(Active Directory 도메인 서비스)에 만들어집니다. 클라이언트 응용 프로그램은 SPN을 통해 특정 서비스를 찾을 수 있습니다. 자세한 내용은 작업 설명서에서 [New-CsKerberosAccount](new-cskerberosaccount.md)를 참조하세요.

## 유용한 정보

IIS의 보안을 향상시키기 위해서는 IIS에 대해 Kerberos 계정을 구현하는 것이 좋습니다. Kerberos 계정을 구현하지 않을 경우 IIS는 표준 사용자 계정으로 실행됩니다.

