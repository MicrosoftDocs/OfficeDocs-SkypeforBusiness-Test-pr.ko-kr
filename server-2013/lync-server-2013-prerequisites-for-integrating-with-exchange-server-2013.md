---
title: Microsoft Lync Server 2013과 Microsoft Exchange Server 2013 통합을 위한 필수 구성 요소
TOCTitle: Microsoft Lync Server 2013과 Microsoft Exchange Server 2013 통합을 위한 필수 구성 요소
ms:assetid: ea22beb9-c02e-47cb-836d-97a556969052
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721919(v=OCS.15)
ms:contentKeyID: 49886039
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Microsoft Lync Server 2013과 Microsoft Exchange Server 2013 통합을 위한 필수 구성 요소

 

_**마지막으로 수정된 항목:** 2014-04-22_

Microsoft Lync Server 2013과 Microsoft Exchange Server 2013을 통합하려면 먼저 모든 필수 단계를 완료해야 합니다. Exchange 2013과 Lync Server 2013이 완전히 설치되고 실행될 때까지는 통합을 수행할 수 없습니다. Exchange 설치에 대한 자세한 내용은 Exchange 2013 계획 및 배포 설명서()([http://go.microsoft.com/fwlink/?linkid=268539\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=268539%26clcid=0x412))를 참조하십시오. Lync Server 2013 설치에 대한 자세한 내용은 계획 및 배포 설명서()([http://go.microsoft.com/fwlink/?linkid=254806\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=254806%26clcid=0x412))를 참조하십시오.

서버가 실행된 후에는 서버 간 인증 인증서를 Lync Server 2013과 Exchange 2013에 모두 할당해야 합니다. 이러한 인증서를 통해 Lync Server과 Exchange은 서로 정보를 교환하고 통신할 수 있습니다. Exchange 2013을 설치할 때 Microsoft Exchange Server Auth Certificate라는 이름의 자체 서명된 인증서가 자동으로 만들어집니다. Exchange 2013의 서버 간 인증에는 이 인증서를 사용해야 하며, 이 인증서는 로컬 컴퓨터 인증서 저장소에 있습니다. Exchange 2013에서 인증서 할당에 대한 자세한 내용은 "메일 흐름 및 클라이언트 액세스 구성()"( [http://go.microsoft.com/fwlink/?linkid=268540\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=268540%26clcid=0x412))을 참조하십시오.

Lync Server 2013의 경우 기존 Lync Server 인증서를 서버 간 인증 인증서로 사용할 수 있습니다. 예를 들어 기본 인증서를 OAuthTokenIssuer 인증서로 사용할 수 있습니다. Lync Server 2013에서는 다음 조건을 충족하는 경우 서버 간 인증용 인증서로 웹 서버 인증서를 사용할 수 있습니다.

  - 인증서의 주체 필드에 SIP 도메인 이름이 포함됩니다.

  - 동일한 인증서가 모든 프런트 엔드 서버에서 OAuthTokenIssuer 인증서로 구성됩니다.

  - 인증서 길이가 2048비트 이상입니다.

Microsoft Lync Server 2013에 대한 서버 간 인증 인증서에 대한 자세한 내용은 [Microsoft Lync Server 2013에 서버 간 인증 인증서 할당](lync-server-2013-assigning-a-server-to-server-authentication-certificate-to-lync-server-2013.md)을 참조하십시오.

인증서를 할당한 후에는 Exchange 2013에서 자동 검색 서비스를 구성해야 합니다. Exchange 2013에서 자동 검색 서비스는 사용자 프로필을 구성하며 사용자가 시스템에 로그온할 때 Exchange 서비스에 대한 액세스 권한을 제공합니다. 사용자는 자동 검색 서비스에 자신의 전자 메일 주소와 암호를 제공합니다. 그러면 서비스는 사용자에게 다음과 같은 정보를 제공합니다.

  - Exchange 2013과의 내부 및 외부 연결에 대한 연결 정보

  - 사용자의 사서함 서버 위치

  - 약속 있음/없음, 통합 메시징 및 오프라인 주소록 등 Outlook 기능의 URL

  - 외부에서 Outlook 사용 서버 설정

Lync Server 2013과 Exchange 2013을 통합하려면 먼저 자동 검색 서비스를 구성해야 합니다. Exchange 관리 셸에서 다음 명령을 실행하고 AutoDiscoverServiceInternalUri 속성의 값을 확인하여 자동 검색 서비스가 구성되었는지 여부를 확인할 수 있습니다.

    Get-ClientAccessServer | Select-Object Name, AutoDiscoverServiceInternalUri | Format-List

이 값이 비어 있으면 자동 검색 서비스에 URI를 할당해야 합니다. 일반적으로 이 URI의 형식은 다음과 같습니다.

    https://autodiscover.litwareinc.com/autodiscover/autodiscover.xml

다음과 같은 명령을 실행하여 자동 검색 URI를 할당할 수 있습니다.

    Get-ClientAccessServer | Set-ClientAccessServer -AutoDiscoverServiceInternalUri "https://autodiscover.litwareinc.com/autodiscover/autodiscover.xml"

자동 검색 서비스에 대한 자세한 내용은 "Autodiscover 서비스 이해"([http://go.microsoft.com/fwlink/?linkid=268542\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=268542%26clcid=0x412))를 참조하십시오.

자동 검색 서비스가 구성된 후에는 Lync Server OAuth 구성 설정을 수정해야 합니다. 이렇게 화면 Lync Server에서 자동 검색 서비스를 찾을 위치를 알 수 있습니다. Lync Server 2013에서 OAuth 구성 설정을 수정하려면 Lync Server 관리 셸 내에서 다음 명령을 실행합니다. 이 명령을 실행할 때 Exchange 서버에서 실행 중인 자동 검색 서비스에 대한 URI를 지정하고 **autodiscover.xml** 대신에 **autodiscover.svc**를 사용하여 서비스 위치를 가리켜야 합니다(서비스에 사용되는 XML 파일을 가리킴).

    Set-CsOAuthConfiguration -Identity global -ExchangeAutodiscoverUrl "https://autodiscover.litwareinc.com/autodiscover/autodiscover.svc


> [!NOTE]
> 이전 명령의 Identity 매개 변수는 선택 사항입니다. Lync Server에서는 단일 전역 OAuth 구성 설정 컬렉션만 사용하도록 허용하기 때문입니다. 따라서 다음과 같은 간단한 명령을 사용하여 자동 검색 URL을 구성할 수 있습니다.<BR>Set-CsOAuthConfiguration–ExchangeAutodiscoverUrl "https://autodiscover.litwareinc.com/autodiscover/autodiscover.svc"<BR>OAuth는 주요 웹 사이트에서 사용되는 표준 인증 프로토콜입니다. OAuth를 사용하면 사용자 자격 증명과 암호가 컴퓨터 간에 전달되지 않습니다. 대신에 보안 토큰 교환을 기반으로 인증과 권한 부여가 이루어집니다. 이러한 토큰은 특정 시간 동안 특정 리소스에 대한 액세스 권한을 부여합니다.



자동 검색 서비스 구성 외에도 Exchange 서버로 지정된 서비스에 대한 DNS 레코드를 만들어야 합니다. 예를 들어 자동 검색 서비스가 autodiscover.litwareinc.com에 있으면 Exchange 서버(예: atl-exchange-001.litwareinc.com)의 정규화된 도메인 이름으로 확인되는 autodiscover.litwareinc.com에 대한 DNS 레코드를 만들어야 합니다.

