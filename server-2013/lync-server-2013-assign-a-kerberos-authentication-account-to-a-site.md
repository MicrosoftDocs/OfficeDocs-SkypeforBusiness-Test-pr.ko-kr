---
title: 'Lync Server 2013: 사이트에 Kerberos 인증 계정 할당'
TOCTitle: 사이트에 Kerberos 인증 계정 할당
ms:assetid: 3d9c587c-c8b8-4f81-8ed9-1458a31fc292
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425901(v=OCS.15)
ms:contentKeyID: 49303396
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 사이트에 Kerberos 인증 계정 할당

 

_**마지막으로 수정된 항목:** 2012-01-16_

이 절차를 성공적으로 완료하려면 RTCUniversalServerAdmins 그룹의 구성원인 사용자로 로그온해야 합니다.

Kerberos 계정을 만든 후 이를 사이트에 지정해야 합니다. 이 사이트는 Lync Server 2013 사이트이며 Active Directory 사이트가 아닙니다. 배포별로 여러 개의 Kerberos 인증 계정을 만들 수 있지만 사이트에는 계정을 하나만 지정할 수 있습니다. 다음 절차에 따라 이전에 만든 Kerberos 인증 계정을 사이트에 지정하십시오. Kerberos 계정을 만드는 방법에 대한 자세한 내용은 [Lync Server 2013에서 Kerberos 인증 계정 만들기](lync-server-2013-create-a-kerberos-authentication-account.md)를 참조하십시오.

## Kerberos 인증 계정을 사이트에 지정하려면

1.  RTCUniversalServerAdmins 그룹의 구성원으로 Lync Server 2013을 실행하는 도메인의 컴퓨터 또는 관리 도구가 설치된 컴퓨터에 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  명령줄에서 다음의 두 명령을 실행합니다.
    
        New-CsKerberosAccountAssignment -UserAccount "Domain\UserAccount" -Identity "site:SiteName"
    
        Enable-CsTopology
    
    예를 들면 다음과 같습니다.
    
        New-CsKerberosAccountAssignment -UserAccount "contoso\kerbauth" -Identity "site:redmond"
    
        Enable-CsTopology
    

    > [!NOTE]
    > 도메인\사용자 형식을 사용하여 UserAccount 매개 변수를 지정해야 합니다. User@Domain.extension 형식은 Kerberos 인증 용도로 만든 컴퓨터 개체를 나타내는 데 사용할 수 없습니다.

    

    > [!IMPORTANT]
    > 계정을 추가하거나 제거하는 등 Kerberos 인증을 변경한 후에는 Lync Server 관리 셸 명령 프롬프트에서 <STRONG>Enable-CsTopology</STRONG>를 실행해야 합니다.


