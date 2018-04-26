---
title: 'Lync Server 2013: 잠긴 Active Directory 도메인 서비스 준비'
TOCTitle: 잠긴 Active Directory 도메인 서비스 준비
ms:assetid: 68bde963-3fa3-4102-88d6-ac931c1dd2d7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398492(v=OCS.15)
ms:contentKeyID: 49303908
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 잠긴 Active Directory 도메인 서비스 준비

 

_**마지막으로 수정된 항목:** 2012-05-14_

조직에서는 보안 위험을 완화하기 위해 Active Directory 도메인 서비스를 잠그는 경우가 많습니다. 그러나 Active Directory 환경이 잠겨 있으면 Lync Server 2013에 필요한 사용 권한이 제한될 수 있습니다. 잠겨 있는 Lync Server 2013용 Active Directory 환경을 올바르게 준비하려면 추가 사항을 고려하고 단계를 수행해야 합니다.

잠겨 있는 Active Directory 환경에서 사용 권한이 제한되는 일반적인 두 가지 방식은 다음과 같습니다.

  - 인증된 사용자 ACE(액세스 제어 항목)가 컨테이너에서 제거됩니다.

  - User, Contact, InetOrgPerson 또는 Computer 개체의 컨테이너에서 권한 상속이 비활성화됩니다.

## 이 섹션의 내용

  - [Lync Server 2013에서 인증된 사용자 권한이 제거됨](lync-server-2013-authenticated-user-permissions-are-removed.md)

  - [Lync Server 2013의 Computer, User 또는 InetOrgPerson 컨테이너에서 권한 상속이 비활성화됨](lync-server-2013-permissions-inheritance-is-disabled-on-computers-users-or-inetorgperson-containers.md)

