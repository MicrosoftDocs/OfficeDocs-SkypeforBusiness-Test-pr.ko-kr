---
title: Microsoft Lync Server 2013 및 Microsoft Exchange Server 2013에서 파트너 응용 프로그램 구성
TOCTitle: Microsoft Lync Server 2013 및 Microsoft Exchange Server 2013에서 파트너 응용 프로그램 구성
ms:assetid: 9c3a3054-6201-433f-b128-4c49d3341370
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688151(v=OCS.15)
ms:contentKeyID: 49885894
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Microsoft Lync Server 2013 및 Microsoft Exchange Server 2013에서 파트너 응용 프로그램 구성

 

_**마지막으로 수정된 항목:** 2014-11-05_

일반적으로 서버 간 인증에는 세 가지 엔터티, 즉 서로 통신해야 하는 두 서버와 타사 보안 토큰 서버가 필요합니다. 예를 들어 서버 A와 서버 B의 두 서버가 통신해야 할 경우 대개 이러한 두 서버는 모두 토큰 서버에 먼저 연결하여 상호 트러스트된 보안 토큰을 얻습니다. 그런 다음 해당 보안 토큰을 서버 A는 서버 B에 제시하고 서버 B는 서버 A에 제시하여 상호 신뢰성을 보증합니다.

그러나 이것은 일반적인 경우이며, Lync Server 2013, Microsoft Exchange Server 2013 및 Microsoft SharePoint Server 2013은 서로 통신할 때 타사 토큰 서버를 사용하지 않아도 됩니다. 이러한 서버 제품은 별도의 토큰 서버가 필요 없이 서로 수락할 수 있는 보안 토큰을 만들 수 있기 때문입니다. 이 기능은 Lync Server 2013, Exchange 2013 및 SharePoint Server 2013에서만 사용할 수 있으며, 다른 Microsoft 서버 제품을 포함한 기타 서버를 사용하여 서버 간 인증을 설정하는 경우 타사 토큰 서버를 사용해야 합니다.

Lync Server와 Exchange 사이에 서버 간 인증을 설정하려면 다음 두 가지 작업을 수행해야 합니다. 1) 각 서버에 적절한 인증서를 할당해야 합니다. 2) 각 서버를 다른 서버의 파트너 응용 프로그램으로 구성해야 합니다. 즉, Lync Server 2013을 Exchange 2013의 파트너 응용 프로그램으로 구성하고, Exchange 2013을 Lync Server 2013의 파트너 응용 프로그램으로 구성해야 합니다.

## Lync Server 2013을 Exchange 2013의 파트너 응용 프로그램으로 구성

Lync Server 2013을 Exchange 2013의 파트너 응용 프로그램으로 구성하는 가장 손쉬운 방법은 Exchange 2013에 기본으로 제공되는 Windows PowerShell 스크립트인 Configure-EnterprisePartnerApplication.ps1 스크립트를 실행하는 것입니다. 이 스크립트를 실행하려면 Lync Server 인증 메타데이터 문서의 URL을 제공해야 합니다. 이것은 대개 SharePoint 풀의 정규화된 도메인 이름 뒤에 접미사 /metadata/json/1을 포함하여 구성됩니다. 예를 들면 다음과 같습니다.

    https://atl-cs-001.litwareinc.com/metadata/json/1

Lync Server을 파트너 응용 프로그램으로 구성하려면 Exchange 관리 셸을 열고 다음과 같은 명령을 실행합니다. 이 예에서는 Exchange이 C: 드라이브에 설치되어 있고 기본 폴더 경로를 사용하는 것으로 가정합니다.

    "C:\Program Files\Microsoft\Exchange Server\V15\Scripts\Configure-EnterprisePartnerApplication.ps1 -AuthMetaDataUrl 'https://atl-cs-001.litwareinc.com/metadata/json/1' -ApplicationType Lync"

파트너 응용 프로그램을 구성한 후에는 Exchange 사서함과 클라이언트 액세스 서버에서 IIS(인터넷 정보 서비스)를 중지하고 다시 시작하는 것이 좋습니다. 다음과 같은 명령을 사용하여 IIS를 다시 시작할 수 있습니다. 이 예에서는 atl-exchange-001이라는 컴퓨터에서 서비스를 다시 시작합니다.

    iisreset atl-exchange-001

이 명령은 Exchange 관리 셸 내에서 실행하거나 다른 명령 창에서 관리자 권한으로 실행할 수 있습니다.

## Exchange 2013을 Lync Server 2013의 파트너 응용 프로그램으로 구성

Lync Server 2013을 Exchange 2013의 파트너 응용 프로그램으로 구성한 후에는 Exchange을 Lync Server의 파트너 응용 프로그램으로 구성해야 합니다. 이를 위해 Lync Server 관리 셸을 사용하여 Exchange에 대한 인증 메타데이터 문서의 URL을 지정해야 합니다. 이것은 대개 Exchange 자동 검색 서비스의 URI 뒤에 접미사 /metadata/json/1을 포함하여 구성됩니다. 예를 들면 다음과 같습니다.

    https://autodiscover.litwareinc.com/autodiscover/metadata/json/1

Lync Server에서 파트너 응용 프로그램은 [New-CsPartnerApplication](new-cspartnerapplication.md) cmdlet을 사용하여 구성됩니다. 메타데이터 URI를 지정하는 것 이외에도 응용 프로그램 신뢰 수준을 전체로 설정해야 합니다. 이렇게 하면 Exchange가 자신과 해당 영역의 권한 있는 모든 사용자를 모두 나타낼 수 있습니다.

    New-CsPartnerApplication -Identity Exchange -ApplicationTrustLevel Full -MetadataUrl "https://autodiscover.litwareinc.com/autodiscover/metadata/json/1"

또한 Lync Server 2013 서버 간 인증 설명서에 있는 스크립트 코드를 복사하여 수정하는 방법으로 파트너 응용 프로그램을 만들 수도 있습니다. 자세한 내용은 [Lync Server 2013에서 서버 간 인증(Oauth) 및 파트너 응용 프로그램 관리](lync-server-2013-managing-server-to-server-authentication-oauth-and-partner-applications.md) 문서를 참조하십시오.

Lync Server과 Exchange을 모두 서로의 파트너 응용 프로그램으로 성공적으로 구성했으면 두 제품 사이의 서버 간 인증도 성공적으로 구성한 것입니다. Lync Server 2013에는 Windows PowerShell cmdlet인 [Test-CsExStorageConnectivity](test-csexstorageconnectivity.md)가 포함되어 있어, 이를 사용하여 서버 간 인증이 올바르게 구성되었는지, 그리고 Lync Server 저장소 서비스에서 Exchange 2013에 연결할 수 있는지 확인할 수 있습니다. 이 cmdlet은 Exchange 2013 사용자의 사서함에 연결하여 해당 사용자의 대화 내용 폴더에 항목을 기록하고 선택적으로 해당 항목을 삭제함으로써 저장소 서비스에서 Exchange 2013에 연결할 수 있는지를 확인합니다.

Lync Server 2013과 Exchange 2013의 통합을 테스트하려면 Lync Server 관리 셸 내에서 다음과 같은 명령을 실행합니다.

    Test-CsExStorageConnectivity -SipUri "sip:kenmyer@litwareinc.com"

위의 명령에서 SipUri는 Exchange 2013에 계정이 있는 사용자의 SIP 주소를 나타내며, 이것이 올바른 사용자 계정이 아닌 경우 명령이 실패합니다.

테스트가 성공하고 연결이 설정된 후에는 통합 보관 및 통합 연락처 저장소와 같은 선택적인 기능을 구성할 수 있습니다.

