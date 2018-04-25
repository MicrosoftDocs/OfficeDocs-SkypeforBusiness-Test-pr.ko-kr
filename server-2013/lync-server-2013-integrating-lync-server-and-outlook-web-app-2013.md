---
title: Microsoft Lync Server 2013과 Microsoft Outlook Web App 2013 통합
TOCTitle: Microsoft Lync Server 2013과 Microsoft Outlook Web App 2013 통합
ms:assetid: 513d4cc7-aa87-4f68-b99d-d58b63bdf242
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688055(v=OCS.15)
ms:contentKeyID: 49885766
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Microsoft Lync Server 2013과 Microsoft Outlook Web App 2013 통합

 

_**마지막으로 수정된 항목:** 2013-02-03_

Microsoft Outlook 2013과의 통합 외에도 Microsoft Lync Server 2013은 무엇보다도 Microsoft Outlook Web App 2013과 완벽하게 통합될 수 있습니다. 이를 통해 Outlook Web App에 인스턴트 메시징과 현재 상태를 추가하고 통합 연락처 목록을 Outlook Web App과 Microsoft Lync 2013 사이에 공유할 수 있습니다. Lync Server 2013을 Outlook Web App과 통합하기 위해서는 먼저 Unified Communications Managed API 4.0 런타임이 Microsoft Exchange Server 2013 백 엔드 서버에 설치되어 있는지 확인해야 합니다. 이 작업은 다음 레지스트리 값이 있는지 조사하여 확인할 수 있습니다.

HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\MSExchange OWA\\InstantMessaging\\ImplementationDLLPath

ImplementationDLLPath는 Microsoft.Rtc.Internal.Ucweb.dll 파일의 폴더 위치를 가리킵니다. 이 항목이 없거나 레지스트리 값이 없으면 Microsoft 다운로드 센터 <http://www.microsoft.com/ko-kr/download/details.aspx?id=34992>에서 UCMA 런타임 설치 프로그램을 다운로드하고 설치해야 합니다. UCMA 런타임을 설치하는 방법에 대한 정보도 같은 웹 페이지에서 확인할 수 있습니다.

**이전 버전과의 호환성**

