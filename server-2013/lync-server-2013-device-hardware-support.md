---
title: Lync Server 2013 장치 하드웨어 지원
TOCTitle: 장치 하드웨어 지원
ms:assetid: ba07ca91-32b4-49cf-801c-47a2d1d96e18
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412908(v=OCS.15)
ms:contentKeyID: 49304841
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 장치 하드웨어 지원

 

_**마지막으로 수정된 항목:** 2012-12-14_

IP 전화와 아날로그 장치를 배포하려면 특정 하드웨어 구성을 설정해야 합니다.

Lync Phone Edition을 실행하는 IP 전화는 LLDP-MED(Link Layer Discovery Protocol-Media Endpoint Discovery) 및 PoE(Power over Ethernet)를 지원합니다. LLDP-MED를 활용하려면 스위치가 IEEE802.1AB 및 ANSI/TIA-1057을 지원해야 합니다. PoE를 활용하려면 스위치가 PoE802.3AF 또는 802.3at를 지원해야 합니다.

LLDP-MED를 사용하도록 설정하려면 관리자가 스위치 콘솔 창을 사용하여 LLDP를 사용하도록 설정하고 올바른 음성 VLAN ID를 사용하여 LLDP-MED 네트워크 정책을 설정해야 합니다.

또한 배포에 아날로그 장치가 포함된 경우 Lync Server을 사용하도록 아날로그 게이트웨이를 구성해야 하며 게이트웨이가 다음 중 하나여야 합니다.

  - ATA(Analog Telephone Adapter)

  - PSTN 아날로그 게이트웨이

  - PSTN 아날로그 게이트웨이가 포함된 SBA(Survivable Branch Appliance)

  - ATA를 사용하여 통신하는 PSTN 아날로그 게이트웨이가 포함된 SBA(Survivable Branch Appliance)

아날로그 게이트웨이를 구성하는 방법에 대한 자세한 내용은 Lync Server 2010 TechNet 라이브러리에서 "아날로그 장치 배포 계획"( [http://go.microsoft.com/fwlink/?linkid=268537\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=268537%26clcid=0x412))을 참조하십시오. 아날로그 장치는 Lync Server 2013에서 Lync Server 2010과 동일한 방식으로 작동합니다.


> [!IMPORTANT]
> 스위치에서 지원하는 경우 E9-1-1(Enhanced 9-1-1)을 사용하도록 스위치를 구성할 수 있습니다.


