---
title: Lync Server 2013 호스팅된 Exchange UM 통합 지원
TOCTitle: 호스팅된 Exchange UM 통합 지원
ms:assetid: c7573ec3-013c-48d9-b59b-2a5427e6da35
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398821(v=OCS.15)
ms:contentKeyID: 49304999
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 호스팅된 Exchange UM 통합 지원

 

_**마지막으로 수정된 항목:** 2012-09-21_

Lync Server 2013 ExUM 라우팅 응용 프로그램은 다음 다이어그램에 표시된 바와 같이 Lync Server 2013 및 Exchange UM이 모두 로컬로 회사에 설치되는 온-프레미스 환경에서 Exchange 통합 메시징(UM)과의 통합 또는 서비스 공급자에서 호스팅된 Exchange UM과의 통합을 지원합니다.

![온-프레미스 Lync Server Exchange UM 배포](images/Gg398821.d6498eb9-87ee-40f3-8ecd-852f91546590(OCS.15).jpg "온-프레미스 Lync Server Exchange UM 배포")

다음과 같은 모드가 지원됩니다.

  - **온-프레미스 모드**    Lync Server 2013 및 Exchange UM이 둘 다 회사 내의 로컬 서버에 배포됩니다.

  - **교차 프레미스 모드**    Lync Server 2013은 회사 내의 로컬 서버에 배포되고, Exchange UM은 Microsoft Exchange Online 데이터 센터와 같은 온라인 서비스 공급자의 시설에서 호스팅됩니다.

  - **혼합 모드**    Lync Server 2013 에서 일부 사용자 사서함은 회사 내의 Microsoft Exchange Server를 실행하는 로컬 서버에 속하며 일부 사서함은 호스팅되는 Exchange 서비스 데이터 센터를 기반으로 합니다.
    

    > [!NOTE]
    > 혼합 모드는 호스팅되는 Exchange UM으로의 단계적 마이그레이션 및 평가 중에 전환 솔루션으로 사용되거나 나머지를 마이그레이션한 후 일부 사용자의 Exchange UM 서비스를 온-프레미스에 유지하려는 경우에 영구 솔루션으로 사용될 수 있습니다.



Lync Server 2013을 호스팅된 Exchange UM과 통합하려면 *공유 SIP 주소 공간* ( *분할 도메인* )을 구성해야 합니다. 이 구성에서는 Lync Server 2013 및 타사에서 호스팅된 Exchange UM 서비스 공급자 둘 다 동일한 SIP 도메인 주소 공간에 액세스할 수 있습니다. 자세한 내용은 계획 설명서에서 [Lync Server 2013의 호스팅된 Exchange UM 통합 아키텍처](lync-server-2013-hosted-exchange-um-integration-architecture.md)를 참조하십시오.

