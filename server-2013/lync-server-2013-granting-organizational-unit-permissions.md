---
title: 'Lync Server 2013: 조직 구성 단위 권한 부여'
TOCTitle: 조직 구성 단위 권한 부여
ms:assetid: 95ee5ffa-39b1-4d80-87a2-27bb364f7396
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398763(v=OCS.15)
ms:contentKeyID: 49304438
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 조직 구성 단위 권한 부여

 

_**마지막으로 수정된 항목:** 2012-05-14_

포리스트 준비에서 만든 RTC 유니버설 그룹의 구성원이 Domain Admins 그룹의 구성원이 되지 않고도 지정된 OU(조직 구성 단위)에 있는 개체에 액세스할 수 있도록 **Grant-CsOuPermission** cmdlet을 사용하여 해당 개체에 권한을 부여할 수 있습니다. 지정된 OU에 추가된 권한은 도메인 준비가 진행되는 동안 **Enable-CsAdDomain** cmdlet이 컴퓨터 및 사용자 컨테이너에 추가하는 권한과 동일합니다.

**Test-CsOuPermission** cmdlet을 통해 설치하는 권한을 확인합니다. 이렇게 하려면 **Grant-CsOuPermission** cmdlet을 사용합니다.

**Revoke-CsOuPermission** cmdlet을 통해 부여한 권한을 제거할 수 있습니다. 이렇게 하려면 **Grant-CsOuPermission** cmdlet을 사용합니다.

## OU 권한을 부여하려면

1.  OU 권한을 부여할 도메인에서 Lync Server 2013을 실행 중인 컴퓨터에 로그온합니다. Domain Admins 그룹 또는 Enterprise Admins 그룹(OU가 다른 하위 도메인에 있는 경우)의 구성원인 계정을 사용합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  다음을 실행합니다.
    
        Grant-CsOuPermission -ObjectType <User | Computer | InetOrgPerson | Contact | AppContact | Device> -OU <DN of the OU> [-Domain <Domain FQDN>]
    
    Domain 매개 변수를 지정하지 않는 경우에는 로컬 도메인이 기본값으로 사용됩니다.

## OU 권한을 확인하려면

1.  **Grant-CsOuPermission** cmdlet을 사용하여 부여한 OU 권한을 확인할 도메인에서 Lync Server 2013을 실행 중인 컴퓨터에 로그온합니다. Domain Admins 그룹 또는 Enterprise Admins 그룹(OU가 다른 하위 도메인에 있는 경우)의 구성원인 계정을 사용합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  다음을 실행합니다.
    
        Test-CsOuPermission -ObjectType <User | Computer | InetOrgPerson | Contact | AppContact | Device> -OU <DN of the OU> [-Domain <Domain FQDN>]
    
    Domain 매개 변수를 지정하지 않는 경우에는 로컬 도메인이 기본값으로 사용됩니다.

## OU 권한을 해지하려면

1.  **Grant-CsOuPermission** cmdlet을 사용하여 부여한 OU 권한을 해지할 도메인에서 Lync Server 2013을 실행 중인 컴퓨터에 로그온합니다. Domain Admins 그룹 또는 Enterprise Admins 그룹(OU가 다른 하위 도메인에 있는 경우)의 구성원인 계정을 사용합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  다음을 실행합니다.
    
        Revoke-CsOuPermission -ObjectType <User | Computer | InetOrgPerson | Contact | AppContact | Device> -OU <DN of the OU> [-Domain <Domain FQDN>]
    
    Domain 매개 변수를 지정하지 않는 경우에는 로컬 도메인이 기본값으로 사용됩니다.

