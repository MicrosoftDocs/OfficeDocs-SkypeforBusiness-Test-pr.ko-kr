---
title: 'Lync Server 2013: Microsoft Exchange Server 2013과 통합'
TOCTitle: Lync Server 2013과 Exchange Server 2013 통합
ms:assetid: 795dc1c6-524f-4012-8b66-103b55198044
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688098(v=OCS.15)
ms:contentKeyID: 49885829
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Microsoft Lync Server 2013과 Microsoft Exchange Server 2013 통합

 

_**마지막으로 수정된 항목:** 2014-07-09_

Exchange 및 Lync Server은 예전부터 지속적인 통합 및 호환성을 제공했습니다. 이러한 통합은 각각의 클라이언트 응용 프로그램 내에서 더욱 두드러집니다. 예를 들어 Lync 현재 상태 정보는 Microsoft Outlook에 보고될 수 있습니다. 마찬가지로 Lync은 Outlook 일정을 사용해서 현재 상태 정보를 자동으로 업데이트할 수 있습니다. 예를 들어 일정에서 사용자에게 예약된 모임이 있는 것으로 표시될 때마다 Lync에서 사용자 상태를 다른 용무 중으로 변경할 수 있습니다. Lync Server을 실행하기 위해 Exchange를 실행할 필요는 없지만(혹은 그 반대로) 두 제품을 함께 사용함으로써 시너지 효과를 극대화할 수 있다는 점에는 의심의 여지가 없습니다.

특히 Microsoft Lync Server 2013 및 Microsoft Exchange Server 2013에서는 이러한 시너지 효과가 더욱 커졌습니다. Microsoft Exchange Server 2010 및 Microsoft Lync Server 2010에서 제공되는 통합 메시징 및 IM과 현재 상태와 같은 기능 외에도 2013 릴리스 서버 제품에는 다양한 새 기능들이 포함됩니다. 이러한 기능은 다음과 같습니다.

  - **Lync 보관 통합** . Lync Server 2013에서도 관리자는 여전히 인스턴트 메시징 및 웹 회의 대화 내용을 SQL Server에 보관하도록 선택할 수 있습니다( Lync Server 2010에서 대화 내용을 보관할 때와 동일한 방식). 하지만 Exchange에서 통신 내용을 보관하는 것과 같이 개별 사용자 사서함에 해당 대화 내용을 저장하는 방식으로 Exchange 2013에 대화 내용을 보관하도록 선택할 수 있습니다. 즉, 모든 전자 통신( Exchange 및 Lync Server 모두 포함)에 대한 단일 저장소를 구성함으로써 필요에 따라 보관된 통신을 보다 쉽게 검색할 수 있습니다.

  - **통합 연락처 저장소** . Lync Server 2010에서는 사용자가 Outlook 및 Lync에서 연락처 목록을 별도로 유지 관리해야 했습니다. 실제로 두 제품에서 연락처를 동일하게 유지하기 위해서는 Outlook용과 Lync용으로 하나씩 연락처 목록을 중복해서 유지 관리해야 했습니다. 하지만 Lync Server 2013에서는 사용자 연락처를 Exchange 2013 및 통합 연락처 저장소에 저장할 수 있습니다. 단일 연락처 저장소를 사용함으로써 연락처 집합을 하나만 유지 관리할 수 있으며 동일한 연락처 집합을 Lync 2013, Outlook 2013 및 Outlook Web Access 2013에서 사용할 수 있습니다.

  - **OWA에서 Lync 모임 예약** . Lync Server 2013 및 Exchange 2013 통합을 통해 사용자가 Outlook Web Access 2013에서 Lync 모임을 예약할 수 있습니다.

  - **고해상도 사진** . Lync 2010에서는 연락처에 대해 작은 사진만 표시할 수 있었습니다. 왜냐하면 이러한 사진이 Active Directory에 저장되었고 Active Directory에서는 저장된 사진의 크기가 48 x 48 픽셀로 제한되었기 때문입니다. 하지만 Lync Server 2013에서는 사진을 Microsoft Exchange에 저장할 수 있습니다. 따라서 최대 648 x 648 픽셀까지 큰 고해상도 사진을 사용할 수 있습니다. 그리고 Lync 2013도 이러한 고해상도 사진을 표시할 수 있도록 업그레이드되었습니다.

이러한 새 기능을 사용하기 위해서는 Lync Server 2013과 Exchange 2013을 모두 사용해야 합니다. 이외에도 이러한 기능을 완전히 활용하기 위해서는 Lync Server 2013 및 Exchange 2013에 대한 계정이 있어야 하며 최신 버전의 클라이언트 소프트웨어(예: Lync 2013)를 사용해야 합니다. 예를 들어 Lync Server 2010에 있는 사용자는 통합 연락처 저장소를 사용할 수 없습니다. 마찬가지로 Lync 2010에서는 고해상도 사진을 표시할 수 없습니다.

이 설명서에서는 보관 통합 및 통합 연락처 저장소와 같은 새 기능을 설정하는 방법에 대한 단계별 정보를 포함하여 Lync Server 2013 및 Exchange 2013 통합에 대한 정보를 제공합니다. 이러한 두 제품의 초기 설정 및 구성에 대해서는 이 설명서에서 다루지 않습니다. Lync Server 2013 배포에 대한 자세한 내용은 Lync Server 2013 Tech Center, [http://go.microsoft.com/fwlink/?linkid=246127\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=246127%26clcid=0x412)를 참고하세요. Exchange 2013 배포에 대한 자세한 내용은 Exchange 2013 Tech Center, [http://go.microsoft.com/fwlink/?linkid=268528\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=268528%26clcid=0x412)를 참고하세요.

## 이 단원의 내용

[Microsoft Lync Server 2013과 Microsoft Exchange Server 2013 통합을 위한 필수 구성 요소](lync-server-2013-prerequisites-for-integrating-with-exchange-server-2013.md)

[Microsoft Lync Server 2013 및 Microsoft Exchange Server 2013에서 파트너 응용 프로그램 구성](lync-server-2013-configuring-partner-applications-in-lync-server-2013-and-exchange-server-2013.md)

[Microsoft Exchange Server 2013 보관을 사용하도록 Microsoft Lync Server 2013 구성](configuring-lync-server-2013-to-use-microsoft-exchange-server-2013-archiving.md)

[보관된 Microsoft Lync Server 2013 데이터를 검색하도록 Microsoft SharePoint Server 2013 구성](lync-server-2013-configuring-microsoft-sharepoint-server-2013-to-search-for-archived-lync-server-2013-data.md)

[통합 연락처 저장소를 사용하도록 Microsoft Lync Server 2013 구성](lync-server-2013-configuring-lync-server-to-use-the-unified-contact-store.md)

[Microsoft Lync Server 2013에서 고해상도 사진 사용 구성](lync-server-2013-configuring-the-use-of-high-resolution-photos.md)

[Microsoft Lync Server 2013 음성 사서함에 대해 Microsoft Exchange Server 2013 통합 메시징 구성](lync-server-2013-configuring-microsoft-exchange-server-2013-unified-messaging-for-lync-server-2013-voice-mail.md)

[Microsoft Lync Server 2013과 Microsoft Outlook Web App 2013 통합](lync-server-2013-integrating-lync-server-and-outlook-web-app-2013.md)

