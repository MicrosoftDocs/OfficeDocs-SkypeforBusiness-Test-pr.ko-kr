---
title: 'Lync Server 2013: 에지 서버 계획에 영향을 주는 Lync Server의 변경 사항'
TOCTitle: 에지 서버 계획에 영향을 주는 Lync Server 2013의 변경 사항
ms:assetid: 66305160-c9b8-4bc4-9f24-8ee8d9a294f7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204965(v=OCS.15)
ms:contentKeyID: 49303866
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 에지 서버 계획에 영향을 주는 Lync Server 2013의 변경 사항

 

_**마지막으로 수정된 항목:** 2012-10-22_

Lync Server 2013에서는 사용자를 위한 기능 및 통신 방법을 확장하는 새로운 기능이 도입되었습니다. 또한 Lync Server 2013에서는 기존 서비스를 보다 효과적으로 통합하고 조직에 제공되는 서비스를 확장할 수 있도록 기능이 변경되었습니다. 다음은 Lync Server 2013  에지 서버 서비스의 계획 및 배포에 영향을 줄 수 있는 변경 내용들에 대한 요약 설명입니다.

## IPv6 주소 지정 지원

Lync Server 2013에서는 모든 에지 서버 서비스에 대해 IPv6 주소 지정이 지원됩니다. Windows Server에서 구성을 통해 인터페이스에 대한 IPv6 주소를 제공한 경우, 토폴로지 작성기의 IP 주소 구성을 통해 에지 서버 구성에서 IPv6 주소를 사용할 수 있습니다. 또한 XMPP(Extensible Messaging and Presence Protocol)에서도 IPv6이 지원됩니다. 추가 구성은 필요하지 않습니다. 토폴로지에 IPv6가 구성된 경우 XMPP에서 IPv6가 사용됩니다(필요한 경우).

Lync Server 2013에서 IPv6를 지원하기 위해 추가된 한 가지 요구 사항은 검색하고 IPv6 주소로 확인되어야 하는 레코드에 대한 DNS(Domain Name System) 레코드를 만들어야 한다는 것입니다. IPv6 DNS는 **AAAA** ("quad-A"라고 부름)로 정의되는 호스트 레코드를 사용합니다. 다른 레코드 유형은 해당 IPv4 항목과 비슷합니다.

## XMPP(Extensible Messaging and Presence Protocol) 배포 지원

에지 서버에는 완전히 통합된 XMPP 프록시(에지 서버에 배포됨)와 XMPP 게이트웨이(프런트 엔드 서버에 배포됨)가 도입되었습니다. XMPP 페더레이션은 선택적인 구성 요소로 배포할 수 있습니다. XMPP 프록시 및 XMPP 게이트웨이를 추가하고 구성하면 Microsoft Lync 2013 사용자가 IM(인스턴트 메시징) 및 현재 상태에 대해 XMPP 기반 파트너의 연락처를 추가하도록 설정할 수 있습니다.


> [!NOTE]
> 현재까지 에지 서버의 XMPP 서비스에서는 Lync Server 클라이언트와 XMPP 기반 연락처 사이에 IM 및 현재 상태만 제공합니다. 또한 XMPP는 하나의 사이트에서만 호스팅됩니다.




> [!IMPORTANT]
> Lync Server 2013의 XMPP 기능은 Microsoft에서 Google Talk와의 메신저 페더레이션에 대해 지원 및 테스트합니다. 다른 모든 XMPP 시스템의 경우 타사 공급업체에 문의하여 Lync Server 2013과의 페더레이션 지원 여부, 배포 또는 문제 해결 권장 사항에 대해 알아보십시오.



## 오디오/비디오 인증 롤링 및 서버 간 인증 인증서 지원

인증서는 A/V 인증 서비스의 클라이언트 및 기타 소비자와 서버 간 인증을 위해 발급되는 토큰을 생성하는 데 사용됩니다. 오디오/비디오 인증 인증서는 *AudioVideoAuthentication* 유형이며 서버 간 인증 인증서는 *OAuthTokenIssuer* 유형입니다.

오디오/비디오 인증의 경우 토큰은 포트 할당 요청을 인증하는 데 사용되며, 토큰이 최대 8시간(토큰의 기본 수명) 동안 캐시에 저장됩니다. 정상 작동 상황에서는 A/V 소비자에 대해 인증 자료를 만들고 배포하는 데 매우 안정적인 방법이지만 인증서는 제한된 수명을 갖고 있으며 미리 정의된 날짜 및 시간(만든 날짜와 인증서를 만든 인증 기관에서 적용되는 정책 기반, 이 유형의 인증서의 경우 일반적으로 2년)에 만료됩니다. 인증서가 만료되면 만료된 인증서로 만들어지고 소비자가 캐시한 모든 토큰이 무효가 됩니다. 만료된 인증서로 만들어진 토큰을 사용하려고 시도하면 미디어 중계 할당이 실패하고 현재 오디오/비디오 세션이 실패합니다. 클라이언트가 정상적인 오디오 및 비디오 기능을 다시 사용하려면 유효한 인증서로 만들어진 새 토큰을 얻어야 합니다.

서버 간 인증은 배포의 모든 서버에서 요청되고 적용되는 전역 인증서로 관리됩니다. 이 인증서는 Lync Server 2013의 서버 인증뿐만 아니라 Exchange 2013 및 Microsoft SharePoint Server 2013에 대한 인증도 수행합니다. 서버 간 인증의 작동 방식에 대한 자세한 내용은 [Lync Server 2013에서 서버 간 인증(Oauth) 및 파트너 응용 프로그램 관리](lync-server-2013-managing-server-to-server-authentication-oauth-and-partner-applications.md)를 참조하십시오. 오디오/비디오 인증 프로세스와 서버 간 인증 프로세스 간의 중요한 차이점은 인증 또는 토큰의 수명입니다. 오디오/비디오 인증의 경우 인증은 8시간 후에 만료되며, 서버 간 인증은 수명이 24시간입니다. 각 인증서 유형에 맞게 계획을 세워야 합니다.

