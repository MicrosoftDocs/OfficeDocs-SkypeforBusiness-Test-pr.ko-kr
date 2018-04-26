---
title: Lync Server 2013의 전역 미디어 바이패스 옵션
TOCTitle: Lync Server 2013의 전역 미디어 바이패스 옵션
ms:assetid: 1bd35f90-8587-48a1-b0c2-095a4053fc77
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398255(v=OCS.15)
ms:contentKeyID: 49302975
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 전역 미디어 바이패스 옵션

 

_**마지막으로 수정된 항목:** 2012-10-04_


> [!NOTE]
> 이 항목에서는 미디어가 중재 서버를 바이패스하도록 할 특정 사이트 또는 서비스에 대해 모든 트렁크에 대한 미디어 바이패스를 피어(인터넷 전화 통신 서비스 공급자의 SBC(Session Border Controller), IP-PBX 또는 공중 전화망(PSTN) 게이트웨이)로 이미 구성했다고 가정합니다.



피어와 연결된 개별 트렁크 연결에 대한 미디어 바이패스를 사용하도록 설정하는 것 외에, 전역적으로도 미디어 바이패스를 사용하도록 설정해야 합니다. 전역 미디어 바이패스 설정은 PSTN으로 건 전화에 대해 항상 미디어 바이패스를 시도하거나, 네트워크 사이트 및 네트워크 지역에 대한 서브넷 매핑을 사용하여 미디어 바이패스를 적용하도록 지정할 수 있습니다(또 다른 고급 음성 기능인 통화 허용 제어를 사용하여 지정하는 것과 비슷함). 미디어 바이패스 및 통화 허용 제어가 모두 사용하도록 설정된 경우에는 미디어 바이패스 적용 여부를 결정할 때 통화 허용 제어에 대해 지정된 네트워크 지역, 네트워크 사이트 및 서브넷 정보가 자동으로 사용됩니다. 즉, 통화 허용 제어가 사용하도록 설정된 경우에는 PSTN으로 건 전화에 대해 항상 미디어 바이패스를 시도하도록 지정할 수 없습니다.

이 항목에서는 Lync Server 제어판 및 Lync Server 관리 셸을 함께 사용하여 전역 미디어 바이패스 설정을 구성하는 방법을 설명합니다.


> [!NOTE]
> 여기서 설명하는 단계를 수행하여 미디어 바이패스를 구성하는 경우, 클라이언트와 중재 서버 피어(예: SIP 트렁크 공급자의 SBC, IP-PBX 또는 PSTN 게이트웨이) 간의 연결이 원활하다고 가정합니다. 링크에 대한 대역폭 제한이 있는 경우에는 미디어 바이패스를 통화에 적용할 수 없습니다. 미디어 바이패스가 모든 PSTN 게이트웨이, IP-PBX 및 SBC에서 작동하지는 않습니다. Microsoft는 인증된 파트너를 통해 일련의 PSTN 게이트웨이 및 SBC에서 테스트를 수행하고 Cisco IP-PBX에서도 테스트를 진행했습니다. 미디어 바이패스는 Infrastructure qualified for Microsoft Lync(<A class=uri href="http://go.microsoft.com/fwlink/?linkid=214406%26clcid=0x412">http://go.microsoft.com/fwlink/?linkid=214406&amp;clcid=0x412</A>)에 나열된 제품 및 버전에 대해서만 지원됩니다.



## 다음 단계: 전역 미디어 바이패스 설정 선택

특정 사이트 또는 서비스에서 피어로의 트렁크 연결에 미디어 바이패스를 사용하도록 설정한 후에는 다음 콘텐츠를 참조하여 각 작업을 수행하십시오.

  - [Lync Server 2013에서 중재 서버를 항상 바이패스하도록 미디어 바이패스 구성](lync-server-2013-configure-media-bypass-to-always-bypass-the-mediation-server.md)에 설명된 대로 항상 미디어 바이패스를 사용하도록 설정합니다.

  - 또는 [사이트 및 지역 정보를 사용하도록 Lync Server 2013에서 미디어 바이패스 전역 설정 구성](lync-server-2013-configure-media-bypass-global-settings-to-use-site-and-region-information.md)에 설명된 대로 사이트 및 지역 정보를 사용하도록 미디어 바이패스를 구성합니다.

## 참고 항목

#### 작업

[Lync Server 2013에서 미디어 바이패스로 트렁크 구성](lync-server-2013-configure-a-trunk-with-media-bypass.md)  
[Lync Server 2013 에서 네트워크 사이트에 서브넷 연결](lync-server-2013-associate-a-subnet-with-a-network-site.md)  

#### 개념

[Lync Server 2013에서 미디어 바이패스 구성](lync-server-2013-configure-media-bypass.md)  
[Lync Server 2013의 미디어 바이패스 및 중재 서버](lync-server-2013-media-bypass-and-mediation-server.md)

