---
title: Lync Server 2013에서 내부 및 외부 통신의 보관 관리
TOCTitle: Lync Server 2013에서 내부 및 외부 통신의 보관 관리
ms:assetid: 6c2cf941-3204-4f1a-a7e0-416c828056d9
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204977(v=OCS.15)
ms:contentKeyID: 49303955
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 내부 및 외부 통신의 보관 관리

 

_**마지막으로 수정된 항목:** 2012-10-09_

Lync Server 2013에서는 Microsoft Exchange 통합을 사용하지 않을 경우 또는 사용자가 Exchange 2013에 있고 사용자의 사서함이 원본 위치 유지로 설정된 경우 보관 정책을 사용하여 내부 통신 및 외부 통신에 대한 보관을 사용하거나 사용하지 않도록 설정할 수 있습니다. 여기에는 다음과 같은 보관 정책이 포함됩니다.

  - Lync Server 2013을 배포할 때 기본적으로 만들어지는 글로벌 정책

  - 특정 사이트 또는 사용자에 대한 보관 구현 방법을 지정하기 위해 만들고 사용할 수 있는 선택적인 사이트 수준 및 사용자 수준의 정책

처음에 보관을 배포할 때 보관 정책을 설정하지만 배포 후 정책을 변경, 추가 및 삭제할 수 있습니다. Lync Server 2013 제어판에서는 **보관 및 모니터링** 그룹의 **보관 정책** 페이지를 사용하여 전역 수준, 사이트 수준 및 사용자 수준에서 정책을 관리할 수 있습니다. Lync Server 저장소를 Exchange 2013 저장소와 통합하면 Exchange 사용자 정책이 Lync Server 2013 보관 정책보다 우선 적용됩니다.

정책 계층을 포함하여 정책 구현 방법에 대한 자세한 내용은 계획 설명서, 배포 설명서 또는 작업 설명서에서 [Lync Server 2013의 보관 작동 방식](lync-server-2013-how-archiving-works.md)을 참조하십시오.


> [!NOTE]
> 보관 구현을 제어하려면 보관 구성에서 IM 또는 회의 내용을 보관할지 여부, 중요 모드 사용, 삭제 옵션 등과 같은 옵션을 지정해야 합니다. 기본적으로 전역 보관 구성이나 사이트 또는 풀 보관 구성에서는 어떤 옵션도 사용하도록 설정되어 있지 않습니다. 보관 정책에서 내부 또는 외부 통신에 대한 보관을 사용하도록 설정하려면 먼저 보관 구성에서 모든 적합한 옵션을 지정해야 합니다. 자세한 내용은 작업 설명서에서 <A href="lync-server-2013-managing-archiving-configuration-options-for-your-organization-sites-and-pools.md">Lync Server 2013에서 조직, 사이트 및 풀에 대한 보관 구성 옵션 관리</A>를 참조하십시오.<BR>배포에서 Microsoft Exchange 통합을 사용하도록 설정할 경우 Exchange 정책은 Exchange 2013에 있고 해당 사서함이 원본 위치 유지로 설정된 사용자에 대해 보관 기능을 설정할지 여부를 제어합니다. 자세한 내용은 배포 설명서에서 <A href="lync-server-2013-setting-up-policies-for-archiving-when-using-exchange-server-integration.md">Exchange Server 통합 사용 시 보관용 정책 설정</A>을 참조하십시오.



## 이 단원의 내용

  - [보관 정책을 만들어 특정 사이트 및 사용자에 대해 내부 또는 외부 통신의 보관 사용 또는 사용 안 함](lync-server-2013-creating-an-archiving-policy-to-enable-or-disable-archiving-of-internal-or-external-communications-for-specific-sites-or-users.md)

  - [조직, 사이트 또는 사용자에 대한 내부 또는 외부 통신의 보관을 사용하거나 사용하지 않도록 보관 정책 변경](lync-server-2013-changing-an-archiving-policy-to-enable-or-disable-archiving-of-internal-or-external-communications-for-your-organization-sites-or-us.md)

  - [사용자에게 보관 정책 적용](lync-server-2013-applying-an-archiving-policy-to-users.md)

  - [Exchange Server 통합 사용 시 보관용 정책 설정](lync-server-2013-setting-up-policies-for-archiving-when-using-exchange-server-integration.md)

  - [보관 정책 삭제](lync-server-2013-deleting-an-archiving-policy.md)

