---
title: 보관 정책 구성 및 할당
TOCTitle: 보관 정책 구성 및 할당
ms:assetid: acd18ea8-c7f1-4178-871a-cd3b75bdaa8b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205175(v=OCS.15)
ms:contentKeyID: 49304702
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 보관 정책 구성 및 할당

 

_**마지막으로 수정된 항목:** 2012-10-01_

Lync Server 2013에서는 정책을 사용하여 Lync Server 2013에 속해 있는 사용자의 내부 및 외부 통신에 보관을 사용하거나 사용하지 않도록 설정합니다. 여기에는 다음과 같은 보관 정책이 포함됩니다.

  - Lync Server 2013을 배포할 때 기본적으로 만들어지는 전역 정책

  - 특정 사이트 또는 사용자에 대해 보관이 구현되는 방식을 지정하도록 만들어서 사용하는 선택적인 사이트 수준 및 사용자 수준 정책

보관을 배포할 때 처음으로 보관 정책을 설정하게 되며, 배포 후에 정책을 변경, 추가 및 삭제할 수 있습니다. Lync Server 2013 제어판에서는 **보관 및 모니터링** 그룹의 **보관 정책** 페이지를 사용하여 전역 수준, 사이트 수준 및 사용자 수준으로 정책을 관리할 수 있습니다.


> [!NOTE]
> 보관의 구현을 제어하려면 IM 또는 회의 보관 여부, 중요 모드 및 제거 옵션 사용 등의 옵션을 보관 구성에서 지정해야 합니다. 기본적으로 전역 보관 구성 또는 사이트 또는 풀 보관 구성에서 모든 옵션이 사용하도록 설정되어 있지 않습니다. 보관을 사용하도록 설정하기 전에 보관 구성에서 모든 해당 옵션을 지정해야 합니다. 자세한 내용은 작업 설명서에서 <A href="lync-server-2013-managing-archiving-configuration-options-for-your-organization-sites-and-pools.md">Lync Server 2013에서 조직, 사이트 및 풀에 대한 보관 구성 옵션 관리</A>를 참조하십시오.<BR>Exchange 2013 저장소와 Lync Server 저장소를 통합하는 경우 Exchange 2013에 속해 있고 사서함을 원본 위치 유지로 설정한 사용자에 한해 Exchange 사용자 정책이 Lync Server 2013 보관 정책보다 우선합니다.



정책 계층 구조를 포함하여 정책이 구현되는 방식에 대한 자세한 내용은 계획 설명서, 배포 설명서 또는 작업 설명서에서 [Lync Server 2013의 보관 작동 방식](lync-server-2013-how-archiving-works.md)을 참조하십시오. 배포 후에 정책을 관리하는 방법에 대한 자세한 내용은 작업 설명서에서 [Lync Server 2013에서 내부 및 외부 통신의 보관 관리](lync-server-2013-managing-the-archiving-of-internal-and-external-communications.md)를 참조하십시오.

## 이 단원의 내용

  - [보관에 대한 글로벌 정책 구성](lync-server-2013-configuring-the-global-policy-for-archiving.md)

  - [보관용 사이트 정책 설정](lync-server-2013-setting-up-site-policies-for-archiving.md)

  - [사용자에 대한 보관 정책 설정](lync-server-2013-setting-up-archiving-policies-for-users.md)

