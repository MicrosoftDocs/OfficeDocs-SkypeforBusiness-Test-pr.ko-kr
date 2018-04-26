---
title: 'Lync Server 2013: 설치 권한 부여'
TOCTitle: 설치 권한 부여
ms:assetid: 15982bfe-6844-44f6-815a-72dcaf0e4d21
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398225(v=OCS.15)
ms:contentKeyID: 49302907
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 설치 권한 부여

 

_**마지막으로 수정된 항목:** 2012-08-27_

**Grant-CsSetupPermission** cmdlet을 사용하여 지정된 Active Directory OU(조직 구성 단위)의 RTCUniversalServerAdmins 그룹에 Read, Write, ReadSPN 및 WriteSPN 권한을 추가할 수 있습니다. 그리고 나면 해당 OU의 RTCUniversalServerAdmins 구성원이 Domain Admins 그룹의 구성원이 아니어도 지정된 도메인에서 Lync Server 2013을 실행하는 서버를 설치할 수 있습니다.

**Test-CsSetupPermission** cmdlet을 통해 설치하는 권한을 확인합니다. 이렇게 하려면 **Grant-CsSetupPermission** cmdlet을 사용합니다.

**Revoke-CsSetupPermission** cmdlet을 통해 부여한 권한을 제거할 수 있습니다. 이렇게 하려면 **Grant-CsSetupPermission** cmdlet을 사용합니다.

## 설치 권한을 부여하려면

1.  설치 권한을 부여할 도메인에서 Lync Server 2013을 실행하는 컴퓨터에 로그온합니다. Domain Admins 그룹 또는 Enterprise Admins 그룹(OU가 다른 하위 도메인에 있는 경우)의 구성원인 계정을 사용합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  다음을 실행합니다.
    
        Grant-CsSetupPermission -ComputerOu <DN of the OU or container where the computer objects that will run Lync Server reside > [-Domain <Domain FQDN>]
    
    지정된 도메인의 기본 명명 컨텍스트를 기준으로 ComputerOu 매개 변수를 지정할 수 있습니다(예: CN=computers). 이 매개 변수를 전체 OU DN(고유 이름)으로 지정할 수도 있습니다(예: "CN=computers,DC=Contoso,DC=com"). 이 경우에는 지정하는 도메인과 일치하도록 OU DN을 지정해야 합니다.
    
    Domain 매개 변수를 지정하지 않는 경우에는 로컬 도메인이 기본값으로 사용됩니다.

## 설치 권한을 확인하려면

1.  **Grant-CsSetupPermission** cmdlet을 사용하여 부여한 설치 권한을 확인할 도메인에서 Lync Server 2013을 실행하는 컴퓨터에 로그온합니다. Domain Admins 그룹 또는 Enterprise Admins 그룹(OU가 다른 하위 도메인에 있는 경우)의 구성원인 계정을 사용합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  다음을 실행합니다.
    
        Test-CsSetupPermission -ComputerOu <DN of the OU or container where the computer objects that will run Lync Server reside> [-Domain <Domain FQDN>]
    
    지정된 도메인의 기본 명명 컨텍스트를 기준으로 ComputerOu 매개 변수를 지정할 수 있습니다(예: CN=computers). 이 매개 변수를 전체 OU DN(고유 이름)으로 지정할 수도 있습니다(예: "CN=computers,DC=Contoso,DC=com"). 이 경우에는 지정하는 도메인과 일치하도록 OU DN을 지정해야 합니다.
    
    Domain 매개 변수를 지정하지 않는 경우에는 로컬 도메인이 기본값으로 사용됩니다.

## 설치 권한을 해지하려면

1.  **Grant-CsSetupPermission** cmdlet을 사용하여 부여한 설치 권한을 해지할 도메인에서 Lync Server 2013을 실행하는 컴퓨터에 로그온합니다. Domain Admins 그룹 또는 Enterprise Admins 그룹(OU가 다른 하위 도메인에 있는 경우)의 구성원인 계정을 사용합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  다음을 실행합니다.
    
        Revoke-CsSetupPermission -ComputerOu <DN of the OU or container where the computer objects that will run Lync Server reside > [-Domain <Domain FQDN>]
    
    지정된 도메인의 기본 명명 컨텍스트를 기준으로 ComputerOu 매개 변수를 지정할 수 있습니다(예: CN=computers). 이 매개 변수를 전체 OU DN(고유 이름)으로 지정할 수도 있습니다(예: "CN=computers,DC=Contoso,DC=com"). 이 경우에는 지정하는 도메인과 일치하도록 OU DN을 지정해야 합니다.
    
    Domain 매개 변수를 지정하지 않는 경우에는 로컬 도메인이 기본값으로 사용됩니다.

