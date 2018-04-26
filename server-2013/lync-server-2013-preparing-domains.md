---
title: 'Lync Server 2013: 도메인 준비'
TOCTitle: 도메인 준비
ms:assetid: 8eea541c-5f9d-4afc-92a8-a31d6f742544
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398721(v=OCS.15)
ms:contentKeyID: 49304354
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에 대한 도메인 준비

 

_**마지막으로 수정된 항목:** 2012-10-29_

도메인 준비는 Lync Server 2013에 대해 Active Directory 도메인 서비스를 준비하는 마지막 단계입니다. 도메인 준비 단계에서는 호스트에 권한을 부여하고 도메인 내의 사용자를 관리하는 유니버설 그룹에 필요한 ACE(액세스 제어 항목)를 추가합니다. 도메인 준비는 도메인 루트와 세 개의 기본 제공 컨테이너인 사용자, 컴퓨터 및 도메인 컨트롤러에 ACE를 만듭니다.

Lync Server를 배포하고 있는 도메인의 모든 컴퓨터에서 도메인 준비를 실행할 수 있습니다. Lync Server 또는 사용자를 호스팅할 모든 도메인을 준비해야 합니다.

조직에서 권한 상속이 비활성화되어 있거나 인증된 사용자 권한을 비활성화해야 하는 경우 도메인 준비 작업 중에 추가 단계를 수행해야 합니다. 자세한 내용은 [Lync Server 2013에서 잠긴 Active Directory 도메인 서비스 준비](lync-server-2013-preparing-a-locked-down-active-directory-domain-services.md)를 참조하십시오.

조직에서 세 개의 기본 제공 컨테이너(즉, 사용자, 컴퓨터 및 도메인 컨트롤러) 대신에 OU(조직 구성 단위)를 사용하는 경우 OU에 Authenticated Users 그룹에 대한 읽기 권한을 부여해야 합니다. 컨테이너에 대한 읽기 권한은 도메인을 준비하는 데 필요합니다. Authenticated Users 그룹에 OU에 대한 읽기 권한이 없는 경우 각 OU에 읽기 권한을 부여하는 다음 코드 예제와 같이 **Grant-CsOuPermission** cmdlet을 실행합니다.

    Grant-CsOuPermission -ObjectType <User | Computer | InetOrgPerson | Contact | AppContact | Device> -OU <DN of the OU > 

    Grant-CsOuPermission -ObjectType "user","contact",inetOrgPerson" -OU "ou=Redmond,dc=contoso,dc=net"

**Grant-CsOuPermission** cmdlet에 대한 자세한 내용은 Lync Server 관리 셸 설명서를 참조하십시오.


> [!TIP]
> 도메인 루트와 사용자, 컴퓨터 및 도메인 컨트롤러 컨테이너에서 만들어진 ACE에 대한 자세한 내용은 <A href="lync-server-2013-changes-made-by-domain-preparation.md">Lync Server 2013에서 도메인 준비로 인한 변경</A>을 참조하십시오.



## 이 단원의 내용

  - [Lync Server 2013에 대한 도메인 준비 실행](lync-server-2013-running-domain-preparation.md)

  - [Lync Server 2013에 대해 cmdlet을 사용하여 도메인 준비 되돌리기](lync-server-2013-using-cmdlets-to-reverse-domain-preparation.md)

