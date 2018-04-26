---
title: 'Lync Server 2013: Computer, User 또는 InetOrgPerson 컨테이너에서 권한 상속이 비활성화됨'
TOCTitle: Computer, User 또는 InetOrgPerson 컨테이너에서 권한 상속이 비활성화됨
ms:assetid: c472ad21-a93d-4fcb-a3d9-60a2134a87fa
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412970(v=OCS.15)
ms:contentKeyID: 49304966
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 Computer, User 또는 InetOrgPerson 컨테이너에서 권한 상속이 비활성화됨

 

_**마지막으로 수정된 항목:** 2014-12-19_

잠겨 있는 Active Directory 도메인 서비스에서는 관리 위임의 보안을 유지하고 보안 정책 적용을 위한 GPO(그룹 정책 개체) 사용을 활성화하기 위해 사용자 및 컴퓨터 개체를 사용 권한 상속이 비활성화된 특정 OU(조직 구성 단위)에 두는 경우가 자주 있습니다.

도메인 준비 및 서버 활성화는 Lync Server 2013에서 필요한 ACE(액세스 제어 항목)를 설정합니다. 사용 권한 상속이 비활성화되면 Lync Server 보안 그룹은 이러한 ACE를 상속할 수 없습니다. 이러한 사용 권한을 상속하지 못하면 Lync Server 보안 그룹은 설정에 액세스하지 못하게 되며 다음 두 가지 문제가 발생합니다.

  - 사용자, InetOrgPerson 및 대화 상대를 관리하고 서버를 운영하기 위해서는 Lync Server 보안 그룹에 RTC(실시간 통신), RTC 사용자 검색, 공용 정보 등 각 사용자 속성 집합에 대해 도메인 준비 절차에서 설정한 ACE가 있어야 합니다. 사용 권한 상속이 비활성화되면 보안 그룹이 이러한 ACE를 상속하지 못하며 서버나 사용자를 관리할 수 없습니다.

  - 서버와 풀을 검색하기 위해 Lync Server 실행 서버는 Microsoft 컨테이너와 Server 개체를 비롯한 컴퓨터 관련 개체에 대한 활성화에서 설정한 ACE를 사용합니다. 사용 권한 상속이 비활성화되면 보안 그룹, 서버 및 풀이 이러한 ACE를 상속하지 않으므로 이러한 ACE를 활용할 수 없습니다.

Lync Server에서 제공한 **Grant-CsOuPermission** cmdlet를 사용하면 이러한 문제를 해결할 수 있습니다. 이 cmdlet는 지정된 컨테이너 및 조직 구성 단위 및 컨테이너나 조직 구성 단위 내 개체에 대해 필요한 Lync Server ACE를 직접 설정합니다.

## 도메인 준비 실행 후 사용자, InetOrgPerson 및 연락처 개체에 대한 사용 권한 설정

사용 권한 상속이 비활성화된 경우 잠겨 있는 Active Directory 환경에서는 도메인 준비 중에 도메인 내의 사용자 또는 InetOrgPerson 개체를 보유하는 컨테이너나 조직 구성 단위에 대해 필요한 ACE가 설정되지 않습니다. 이 상황에서는 사용 권한 상속이 비활성화된 사용자 또는 InetOrgPerson 개체가 있는 각 컨테이너나 OU에 대해 **Grant-CsOuPermission** cmdlet를 실행해야 합니다. 중앙 포리스트 토폴로지가 있는 경우 대화 상대 개체를 보유하는 컨테이너나 OU에 대해서도 이 절차를 수행해야 합니다. 중앙 포리스트 토폴로지에 대한 자세한 내용은 지원 가능성 설명서에서 [Lync Server 2013에서 지원되는 Active Directory 토폴로지](lync-server-2013-supported-active-directory-topologies.md)를 참조하십시오. ObjectType 매개 변수는 개체 유형을 지정합니다. OU 매개 변수는 조직 구성 단위를 지정합니다.

이 cmdlet는 지정된 컨테이너나 OU 및 컨테이너 내의 사용자 또는 InetOrgPerson 개체에 대해 필요한 ACE를 직접 추가합니다.

이 cmdlet를 실행하려면 Domain Admins 그룹의 구성원 자격과 동등한 사용자 권한이 필요합니다. 잠겨 있는 환경에서 인증된 사용자 ACE도 제거된 경우 [Lync Server 2013에서 인증된 사용자 권한이 제거됨](lync-server-2013-authenticated-user-permissions-are-removed.md)에서 설명한 대로 이 계정에 포리스트 루트 도메인의 관련 컨테이너나 OU에 대한 읽기 권한 ACE를 부여하거나 EnterpriseAdmins 그룹 구성원인 계정을 사용해야 합니다.

**사용자, InetOrgPerson 및 연락처 개체에 대해 필요한 ACE를 설정하려면**

