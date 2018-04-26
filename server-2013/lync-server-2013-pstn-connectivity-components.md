---
title: 'Lync Server 2013: PSTN 연결 구성 요소'
TOCTitle: PSTN 연결 구성 요소
ms:assetid: 6b2a3f7d-760f-4f09-8432-312c98a7e6b7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398504(v=OCS.15)
ms:contentKeyID: 49303942
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 PSTN 연결 구성 요소

 

_**마지막으로 수정된 항목:** 2012-10-04_

엔터프라이즈급 VoIP 솔루션에서는 QoS(서비스 품질) 저하 없이 공중 전화망(PSTN)과 통화를 주고받을 수 있어야 합니다. 또한 전화를 걸고 받는 사용자가 기반 기술을 알지 못하도록 해야 합니다. 사용자의 입장에서는 Enterprise Voice 인프라와 PSTN 간의 통화가 또 다른 SIP 세션인 것처럼 보여야 합니다.

PSTN 연결의 경우 SIP 트렁크나 PSTN 게이트웨이(PBX가 있는 경우 Direct SIP 링크라고도 함 또는 PBX가 없는 경우)를 배포할 수 있습니다.

## SIP 트렁크

PSTN 게이트웨이를 사용하는 대신 SIP 트렁크를 사용하여 Enterprise Voice 솔루션을 PSTN에 연결할 수 있습니다. SIP 트렁크는 다음과 같은 시나리오를 가능하게 합니다.

  - 회사 방화벽 내부 또는 외부의 엔터프라이즈 사용자는 E.164 규격 번호로 지정된 시내 또는 시외 전화를 걸 수 있으며, 이러한 호출은 해당 서비스 공급자의 서비스로 PSTN에서 종료됩니다.

  - PSTN 가입자는 엔터프라이즈 사용자와 연관된 DID(Direct Inward Dialing) 번호로 전화를 걸어 회사 방화벽 내부 또는 외부의 엔터프라이즈 사용자에게 연락할 수 있습니다.

이 배포 솔루션을 사용하려면 SIP 트렁크 서비스 공급자가 필요합니다.

## PSTN 게이트웨이

PSTN 게이트웨이는 Enterprise Voice 인프라와 PSTN 또는 PBX 간의 신호 및 미디어를 변환하는 타사 장치입니다. PSTN 게이트웨이는 중재 서버와 함께 작동하여 PSTN 또는 PBX 통화를 Enterprise Voice 클라이언트에 보냅니다. 또한 중재 서버는 Enterprise Voice 클라이언트에서 PSTN 게이트웨이로 통화를 보내 PSTN 또는 PBX에 라우팅할 수 있습니다. Lync Server에서 사용할 수 있는 장치를 제공하는 Microsoft 협력 파트너 목록은 Microsoft 통합 통신 파트너 웹 사이트( [http://go.microsoft.com/fwlink/?linkid=202836\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=202836%26clcid=0x412))를 참조하십시오.

## PBX(Private Branch Exchange)

PBX(Private Branch Exchange)를 사용하는 기존 음성 인프라가 있는 경우 Lync Server Enterprise Voice에서 PBX를 사용할 수 있습니다.

지원되는 Enterprise Voice-PBX 통합 시나리오는 다음과 같습니다.

  - 미디어 바이패스를 지원하는 IP-PBX(중재 서버 포함)

  - 독립 실행형 PSTN 게이트웨이가 필요한 IP-PBX

  - TDM(Time Division Multiplexing) PBX(독립 실행형 PSTN 게이트웨이 포함)


> [!NOTE]
> 미디어 바이패스가 모든 PSTN 게이트웨이, IP-PBX 및 SBC에서 작동하지는 않습니다. Microsoft는 인증된 파트너를 통해 일련의 PSTN 게이트웨이 및 SBC에서 테스트를 수행하고 Cisco IP-PBX에서도 테스트를 진행했습니다. SBC에 대한 인증은 진행 중입니다. 미디어 바이패스는 Infrastructure qualified for Microsoft Lync( <A class=uri href="http://go.microsoft.com/fwlink/?linkid=214406%26clcid=0x412">http://go.microsoft.com/fwlink/?linkid=214406&amp;clcid=0x412</A>)에 나열된 제품 및 버전에 대해서만 지원됩니다.



Enterprise Voice 솔루션을 제공하는 파트너에 대한 자세한 내용은 Microsoft 통합 통신 파트너 웹 사이트( [http://go.microsoft.com/fwlink/?linkid=202836\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=202836%26clcid=0x412))를 참조하십시오.

PSTN 게이트웨이를 비롯한 Enterprise Voice 하드웨어 솔루션을 제공하는 파트너에 대한 자세한 내용은 Microsoft 통합 통신 파트너 웹 사이트( [http://go.microsoft.com/fwlink/?linkid=202836\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=202836%26clcid=0x412))를 참조하십시오.

