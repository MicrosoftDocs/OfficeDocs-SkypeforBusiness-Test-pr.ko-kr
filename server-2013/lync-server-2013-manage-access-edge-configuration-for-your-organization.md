---
title: 'Lync Server 2013: 조직에 대한 액세스 에지 구성 관리'
TOCTitle: 조직에 대한 액세스 에지 구성 관리
ms:assetid: 0145eb08-984f-4ecd-bf9c-364817619c2a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ552443(v=OCS.15)
ms:contentKeyID: 49302610
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 조직에 대한 액세스 에지 구성 관리

 

_**마지막으로 수정된 항목:** 2012-11-01_

이 설명서는 준비 단계인 설명서이므로 변경될 수 있습니다. 빈 항목은 자리 표시자로 포함되어 있습니다.

하나 이상의 에지 서버를 배포한 후에는 조직에 대해 지원할 에지 서버를 통해 회의에 대한 외부 도메인 또는 공급자 액세스, 원격 사용자 액세스 및 익명 사용자 액세스 유형을 사용하도록 설정해야 합니다.

이러한 옵션에는 **액세스 에지 구성** 페이지를 통해 구성할 수 있는 다음과 같은 액세스 유형이 포함됩니다.

  - **페더레이션 및 공용 메신저 연결 사용**    페더레이션 파트너 도메인에 대한 사용자 액세스를 지원하려면 이 설정을 사용하도록 설정합니다. 이 설정은 **외부 액세스 정책** 페이지에서 전역, 사이트 또는 사용자 범위에 대해 구성되는 SIP 페더레이션 및 XMPP 페더레이션에 모두 적용됩니다. 페더레이션 설정을 적용하려면 두 페이지에서 모두 페더레이션 지원을 구성해야 합니다.
    
    페더레이션 파트너를 검색하는 방법 및 보관 고지 사항(배포에서 보관이 사용하도록 설정되었으며 통신 세부 정보가 보관됨을 알리는 통신 대상 페더레이션 연락처에 대한 알림)을 연락처에게 보낼지 여부에 대한 선택적 설정인 두 가지 옵션이 있습니다.
    
      - **파트너 도메인 검색 사용**    이 옵션을 선택하면 페더레이션 가능한 도메인을 자동으로 검색할 수 있도록 설정됩니다. Lync Server 2013에서는 DNS(Domain Name System) 레코드를 사용하여 허용 도메인 목록에 나열되지 않은 도메인을 검색하고, 검색된 페더레이션 파트너에서 받는 트래픽을 자동으로 평가하고, 트러스트 수준/트래픽의 양/관리자 설정에 따라 해당 트래픽을 제한하거나 차단합니다. 이 옵션을 선택하지 않으면 허용 도메인 목록에 포함하는 도메인의 사용자만 페더레이션 사용자 액세스를 사용할 수 있습니다. 이 옵션을 선택하는지 여부에 관계없이 페더레이션 도메인의 액세스 에지 서비스를 실행하는 특정 서버에 대한 액세스 제한을 포함하여 개별 도메인을 차단하거나 허용하도록 지정할 수 있습니다. 자세한 내용은 [Lync Server 2013에서 허용되는 외부 도메인 지원 구성](lync-server-2013-configure-support-for-allowed-external-domains.md)를 참조하십시오.
    
      - **페더레이션 파트너에게 보관 고지 사항 보내기**    이 옵션을 선택하면 페더레이션 파트너에게 통신 세부 정보가 기록됨을 알리는 보관 고지 사항 메시지를 보낼 수 있도록 설정됩니다. 페더레이션 파트너 도메인과의 외부 통신을 보관하는 경우에는 보관 고지 사항 알림을 사용하도록 설정하여 파트너에게 메시지 및 통신 세부 정보가 배포에 의해 보관되고 있다는 경고를 보내야 합니다. 보관에 대한 자세한 내용은 [Lync Server 2013에서 보관에 대한 요구 사항 정의](lync-server-2013-defining-your-requirements-for-archiving.md)를 참조하십시오.

  - **원격 사용자 액세스 사용**    조직에서 방화벽 외부에 있는 사용자(예: 출장 중인 사용자 및 원격 근무자)가 Lync Server에 연결할 수 있도록 하려면 이 옵션을 사용하도록 설정합니다. 자세한 내용은 [Lync Server 2013에서 원격 사용자 액세스 사용 또는 사용 안 함](lync-server-2013-enable-or-disable-remote-user-access.md)을 참조하십시오.

  - **전화 회의에 대한 익명 사용자 액세스 사용**    내부 사용자가 자신이 이끄는 전화 회의에 외부 익명 사용자를 초대할 수 있도록 하려면 이 옵션을 사용하도록 설정합니다. 이 설정을 사용하는 경우 익명 사용자만 전화 회의에 참가하도록 허용됩니다. 사용자가 전화 회의에서 수행할 수 있는 작업 및 작업 방법을 정의하는 회의 환경 및 옵션을 구성하고 익명 사용자를 포함하려면 [사이트 또는 사용자 그룹에 대한 회의 사용자 환경 만들기 또는 수정](https://technet.microsoft.com/ko-kr/library/gg429715\(v=ocs.15\)) 및 [Lync Server 2013용 회의 정책 설정 참조](lync-server-2013-conferencing-policy-settings-reference.md)의 세부 정보를 참조하십시오.


> [!NOTE]
> 외부 사용자 액세스 지원을 사용하도록 설정하는 것 외에도, 정책을 구성하여 조직에서 원격 사용자 액세스 사용을 제어해야 사용자들이 외부 사용자 액세스 유형을 사용할 수 있습니다. 외부 사용자 액세스용 정책을 만들고 구성하고 적용하는 방법에 대한 자세한 내용은 <A href="lync-server-2013-manage-external-access-policy-for-your-organization.md">Lync Server 2013에서 외부 액세스 정책 관리</A>를 참조하십시오.



**Windows PowerShell cmdlet을 사용하여 액세스 에지 구성 정보 보기**

  - 액세스 에지 구성 정보는 Windows PowerShell 및 **Get-CsAccessEdgeConfiguration** cmdlet을 사용하여 볼 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.의 원격 세션에서 실행할 수 있습니다.
    
    모든 액세스 에지 구성 설정에 대한 정보를 보려면 Lync Server 관리 셸에서 다음 명령을 입력하고 Enter 키를 누릅니다.
    
        Get-CsAccessEdgeConfiguration
    
    그러면 다음과 같은 정보가 반환됩니다.
    
        Identity                               : Global
        AllowAnonymousUsers                    : False
        AllowFederatedUsers                    : False
        AllowOutsideUsers                      : True
        BeClearingHouse                        : False
        EnablePartnerDiscovery                 : False
        EnableArchivingDisclaimer              : False
        EnableUserReplicator                   : True
        KeepCrlsUpToDateForPeers               : True
        MarkSourceVerifiableOnOutgoingMessages : True
        OutgoingTlsCountForFederatedPartners   : 4
        DiscoveredPartnerStandardRate          : 20
        EnableDiscoveredPartnerContactsLimit   : True
        MaxContactsPerDiscoveredPartner        : 1000
        DiscoveredPartnerReportPeriodMinutes   : 60
        MaxAcceptedCertificatesStored          : 1000
        MaxRejectedCertificatesStored          : 500
        CertificatesDeletedPercentage          : 20
        RoutingMethod                          : UseDnsSrvRouting

## 이 단원의 내용

  - [Lync Server 2013에서 페더레이션 및 공용 메신저 연결 사용 또는 사용 안 함](lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md)

  - [Lync Server 2013에서 페더레이션 파트너 검색을 사용하거나 사용하지 않도록 설정](lync-server-2013-enable-or-disable-discovery-of-federation-partners.md)

  - [Lync Server 2013에서 페더레이션 파트너에게 보관 고지 사항 보내기를 사용하거나 사용하지 않도록 설정](lync-server-2013-enable-or-disable-sending-an-archiving-disclaimer-to-federated-partners.md)

  - [Lync Server 2013에서 원격 사용자 액세스 사용 또는 사용 안 함](lync-server-2013-enable-or-disable-remote-user-access.md)

  - [Lync Server 2013에서 익명 사용자 액세스 사용 또는 사용 안 함](lync-server-2013-enable-or-disable-anonymous-user-access.md)

  - [Lync Server 2013에서 익명 사용자 지원을 위한 회의 정책 할당](lync-server-2013-assign-conferencing-policies-to-support-anonymous-users.md)

