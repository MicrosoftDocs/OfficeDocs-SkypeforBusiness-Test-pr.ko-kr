---
title: 'Lync Server 2013: 통화 허용 제어 서비스 구성'
TOCTitle: 통화 허용 제어 서비스 구성
ms:assetid: ce3e6e71-1e33-4cff-849a-c0468e61fef6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398870(v=OCS.15)
ms:contentKeyID: 49305068
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 통화 허용 제어 서비스 구성

 

_**마지막으로 수정된 항목:** 2012-09-21_

CAC(통화 허용 제어)는 혼잡한 네트워크에서 사용자의 오디오/비디오 품질이 저하되지 않도록 방지하기 위해 사용 가능한 대역폭을 기반으로 실시간 세션을 설정할 수 있는지 여부를 결정하는 솔루션입니다. CAC는 오디오 및 비디오에 대해서만 실시간 트래픽을 제어하며 데이터 트래픽에는 영향을 주지 않습니다. CAC는 기본 WAN 경로에서 필요한 대역폭을 확보할 수 없는 경우 인터넷 경로를 통해 통화를 라우팅할 수 있습니다. 자세한 내용은 계획 설명서의 [Lync Server 2013의 통화 허용 제어 서비스 계획](lync-server-2013-planning-for-call-admission-control.md)를 참조하십시오.

이 섹션에서는 네트워크에서 CAC를 배포하고 관리하는 방법을 설명하는 일련의 절차(예)를 제공합니다.


> [!IMPORTANT]
> CAC 배포를 시작하려면 계회 설명서의 <A href="lync-server-2013-example-of-gathering-your-requirements-for-call-admission-control.md">예: Lync Server 2013에서 통화 허용 제어 서비스에 대한 요구 사항 수집</A>에 설명된 대로 엔터프라이즈 네트워크 토폴로지에 필요한 모든 정보를 수집해야 합니다. 또한 배포 설명서의 <A href="lync-server-2013-define-and-configure-a-front-end-pool-or-standard-edition-server.md">Lync Server 2013에서 프런트 엔드 풀 또는 Standard Edition 서버 정의 및 구성</A>에 설명된 대로 CAC 구성 요소가 설치 및 활성화되어 있어야 합니다.




> [!NOTE]
> 이 섹션의 모든 CAC 배포 및 관리 예는 Lync Server 관리 셸을 사용하여 수행됩니다. 또는 Lync Server 제어판의 <STRONG>네트워크 구성</STRONG> 섹션을 통해 CAC를 관리할 수도 있습니다.



## 이 단원의 내용

  - [Lync Server 2013에서 CAC에 대한 네트워크 지역 구성](lync-server-2013-configure-network-regions-for-cac.md)

  - [Lync Server 2013에서 대역폭 정책 프로필 만들기](lync-server-2013-create-bandwidth-policy-profiles.md)

  - [Lync Server 2013에서 CAC에 대한 네트워크 사이트 구성](lync-server-2013-configure-network-sites-for-cac.md)

  - [Lync Server 2013에서 CAC를 위해 네트워크 사이트에 서브넷 연결](lync-server-2013-associate-subnets-with-network-sites-for-cac.md)

  - [Lync Server 2013에서 네트워크 지역 링크 만들기](lync-server-2013-create-network-region-links.md)

  - [Lync Server 2013에서 네트워크 지역 간 경로 만들기](lync-server-2013;-create-network-interregion-routes.md)

  - [Lync Server 2013에서 새 네트워크 사이트 간 정책 만들기](lync-server-2013-create-network-intersite-policies.md)

  - [Lync Server 2013에서 통화 허용 제어 사용](lync-server-2013-enable-call-admission-control.md)

  - [Lync Server 2013의 통화 허용 제어 배포 검사 목록](lync-server-2013-call-admission-control-deployment-checklist.md)