Lync Server 2013에서 새로운 기능은 현재 인증서가 만료되기 전에 미리 오디오/비디오 인증 인증서 및 서버 간 인증 인증서에 대한 교체 인증서를 준비할 수 있는 기능입니다. 그 다음에는 새로운 토큰 또는 새로운 인증 요청을 생성할 때 새로운 인증서가 사용됩니다. 하지만 이전 인증서는 현재 세션 및 인증을 확인하기 위해 보존됩니다. 이러한 방식으로 토큰 및 인증서 만료로 인한 모든 오류를 효과적으로 방지할 수 있습니다. 이 기능에 대한 자세한 내용 및 구성 방법은 [Set-CsCertificate에 -Roll을 사용하여 Lync Server 2013에서 AV 및 OAuth 인증서 준비](lync-server-2013-staging-av-and-oauth-certificates-using-roll-in-set-cscertificate.md)를 참조하십시오.

## 쿠키 기반 선호도에 대한 의존성 감소

이전 버전의 Lync Server 및 Office Communications Server에서는 클라이언트와 웹 서비스 세션 상태를 유지 관리하기 위해 웹 서비스에서 쿠키 기반 선호도가 사용되었습니다. Lync Server 2013 웹 서비스는 쿠키 기반 선호도에 대한 대부분의 요구 사항을 없애주는 내장된 선호도 메커니즘이 사용됩니다.


> [!WARNING]
> Microsoft Lync 2010 Mobile 클라이언트는 계속해서 쿠키 기반 선호도를 사용해야 하며 모든 클라이언트를 최신 Microsoft Lync Mobile 클라이언트(출시 날짜 미정)로 마이그레이션할 때까지 쿠키 기반 선호도 구성이 필요합니다.



Lync Server 2013의 쿠키 기반 선호도에 대한 자세한 내용은 [Lync Server 2013의 외부 사용자 액세스에 필요한 구성 요소](lync-server-2013-components-required-for-external-user-access.md)를 참조하십시오.

## 자동 검색 향상 기능

Lync Server 2013의 자동 검색 기능을 통해 클라이언트는 통신에 사용할 수 있는 추가 기능을 확인할 수 있습니다. 자동 검색은 원래 Lync Server 2010: 2011년 11월 이동성 및 Microsoft Lync 2010 Mobile을 위한 누적 업데이트로 소개되었습니다. 자동 검색 기능(DNS 레코드 이름 LyncDiscover 및 LyncDiscoverInternal이라고도 부름)을 통해 클라이언트는 이동성 서비스( Microsoft Lync 2010 Mobile 클라이언트용), Microsoft Lync Web App 및 Lync Web 스케줄러는 물론 Microsoft Exchange Server 및 SharePoint Server와의 통신을 위한 기능을 찾아서 사용할 수 있습니다. 자동 검색은 사용자의 인프라 및 Lync Server 2013 서버의 일반 설치 및 배포의 일부로 설치됩니다. 토폴로지 작성기 및 Lync Server 배포 마법사에서는 Lync Server 2010: 2011년 11월 누적 업데이트에 필요하던 대부분의 구성 작업을 수행할 필요가 없습니다.

## 모바일 클라이언트를 위한 서비스

Lync Server 2010: 2011년 11월 누적 업데이트로 소개된 Lync Server 2013의 모바일 서비스는 Lync Mobile 실행 휴대폰, 지원되는 Apple iOS, Android, Windows Phone을 사용하는 태블릿 장치나 Nokia 모바일 장치가 인스턴트 메시지 전송 및 수신, 연락처 보기 및 현재 상태 보기와 같은 작업을 수행할 수 있게 해줍니다. 또한 모바일 장치는 클릭하여 회의 참가하기, 회사번호로 전화, 단일 번호 연결, 음성 메일, 부재 중 통화 알림 등 일부 Enterprise Voice 기능도 지원합니다.


> [!NOTE]
> 모바일 서비스에는 역방향 프록시 및 프런트 엔드 서버에 배포되는 게시된 서비스가 사용됩니다. 에지 서버는 변경할 필요가 없습니다. Lync Server 액세스 에지 서비스를 실행하는 서버에서 아웃바운드 SIP/TCP/5061만 최소한으로 필요합니다.



## 디렉터 역할이 선택 사항임

Lync Server 2013 토폴로지에서 디렉터 서버의 역할은 변경되지 않았습니다. 이 서버는 여전히 웹 서비스를 호스팅하고, 수신되는 사용자 요청을 사전 인증하고, 외부 사용자를 해당 홈 풀로 전달합니다. Microsoft에서 디렉터를 권장 역할에서 선택적인 역할로 변경한 것은 디렉터의 가치를 줄이기 위한 것이 아닙니다. 이러한 변경 목적은 기능을 훼손하지 않으면서 서버 수 및 기타 하드웨어 요구 사항(예: 디렉터에 대한 하드웨어 부하 분산 장치)을 줄이기 위한 것입니다. 프런트 엔드 서버는 제공된 서비스에 영향을 주지 않으면서 디렉터와 동일한 역할을 수행하므로, 필요한 경우에만 디렉터를 배포할 수 있습니다. 프런트 엔드 서버가 디렉터 대신 동일한 서비스를 제공하는 것이 확실하면 디렉터를 제외시켜도 안전합니다.

