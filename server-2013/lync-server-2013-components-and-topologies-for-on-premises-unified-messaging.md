---
title: 'Lync Server 2013: 온-프레미스 통합 메시징의 구성 요소 및 토폴로지'
TOCTitle: 온-프레미스 통합 메시징의 구성 요소 및 토폴로지
ms:assetid: 22fc87cf-a7e5-4c8c-bb9b-101e5380cdcf
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425711(v=OCS.15)
ms:contentKeyID: 49303057
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 온-프레미스 통합 메시징의 구성 요소 및 토폴로지

 

_**마지막으로 수정된 항목:** 2012-09-25_

이 항목에서는 Lync Server 2013 배포에 대해 Exchange 통합 메시징(UM) 기능을 제공하는 데 필요한 Microsoft Exchange Server 2013 구성 요소에 대해 설명합니다. 또한 온-프레미스 Exchange UM 통합에 대해 지원되는 토폴로지도 설명합니다.

## Exchange Server 구성 요소

[통합 메시징 및 Lync Server 2013의 기능](lync-server-2013-features-of-integrated-unified-messaging.md)에 설명된 Exchange UM 기능을 조직의 Enterprise Voice 사용자에게 제공하려면 Microsoft Exchange 사서함 서버 및 클라이언트 액세스 서버(사용자 사서함을 호스팅하며 전자 메일 및 음성 메일을 저장하기 위한 단일 위치 제공)를 배포해야 합니다. Exchange UM은 Exchange 사서함 및 클라이언트 액세스 서버에서 서비스로 실행됩니다.

Microsoft Exchange Server 2007 및 Microsoft Exchange Server 2010의 Exchange UM 구성 요소에 대한 자세한 내용은 배포 설명서에서 [Lync Server 2013 음성 메일을 제공하도록 온-프레미스 Exchange UM 배포](lync-server-2013-deploying-on-premises-exchange-um-to-provide-lync-server-2013-voice-mail.md)를 참조하십시오.

## 지원되는 토폴로지

Lync Server 2013 및 Exchange 통합 메시징(UM)을 동일한 포리스트에 배포할 수도 있고 여러 포리스트에 배포할 수도 있습니다. 여러 포리스트에 배포하는 경우에는 각 Exchange UM 포리스트에 대해 Exchange 통합 단계를 수행해야 합니다. 또한 각 Microsoft Exchange 포리스트가 Lync Server 2013 포리스트를 신뢰하고 Lync Server 2013 포리스트가 각 Exchange UM 포리스트를 신뢰하도록 구성해야 합니다. 이러한 포리스트 신뢰 외에도, 모든 사용자에 대한 Exchange UM 설정을 Lync Server 2013 포리스트의 사용자 개체에 대해 지정해야 합니다.

Lync Server 2013은 Exchange UM 통합용으로 다음 토폴로지를 지원합니다.

  - 단일 포리스트

  - 단일 도메인(단일 도메인이 포함된 단일 포리스트). Lync Server 2013, Microsoft Exchange 및 사용자는 모두 같은 도메인에 있습니다.

  - 여러 도메인(자식 도메인이 하나 이상 포함된 루트 도메인). Lync Server 2013 및 Microsoft Exchange 서버는 사용자를 만드는 도메인과 다른 도메인에 배포됩니다. Exchange UM 서버는 지원되는 Lync Server 2013 풀과 다른 도메인에 배포할 수 있습니다.

  - 여러 포리스트(리소스 포리스트). Lync Server 2013은 단일 포리스트에 배포되며, 사용자가 여러 포리스트에 분산됩니다. 사용자의 Exchange UM 특성을 Lync Server 2013 포리스트로 복제해야 합니다.
    

    > [!NOTE]
    > Exchange는 여러 포리스트에 배포할 수 있습니다. 각 Exchange 조직은 사용자에게 Exchange UM을 제공할 수도 있고, Lync Server 2013과 같은 포리스트에 Exchange UM을 배포할 수도 있습니다.


