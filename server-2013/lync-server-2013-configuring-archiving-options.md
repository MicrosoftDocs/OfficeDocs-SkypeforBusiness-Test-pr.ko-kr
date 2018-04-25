---
title: 보관 옵션 구성
TOCTitle: 보관 옵션 구성
ms:assetid: b2f7f74d-e1ad-494e-9d46-5eb0efe5fb29
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205182(v=OCS.15)
ms:contentKeyID: 49304770
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 보관 옵션 구성

 

_**마지막으로 수정된 항목:** 2012-10-10_

Lync Server 2013 제어판에서는 보관 구성을 사용하여 보관이 구현되는 방식을 지정합니다. 여기에는 다음과 같은 보관 구성이 포함됩니다.

  - Lync Server 2013을 배포할 때 기본적으로 만들어지는 전역 구성

  - 특정 사이트 또는 풀에 대해 보관이 구현되는 방식을 지정하도록 만들어서 사용하는 선택적인 사이트 수준 및 풀 수준 구성

보관을 배포할 때 처음으로 보관 구성을 설정하게 되며, 배포 후에 구성을 변경, 추가 및 삭제할 수 있습니다. Lync Server 2013 제어판에서는 **보관 및 모니터링** 그룹의 **보관 구성** 페이지를 사용하여 전역 수준, 사이트 수준 및 풀 수준으로 구성을 관리할 수 있습니다. 지정할 수 있는 옵션과 보관 구성의 계층 구조를 비롯하여 보관 구성이 구현되는 방식에 대한 자세한 내용은 계획 설명서, 배포 설명서 또는 작업 설명서에서 [Lync Server 2013의 보관 작동 방식](lync-server-2013-how-archiving-works.md)을 참조하십시오. 배포 후에 구성을 관리하는 방법에 대한 자세한 내용은 작업 설명서에서 [Lync Server 2013에서 조직, 사이트 및 풀에 대한 보관 구성 옵션 관리](lync-server-2013-managing-archiving-configuration-options-for-your-organization-sites-and-pools.md)를 참조하십시오.


> [!NOTE]
> 보관을 사용하려면 Lync Server 2013에 속한 사용자가 내부 통신, 외부 통신 또는 둘 다에 대해 보관을 사용할 수 있도록 할지를 지정하는 보관 정책을 구성해야 합니다. 기본적으로 내부 통신 또는 외부 통신에 대한 보관이 사용할 수 없도록 설정됩니다. 정책에 보관을 사용할 수 있도록 설정하기 전에 이 섹션에 설명된 대로 배포 및 선택적으로 특정 사이트와 풀에 대해 적절한 보관 구성을 지정해야 합니다. 보관을 사용할 수 있도록 설정하는 방법에 대한 자세한 내용은 배포 설명서에서 <A href="lync-server-2013-configuring-and-assigning-archiving-policies.md">보관 정책 구성 및 할당</A>을 참조하십시오.<BR>배포의 일부 사용자에 대해 Microsoft Exchange 통합을 사용하지 않는 경우 내부 통신, 외부 통신 또는 둘 다에 대해 보관을 사용할 수 있도록 설정할지를 지정하는 보관 정책을 구성해야 합니다. 기본적으로 Lync Server 2013 보관 데이터베이스를 사용할 때 데이터를 보관하기 위한 내부 통신 또는 외부 통신에 대한 보관이 사용할 수 없도록 설정됩니다. 정책에 보관을 사용할 수 있도록 설정하기 전에 이 섹션에 설명된 대로 배포 및 선택적으로 특정 사이트와 풀에 대해 적절한 보관 구성을 지정해야 합니다. Lync Server 2013 보관 데이터베이스와 함께 사용하도록 보관을 사용할 수 있도록 설정하는 방법에 대한 자세한 내용은 배포 설명서에서 <A href="lync-server-2013-configuring-and-assigning-archiving-policies.md">보관 정책 구성 및 할당</A>을 참조하십시오.



## 이 단원의 내용

  - [전역 수준의 보관 옵션 구성](lync-server-2013-configuring-archiving-options-at-the-global-level.md)

  - [사이트에 대한 보관 옵션 구성](lync-server-2013-configuring-archiving-options-for-a-site.md)

  - [풀에 대한 보관 옵션 구성](lync-server-2013-configuring-archiving-options-for-a-pool.md)

