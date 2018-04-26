---
title: Lync Server 2013의 자동 검색 이해
TOCTitle: Lync Server 2013의 자동 검색 이해
ms:assetid: d70a15b7-750b-4e0f-9a7f-0254d6d486c3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ945654(v=OCS.15)
ms:contentKeyID: 52056970
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 자동 검색 이해

 

_**마지막으로 수정된 항목:** 2013-06-03_

Lync Server 2013 자동 검색 서비스는 원래 Lync Server 2010용 누적 업데이트(2011년 11월)의 일부분으로 Microsoft Lync Server 2010에 도입된 기능입니다. 이 누적 업데이트를 통해 필요한 사항이 수정되었으며 Lync Mobile 및 Lync 2013 클라이언트 지원도 제공되었습니다.

Lync Server 2013에서 자동 검색 서비스는 외부 및 내부 모바일 클라이언트의 작동에 필수적인 요소이며, 최근 도입된 Windows 8용 Lync Windows 스토어 앱과 같은 새로운 클라이언트에서도 사용할 수 있도록 확대되었습니다. Lync 2013 데스크톱 클라이언트에서도 자동 검색이 사용됩니다. Lync Server에서 자동 검색은 필수 DNS(Domain Name System) 레코드 **lyncdiscover.\<도메인\>** 및 **lyncdiscoverinternal.\<도메인\>**으로 인식됩니다. 또한 Lync 2010 및 Lync 2013 데스크톱 클라이언트의 최신 버전에서는 DNS(Domain Name System) SRV 레코드보다 자동 검색이 우선적으로 사용되며, lyncdiscover.\<도메인\> 또는 lyncdiscoverinternal.\<도메인\>이 응답하지 않거나 확인되지 않는 경우에만 DNS SRV 레코드가 사용됩니다. Windows 8용 Lync Windows 스토어 앱 및 Lync Mobile에서는 자동 검색만 사용하며 기존의 DNS SRV 레코드는 참조하지 않습니다.

Lync Server 2013에서는 자동 검색이 확장되어 클라이언트가 사용할 수 있는 요소, 기능 및 통신 방법에 대한 정보를 클라이언트에 전달합니다. 이 정보는 클라이언트에서 발송되는 요청을 통해 전달되며, Lync Server 웹 서비스는 클라이언트가 사용 가능한 기능과 해당 기능에 연결하는 방법을 보여 주는 명확하게 정의된 응답을 자동 검색 응답 문서 형식으로 제공합니다.

자동 검색 응답 문서(웹 서비스가 이 문서를 통해 클라이언트에 기능을 전달하는 방법 포함)를 가장 효율적으로 파악하려면 Lync 웹 서비스 자동 검색 응답 문서를 분할하여 각 줄을 일반적인 응답으로 정의하면 됩니다.


> [!NOTE]
> 아래에서 설명하는 세부 정보에서는 사용자가 이미 인증 요청에 응답하여 홈 서버에 인증한 상태입니다.




