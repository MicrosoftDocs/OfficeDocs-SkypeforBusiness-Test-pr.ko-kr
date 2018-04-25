---
title: 'Lync Server 2013: 미디어 바이패스 구성'
TOCTitle: 미디어 바이패스 구성
ms:assetid: f50a7a13-c6a0-48f1-bee1-e45fa2b2f9b8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413028(v=OCS.15)
ms:contentKeyID: 49305538
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 미디어 바이패스 구성

 

_**마지막으로 수정된 항목:** 2013-02-24_

이 섹션에서는 배포 설명서에서 [Lync Server 2013의 토폴로지 작성기에서 중재 서버 정의](lync-server-2013-define-a-mediation-server-in-topology-builder.md) 및 [Lync Server 2013에서 토폴로지 게시](lync-server-2013-publish-the-topology.md) 또는 [Lync Server 2013에서 프런트 엔드 풀 또는 Standard Edition 서버 정의 및 구성](lync-server-2013-define-and-configure-a-front-end-pool-or-standard-edition-server.md) 및 [Lync Server 2013에서 토폴로지 게시](lync-server-2013-publish-the-topology.md) 각각에서 설명한 대로 하나 이상의 중재 서버를 이미 게시 및 구성했다고 가정합니다.

또한 [Lync Server 2013의 토폴로지 작성기에서 게이트웨이 정의](lync-server-2013-define-a-gateway-in-topology-builder.md)에 설명된 대로 PSTN 연결을 제공하기 위해 하나 이상의 게이트웨이 피어를 정의했다고 가정합니다. 연결한 피어가 SIP 트렁크 공급자의 SBC일 경우 공급자가 정식 공급자인지, 미디어 바이패스를 지원하는지 확인합니다. 예를 들어 대부분의 SIP 트렁크 공급자는 중재 서버로부터 트래픽을 수신할 때 해당 공급자의 SBC만 허용합니다. 이 경우 해당 트렁크에 대해 바이패스를 사용하도록 설정하면 안 됩니다. 또한 조직에서 SIP 트렁크 공급자에게 내부 네트워크 IP 주소를 공개하지 않으면 미디어 바이패스를 사용하도록 설정할 수 없습니다.


> [!NOTE]
> 미디어 바이패스가 모든 PSTN 게이트웨이, IP-PBX 및 SBC에서 작동하지는 않습니다. Microsoft는 인증된 파트너를 통해 일련의 PSTN 게이트웨이 및 SBC에서 테스트를 수행하고 Cisco IP-PBX에서도 테스트를 진행했습니다. SBC에 대한 인증은 진행 중입니다. 미디어 바이패스는 Infrastructure qualified for Microsoft Lync( <A class=uri href="http://go.microsoft.com/fwlink/?linkid=214406%26clcid=0x412">http://go.microsoft.com/fwlink/?linkid=214406&amp;clcid=0x412</A>)에 나열된 제품 및 버전에 대해서만 지원됩니다.



이 섹션에서는 미디어 바이패스를 사용하도록 설정하여 중재 서버에서 처리해야 하는 항목을 줄이는 방법에 대해 설명합니다. 미디어 바이패스를 사용하도록 설정하기 전에 계획 설명서의 [Lync Server 2013의 미디어 바이패스 계획](lync-server-2013-planning-for-media-bypass.md)에서 설명한 대로 사용자 환경이 미디어 바이패스를 지원하는 데 필요한 조건을 충족하는지 확인합니다. 또한 중재 서버를 바이패스할지 여부를 결정할 때 사이트와 지역 정보를 사용할지 또는 미디어 바이패스 전역 설정을 사용하도록 설정하여 중재 서버를 항상 바이패스할지 여부를 결정하는 데 있어 [Lync Server 2013의 미디어 바이패스 계획](lync-server-2013-planning-for-media-bypass.md)의 정보를 사용했는지 확인합니다.

경우에 따라 CAC(통화 허용 제어), 다른 고급 Enterprise Voice 기능을 이미 구성한 경우 통화 허용 제어에서 수행된 대역폭 예약은 미디어 바이패스가 사용된 통화에 적용되지 않습니다. 미디어 바이패스 사용 여부가 먼저 확인되고 미디어 바이패스가 사용된 경우 통화에 대해 통화 허용 제어가 사용되지 않습니다. 미디어 바이패스 검사가 실패한 경우에만 통화 허용 제어를 위한 검사가 수행됩니다. 따라서 두 개의 기능은 PSTN으로 라우팅되는 특정 통화에 대해 함께 사용할 수 없습니다. 미디어 바이패스에서는 통화에 대해 미디어 끝점 간 대역폭 제약 조건이 없다고 가정하므로 이는 논리적입니다. 대역폭이 제한된 링크에서는 미디어 바이패스를 수행할 수 없습니다. 따라서 다음 중 하나가 PSTN 통화에 적용됩니다. a) 미디어가 중재 서버를 바이패스하고 통화 허용 제어가 통화에 대해 대역폭을 예약하지 않습니다. b) 통화 허용 제어가 대역폭 예약을 통화에 적용하고 통화와 관련된 중재 서버에서 미디어가 처리됩니다.

## 다음 단계: 트렁크 연결에서 미디어 바이패스를 사용하도록 설정

PSTN 연결에 대해 초기 설정(다이얼 플랜, 음성 정책, PSTN 사용 레코드, 아웃바운드 통화 경로 및 변환 규칙)을 구성했으면 [Lync Server 2013에서 미디어 바이패스로 트렁크 구성](lync-server-2013-configure-a-trunk-with-media-bypass.md)의 단계를 통해 미디어 바이패스를 사용하도록 설정하는 프로세스를 시작합니다.

## 참고 항목

#### 작업

[Lync Server 2013에서 미디어 바이패스로 트렁크 구성](lync-server-2013-configure-a-trunk-with-media-bypass.md)  
[Lync Server 2013에서 중재 서버를 항상 바이패스하도록 미디어 바이패스 구성](lync-server-2013-configure-media-bypass-to-always-bypass-the-mediation-server.md)  
[사이트 및 지역 정보를 사용하도록 Lync Server 2013에서 미디어 바이패스 전역 설정 구성](lync-server-2013-configure-media-bypass-global-settings-to-use-site-and-region-information.md)  

#### 개념

[Lync Server 2013의 전역 미디어 바이패스 옵션](lync-server-2013-global-media-bypass-options.md)  

#### 기타 리소스

[Lync Server 2013의 미디어 바이패스 계획](lync-server-2013-planning-for-media-bypass.md)

