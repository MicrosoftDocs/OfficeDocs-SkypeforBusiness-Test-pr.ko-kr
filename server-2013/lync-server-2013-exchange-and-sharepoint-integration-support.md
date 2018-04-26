---
title: 'Lync Server 2013: Exchange Server 및 SharePoint 통합 지원'
TOCTitle: Exchange Server 및 SharePoint 통합 지원
ms:assetid: 72bf8aa5-55b1-4851-8a59-c96bf85d215a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205005(v=OCS.15)
ms:contentKeyID: 49304015
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 Exchange Server 및 SharePoint 통합 지원

 

_**마지막으로 수정된 항목:** 2014-09-29_

Lync Server 2013 및 Lync 2013은 Office 2013, Exchange 2013 및 SharePoint(이러한 제품과 통합된 경우)을 포함하여 다른 응용 프로그램 및 서버 제품과 안전하고 효율적으로 통신할 수 있습니다. Lync Server 2013 및 Office를 통합하면 Lync의 IM(메신저 대화), 향상된 현재 상태, 전화 통신 및 회의 기능에 대한 컨텍스트 내 액세스를 사용자에게 제공할 수 있습니다. Office 사용자는 Outlook 2013 메시징 및 공동 작업 클라이언트 및 기타 Office 프로그램 또는 Microsoft SharePoint Server 2010 페이지 내에서 Lync 기능에 액세스할 수 있습니다. 사용자는 또한 Outlook 대화 내용 폴더에서 Lync 대화에 대한 기록을 볼 수 있습니다. Exchange 2013 또는 Exchange Online과 통합된 Lync Server 2013은 또한 다음과 같은 기능을 지원합니다.

  - 통합 연락처 저장소 - Lync 2013, Exchange, Outlook 및 Outlook Web App에서 연락처 정보를 전역으로 사용할 수 있도록 Exchange 2013 또는 Exchange Online에 모든 연락처 정보를 저장할 수 있습니다.

  - 대화 내용 및 웹 회의 내용 - Exchange 사용자 폴더에 저장됩니다.

  - IM 및 모임 콘텐츠처럼 Lync에서 보관된 콘텐츠는 Exchange 저장소에 저장할 수 있습니다.


> [!NOTE]
> Lync Server 2013에서는 이전 버전의 Microsoft Exchange Server 및 SharePoint와의 통합이 지원되지만 Microsoft Exchange와의 보관 저장소 통합 등 이전 버전에서 모든 기능이 지원되는 것은 아닙니다.<BR>사용자를 Exchange 2013에 마이그레이션하는 경우 마이그레이션을 완료하는 동안 중간 위치에서 Exchange 저장소 및 Lync Server 저장소를 모두 사용할 수 있습니다. Exchange 및 Lync Server 저장소를 모두 영구적으로 사용하는 기능은 지원되지 않습니다.



Lync Server 2013과 Exchange 2013 및 SharePoint Server의 통합을 위해서는 Lync Server 2013, Microsoft Exchange Server, SharePoint Server를 실행하는 서버 사이에 서버 간 인증이 필요합니다. Lync Server 2013에서는 서버 간 인증 및 권한 부여를 위한 OAuth(Open Authorization) 프로토콜이 지원됩니다. 두 개의 Microsoft 서버 사이에 온-프레미스 서버 간 인증을 위해서는 타사 토큰 서버를 사용할 필요가 없습니다. Lync Server 2013, Exchange 2013 및 SharePoint에는 서로 인증 목적으로 사용할 수 있는 기본 제공되는 토큰 서버가 들어 있습니다. 예를 들어 Lync Server 2013은 자체적으로 보안 토큰을 발행하고 서명할 수 있으며, Exchange 2013과 통신할 때 이 토큰을 사용할 수 있습니다. 이 경우에는 타사 토큰 서버를 사용할 필요가 없습니다.

Lync Server 2013에서는 두 개의 서버 간 인증 시나리오가 지원됩니다. 여기에는 다음 항목 사이의 서버 간 인증 구성이 포함됩니다.

  - Lync Server 2013의 온-프레미스 설치 및 Exchange 2013 및/또는 SharePoint Server의 온-프레미스 설치

  - Office 구성 요소의 쌍(예: Microsoft Exchange 365와 Microsoft Lync Server 365 사이 또는 Microsoft Lync Server 365와 Microsoft SharePoint 365 사이).


> [!NOTE]
> 이번 Lync Server 2013 릴리스에서는 온-프레미스 서버와 Office 365 구성 요소 사이의 서버 간 인증이 지원되지 않습니다. 특히 Lync Server 2013의 온-프레미스 설치와 Microsoft Exchange 365 사이에는 서버 간 인증을 설정할 수 없습니다.



서버 간 인증에 대한 자세한 내용은 배포 설명서 또는 작업 설명서에서 [Lync Server 2013에서 서버 간 인증(Oauth) 및 파트너 응용 프로그램 관리](lync-server-2013-managing-server-to-server-authentication-oauth-and-partner-applications.md)를 참조하세요.