> [!NOTE]
> Lync 자동 검색 웹 서비스는 MSDN(<STRONG>Microsoft Developer Network</STRONG>) <STRONG>Microsoft Office 프로토콜</STRONG>의 <STRONG>공개 사양</STRONG> 섹션에 정의되어 있습니다. 자세한 내용은 전체 사양 문서 "Lync 자동 검색 웹 서비스 프로토콜"(<A class=uri href="http://go.microsoft.com/fwlink/?linkid=273839">http://go.microsoft.com/fwlink/?linkid=273839</A>)을 참고하세요. 인증에 대한 자세한 내용은 "OC 인증 웹 서비스 프로토콜"(<A class=uri href="http://go.microsoft.com/fwlink/?linkid=279015">http://go.microsoft.com/fwlink/?linkid=279015</A>)을 참고하세요.



## Lync Server 웹 서비스 자동 검색 응답

자동 검색 요청을 발송하면 반환되는 응답은 내부 클라이언트나 외부 클라이언트에서 동일합니다. 위치를 인식하는 일부 매개 변수는 변경될 수 있습니다. 클라이언트 요청은 수신되었는데 실제 풀이 연결된 풀과 다른 경우에는 해당 사용자에 대해 사용자의 홈 풀이 설정됩니다. 사용자 계정은 다른 풀에 있지만 같은 사무실에서 로그인하는 동료의 경우 응답이 약간 달라집니다. 응답은 해당 사용자에 대한 올바른 프런트 엔드 서버 또는 프런트 엔드 풀을 나타냅니다.

자동 검색 응답 문서의 예는 다음과 같습니다.

    <AutodiscoverResponse xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" AccessLocation="External">
       <User>
          <SipServerInternalAccess fqdn="pool01.contoso.com" port="5061"/>
          <SipClientInternalAccess fqdn=" pool01.contoso.com" port="443"/>
          <SipServerExternalAccess fqdn="sip.contoso.com" port="5061"/>
          <SipClientExternalAccess fqdn="sip.contoso.com " port="443"/>
          <Link token ="External/Autodiscover" href="https://webexternal.contoso.com/Autodiscover/AutodiscoverService.svc/root"/>
          <Link token="Internal/Autodiscover" href="https://webinternal.contoso.net/Autodiscover/AutodiscoverService.svc/root"/>
          <Link token="External/AuthBroker" href="https://webexternal.contoso.com/Reach/sip.svc"/>
          <Link token="Internal/AuthBroker" href="https://webinternal.contoso.net/Reach/sip.svc"/>
          <Link token="External/WebScheduler" href="https://webexternal.contoso.com/Scheduler"/>
          <Link token="Internal/WebScheduler" href="https://webinternal.contoso.net/Scheduler"/>
          <Link token="External/Mcx" href="https://webexternal.contoso.com/Mcx/McxService.svc"/>
          <Link token="Internal/Mcx" href="https://webexternal.contoso.net/Mcx/McxService.svc"/>
          <Link token="External/Ucwa" href="https://webexternal.contoso.com/ucwa/v1/applications"/>
          <Link token="Internal/Ucwa" href="https://webinternal.contoso.net/ucwa/v1/applications"/>
          <Link token="Ucwa" href="https://webexternal.contoso.com/ucwa/v1/applications"/>
          <Link token="External/XFrame" href="https://webexternal.contoso.com/Autodiscover/XFrame/XFrame.html"/>
          <Link token="Internal/XFrame" href="https://webinternal.contoso.net/Autodiscover/XFrame/XFrame.html"/>
          <Link token="XFrame" href="https://webexternal.contoso.com/Autodiscover/XFrame/XFrame.html"/>
          <Link token="Self" href="https://webexternal.contoso.net/Autodiscover/AutodiscoverService.svc/root/user"/>
       </User>
    </AutodiscoverResponse>

## 자동 검색 응답 문서 세부 정보

자동 검색 응답 문서는 두 가지 형식 중 하나일 수 있습니다. 기본 형식은 JSON(JavaScript Object Notation)입니다. 다른 형식은 XML(Extensible Markup Language) 문서입니다. 이 예제에는 XML이 사용되었습니다. 응답 문서에는 형식을 결정하는 스키마가 정의되어 있으므로 요청과 응답을 예측할 수 있습니다. 문서에서 사용된 스키마를 설명하는 줄은 요청이나 응답의 첫 줄입니다.

    <AutodiscoverResponse xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" AccessLocation="External">

**AccessLocation=”External”** 정의는 외부 사용자가 요청을 보냈음을 나타냅니다.

    <SipServerInternalAccess fqdn="pool01.contoso.com" port="5061"/>

    <SipServerExternalAccess fqdn="sip.contoso.com" port="5061"/>

SipServerInternalAccess 및 SipServerExternalAccess는 현재 사용되지 않습니다. 이러한 항목은 이후 사용하기 위해 예약됩니다.

    <SipClientInternalAccess fqdn=" pool01.contoso.com" port="443"/>

    <SipClientExternalAccess fqdn="sip.contoso.com " port="443"/>

SipClientInternalAccess 및 SipClientExternalAccess는 내부 또는 외부 클라이언트가 정의된 SIP 서버에 액세스하는 데 사용할 정규화된 도메인 이름과 포트를 설명합니다. Lync 데스크톱 클라이언트 및 Lync Windows 스토어 앱은 해당 위치(내부 또는 외부)에 따라 이러한 항목을 사용하여 디렉터 또는 프런트 엔드 서버를 찾습니다.

    <Link token="Internal/Autodiscover" href="https://webinternal.contoso.net/Autodiscover/AutodiscoverService.svc/root"/>

    <Link token ="External/Autodiscover" href="https://webexternal.contoso.com/Autodiscover/AutodiscoverService.svc/root"/>

`Autodiscover` 참조는 자동 검색 서비스의 서비스 진입점을 포함합니다. 토큰 특성에는 서비스 이름이 포함되며, href는 클라이언트를 위해 서비스를 찾을 수 있는 위치를 정의하는 URL입니다. 외부 네트워크의 클라이언트는 `External/Autodiscover`를 사용합니다. 자동 검색 서비스는 배포 프로세스의 일부분으로 설치됩니다. `Internal/Autodiscover`는 현재 사용되지 않으며 이후 사용하기 위해 예약됩니다.

    <Link token="Internal/AuthBroker" href="https://webinternal.contoso.net/Reach/sip.svc"/>

    <Link token="External/AuthBroker" href="https://webexternal.contoso.com/Reach/sip.svc"/>

`AuthBroker` 참조는 내부 및 외부 인증 브로커 서비스(여기서는 sip.svc)의 서비스 진입점을 포함합니다. 토큰 특성에는 서비스 이름이 포함되며, href는 클라이언트를 위해 서비스를 찾을 수 있는 위치를 정의하는 URL입니다. 내부 네트워크의 클라이언트는 `Internal/AuthBroker`를 사용합니다. 외부 네트워크의 클라이언트는 `External/AuthBroker`를 사용합니다. AuthBroker 서비스는 내부 Lync Server 2013 배포 웹 서비스 배포 프로세스의 일부분으로 설치됩니다.

    <Link token="Internal/WebScheduler" href="https://webinternal.contoso.net/Scheduler"/>

    <Link token="External/WebScheduler" href="https://webexternal.contoso.com/Scheduler"/>

`WebScheduler` 토큰은 Lync Server 회의의 웹 기반 일정에 대한 클라이언트 액세스용 URL을 참조합니다. 현재는 `External/WebScheduler`만 사용됩니다. WebScheduler는 내부 Lync Server 2013 배포 웹 서비스 배포 프로세스의 일부분으로 설치됩니다.

    <Link token="Internal/Mcx" href="https://webexternal.contoso.net/Mcx/McxService.svc"/>

    <Link token="External/Mcx" href="https://webexternal.contoso.com/Mcx/McxService.svc"/>

`Internal/Mcx` 및 `External/Mcx`는 Lync Server 2010용 누적 업데이트(2011년 11월)에 도입된 Mobility Service의 위치입니다. 이러한 참조는 Lync 2010 Mobile에서도 지원되는 모든 장치에 계속 사용됩니다. Mcx 서비스는 내부 Lync Server 2013 배포 웹 서비스 배포 프로세스의 일부분으로 설치됩니다.

    <Link token="Internal/Ucwa" href="https://webinternal.contoso.net/ucwa/v1/applications"/>

    <Link token="External/Ucwa" href="https://webexternal.contoso.com/ucwa/v1/applications"/>

    <Link token="Ucwa" href="https://webexternal.contoso.com/ucwa/v1/applications"/>

클라이언트는 **Internal/Ucwa**, **External/Ucwa** 및 **Ucwa**를 통해 UCWA API(통합 통신 웹 응용 프로그래밍 인터페이스, 간단하게 UCWA)에 액세스할 수 있습니다. `Internal/Ucwa` 및 `External/Ucwa` 가상 디렉터리는 이후 기능 개선용으로 예약된 액세스 지점이며 사용되지 않습니다. `Ucwa` 가상 디렉터리는 지원되는 모든 장치에서 Microsoft Lync Mobile용으로 사용됩니다(Lync Server 2013에서 도입됨). UCWA 서비스는 내부 Lync Server 2013 배포 웹 서비스 배포 프로세스의 일부분으로 설치됩니다.

    <Link token="Internal/XFrame" href="https://webinternal.contoso.net/Autodiscover/XFrame/XFrame.html"/>

    <Link token="External/XFrame" href="https://webexternal.contoso.com/Autodiscover/XFrame/XFrame.html"/>

    <Link token="XFrame" href="https://webexternal.contoso.com/Autodiscover/XFrame/XFrame.html"/>

`Internal/XFrame`, **External/XFrame** 및 **XFrame**을 통해 UCWA 기반 서버 응용 프로그램에 액세스할 수 있습니다. XFrame은 내부 Lync Server 2013 배포 웹 서비스 배포 프로세스의 일부분으로 설치됩니다.

    <Link token="Self" href="https://webexternal.contoso.net/Autodiscover/AutodiscoverService.svc/root/user"/>

`Self` 토큰은 요청을 하는 클라이언트와 관련된 정보(사용자 응답 유형)를 참조합니다. 이 요청을 한 클라이언트는 외부 클라이언트이며 이 자동 검색 참조는 자동 검색 서비스의 사용자 부분에 대한 참조입니다.

## 참고 항목

#### 기타 리소스

[Lync Server 2013의 외부 사용자 액세스 구성 요소에 대한 시스템 요구 사항](lync-server-2013-system-requirements-for-external-user-access-components.md)  
[Lync Server 2013의 자동 검색 계획](lync-server-2013-planning-for-autodiscover.md)

