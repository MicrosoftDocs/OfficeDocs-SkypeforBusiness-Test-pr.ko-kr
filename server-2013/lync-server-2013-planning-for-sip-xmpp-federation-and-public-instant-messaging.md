---
title: Lync Server 2013에서 SIP, XMPP 페더레이션 및 공용 IM 계획
TOCTitle: Lync Server 2013에서 SIP, XMPP 페더레이션 및 공용 IM 계획
ms:assetid: 3b234d92-b9ff-4b1d-910e-084c6f17e751
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204825(v=OCS.15)
ms:contentKeyID: 49303357
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 SIP, XMPP 페더레이션 및 공용 IM 계획

 

_**마지막으로 수정된 항목:** 2013-10-28_

내부 및 외부 사용자가 파트너 조직 또는 서비스의 연락처에 액세스할 수 있도록 에지 서버를 구성할 수 있습니다. 페더레이션이라고도 하는 이러한 파트너 계약은 다음 기능 중 하나 또는 모든 기능을 파트너 페더레이션에 포함된 사용자 조직 내의 연락처 또는 사용자에 대한 파트너 페더레이션 내의 연락처에게 제공할 수 있습니다.

  - 메신저 대화 및 현재 상태

  - 공동 작업 및 회의(예: 웹 회의)

  - 오디오 회의나 비디오 회의 중 하나 또는 둘 다

경우에 따라 Microsoft Lync Server 2013과 XMPP(Extensible Messaging and Presence Protocol) 연락처 간의 IM(메신저 대화) 및 현재 상태와 같은 통신은 피어 투 피어 전용으로, 사용자와 페더레이션 파트너의 연락처만 지원합니다. Lync Server, Lync Server 2010에서 Lync Server 2013으로의 페더레이션과 같은 경우에는 여러 참가자를 대화에 참가하도록 초대할 수 있습니다.

## Lync Server 및 Office Communications Server 페더레이션

Microsoft Lync Server 2013, Lync Server 2010 및 Office Communications Server 간에 페더레이션을 구성하면 피어 투 피어 및 단체 통신이 지원됩니다. 피어 투 피어 대화는 단체 대화로 확대되어 임시 모임을 허용할 수 있습니다. 웹 회의 또는 오디오/비디오 회의 같은 모임은 페더레이션 파트너의 대화 상대뿐 아니라 조직 내 대화 상대를 포함하도록 예약할 수 있습니다.

페더레이션은 Microsoft Office Live Communications Server 2005에서 처음 도입되었으며 단일 유형의 페더레이션인 '직접 페더레이션'만 지원했습니다. 직접 페더레이션을 사용하려면 페더레이션 파트너의 SIP(Session Initiation Protocol) 도메인 및 에지 서버의 FQDN(정규화된 도메인 이름)을 알아야 했습니다. Live Communications Server 2005 SP1에서 추가 페더레이션 유형이 도입되었으며 여기에는 에지 서버를 찾기 위해 페더레이션 파트너에 의해 게시되는 DNS(Domain Name System) SRV 레코드만 필요합니다. 해당 릴리스에 사용되는 용어는 다음과 같습니다.

  - *개방형 확장 페더레이션* : 모든 SIP 도메인 이름이 수락되고 DNS SRV를 사용하여 파트너 에지 서버를 찾습니다.

  - *확장 페더레이션* : 파트너의 SIP 도메인 이름을 조직의 페더레이션 파트너로 구성하고 DNS SRV를 사용하여 파트너 에지 서버를 찾습니다.

  - *직접 페더레이션* : 파트너의 SIP 도메인 이름과 에지 서버 FQDN을 구성합니다.

  - *서버 허용 목록* : 모든 도메인을 수락하고 DNS SRV를 사용하여 호스팅 공급자 또는 공용 IM 연결 공급자의 에지 서버를 찾습니다.

Microsoft Office Communications Server 2007에서는 페더레이션 유형의 이름이 실제 수행 작업을 더 잘 표현하도록 업데이트되었습니다.

  - 개방형 확장 페더레이션은 *검색된 파트너 도메인* 으로 변경되었습니다.

  - 확장 페더레이션은 *허용된 파트너 도메인* 으로 변경되었습니다.

  - 직접 페더레이션은 *허용된 파트너 서버* 로 변경되었습니다.

  - 서버 허용 목록은 *호스팅 공급자* 및 *공용 IM 공급자* 로 변경되었습니다.

