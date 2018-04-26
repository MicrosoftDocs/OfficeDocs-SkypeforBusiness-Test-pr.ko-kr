---
title: Lync Server 2013의 XMPP(Extensible Messaging and Presence Protocol) 페더레이션 계획
TOCTitle: Lync Server 2013의 XMPP(Extensible Messaging and Presence Protocol) 페더레이션 계획
ms:assetid: 952b33e2-1f58-4831-9a39-1dfec2a316ad
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205107(v=OCS.15)
ms:contentKeyID: 49304422
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 XMPP(Extensible Messaging and Presence Protocol) 페더레이션 계획

 

_**마지막으로 수정된 항목:** 2012-10-22_

이전 버전의 Lync Server 및 Office Communications Server는 XMPP(Extensible Messaging and Presence Protocol) 배포와의 페더레이션을 위해 별도의 서버 역할로 배포할 수 있는 XMPP 게이트웨이를 제공했습니다. Microsoft Lync Server 2013에서는 XMPP 기능을 하나의 기능으로 배포할 수 있습니다. XMPP 기능은 두 부분, 즉 에지 서버에서 실행되는 XMPP 프록시와 프런트 엔드 서버에서 실행되는 XMPP 게이트웨이로 설치됩니다.

XMPP의 배포와 구성에 대해서는 [Lync Server 2013에서 외부 사용자 액세스 배포](lync-server-2013-deploying-external-user-access.md)에서 다룹니다. 방화벽 포트 및 프로토콜 규칙을 정의하고, 인증서를 구성하고, DNS 레코드를 추가하여 조직의 XMPP 지원을 계획해야 합니다. 이 섹션의 다음 항목에는 배포에 대한 XMPP 페더레이션을 성공적으로 계획하는 데 필요한 정보가 요약되어 있습니다.


> [!IMPORTANT]
> Lync Server 2013의 XMPP 기능은 Microsoft에서 Google Talk와의 메신저 페더레이션에 대해 지원 및 테스트합니다. 다른 모든 XMPP 시스템의 경우 타사 공급업체에 문의하여 Lync Server 2013과의 페더레이션 지원 여부, 배포 또는 문제 해결 권장 사항에 대해 알아보십시오.



## 이 단원의 내용

  - [인증서 요약 - XMPP(Extensible Messaging and Presence Protocol) 페더레이션](lync-server-2013-certificate-summary-extensible-messaging-and-presence-protocol-xmpp-federation.md)

  - [포트 요약 - XMPP(확장 가능 메시징 및 현재 상태 프로토콜) 페더레이션](lync-server-2013-port-summary-extensible-messaging-and-presence-protocol-xmpp-federation.md)

  - [DNS 요약 - XMPP(Extensible Messaging and Presence Protocol) 페더레이션](lync-server-2013-dns-summary-extensible-messaging-and-presence-protocol-xmpp-federation.md)

## 참고 항목

#### 작업

[Lync Server 2013에서 XMPP 페더레이션 설정](lync-server-2013-setting-up-xmpp-federation.md)  
[Lync Server 2013에서 XMPP 페더레이션 사용자 액세스를 제어하도록 정책 구성](lync-server-2013-configure-policies-to-control-xmpp-federated-user-access.md)  

#### 기타 리소스

[Lync Server 2013에서 XMPP 페더레이션 파트너 관리](lync-server-2013-manage-xmpp-federated-partners-for-your-organization.md)  
[Get-CsExternalAccessPolicy](get-csexternalaccesspolicy.md)  
[Get-CsXmppAllowedPartner](get-csxmppallowedpartner.md)  
[Get-CsXmppGatewayConfiguration](get-csxmppgatewayconfiguration.md)

