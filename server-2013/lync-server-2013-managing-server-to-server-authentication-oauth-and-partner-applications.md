---
title: Lync Server 2013에서 서버 간 인증(Oauth) 및 파트너 응용 프로그램 관리
TOCTitle: Lync Server 2013에서 서버 간 인증(Oauth) 및 파트너 응용 프로그램 관리
ms:assetid: 38848373-c8c6-4097-bf7f-699fe471348d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204817(v=OCS.15)
ms:contentKeyID: 49303318
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 서버 간 인증(Oauth) 및 파트너 응용 프로그램 관리

 

_**마지막으로 수정된 항목:** 2015-05-14_

Microsoft Lync Server 2013은 다른 응용 프로그램 및 서버 제품과 안전하고 원활하게 통신할 수 있어야 합니다. 예를 들어 연락처 데이터 및/또는 보관 데이터가 Microsoft Exchange Server 2013에 저장되도록 Lync Server 2013을 구성할 수 있습니다. 그러나 이 작업은 Lync Server 및 Exchange가 서로 안전하게 통신할 수 있는 경우에만 가능합니다. 마찬가지로 Microsoft SharePoint Server 내에서 Lync Server 전화 회의를 예약할 수 있습니다. 그러나 이 작업은 두 서버(SharePoint 및 Lync Server)가 서로를 신뢰하는 경우에만 가능합니다. Lync-Exchange 통신과 Lync-SharePoint 통신에 서로 다른 인증 메커니즘을 사용할 수는 있지만, 보다 효율적인 방식은 모든 서버 간 인증 및 권한 부여에 표준화된 방법을 사용하는 것입니다.

Lync Server 2013에서는 서버 간 인증에 표준화된 한 가지 방법을 사용합니다. 2013 릴리스의 경우 Lync Server 2013(Exchange 2013 및 Microsoft SharePoint Server를 포함한 기타 Microsoft Server 제품도 마찬가지)에서는 서버 간 인증 및 권한 부여에 대해 OAuth(Open Authorization) 프로토콜을 지원합니다. 대부분의 주요 웹 사이트에서 사용되는 표준 권한 부여 프로토콜인 OAuth를 사용하는 경우 사용자 자격 증명과 암호가 컴퓨터 간에 전달되지 않습니다. 대신 인증 및 권한 부여는 보안 토큰 교환을 기반으로 하며, 이러한 토큰이 일정 기간 동안 특정 리소스 집합에 대한 액세스 권한을 부여합니다.

OAuth 인증에는 보통 세 당사자(단일 권한 부여 서버 및 서로 통신해야 하는 두 영역)가 포함됩니다. 권한 부여 서버를 사용하지 않고 서버 간 인증을 수행할 수도 있는데, 이 프로세스에 대해서는 이 문서 뒷부분에서 설명합니다. 권한 부여 서버(보안 토큰 서버라고도 함)가 서로 통신해야 하는 두 영역에 보안 토큰을 발급합니다. 이러한 토큰은 한 영역에서 시작되는 통신을 다른 영역에서 신뢰해야 하는지를 확인합니다. 예를 들어 권한 부여 서버는 특정 Lync Server 2013 영역의 사용자가 지정된 Exchange 2013 영역에 액세스할 수 있는지 및 그 반대 방향의 액세스도 가능한지를 확인하는 토큰을 발급할 수 있습니다.


> [!NOTE]
> 영역은 단순한 보안 컨테이너입니다. 기본적으로 Lync Server 2013에서는 기본 SIP 도메인을 OAuth 영역으로 사용합니다.



Lync Server 2013에서는 세 가지 서버 간 인증 시나리오를 지원합니다. Lync Server 2013을 사용하면 다음과 같은 작업을 수행할 수 있습니다.

  - 온-프레미스 Lync Server 2013 설치 간, 그리고 온-프레미스 Exchange 2013 설치 및/또는 Microsoft SharePoint Server 간의 서버 간 인증 구성

  - Office 365 구성 요소 쌍 간(예: Microsoft Exchange와 Microsoft Lync Server 간 또는 Microsoft Lync Server와 Microsoft SharePoint 간)의 서버 간 인증 구성

  - 크로스-프레미스 환경의 서버 간 인증(온-프레미스 서버와 Office 365 구성 요소 간의 서버 간 인증) 구성