Microsoft Lync Server 2010에서는 Microsoft Lync Online 2010 및 Microsoft Office 365에 따라 좁은 의미의 호스팅 공급자 유형을 도입했으며 '허용된 파트너 도메인' 페더레이션 유형으로 정의되는 동일한 허용 목록에 따라 변하도록 설정할 수 있습니다.

Microsoft Lync Server 2013, Lync Server 2010 및 Office Communications Server 간에 페더레이션을 사용하도록 설정하면 에지 서버 및 역방향 프록시를 사용하여 정의하는 규칙 및 허용된 파트너 도메인이 적용됩니다. 계획 관점에서 봤을 때 다른 Lync Server와 페더레이션하는 경우 Office Communications Server에 다음이 요구됩니다.

  - 토폴로지 작성기에서 페더레이션을 사용하도록 설정해야 합니다. 자세한 내용은 배포 항목인 [Lync Server 2013에서 SIP 페더레이션, XMPP 페더레이션 및 공용 메신저 구성](lync-server-2013-configuring-sip-federation-xmpp-federation-and-public-instant-messaging.md) 섹션을 참고하세요.

  - 페더레이션 도메인 검색에 필요한 요구 사항을 결정합니다.
    
       페더레이션을 수동으로 구성하는 경우 Lync Server 제어판의 **페더레이션 및 외부 액세스** , **SIP 페더레이션 도메인** 에 입력할 수 있도록 파트너 에지 서버의 FQDN(정규화된 도메인 이름)과 도메인 이름(또는 온라인 도메인 이름)이 필요합니다. FQDN으로 도메인을 허용하거나 차단하려면 **새로 만들기** 로 정책을 새로 만들거나 **편집** 으로 기존 정책을 편집합니다.
        

      > [!WARNING]
      > 페더레이션 파트너의 에지 서버를 수동으로 구성하는 경우 파트너가 에지 서버의 IP 주소를 변경하면 오류가 발생할 수 있습니다.        

      > [!NOTE]
      > <STRONG>새 SIP 페더레이션 도메인</STRONG> 의 경우 Microsoft Lync Online, Microsoft Office 365에 <STRONG>도메인 이름 또는 FQDN</STRONG> 을 지정해야 합니다. Microsoft Lync Server 2013, Lync Server 2010 및 Office Communications Server의 경우 <STRONG>액세스 에지 서비스(FQDN)</STRONG> 도 지정해야 합니다.

    
       파트너가 사용자의 에지 서버를 검색할 수 있는 '검색된 파트너 페더레이션'의 경우 포트 5061과 에지 서버의 호스트(A) 레코드를 가리키도록 외부 DNS(\_sipfederationtls.\_tcp.contoso.com)에 SRV 레코드를 만들어야 합니다.        

      > [!IMPORTANT]
      > Windows Phone 또는 Apple iPhone, iPad, 기타 Apple 장치에서 Microsoft Lync Mobile 클라이언트를 지원하는 경우 푸시 알림 서비스 또는 푸시 알림 서비스를 사용하면 Lync Mobile 클라이언트가 있는 각 SIP 도메인마다 _sipfederationtls._tcp. <EM>&lt;SIP 도메인&gt;</EM> SRV 레코드가 존재하도록 계획해야 합니다. Android 및 Nokia Symbian Lync Mobile은 푸시 알림을 사용하지 않으므로 이러한 요구 사항의 적용을 받지 않습니다.



  - 페더레이션 도메인을 지원하도록 외부 사용자 액세스 정책을 구성해야 합니다.

  - 사용하는 대화 상대 또는 페더레이션을 수용할 수 있도록 SIP(Session Initiation Protocol), 웹 회의 및 오디오/비디오용 방화벽 포트를 열어야 합니다. 자세한 내용은 [Lync Server 2013에 대한 외부 A/V 방화벽 및 포트 요구 사항 확인](lync-server-2013-determine-external-a-v-firewall-and-port-requirements.md) 섹션을 참고하세요.