Lync Server 2013은 통합 메시징 및 Outlook Web App 둘 다의 Microsoft Exchange Server 2010 버전과 통합할 수 있습니다. 자세한 내용은 [http://technet.microsoft.com/ko-kr/library/gg398768.aspx](lync-server-2013-deploying-on-premises-exchange-um-to-provide-lync-server-2013-voice-mail.md)에서 Lync Server 2010 음성 사서함을 제공하도록 온-프레미스 Exchange UM 배포 문서를 참조하십시오. Exchange 2010과 통합하는 경우에는 통합 연락처 저장소 및 Lync-Exchange 간 보관과 같은 Lync Server 관련 기능을 사용할 수 없습니다.

Microsoft Lync 2013은 Exchange 2010 및 Outlook 2010과 함께 사용할 수도 있습니다. 그러나 이 경우에도 Lync 2013 사용자는 통합 연락처 저장소 및 고해상도 사진과 같은 새로운 기능을 사용할 수 없습니다. 이러한 새 기능을 사용하려면 Lync Server 2013 및 Exchange 2013이 모두 필요합니다.

**Outlook Web App용 신뢰할 수 있는 응용 프로그램 풀 만들기**

Microsoft Exchange 통합 메시징 통화 라우터 서비스와 Microsoft Exchange 통합 메시징 서비스를 같은 컴퓨터에 설치했다면 Outlook Web App용으로 신뢰할 수 있는 응용 프로그램 풀을 만들 필요가 없습니다. 여기서는 해당 서버가 SipName UM 다이얼 플랜을 호스트한다고 가정합니다. 컴퓨터 한 대로 두 서비스를 모두 호스트하는 경우에는 이 문서의 **Outlook Web App에서 인스턴트 메시징을 사용하도록 설정** 섹션을 건너뛰어도 됩니다.

Lync Server 2013에서는 SipName UM 다이얼 플랜을 호스트하는 모든 Exchange 서버를 자동 검색할 수 있습니다. 이러한 서버는 Lync Server 알려진 서버 목록에 자동으로 추가됩니다. 따라서 신뢰할 수 있는 응용 프로그램 풀을 만들어 이러한 서버를 알려진 서버 목록에 추가하지 않아도 됩니다. 실제로 이렇게 하면 Outlook Web App 통합이 작동하지 않습니다.


> [!NOTE]
> 이처럼 통합의 작동이 중지되는 이유는 이 경우 Lync Server 토폴로지가 같은 컴퓨터에 대해 두 개의 항목(자동 검색 항목과 수동 추가 항목)을 포함하기 때문입니다. 문제를 해결하고 Outlook Web App이 다시 작동하도록 하려면 Windows PowerShell을 사용하여 서버에 대한 신뢰할 수 있는 풀 및 신뢰할 수 있는 응용 프로그램 항목을 제거합니다. 자세한 내용은 <A href="remove-cstrustedapplicationpool.md">Remove-CsTrustedApplicationPool</A> 및 <A href="remove-cstrustedapplication.md">Remove-CsTrustedApplication</A> cmdlet의 도움말 항목을 참조하십시오.



이 두 서비스를 각기 다른 컴퓨터에서 실행하는 경우에는 Unified Communications Managed API 4.0 런타임이 설치되었는지 확인한 후에 Outlook Web App과 연결된 Lync Server 신뢰할 수 있는 응용 프로그램 풀과 신뢰할 수 있는 응용 프로그램을 만들어야 합니다. 그러면 서버가 알려진 서버 목록에 추가됩니다. 이렇게 하려면 먼저 Lync Server 관리 셸 내에서 다음과 같은 명령을 실행합니다.

    New-CsTrustedApplicationPool -Identity atl-owa-001.litwareinc.com -Registrar atl-cs-001.litwareinc.com -Site Redmond -RequiresReplication $False

위 명령에서 atl-owa-001.litwareinc.com은 Outlook Web App 풀의 정규화된 도메인 이름입니다. 이 이름은 Outlook Web App에 대한 액세스를 제공하는 인증서의 주체 이름 및 SAN(주체 대체 이름) 필드에 표시된 이름과 동일해야 합니다. 마찬가지로 atl-cs-001.litwareinc.com은 새로운 신뢰할 수 있는 응용 프로그램 풀을 호스트하는 Lync Server 2013 풀의 정규화된 도메인 이름입니다. 또한 여기서 지정된 사이트인 Redmond는 Lync Server 사이트의 SiteID를 나타냅니다. SiteID는 사이트의 DisplayName과 반드시 같을 필요는 없습니다. Lync Server 사이트의 SiteID는 Lync Server 관리 셸에서 다음 명령을 실행하여 검색할 수 있습니다.

    Get-CsSite | Select-Object DisplayName, SiteID

신뢰할 수 있는 응용 프로그램 풀을 만든 후에는 다음과 비슷한 명령을 사용하여 Outlook Web App에 대한 응용 프로그램 ID 및 포트를 구성합니다.

    New-CsTrustedApplication -ApplicationId OutlookWebApp -TrustedApplicationPoolFqdn atl-owa-001.litwareinc.com  -Port 5199

위 명령에서 ApplicationID는 단순히 신뢰할 수 있는 응용 프로그램들을 구분하기 위해 사용되는 식별자입니다. ApplicationID는 공백 및 기타 금지된 문자를 포함하지 않는 아무 텍스트 문자열이나 될 수 있습니다. 식별자를 올바르게 만들 수 있도록 ApplicationId를 지정할 때는 문자와 숫자만 사용하는 것이 좋습니다. 포트 매개 변수에 지정되는 값은 사용 가능한 네트워크 포트 중에서 관리자가 임의로 지정할 수 있습니다.

신뢰할 수 있는 응용 프로그램을 만든 후에는 다음 명령을 실행하여 변경 내용을 Lync Server 토폴로지에서 사용하도록 설정해야 합니다.

    Enable-CsTopology

모든 SIP URI 다이얼 플랜에 대해 Exchange 클라이언트 액세스 및 사서함 서버도 추가해야 합니다. 이렇게 하면 Lync Server용 ExUmRouting 토폴로지를 사용하여 서버가 신뢰할 수 있는 SIP 피어로 구성됩니다.

**Outlook Web App에서 인스턴트 메시징을 사용하도록 설정**

Lync Server를 올바르게 구성한 후에는 Outlook Web App 구성을 시작할 수 있습니다. 이 프로세스의 첫 번째 단계는 프런트 엔드 서버의 모든 Outlook Web App 가상 디렉터리에 대해 인스턴트 메시징을 사용하도록 설정하는 것입니다. 백 엔드 서버의 가상 디렉터리에 대해서는 인스턴트 메시징을 사용하도록 설정할 필요가 없습니다. 실제로 백 엔드 서버에서는 인스턴트 메시징을 사용하지 않는 것이 좋습니다. Exchange 관리 셸 내에서 다음 명령을 실행하면 클라이언트 액세스 서버에 대해 인스턴트 메시징을 사용하도록 설정할 수 있습니다.

    Get-OwaVirtualDirectory | Set-OwaVirtualDirectory -InstantMessagingEnabled $True -InstantMessagingType OCS


> [!NOTE]
> 기본적으로 인스턴트 메시징은 Outlook Web App을 설치할 때 사용하도록 설정됩니다. 즉, InstantMessagingEnabled 속성이 True로 설정됩니다. 그래도 인스턴트 메시징 유형을 OCS로 설정하려면 위의 명령을 실행해야 합니다. 기본적으로 InstantMessagingType은 None으로 설정됩니다.



그 다음에는 Outlook Web App의 Web.config 파일(이 파일은 일반적으로 C:\\Program Files\\Microsoft\\Exchange Server\\V15\\ClientAccess\\Owa 폴더에 있음)에 다음 두 행을 추가해야 합니다. 이 두 행은 Web.config 파일의 \<AppSettings\> 노드 아래에 추가해야 하며, 이 절차는 Outlook Web App이 설치된 백 엔드 서버에서만 수행해야 합니다.

    <add key="IMCertificateThumbprint" value="EA5A332496CC05DA69B75B66111C0F78A110D22d"/>
    <add key="IMServerName" value="atl-cs-001.litwareinc.com"/>

위 예에서 IMCertificateThumbprint 값은 백 엔드 서버에 설치된 Exchange 2013 인증서의 지문이어야 합니다. 이 정보는 Exchange 관리 셸에서 다음 명령을 실행하여 검색할 수 있습니다.

    Get-ExchangeCertificate

또한 IMServerName에 지정된 값은 Outlook Web App에 대한 신뢰할 수 있는 응용 프로그램 풀을 만든 Lync Server 풀의 정규화된 도메인 이름입니다.

Outlook Web App에 대해 사용하는 인증서는 Lync Server에서 신뢰하는 인증서여야 합니다. 인증서가 Lync Server 및 Exchange에서 모두 신뢰되는지 확인하는 한 가지 방법은 내부 인증 기관을 사용하여 사서함 서버에서 인증서를 만드는 것입니다. 이때 주체 이름으로 서버 FQDN을 사용하고 이 FQDN이 인증서 대체 이름 필드에 표시되는지 확인합니다. 만든 인증서는 백 엔드 서버로 가져올 수 있습니다. 그러면 같은 인증서가 1) Exchange 통합 메시징과 Lync Server 간의 통신, 그리고 2) Outlook Web App과 Lync Server 간의 통합 등 두 가지 용도로 사용됩니다.

