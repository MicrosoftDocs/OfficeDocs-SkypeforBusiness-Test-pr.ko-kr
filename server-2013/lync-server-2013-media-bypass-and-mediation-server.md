---
title: 'Lync Server 2013: 미디어 바이패스 및 중재 서버'
TOCTitle: 미디어 바이패스 및 중재 서버
ms:assetid: 8ed35f95-05cd-4b5d-8470-442d2323df71
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398719(v=OCS.15)
ms:contentKeyID: 49304348
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 미디어 바이패스 및 중재 서버

 

_**마지막으로 수정된 항목:** 2012-09-21_

미디어 바이패스는 관리자가 통화 라우팅이 중재 서버를 트래버스하지 않고 사용자 끝점과 PSTN(공중 전화망) 게이트웨이 간을 직접 흐르도록 구성하는 데 사용할 수 있는 Lync Server 기능입니다. 미디어 바이패스는 대기 시간, 불필요한 변환, 패킷 손실 가능성 및 잠재적 오류 지점 수를 줄여 통화 품질을 향상시킵니다. 중재 서버 없이 원격 사이트가 대역폭이 제한된 하나 이상의 WAN 링크에 의해 중앙 사이트에 연결된 경우 미디어 바이패스는 먼저 WAN 링크에서 중앙 사이트의 중재 서버로 그리고 역으로 흐를 필요 없이 원격 사이트의 클라이언트에서 미디어가 해당 로컬 게이트웨이로 직접 흐르도록 하여 대역폭 요구 사항을 줄입니다. 이렇게 줄어든 미디어 처리는 중재 서버의 여러 게이트웨이를 제어할 수 있는 기능도 보완합니다.

미디어 바이패스와 CAC(통화 허용 제어)는 함께 사용할 수 없습니다. 통화에 미디어 바이패스가 사용되는 경우 해당 통화에 대해 CAC가 수행되지 않습니다. 통화에 관련된 제한된 대역폭에 대한 링크가 없다고 가정합니다.

## 참고 항목

#### 개념

[Lync Server 2013의 통화 허용 제어 서비스 및 중재 서버](lync-server-2013-call-admission-control-and-mediation-server.md)  

#### 기타 리소스

[Lync Server 2013의 미디어 바이패스 계획](lync-server-2013-planning-for-media-bypass.md)