다음은 Microsoft Lync Server 2013 및 Lync Server 2010의 페더레이션에 대한 인증서, 포트/프로토콜 및 DNS 요구 사항을 정의하는 데 도움이 되는 정보입니다.

Microsoft Lync Server 2013  에지 서버를 계획 또는 배포했다면 인증서, 방화벽 및 포트/프로토콜 요구 사항과 DNS 요구 사항을 계획하는 것은 일반적으로 간단합니다. 페더레이션은 기존 에지 서버를 사용하는 추가 기능이므로, 페더레이션 계획 요구 사항이 일반적으로 에지 서버 계획 및 배포 요구 사항과 일치하기 때문입니다. 다음 표를 참조하여 현재 요구 사항이 충족되는지, 표에 따라 포트/프로토콜 및 DNS를 변경해야 하는지 확인해야 합니다.


> [!IMPORTANT]
> 에지 서버의 풀이 있고 Lync Server 2013 또는 Lync Server 2010 파트너와 페더레이션하는 경우 에지 서버의 내부 측 및 외부 측에 DNS 부하 분산 또는 하드웨어 부하 분산 중 하나를 사용할 수 있습니다. Office Communications Server 2007 또는 Office Communications Server 2007 R2와 페더레이션하는 경우 에지 서버에 오류가 발생하면 하드웨어 부하 분산이 장애 조치(failover) 기능을 제공합니다. Office Communications Server 2007 및 Office Communications Server 2007 R2는 DNS 부하 분산을 인식하지 못합니다. 파트너 에지 서버는 풀에서 응답하는 첫 번째 에지 서버와 통신을 설정합니다. 해당 에지 서버에 오류가 발생하면 통신은 자동으로 장애 조치되지 않습니다.



인증서 요구 사항은 선택한 에지 서버 또는 에지 서버 풀 계획에 대한 인증서를 계획할 때 주로 충족됩니다.

## 공용 IM 연결

Public Instant Messaging Connectivity는 페더레이션의 한 클래스이며 내부 및 외부 Lync Server 2013 사용자가 다음의 연락처를 추가할 수 있도록 구성됩니다.

  - Messenger 연락처

  - Yahoo\! 연락처

  - AOL(America Online) 연락처


> [!IMPORTANT]
> <UL>
> <LI>
> <P>2012년 9월 1일 현재 신규 또는 갱신 계약에 대해 Microsoft Lync PIC USL(공용 메신저 연결 사용자 구독 라이선스)을 더 이상 구입할 수 없습니다. 유효 라이선스를 보유한 고객은 서비스 종료 날짜(정확한 날짜는 미정이지만 2013년 6월 이후로 예상됨)까지 Yahoo! Messenger와 계속 페더레이션할 수 있습니다.</P>
> <LI>
> <P>PIC USL은 Lync Server 또는 Office Communications Server가 Yahoo! Messenger와 페더레이션하는 데 필요한 월별 사용자 단위 구독 라이선스입니다. Microsoft는 Yahoo!의 지원 여부에 따라 이 서비스를 제공할 수 있었으며 해당 서비스의 기본 계약은 갱신되지 않을 예정입니다.</P>
> <LI>
> <P>Lync는 전 세계의 여러 조직과 개별 사용자를 연결해 주는 매우 효율적인 도구입니다. Lync Standard CAL 외의 추가 사용자/장치 라이선스가 없어도 Windows Live Messenger와의 페더레이션이 가능합니다. Skype 페더레이션도 이 목록에 추가될 예정이므로 Lync 사용자는 IM 및 음성을 통해 수많은 사람들과 연결할 수 있습니다.</P></LI></UL>



이 클래스의 페더레이션을 사용하려면 계획 시 다음 사항을 고려해야 합니다.

  - Windows Live Messenger 사용자는 Lync Server 2013 사용자와 메신저 대화는 물론, 피어 투 피어 오디오/시각적 통신을 할 수 있습니다. 에지 서버에서 특정 포트 및 프로토콜 요구 사항을 충족해야 합니다. 자세한 내용은 [Lync Server 2013에 대한 외부 A/V 방화벽 및 포트 요구 사항 확인](lync-server-2013-determine-external-a-v-firewall-and-port-requirements.md)을 참고하세요.

  - Yahoo 메신저의 경우에는 페더레이션을 제공하는 기본 에지 서버의 계획 및 배포에 일반적으로 사용되는 것과 다른 고유 요구 사항이 없습니다.

  - AOL의 경우에는 액세스 에지 서비스에 할당된 에지 서버 인증서에 클라이언트 EKU(확장된 키 사용)가 있어야 합니다.