Web.config 파일을 업데이트한 후에는 Outlook Web App 풀을 재사용할 수 있도록 Exchange 백 엔드 서버에서 다음 명령을 실행해야 합니다.

    C:\Windows\System32\Inetsrv\Appcmd.exe recycle apppool /apppool.name:"MSExchangeOWAAppPool"

재사용 작업이 성공하면 Exchange 관리 셸에 다음 메시지가 표시됩니다.

    "MSExchangeOWAAppPool" successfully recycled

**Outlook Web App 사서함 정책 구성**

이제 다음 명령을 실행하여 적합한 Outlook Web App 사서함 정책에서 인스턴트 메시징을 구성할 수 있습니다. 예를 들어 이 명령을 사서함 서버 중 하나에서 실행하면 기본 정책에서 인스턴트 메시징이 사용하도록 설정됩니다.

    Set-OwaMailboxPolicy -Identity "Default" -InstantMessagingEnabled $True -InstantMessagingType "OCS"

그리고 다음 명령은 모든 Outlook Web App 사서함 정책에 대해 인스턴트 메시징을 사용하도록 설정합니다.

    Get-OwaMailboxPolicy | Set-OwaMailboxPolicy -InstantMessagingEnabled $True -InstantMessagingType "OCS"

사서함 정책을 사용하도록 설정한 후에는 해당 정책으로 관리되는 모든 사용자에게 Lync Server 및 Outlook Web App이 완전히 통합됩니다. 이러한 통합의 조건은 다음과 같습니다.

  - 사용자에게 Exchange 2013에 사서함이 있습니다.

  - 사용자가 Lync Server 2013을 사용하도록 설정되었습니다.

  - 사용자에게 올바른 SIP 프록시 주소가 있습니다.

