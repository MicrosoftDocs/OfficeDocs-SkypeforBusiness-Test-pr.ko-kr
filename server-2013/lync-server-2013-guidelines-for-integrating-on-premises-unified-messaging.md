---
title: 'Lync Server 2013: 온-프레미스 통합 메시징 통합에 대한 지침'
TOCTitle: 온-프레미스 통합 메시징과 Lync Server의 통합에 대한 지침
ms:assetid: 829ac017-6907-40f9-be22-787a28eae0ac
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398656(v=OCS.15)
ms:contentKeyID: 49304223
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 온-프레미스 통합 메시징과 Lync Server 2013의 통합에 대한 지침

 

_**마지막으로 수정된 항목:** 2012-09-25_

다음은 Enterprise Voice를 배포할 때 고려해야 할 지침 및 모범 사례입니다.


> [!IMPORTANT]
> Exchange 통합 메시징(UM)에서는 UCMA 4를 사용하는 경우에만 IPv6가 지원됩니다.



  - Lync Server 2013 Standard Edition 서버 또는 프런트 엔드 풀을 배포합니다. 설치에 대한 자세한 내용은 배포 설명서에서 [Lync Server 2013 배포](lync-server-2013-deploying-lync-server.md)를 참조하십시오.

  - Exchange 관리자와 함께 원활하고 성공적인 통합을 위해 각자가 수행할 작업을 확인합니다.

  - Exchange UM에 대해 사용자를 설정하려는 각 Exchange 통합 메시징(UM) 포리스트에 Exchange 사서함 서버 역할을 배포합니다. Exchange 서버 역할 설치에 대한 자세한 내용은 Microsoft Exchange Server 2013 설명서를 참조하십시오.
    

    > [!IMPORTANT]
    > Exchange 통합 메시징(UM)이 설치된 경우 자체 서명된 인증서를 사용하도록 구성됩니다.<BR>그러나 자체 서명된 인증서는 Lync Server 2013와 Exchange UM이 서로 신뢰하도록 지원하지 않으므로 두 서버가 신뢰할 수 있는 인증 기관에서 별도의 인증서를 요청해야 합니다.



  - Lync Server 2013과 Exchange UM이 다른 포리스트에 설치된 경우 Lync Server 2013 포리스트를 신뢰하도록 각 Exchange 포리스트를 구성하고, 각 Exchange 포리스트를 신뢰하도록 Lync Server 2013 포리스트를 구성합니다. 또한 ILM(Identity Lifecycle Manager)과 같은 크로스 포리스트 도구 또는 스크립트를 사용하여 Lync Server 2013 포리스트의 사용자 개체에 대해 사용자의 Exchange UM 설정을 지정합니다.

  - 필요한 경우 통합 메시징 서버를 관리할 Exchange 관리 콘솔을 설치합니다.

  - Outlook Voice Access 및 자동 전화 교환을 위한 유효한 전화 번호를 받습니다.

  - Microsoft Exchange Server 2010 SP1(서비스 팩 1) 이전 버전의 Exchange UM을 사용하는 경우 Exchange UM SIP URI 다이얼 플랜과 Enterprise Voice 다이얼 플랜에 대한 이름을 조정합니다.

## 중복 Exchange UM 서버 배포


> [!IMPORTANT]
> 조직에 구성한 각 Exchange UM SIP URI 다이얼 플랜에 대해 Exchange UM 서비스가 실행되는 최소 두 개의 서버를 배포하는 것이 좋습니다. 중복 서버를 배포하면 용량이 확장될 뿐 아니라 고가용성이 제공됩니다. 하나의 서버에서 오류가 발생한 경우 다른 서버로 장애 조치(failover)하도록 Lync Server 2013을 구성할 수 있습니다.



다음 구성 예에서는 Exchange UM 복구를 제공합니다.

**예 1: Exchange UM 복구**

![Exchange UM 예제 1](images/Gg398656.3644b847-0847-4550-a989-e3fc51de5c4b(OCS.15).jpg "Exchange UM 예제 1")

예 1에서 Exchange UM 서버 1과 2는 Tukwila 데이터 센터에서 사용되고, Exchange UM 서버 3과 4는 Dublin 데이터 센터에서 사용됩니다. Tukwila에서 Exchange UM의 작동이 중단된 경우 서버 1과 2의 DNS(Domain Name System) A 레코드는 각각 서버 3과 4를 가리키도록 구성되어야 합니다. 반대로, Dublin에서 Exchange UM의 작동이 중단된 경우 서버 3과 4의 DNS A 레코드는 각각 서버 1과 2를 가리키도록 구성되어야 합니다.


> [!NOTE]
> 예 1의 경우 각 Exchange UM 서버에서 다음 인증서 중 하나를 지정해야 합니다. 
> <UL>
> <LI>
> <P>SAN(주체 대체 이름)에 와일드카드가 포함된 인증서 사용</P>
> <LI>
> <P>SAN에 네 개 Exchange UM 서버 각각의 FQDN(정규화된 도메인 이름)을 입력합니다.</P></LI></UL>



**예 2: Exchange UM 복구**

![Exchange UM 예제 2](images/Gg398656.15754273-306e-448d-b258-84bc2936a2e8(OCS.15).jpg "Exchange UM 예제 2")

예 2의 경우 정상 작동 조건에서 Exchange UM 서버 1과 2는 Tukwila 데이터 센터에서 사용되고, Exchange UM 서버 3과 4는 Dublin 데이터 센터에서 사용됩니다. 네 서버 모두 Tukwila 사용자의 SIP URI 다이얼 플랜에 포함되어 있지만 서버 3과 4는 사용하지 않도록 설정되어 있습니다. Tukwila에서 Exchange UM의 작동이 중단된 경우 예를 들어 Exchange UM 서버 1과 2가 사용할 수 없게 되고, Exchange UM 서버 3과 4를 사용할 수 있으므로 Tukwila Exchange UM 트래픽이 Dublin의 서버로 라우팅됩니다.

Exchange 2013에 통합 메시징을 사용하거나 사용하지 않도록 설정하는 방법에 대한 자세한 내용은 "Microsoft Lync Server 2013"( [http://go.microsoft.com/fwlink/?linkid=265372\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=265372%26clcid=0x412))을 참조하십시오.

Microsoft Exchange Server 2010에서 통합 메시징을 사용하거나 사용하지 않도록 설정하는 방법에 대한 자세한 내용은 다음을 참조하십시오.

  - "Exchange 2010에서 통합 메시징 사용"( [http://go.microsoft.com/fwlink/?linkid=204418\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=204418%26clcid=0x412))

  - "Exchange 2010에서 통합 메시징 사용 안 함"( [http://go.microsoft.com/fwlink/?linkid=204416\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=204416%26clcid=0x412))

## 참고 항목

#### 개념

[온-프레미스 통합 메시징과 Lync Server 2013의 통합을 위한 배포 프로세스](lync-server-2013-deployment-process-for-integrating-on-premises-unified-messaging.md)

