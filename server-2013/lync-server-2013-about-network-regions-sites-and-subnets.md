---
title: 'Lync Server 2013: 네트워크 지역, 사이트 및 서브넷 정보'
TOCTitle: 네트워크 지역, 사이트 및 서브넷 정보
ms:assetid: 6662123a-d011-408c-a290-92b2a8589943
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398467(v=OCS.15)
ms:contentKeyID: 49303876
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 네트워크 지역, 사이트 및 서브넷 정보

 

_**마지막으로 수정된 항목:** 2013-02-24_

이 섹션에서 설명하는 고급 Enterprise Voice 기능은 네트워크 지역, 네트워크 사이트 및 서브넷에 대해 특정 구성 요구 사항을 공유합니다. 예를 들어, 이 세 고급 기능을 사용하려면 토폴로지의 각 서브넷이 특정 *네트워크 사이트* 에 연결되어 있어야 하며, 각 네트워크 사이트는 *네트워크 지역* 에 연결되어 있어야 합니다.


> [!IMPORTANT]
> 통화 허용 제어 서비스, E9-1-1 또는 미디어 바이패스를 위한 네트워크 구성을 시작하기 전에 계획 설명서의 <A href="lync-server-2013-network-settings-for-the-advanced-enterprise-voice-features.md">Lync Server 2013의 고급 Enterprise Voice 기능에 대한 네트워크 설정</A> 항목에 나와 있는 네트워크 설정 관련 추가 정보를 검토하세요. 네트워크 구성(주로 통화 허용 제어 서비스)에 대한 자세한 내용은 계획 설명서에서 <A href="lync-server-2013-defining-your-requirements-for-call-admission-control.md">Lync Server 2013에서 통화 허용 제어 서비스에 대한 요구 사항 정의</A>을 참고하세요.



통화 허용 제어 및 E9-1-1의 경우 네트워크 사이트에 대한 추가 구성 요구 사항이 있습니다.

  - 통화 허용 제어의 경우 WAN 대역폭 제한을 통해 제약되는 각 사이트에 대해 *대역폭 정책 프로필* 을 지정해야 합니다. 통화 허용 제어를 배포하려는 경우에는 네트워크 사이트를 구성하기 전에 [Lync Server 2013에서 대역폭 정책 프로필 만들기](lync-server-2013-create-bandwidth-policy-profiles.md)를 수행해야 합니다.

  - E9-1-1의 경우 각 사이트에 대해 *위치 정책* 을 지정해야 합니다. E9-1-1을 배포하려는 경우 네트워크 사이트를 구성하기 전에 [Lync Server 2013에서 위치 정책 만들기](lync-server-2013-create-location-policies.md)를 수행해야 합니다.

## 네트워크 지역, 네트워크 사이트 및 서브넷 만들기 또는 수정

다음 항목에서는 네트워크 지역과 네트워크 사이트를 만들거나 수정하고, 서브넷을 네트워크 사이트와 연결하는 단계를 제공합니다. 이러한 항목의 내용은 특정 고급 Enterprise Voice 기능에만 해당되는 것이 아닙니다.

  - [Lync Server 2013에서 네트워크 지역 만들기 또는 수정](lync-server-2013-create-or-modify-a-network-region.md)

  - [Lync Server 2013에서 네트워크 사이트 만들기 또는 수정](lync-server-2013-create-or-modify-a-network-site.md)

  - [Lync Server 2013 에서 네트워크 사이트에 서브넷 연결](lync-server-2013-associate-a-subnet-with-a-network-site.md)

