---
title: Lync Server 및 Office Communications Server 페더레이션 계획
TOCTitle: Lync Server 및 Office Communications Server 페더레이션 계획
ms:assetid: c9eaf06b-054f-41a4-ad0c-499400d6c4c7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205335(v=OCS.15)
ms:contentKeyID: 49305029
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 및 Office Communications Server 페더레이션 계획

 

_**마지막으로 수정된 항목:** 2013-02-13_

Microsoft Lync Server 2013, Lync Server 2010 및 Office Communications Server 간에 페더레이션을 구성하면 피어 투 피어 및 단체 통신이 지원됩니다. 피어 투 피어 대화는 단체 대화로 확대되어 임시 모임을 허용할 수 있습니다. 웹 회의 또는 오디오/비디오 회의 같은 모임은 페더레이션 파트너의 대화 상대뿐 아니라 조직 내 대화 상대를 포함하도록 예약할 수 있습니다.

페더레이션은 Microsoft Office Live Communications Server 2005에서 처음 도입되었으며 단일 유형의 페더레이션인 '직접 페더레이션'만 지원했습니다. 직접 페더레이션을 사용하려면 페더레이션 파트너의 SIP(Session Initiation Protocol) 도메인 및 에지 서버의 FQDN(정규화된 도메인 이름)을 알아야 했습니다. Live Communications Server 2005 SP1에서 추가 페더레이션 유형이 도입되었으며 여기에는 에지 서버를 찾기 위해 페더레이션 파트너에 의해 게시되는 DNS(Domain Name System) SRV 레코드만 필요합니다. 해당 릴리스에 사용되는 용어는 다음과 같습니다.

  - *개방형 확장 페더레이션*: 모든 SIP 도메인 이름이 수락되고 DNS SRV를 사용하여 파트너 에지 서버를 찾습니다.

  - *확장 페더레이션*: 파트너의 SIP 도메인 이름을 조직의 페더레이션 파트너로 구성하고 DNS SRV를 사용하여 파트너 에지 서버를 찾습니다.

  - *직접 페더레이션*: 파트너의 SIP 도메인 이름과 에지 서버 FQDN을 구성합니다.

  - *서버 허용 목록*: 모든 도메인을 수락하고 DNS SRV를 사용하여 호스팅 공급자 또는 공용 메신저 연결 공급자의 에지 서버를 찾습니다.

Microsoft Office Communications Server 2007에서는 페더레이션 유형의 이름이 실제 수행 작업을 더 잘 표현하도록 업데이트되었습니다.

  - 개방형 확장 페더레이션은 *검색된 파트너 도메인*으로 변경되었습니다.

  - 확장 페더레이션은 *허용된 파트너 도메인*으로 변경되었습니다.

  - 직접 페더레이션은 *허용된 파트너 서버*로 변경되었습니다.

  - 서버 허용 목록은 *호스팅 공급자* 및 *공용 메신저 공급자*로 변경되었습니다.

Microsoft Lync Server 2010에서는 Microsoft Lync Online 2010 및 Microsoft Office 365에 따라 좁은 의미의 호스팅 공급자 유형을 도입했으며 '허용된 파트너 도메인' 페더레이션 유형으로 정의되는 동일한 허용 목록에 따라 변하도록 설정할 수 있습니다.