1.  Domain Admins 그룹의 구성원이거나 이와 동등한 사용자 권한을 가진 계정을 사용하여 도메인에 가입된 컴퓨터에 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  다음을 실행합니다.
    
        Grant-CsOuPermission -ObjectType <User | Computer | InetOrgPerson | Contact | AppContact | Device> 
        -OU <DN name for the OU container relative to the domain root container DN> [-Domain <Domain FQDN>]
    
    Domain 매개 변수를 지정하지 않는 경우에는 로컬 도메인이 기본값으로 사용됩니다.
    
    예를 들면 다음과 같습니다.
    
        Grant-CsOuPermission -ObjectType "User" -OU "cn=Redmond,dc=contoso,dc=net" -Domain "contoso.net"

4.  로그 파일에서 각 작업 끝의 **\<성공\>** 실행 결과를 찾아서 사용 권한이 설정되었는지 확인한 다음 로그 창을 닫습니다. 또는 다음 명령을 실행하여 사용 권한이 설정되었는지 확인할 수 있습니다.
    
        Test-CsOuPermission -ObjectType <type of object> 
        -OU <DN name for the OU container relative to the domain root container DN> 
        [-Domain <Domain FQDN>] [-Report <fully qualified path and name of file to create>]
    
    예를 들면 다음과 같습니다.
    
        Test-CsOuPermission -ObjectType "User" -OU "cn=Redmond,dc=contoso,dc=net" -Domain "contoso.net" -Report "C:\Log\OUPermissionsTest.html"

## 도메인 준비 실행 후 컴퓨터 개체에 대한 사용 권한 설정

사용 권한 상속이 비활성화된 경우 잠겨 있는 Active Directory 환경에서는 도메인 준비 중에 도메인 내의 컴퓨터 개체를 보유하는 컨테이너나 OU에 대해 필요한 ACE가 설정되지 않습니다. 이 상황에서는 사용 권한 상속이 비활성화된 Lync Server를 실행하는 컴퓨터가 있는 각 컨테이너나 OU에 대해 **Grant-CsOuPermission** cmdlet를 실행해야 합니다. ObjectType 매개 변수는 개체 유형을 지정합니다.

이 절차는 지정된 컨테이너에 대해 필요한 ACE를 직접 추가합니다.

이 cmdlet를 실행하려면 Domain Admins 그룹의 구성원 자격과 동등한 사용자 권한이 필요합니다. 인증된 사용자 ACE도 제거된 경우 [Lync Server 2013에서 인증된 사용자 권한이 제거됨](lync-server-2013-authenticated-user-permissions-are-removed.md)에서 설명한 대로 이 계정에 포리스트 루트 도메인의 관련 컨테이너에 대한 읽기 권한 ACE를 부여하거나 Enterprise Admins 그룹 구성원인 계정을 사용해야 합니다.

**컴퓨터 개체에 대해 필요한 ACE를 설정하려면**

1.  Domain Admins 그룹의 구성원이거나 이와 동등한 사용자 권한을 가진 계정을 사용하여 도메인 컴퓨터에 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  다음을 실행합니다.
    
        Grant-CsOuPermission -ObjectType <Computer> 
        -OU <DN name for the computer OU container relative to the domain root container DN> 
        [-Domain <Domain FQDN>][-Report <fully qualified path and name of output report>]
    
    Domain 매개 변수를 지정하지 않는 경우에는 로컬 도메인이 기본값으로 사용됩니다.
    
    예를 들면 다음과 같습니다.
    
        Grant-CsOuPermission -ObjectType "Computer" -OU "ou=Lync Servers,dc=litwareinc,dc=com" -Report "C:\Logs\OUPermissions.xml"

4.  예 로그 파일 C:\\Logs\\OUPermissions.xml에서 각 작업 끝의 **\<성공\>** 실행 결과를 찾아서 오류가 없는지 확인한 다음 로그를 닫습니다. 다음 cmdlet를 실행하여 사용 권한을 테스트할 수 있습니다.
    
        Test-CsOuPermission -ObjectType <type of object> 
        -OU <DN name for the OU container relative to the domain root container DN> [-Domain <Domain FQDN>]
    
    예를 들면 다음과 같습니다.
    
        Test-CsOuPermission -ObjectType "user","contact" -OU "cn=Bellevue,dc=contoso,dc=net" -Domain "contoso.net"
    

    > [!NOTE]
    > 잠겨 있는 Active Directory 환경의 포리스트 루트 도메인에서 도메인 준비를 실행하는 경우 Lync Server에는 Active Directory 스키마 및 구성 컨테이너에 대한 액세스 권한이 필요합니다.<BR>기본 인증된 사용자 권한이 AD DS의 스키마 또는 구성 컨테이너에서 제거된 경우에는 Schema Admins 그룹(스키마 컨테이너의 경우) 또는 EnterpriseAdmins 그룹(구성 컨테이너의 경우)의 구성원만 이러한 컨테이너에 액세스할 수 있습니다. Setup.exe, Lync Server 관리 셸 cmdlet 및 Lync Server 제어판에서는 이러한 컨테이너에 액세스해야 하므로 설치를 실행하는 사용자에게 Schema Admins 및 Enterprise Admins 그룹 구성원 자격과 동등한 사용자 권한이 없으면 설치 프로그램과 관리 도구 설치가 실패합니다.<BR>이 문제를 해결하려면 RTCUniversalGlobalWriteGroup 그룹에 해당 스키마 및 구성 컨테이너에 대한 읽기/쓰기 권한을 부여해야 합니다.


