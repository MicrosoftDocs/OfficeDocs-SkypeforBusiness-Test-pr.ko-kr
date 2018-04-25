---
title: Lync Server에 보관할 사용자 정책 설정
TOCTitle: Lync Server에 보관할 사용자 정책 설정
ms:assetid: 22d6cc76-6b5c-4a8c-bb8a-7996450ec085
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204742(v=OCS.15)
ms:contentKeyID: 49303055
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server에 보관할 사용자 정책 설정

 

_**마지막으로 수정된 항목:** 2012-10-10_

Lync Server 2013에 있는 특정 사용자에 대해 보관을 사용하거나 사용하지 않도록 설정하려면 하나 이상의 사용자 정책을 만들고 구성한 다음 특정 사용자 또는 사용자 그룹에 적절한 정책을 적용해야 합니다. 사용자 정책은 Lync Server 2013에 있는 사용자에 한해 사이트 및 글로벌 정책을 재정의합니다.

사용자는 항상 Lync Server에 있습니다. Microsoft Exchange 통합을 사용하도록 설정한 경우 사서함이 Microsoft Exchange Server 2013에 있는 사용자는 Lync Server에서 해당 보관 정책을 관리하지 않아도 됩니다. 보관을 사용하는 이러한 사용자는 Exchange 원본 위치 유지를 통해 관리됩니다.

글로벌, 사이트 및 사용자 정책의 계층 구조를 비롯하여 보관 정책이 작동하는 방식에 대한 자세한 내용은 계획 설명서, 배포 설명서 또는 작업 설명서에서 [Lync Server 2013의 보관 작동 방식](lync-server-2013-how-archiving-works.md)을 참조하십시오.


> [!NOTE]
> 배포에 대해 Microsoft Exchange 통합을 사용하도록 설정한 경우 Exchange 원본 위치 유지 정책은 Exchange 2013에 있는 사용자에 대해 보관이 사용하도록 설정되는지 여부를 제어합니다. 이러한 사용자에 대해 보관을 사용하려면 해당 사서함이 원본 위치 유지 상태여야 합니다. 자세한 내용은 배포 설명서에서 <A href="lync-server-2013-setting-up-policies-for-archiving-when-using-exchange-server-integration.md">Exchange Server 통합 사용 시 보관용 정책 설정</A>을 참조하십시오.<BR>보관을 사용하도록 설정하기 전에 보관 구성에서 해당하는 모든 옵션을 지정해야 합니다. 자세한 내용은 배포 설명서에서 <A href="lync-server-2013-configuring-archiving-options.md">보관 옵션 구성</A>을 참조하십시오.



## 이 단원의 내용

  - [Lync Server에서 보관용 사용자 정책 만들기 및 구성](lync-server-2013-creating-and-configuring-user-policies-for-archiving-in-lync-server.md)

  - [사용자에게 Lync Server 보관 정책 적용](lync-server-2013-applying-a-lync-server-archiving-policy-to-a-user.md)