Microsoft Lync Server 2013, Lync Server 2010 및 Office Communications Server 간에 페더레이션을 사용하도록 설정하면 에지 서버 및 역방향 프록시를 사용하여 정의하는 규칙 및 허용된 파트너 도메인이 적용됩니다. 계획 관점에서 봤을 때 다른 Lync Server와 페더레이션하는 경우 Office Communications Server에 다음이 요구됩니다.

  - 토폴로지 작성기에서 페더레이션을 사용하도록 설정해야 합니다. 자세한 내용은 배포 항목인 [Lync Server 2013에서 SIP 페더레이션, XMPP 페더레이션 및 공용 메신저 구성](lync-server-2013-configuring-sip-federation-xmpp-federation-and-public-instant-messaging.md) 섹션을 참조하십시오.

  - 페더레이션 도메인 검색에 필요한 요구 사항을 결정합니다.
    
       페더레이션을 수동으로 구성하는 경우 Lync Server 제어판의 **페더레이션 및 외부 액세스**, **SIP 페더레이션 도메인**에 입력할 수 있도록 파트너 에지 서버의 FQDN(정규화된 도메인 이름)과 도메인 이름(또는 온라인 도메인 이름)이 필요합니다. FQDN으로 도메인을 허용하거나 차단하려면 **새로 만들기**로 정책을 새로 만들거나 **편집**으로 기존 정책을 편집합니다.
        

      > [!WARNING]
      > 페더레이션 파트너의 에지 서버를 수동으로 구성하는 경우 파트너가 에지 서버의 IP 주소를 변경하면 오류가 발생할 수 있습니다.        

      > [!NOTE]
      > <STRONG>새 SIP 페더레이션 도메인</STRONG>의 경우 Microsoft Lync Online, Microsoft Office 365에 <STRONG>도메인 이름 또는 FQDN</STRONG>을 지정해야 합니다. Microsoft Lync Server 2013, Lync Server 2010 및 Office Communications Server의 경우 <STRONG>액세스 에지 서비스(FQDN)</STRONG>도 지정해야 합니다.

    
      파트너가 사용자의 에지 서버를 검색할 수 있는 '검색된 파트너 페더레이션'의 경우 포트 5061과 에지 서버의 호스트(A) 레코드를 가리키도록 외부 DNS(\_sipfederationtls.\_tcp.contoso.com)에 SRV 레코드를 만들어야 합니다.
        

      > [!IMPORTANT]
      > Windows Phone 또는 Apple iPhone, iPad, 기타 Apple 장치에서 Microsoft Lync Mobile 클라이언트를 지원하는 경우 푸시 알림 서비스 또는 푸시 알림 서비스를 사용하면 Lync Mobile 클라이언트가 있는 각 SIP 도메인마다 _sipfederationtls._tcp. <EM>&lt;SIP 도메인&gt;</EM> SRV 레코드가 존재하도록 계획해야 합니다. Android 및 Nokia Symbian Lync Mobile은 푸시 알림을 사용하지 않으므로 이러한 요구 사항의 적용을 받지 않습니다.



  - 페더레이션 도메인을 지원하도록 외부 사용자 액세스 정책을 구성해야 합니다.

  - 사용하는 대화 상대 또는 페더레이션을 수용할 수 있도록 SIP(Session Initiation Protocol), 웹 회의 및 오디오/비디오용 방화벽 포트를 열어야 합니다. 자세한 내용은 [Lync Server 2013에 대한 외부 A/V 방화벽 및 포트 요구 사항 확인](lync-server-2013-determine-external-a-v-firewall-and-port-requirements.md) 섹션을 참조하십시오.

다음은 Microsoft Lync Server 2013 및 Lync Server 2010의 페더레이션에 대한 인증서, 포트/프로토콜 및 DNS 요구 사항을 정의하는 데 도움이 되는 정보입니다.

Microsoft Lync Server 2013 에지 서버를 계획 또는 배포했다면 인증서, 방화벽 및 포트/프로토콜 요구 사항과 DNS 요구 사항을 계획하는 것은 일반적으로 간단합니다. 페더레이션은 기존 에지 서버를 사용하는 추가 기능이므로, 페더레이션 계획 요구 사항이 일반적으로 에지 서버 계획 및 배포 요구 사항과 일치하기 때문입니다. 다음 표를 참조하여 현재 요구 사항이 충족되는지, 표에 따라 포트/프로토콜 및 DNS를 변경해야 하는지 확인해야 합니다.


> [!IMPORTANT]
> 에지 서버의 풀이 있고 Lync Server 2013 또는 Lync Server 2010 파트너와 페더레이션하는 경우 에지 서버의 내부 측 및 외부 측에 DNS 부하 분산 또는 하드웨어 부하 분산 중 하나를 사용할 수 있습니다. Office Communications Server 2007 또는 Office Communications Server 2007 R2와 페더레이션하는 경우 에지 서버에 오류가 발생하면 하드웨어 부하 분산이 장애 조치(failover) 기능을 제공합니다. Office Communications Server 2007 및 Office Communications Server 2007 R2는 DNS 부하 분산을 인식하지 못합니다. 파트너 에지 서버는 풀에서 응답하는 첫 번째 에지 서버와 통신을 설정합니다. 해당 에지 서버에 오류가 발생하면 통신은 자동으로 장애 조치되지 않습니다.



인증서 요구 사항은 선택한 에지 서버 또는 에지 서버 풀 계획에 대한 인증서를 계획할 때 주로 충족됩니다.

## 이 단원의 내용

  - [인증서 요약 - SIP, XMPP 페더레이션 및 공용 IM](lync-server-2013-certificate-summary-sip-xmpp-federation-and-public-instant-messaging.md)

  - [포트 요약 - SIP, XMPP 페더레이션 및 공용 IM](lync-server-2013-port-summary-sip-xmpp-federation-and-public-instant-messaging.md)

  - [DNS 요약 - SIP, XMPP 페더레이션 및 공용 IM](lync-server-2013-dns-summary-sip-xmpp-federation-and-public-instant-messaging.md)

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

