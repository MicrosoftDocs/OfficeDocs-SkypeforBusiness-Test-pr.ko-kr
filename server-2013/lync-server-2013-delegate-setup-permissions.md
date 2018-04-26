---
title: 'Lync Server 2013: 설치 권한 위임'
TOCTitle: 설치 권한 위임
ms:assetid: 9dca1683-4c69-4534-8ebe-6bd635cbae49
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412735(v=OCS.15)
ms:contentKeyID: 49304538
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 설치 권한 위임

 

_**마지막으로 수정된 항목:** 2014-02-05_

Lync Server 2013을 배포하는 사용자나 그룹에 Domain Admins 그룹의 구성원 자격을 부여하지 않으려면 RTCUniversalServerAdmins 그룹 구성원이 Lync Server 2013을 실행하는 서버에서 **Enable-CsTopology**Windows PowerShell cmdlet을 실행할 수 있도록 설정하면 됩니다. 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 이 cmdlet을 실행할 수 없습니다. Lync Server를 실행하는 서버에서 **Enable-CsTopology**를 실행할 수 있는 권한과 관리자 권한은 **Grant-CsSetupPermission** cmdlet을 사용하고 Lync Server 2013를 실행하는 서버에 대한 컴퓨터 개체가 있는 OU(조직 구성 단위)를 지정하여 부여할 수 있습니다.

Lync Server를 설치할 때 수행되는 도메인 준비에서는 RTCUniversalServerAdmins 그룹의 구성원이 Enable-CsTopology cmdlet을 실행할 수 있는 권한을 자동으로 추가하지 않습니다. 이는 기본적으로 토폴로지를 사용하려면 도메인 관리자여야 함을 의미합니다. RTCUniversalServerAdmins 그룹의 구성원에게 토폴로지를 사용할 수 있는 권한을 부여하려면 Grant-CsSetupPermissions cmdlet을 실행해야 합니다. 또한 Lync Server를 실행하는 컴퓨터가 속해 있는 각 Active Directory 컨테이너에 대해 이 cmdlet을 실행해야 합니다.

이 cmdlet은 RTCUniversalServerAdmins 그룹에만 사용 권한을 부여하며, 다른 보안 그룹 또는 개별 사용자에게 사용 권한을 부여하는 데는 사용할 수 없습니다.


> [!NOTE]
> <STRONG>Enable-CsTopology</STRONG>는 RTCUniversalServerAdmins 그룹 구성원이 Lync Server 2013를 설치 및 배포할 수 있도록 해주는 핵심 cmdlet입니다.



## RTCUniversalServerAdmins 그룹에 Enable-CsTopology를 실행할 수 있는 권한을 추가하려면

1.  위임된 사용자가 **Enable-CsTopology**를 실행하는 도메인에 대한 Domain Admins 그룹의 구성원으로 서버에 로그온합니다.

2.  Lync Server 2013 관리 셸을 엽니다. Lync Server 2013 관리 셸은 Lync Server 2013 관리 도구가 설치된 각 프런트 엔드 서버 또는 컴퓨터에 자동으로 설치됩니다. Lync Server 2013 관리 셸에 대한 자세한 내용은 작업 설명서에서 [Lync Server 관리 셸](lync-server-2013-lync-server-management-shell.md)을 참조하십시오.

3.  Lync Server 2013 관리 셸에서 다음 cmdlet을 실행합니다.
    
        Grant-CsSetupPermission -ComputerOU <DN of the OU> -Domain <Domain FQDN>
    

    > [!NOTE]
    > OU가 최상위 수준이 아닌 경우 전체 도메인 이름을 제공해야 합니다.

    
    다음 예에서 OU는 contoso.com 도메인에 있는 "Lync Server"입니다.
    
        Grant-CsSetupPermission -ComputerOU "OU=Lync Servers" -Domain contoso.com