현재는 Exchange 2013, SharePoint Server 및 Lync Server 2013만 서버 간 인증을 지원합니다. 이러한 서버 중 하나를 실행하지 않는 경우에는 OAuth 인증을 완전하게 구현할 수 없습니다.

서버 간 인증을 반드시 사용할 필요는 없다는 점도 기억해야 합니다. 즉, Lync Server 2013을 배포하기 위해 서버 간 인증을 사용할 필요는 없습니다. Lync Server 2013에서 Exchange 2013 등의 다른 서버와 통신하지 않아도 되는 경우에는 서버 간 인증을 사용할 필요가 없습니다.

그러나 "통합 연락처 저장소"와 같은 Lync Server의 일부 새 기능을 사용하려면 서버 간 인증이 필요합니다. 통합 연락처 저장소를 사용하는 경우 Lync Server 2013 연락처 정보가 Lync Server가 아닌 Exchange 2013에 저장됩니다. 따라서 사용자가 Lync, Microsoft Outlook 또는 Microsoft Outlook Web Access 내에서 단일 연락처 집합에 쉽게 액세스할 수 있습니다. 통합 연락처 저장소를 사용하려면 Lync Server 2013에서 Exchange 2013과 정보를 교환해야 하므로, 이 기능을 배포하려면 서버 간 인증을 사용해야 합니다. 또한 인스턴트 메시징 세션 대화 내용이 개별 데이터베이스 레코드가 아닌 Exchange 2013 전자 메일로 저장되는 Exchange 보관을 사용하려는 경우에도 서버 간 인증이 필요합니다.

Office 365 버전의 Lync Server가 해당 Exchange 부분과 통신하려면 먼저 Lync Server 2013에서 권한 부여 서버로부터 보안 토큰을 가져와야 합니다. 그런 다음에 Lync Server는 해당 토큰을 사용하여 Exchange에 대한 식별을 수행합니다. Office 365 버전의 Exchange도 Lync Server 2013과 통신하려면 같은 프로세스를 거쳐야 합니다.

그러나 두 Microsoft 서버 간의 온-프레미스 서버 간 인증에서는 타사 토큰 서버를 사용할 필요가 없습니다. Lync Server 2013, Exchange 2013 등의 서버 제품에서는 서버 간 인증을 지원하는 SharePoint Server와 같은 기타 Microsoft 서버와의 인증용으로 사용할 수 있는 토큰 서버가 기본적으로 제공됩니다. 예를 들어 Lync Server 2013은 보안 토큰을 자체적으로 발급 및 서명한 다음 해당 토큰을 사용하여 Exchange 2013과 통신할 수 있습니다. 이러한 경우에는 타사 토큰 서버가 필요하지 않습니다.

온-프레미스 Lync Server 2013 구현에 대해 서버 간 인증을 구성하려면 다음의 두 가지 작업을 수행해야 합니다.

  - Lync Server의 기본 제공 토큰 발급자에 인증서 할당

  - Lync Server 2013이 "파트너 응용 프로그램"이 되기 위해 통신하는 서버 구성. 예를 들어 Lync Server 2013이 Exchange 2013과 통신해야 하는 경우에는 Exchange가 파트너 응용 프로그램이 되도록 구성해야 합니다.


> [!NOTE]
> "파트너 응용 프로그램"은 Lync Server 2013이 타사 보안 토큰 서버를 거치지 않고 보안 토큰을 직접 교환할 수 있는 응용 프로그램입니다.



OAuth는 제품의 핵심적인 부분이므로 사용하지 않도록 설정하거나 제거할 수 없습니다.

## 참고 항목

#### 개념

[Microsoft Lync Server 2013에 서버 간 인증 인증서 할당](lync-server-2013-assigning-a-server-to-server-authentication-certificate-to-lync-server-2013.md)  
[크로스-프레미스 환경에서 Microsoft Lync Server 2013 구성](lync-server-2013-configuring-lync-server-in-a-cross-premises-environment.md)

