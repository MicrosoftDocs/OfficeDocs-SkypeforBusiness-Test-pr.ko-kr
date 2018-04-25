---
title: 'Lync Server 2013: 호스팅된 Exchange UM 통합 아키텍처'
TOCTitle: 호스팅된 Exchange UM 통합 아키텍처
ms:assetid: 0094d5dc-1836-441c-b6e2-f88e35203a8d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398067(v=OCS.15)
ms:contentKeyID: 49302605
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 호스팅된 Exchange UM 통합 아키텍처

 

_**마지막으로 수정된 항목:** 2012-09-25_

Lync Server 2013 ExUM 라우팅 응용 프로그램은 온-프레미스 Exchange 통합 메시징(UM) 배포, 서비스 공급자가 호스팅하는 Exchange UM 또는 이 둘의 조합과의 통합을 지원합니다. 다음 다이어그램에서는 가능한 이 세 가지 통합을 모두 보여 줍니다.

**온-프레미스 Exchange UM 배포 및 호스팅되는 두 Exchange 공급자와의 통합**

![온-프레미스 Lync Server Exchange UM 배포](images/Gg398821.d6498eb9-87ee-40f3-8ecd-852f91546590(OCS.15).jpg "온-프레미스 Lync Server Exchange UM 배포")

다음과 같은 모드가 지원됩니다.

  - **온-프레미스 배포 :** Lync Server 2013과 Exchange UM은 둘 다 회사 내의 로컬 서버에 배포됩니다.

  - **교차 프레미스 배포 :** Lync Server 2013은 회사 내의 로컬 서버에 배포되고, Exchange UM은 Microsoft Exchange Online 데이터 센터와 같은 온라인 서비스 공급자의 시설에서 호스팅됩니다.

  - **혼합 배포 :** Lync Server 2013 배포에서 일부 사용자 사서함은 회사 내의 로컬 Exchange 서버에 있고 일부 사서함은 호스팅되는 Exchange 서비스 데이터 센터에 있습니다.
    

    > [!NOTE]
    > 혼합 배포는 호스팅되는 Exchange UM으로의 단계적 마이그레이션 및 평가 중에 전환 솔루션으로 사용되거나 나머지를 전송한 후 일부 사용자의 Exchange UM 서비스를 온-프레미스에 유지하려는 경우에 영구 솔루션으로 사용될 수 있습니다.



## 공유 SIP 주소 공간

Lync Server 2013을 온-프레미스 Exchange UM 배포와 통합하려면 Lync Server 2013에 Exchange UM Active Directory 도메인 서비스 개체에 대한 읽기 권한을 부여해야 합니다. 그러나 이 접근 방법은 호스팅되는 Exchange UM과의 통합에는 적용되지 않습니다. Lync Server 2013과 Exchange UM은 상호 신뢰 관계가 없는 별도의 포리스트에 설치되기 때문입니다.

Lync Server 2013을 호스팅되는 Exchange UM과 통합하려면 *공유 SIP 주소 공간* 을 구성해야 합니다. 이 구성에서는 Lync Server 2013과 호스팅되는 Exchange UM 서비스 공급자가 동일한 SIP 도메인 주소 공간을 사용할 수 있습니다.


> [!NOTE]
> 공유 SIP 주소 공간의 사용은 일부 사용자는 온-프레미스 배포에 있고, 다른 사용자는 호스팅되는 배포(예: Lync Server 2013)에 있는 교차 프레미스 Lync Online 환경에서 사용되는 접근 방법과 유사합니다. SIP 도메인은 둘 사이에 분할됩니다. Lync Server 2013을 호스팅되는 Exchange UM과 통합하는 경우 공유 SIP 주소 공간에 Exchange UM 서비스 공급자를 포함해야 합니다.



Exchange UM 서비스 공급자와의 통합을 위해 공유 SIP 주소 공간을 구성하려면 다음과 같이 에지 서버를 구성해야 합니다.

1.  **Set-CsAccessEdgeConfiguration** cmdlet을 실행하여 다음 매개 변수를 설정하는 방식으로 페더레이션에 대해 에지 서버를 구성합니다.
    
      - **UseDnsSrvRouting**은 페더레이션 요청을 보내고 받을 때 에지 서버가 DNS SRV 레코드를 기반으로 하도록 지정합니다.
    
      - **AllowFederatedUsers**는 내부 사용자가 페더레이션 도메인 사용자와 통신할 수 있는지 여부를 지정합니다. 이 속성은 내부 사용자가 분할 도메인 시나리오의 사용자와 통신할 수 있는지 여부도 결정합니다.
    
      - **EnablePartnerDiscovery**는 Lync Server 2013에서 DNS 레코드를 사용하여 Active Directory 허용 도메인 목록에 나열되지 않은 파트너 도메인을 검색할지 여부를 지정합니다. False로 설정하면 Lync Server 2013에서 허용 도메인 목록에 있는 도메인과만 페더레이션합니다. 이 매개 변수는 DNS 서비스 라우팅을 사용하는 경우에 필요합니다. 대부분의 배포에서는 페더레이션을 일부 파트너로 제한하기 위해 이 값이 False로 설정됩니다.

2.  중앙 관리 저장소를 에지 서버에 복제하고 결과를 확인합니다. 자세한 내용은 배포 설명서에서 [Lync Server 2013 토폴로지 내보내기 및 에지 설치용 외부 미디어에 토폴로지 복사](lync-server-2013-export-your-topology-and-copy-it-to-external-media-for-edge-installation.md)를 참조하십시오.

3.  **New-CsHostingProvider** cmdlet을 실행하여 다음 매개 변수를 설정하는 방식으로 에지 서버에 *호스팅 공급자* 를 구성합니다.
    
      - **Identity**는 만들려는 호스팅 공급자(예: **호스팅되는 Exchange UM** )에 대한 고유 문자열 값 식별자를 지정합니다.
    
      - **Enabled**는 도메인과 호스팅 공급자 간의 네트워크 연결을 활성화할지 여부를 나타냅니다. **True** 로 설정해야 합니다.
    
      - **EnabledSharedAddressSpace**는 공유 SIP 주소 공간 시나리오에서 호스팅 공급자를 사용할지 여부를 나타냅니다. **True** 로 설정해야 합니다.
    
      - **HostsOCSUsers**는 호스팅 공급자가 Lync Server 2013 계정을 호스팅하는 데 사용되는지 여부를 나타냅니다. **False** 로 설정해야 합니다.
    
      - **ProxyFQDN**은 호스팅 공급자가 사용하는 프록시 서버의 FQDN(정규화된 도메인 이름)(예: **proxyserver.fabrikam.com** )을 지정합니다. 이 정보는 호스팅 공급자에게 문의하십시오. 이 값은 수정할 수 없습니다. 호스팅 공급자가 프록시 서버를 변경한 경우에는 해당 공급자에 대한 항목을 삭제한 다음 다시 만들어야 합니다.
    
      - **IsLocal**은 호스팅 공급자가 사용하는 프록시 서버가 Lync Server 2013 토폴로지에 포함되는지 여부를 나타냅니다. **False**로 설정해야 합니다.