## XMPP(Extensible Messaging and Presence Protocol) 페더레이션

이전 버전의 Lync Server 및 Office Communications Server는 XMPP(Extensible Messaging and Presence Protocol) 배포와의 페더레이션을 위해 별도의 서버 역할로 배포할 수 있는 XMPP 게이트웨이를 제공했습니다. Microsoft Lync Server 2013에서는 XMPP 기능을 하나의 기능으로 배포할 수 있습니다. XMPP 기능은 두 부분, 즉 에지 서버에서 실행되는 XMPP 프록시와 프런트 엔드 서버에서 실행되는 XMPP 게이트웨이로 설치됩니다.

XMPP의 배포와 구성에 대해서는 [Lync Server 2013에서 외부 사용자 액세스 배포](lync-server-2013-deploying-external-user-access.md)에서 다룹니다. 방화벽 포트 및 프로토콜 규칙을 정의하고, 인증서를 구성하고, DNS 레코드를 추가하여 조직의 XMPP 지원을 계획해야 합니다. 이 섹션의 다음 항목에는 배포에 대한 XMPP 페더레이션을 성공적으로 계획하는 데 필요한 정보가 요약되어 있습니다.


> [!IMPORTANT]
> Lync Server 2013의 XMPP 기능은 Microsoft에서 Google Talk와의 메신저 페더레이션에 대해 지원 및 테스트합니다. 다른 모든 XMPP 시스템의 경우 타사 공급업체에 문의하여 Lync Server 2013과의 페더레이션 지원 여부, 배포 또는 문제 해결 권장 사항에 대해 알아보십시오.




> [!IMPORTANT]
> 사용자가 Survivable Branch Appliance로 이동한 경우에는 XMPP 페더레이션이 지원되지 않습니다. 이는 현재 상태 보기 정보 및 메신저 대화 메시지 교환 보기 모두에 적용됩니다.



다음 항목에는 지원되는 페더레이션 시나리오의 유형에 대해 인증서, 방화벽 포트 및 DNS 항목을 정의하는 방법에 대한 지침이 포함됩니다.

   [인증서 요약 - SIP, XMPP 페더레이션 및 공용 IM](lync-server-2013-certificate-summary-sip-xmpp-federation-and-public-instant-messaging.md)

   [포트 요약 - SIP, XMPP 페더레이션 및 공용 IM](lync-server-2013-port-summary-sip-xmpp-federation-and-public-instant-messaging.md)

   [DNS 요약 - SIP, XMPP 페더레이션 및 공용 IM](lync-server-2013-dns-summary-sip-xmpp-federation-and-public-instant-messaging.md)

## 참고 항목

#### 작업

[Lync Server 2013에서 페더레이션 사용자 액세스를 제어할 정책 구성](lync-server-2013-configure-policies-to-control-federated-user-access.md)  

#### 개념

[Lync Server 2013의 외부 사용자 액세스에 대한 시나리오](lync-server-2013-scenarios-for-external-user-access.md)  
[Lync Server 2013에 대한 외부 A/V 방화벽 및 포트 요구 사항 확인](lync-server-2013-determine-external-a-v-firewall-and-port-requirements.md)  
[Lync Server 2013에 대한 DNS 요구 사항 확인](lync-server-2013-determine-dns-requirements.md)  

#### 기타 리소스

[Lync Server 2013에서 조직에 대한 액세스 에지 구성 관리](lync-server-2013-manage-access-edge-configuration-for-your-organization.md)  
[Lync Server 2013에서 조직의 SIP 페더레이션된 도메인 관리](lync-server-2013-manage-sip-federated-domains-for-your-organization.md)  
[Lync Server 2013에서 조직에 대한 SIP 페더레이션 공급자 관리](lync-server-2013-manage-sip-federated-providers-for-your-organization.md)

