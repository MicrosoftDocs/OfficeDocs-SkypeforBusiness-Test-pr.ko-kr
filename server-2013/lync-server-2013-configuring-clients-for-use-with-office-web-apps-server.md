---
title: Office Web Apps 서버에 사용할 Lync Server 2013의 클라이언트 구성
TOCTitle: Office Web Apps 서버에 사용할 클라이언트 구성
ms:assetid: e5eaead7-0b32-42fb-97eb-ca203af59a9d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205339(v=OCS.15)
ms:contentKeyID: 49305347
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Office Web Apps 서버에 사용할 Lync Server 2013의 클라이언트 구성

 

_**마지막으로 수정된 항목:** 2013-02-25_

사용자가 Office Web App Server의 모든 기능을 사용할 수 있도록 하려면 Microsoft Lync 2013으로 사용자를 업그레이드해야 합니다. Lync 2013의 사용자만 실제 PowerPoint 프레젠테이션과 독립적으로 PowerPoint 슬라이드를 스크롤하는 등의 기능을 사용할 수 있습니다. 즉, 이러한 사용자는 실제 프레젠테이션을 방해하지 않으면서 언제라도 프레젠테이션의 모든 슬라이드를 살펴볼 수 있습니다. Lync 2013을 사용하고 있지 않은 사용자도 여전히 온라인 회의에 참가하고 PowerPoint 프레젠테이션을 볼 수 있습니다. 하지만 슬라이드를 독립적으로 스크롤할 수 없으며 화면 전환을 보거나 포함된 비디오를 볼 수 없습니다.

Lync 2013 사용자는 이러한 기능을 항상 사용할 수 있습니다. 이는 PowerPoint 발표자가 Microsoft Lync 2010을 실행하는 경우에도 적용됩니다. Lync 2010을 실행하는 사용자가 PowerPoint 프레젠테이션을 호스팅하고 있는 경우 Lync 2013 사용자가 해당 프레젠테이션의 Office Web Apps 서버 버전을 볼 수 있도록 Lync Server 2013이 Office Web Apps 서버와 함께 작동합니다. Office Web Apps 서버는 Lync 2013 이외의 클라이언트를 실행하는 사용자에게 PowerPoint 서비스를 제공하지 않습니다. 대신 이러한 사용자는 회의 서버 서비스에 연결하여 Microsoft Lync Server 2010에서와 동일한 방식으로 PowerPoint 프레젠테이션을 볼 수 있습니다. 이는 이러한 사용자가 Lync Server 2010에서 제공하는 보다 제한적인 기능에만 액세스할 수 있음을 의미하기도 합니다.

사용자를 Lync 2013으로 업그레이드하는 것 말고는 Office Web Apps 서버에 대한 클라이언트 구성이 필요하지 않지만 전화 회의 참석자가 Internet Explorer 9로 업그레이드하는 것이 좋습니다. Internet Explorer 8을 사용하여 전화 회의에 액세스할 수 있지만 해당 웹 브라우저 사용 시 몇 가지 제한이 따릅니다. 예를 들어 Internet Explorer 8의 사용자는 PowerPoint 단계를 사용자 지정 크기로 조절할 수 없습니다. 대신 미리 정의된 세 단계 크기 중 하나를 사용하는 것으로 제한됩니다. 또한 Internet Explorer 8 사용자는 미디어 파일도 재생할 수 없습니다.

