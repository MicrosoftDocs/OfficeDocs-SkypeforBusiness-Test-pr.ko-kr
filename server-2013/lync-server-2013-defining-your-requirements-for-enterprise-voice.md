---
title: 'Lync Server 2013: Enterprise Voice에 대한 요구 사항 정의'
TOCTitle: Enterprise Voice에 대한 조직의 요구 사항 정의
ms:assetid: 3310f78e-c658-4557-95fa-159ce3c22953
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425826(v=OCS.15)
ms:contentKeyID: 49303242
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 Enterprise Voice에 대한 요구 사항 정의

 

_**마지막으로 수정된 항목:** 2012-08-07_

이 항목에서는 토폴로지의 사이트 간 링크, 사이트 및 지역에 대해 고려해야 하는 사항에 대한 개요와 Enterprise Voice를 배포할 때 이러한 고려 사항이 얼마나 중요한지에 대해 설명합니다. 이러한 결정을 내리는 데 도움이 되는 자세한 내용은 계획 설명서에서 [Lync Server 2013의 고급 Enterprise Voice 기능에 대한 네트워크 설정](lync-server-2013-network-settings-for-the-advanced-enterprise-voice-features.md)을 참조하십시오.

## 사이트 및 지역

먼저 Enterprise Voice를 배포할 토폴로지의 사이트와 이러한 사이트가 속하는 네트워크 지역을 파악합니다. 특히, 각 사이트에 공중 전화망(PSTN) 연결을 제공할 방법을 고려합니다. 관리 편의성 및 물류상의 이유로, 이러한 사이트가 속하는 지역은 중요한 요인이 될 수 있습니다. 게이트웨이를 로컬로 배포할 위치, SBA(Survivable Branch Appliance)를 배포할 위치, 그리고 ITSP(인터넷 전화 통신 서비스 공급자)에 대한 SIP 트렁크를 구성할 수 있는 위치(로컬 또는 중앙 사이트)를 결정합니다.

## 사이트 간의 네트워크 링크

중앙 사이트 및 해당 분기 사이트 간의 네트워크 링크에 대한 예상 대역폭 사용량도 고려해야 합니다. 사이트 간에 탄력적인 WAN 링크가 있거나 이러한 링크를 배포할 예정이라면, 각 분기 사이트에서 게이트웨이를 배포하여 해당 사이트의 사용자에 대해 로컬 DID(Direct Inward Dial) 종료 기능을 제공하는 것이 좋습니다. 탄력적인 WAN 링크는 있지만 해당 WAN 링크의 대역폭이 제한될 것으로 예상된다면 해당 링크에 대해 통화 허용 제어를 구성합니다. 탄력적인 WAN 링크가 없고, 분기 사이트에서 1천 명 미만의 사용자를 호스팅하며, 숙련된 로컬 Lync Server 관리자가 없는 경우에는 분기 사이트에서 SBA(Survivable Branch Appliance)를 배포하는 것이 좋습니다. 분기 사이트에서 호스팅하는 사용자 수가 1천~5천 명이고, 탄력적인 WAN 연결이 없으며, 숙련된 Lync Server 관리자가 있는 경우에는 분기 사이트에서 소형 게이트웨이와 함께 지속 가능 분기 서버를 배포하는 것이 좋습니다. 또한 미디어 바이패스를 지원하는 게이트웨이 피어가 있는 경우에는 제한된 링크에 대해 미디어 바이패스를 사용하도록 설정하는 것도 고려하십시오.

## 참고 항목

#### 개념

[Lync Server 2013의 고급 Enterprise Voice 기능에 대한 네트워크 설정](lync-server-2013-network-settings-for-the-advanced-enterprise-voice-features.md)