**Outlook Web App에서 인스턴트 메시징을 사용하지 않도록 설정**

위에서 설명한 것처럼 인스턴트 메시징은 Outlook Web App에서 기본적으로 사용하도록 설정됩니다. 즉, Outlook Web App과 Lync Server를 통합하지 않으면 사용자가 Outlook Web App에 로그온할 때마다 현재 상태 아이콘이 비어 있고 오류 메시지가 표시됩니다. 이 문제를 방지하려면 다음 Exchange 관리 셸 명령을 사용하여 Outlook Web App에서 인스턴트 메시징을 사용하지 않도록 설정합니다.

    Get-OwaVirtualDirectory | Set-OwaVirtualDirectory -InstantMessagingEnabled $False

**Outlook Web App과의 통합 확인**

인스턴트 메시징 및 현재 상태가 Outlook Web App과 통합되었는지 확인하려면 Outlook Web App 2013에 로그온합니다. 화면 오른쪽 위 모서리에 Exchange 표시 이름이 나타납니다. 이름 옆에 현재 상태 아이콘(예: 현재 상태가 대화 가능임을 나타내는 녹색 아이콘)이 있으면 Lync Server와 Outlook Web App이 정상적으로 통합된 것입니다.

Outlook Web App에 처음 로그온한 후 이벤트 ID가 112이고 원본이 MSExchange OWA인 이벤트가 사서함 서버의 이벤트 로그에 기록되었는지 확인합니다. 이 이벤트는 인스턴트 메시징 끝점 관리자가 정상적으로 초기화되었음을 나타냅니다. 인스턴트 메시징이 작동하지 않는 것으로 보이면 사서함 서버에서 C:\\Program Files\\Microsoft\\Exchange server\\V15\\Logging\\OWA\\InstantMessaging 폴더의 로그 파일을 확인합니다. Logging 또는 InstantMessaging 폴더가 없으면 통합이 실패한 것입니다. 이 경우에는 Lync Server에서 SIPStack 추적을 사용(모든 수준 및 모든 플래그)하여 통합 실패 이유를 확인할 수 있습니다.

