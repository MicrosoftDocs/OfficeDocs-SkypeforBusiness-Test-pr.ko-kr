---
title: 'Lync Server 2013: 새로운 트렁크 기능'
TOCTitle: 새로운 트렁크 기능
ms:assetid: 9b398bc8-2760-4218-b1a4-89b9694b1171
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688152(v=OCS.15)
ms:contentKeyID: 49885889
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 새로운 트렁크 기능

 

_**마지막으로 수정된 항목:** 2012-09-21_

Microsoft Lync Server 2013에서는 중재 서버와 게이트웨이 간에 여러 트렁크를 정의할 수 있습니다. 반면 Microsoft Lync Server 2010에서는 중재 서버와 PSTN 게이트웨이 간에 단일 트렁크만 사용할 수 있었습니다. 이 기능을 통해 필요에 따라 유연하게 추가 트렁크를 정의할 수 있습니다. 트렁크는 중재 서버 FQDN 및 수신 포트와 PSTN 게이트웨이 FQDN 및 수신 포트 간의 논리적 연결입니다. 이 새로운 기능을 통해 복구(여러 중재 서버를 사용하여 동일한 PSTN 게이트웨이로 통화를 라우팅할 수 있음), PBX 상호 운용성(IP-PBX와 중재 서버 간에 서로 다른 정책이 연결된 여러 트렁크를 사용할 수 있음) 및 SIP 트렁크 구성(여러 사이트의 중재 서버에서 동일한 통신사 FQDN이 참조하는 통신사에 대한 SIP 트렁크를 가질 수 있음)을 위해 손쉽게 트렁크를 정의할 수 있습니다.

## 참고 항목

#### 개념

[Lync Server 2013의 새 Enterprise Voice 기능](lync-server-2013-new-enterprise-voice-features.md)

