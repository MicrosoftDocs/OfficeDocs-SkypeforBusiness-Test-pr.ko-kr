---
title: 'Lync Server 2013: 미디어 바이패스에 대한 기술 요구 사항'
TOCTitle: 미디어 바이패스에 대한 기술 요구 사항
ms:assetid: 6162a204-0e7c-460a-8eb2-e592c6590a8a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398435(v=OCS.15)
ms:contentKeyID: 49303806
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 미디어 바이패스에 대한 기술 요구 사항

 

_**마지막으로 수정된 항목:** 2012-09-21_

PSTN에 대한 각 호출에 대해 중재 서버는 중재 서버를 경유하지 않고도 원래 Lync 끝점의 미디어를 중재 서버 피어로 직접 전송할 수 있는지 확인합니다. 피어는 통화가 라우팅될 때 중재 서버 간 트렁크와 연결된 PSTN 게이트웨이, IP-PBX 또는 ITSP(인터넷 전화 통신 서비스 공급업체)의 SBC(세션 경계 컨트롤러)일 수 있습니다.

다음 요구 사항이 충족되는 경우 미디어 바이패스를 적용할 수 있습니다.

  - 중재 서버 피어가 미디어 바이패스에 필요한 기능을 지원해야 합니다. 그 중 가장 중요한 기능은 분기된 여러 응답("초기 대화"라고 함)을 처리하는 기능입니다. 게이트웨이, PBX 또는 SBC가 허용할 수 있는 최대 초기 대화 수의 값을 확인하려면 게이트웨이, PBX 또는 ITSP 제조업체에 문의하십시오.

  - 중재 서버 피어가 Lync 끝점의 미디어 트래픽을 직접 수락해야 합니다. 대부분의 ITSP는 SBC가 중재 서버를 통해서만 트래픽을 받을 수 있도록 합니다. SBC가 Lync 끝점의 미디어 트래픽을 직접 수락할 수 있는지 여부를 확인하려면 ITSP에 문의하십시오.

  - Lync 클라이언트 및 중재 서버 피어는 올바르게 연결되어야 합니다. 즉, 클라이언트와 피어가 같은 네트워크 지역에 있거나, 대역폭 제약 조건이 없는 WAN 링크를 통해 지역에 연결되는 네트워크 사이트에 있어야 합니다.

## 참고 항목

#### 개념

[Lync Server 2013의 미디어 바이패스 모드](lync-server-2013-media-bypass-modes.md)  
[Lync Server 2013의 미디어 바이패스 및 통화 허용 제어 서비스](lync-server-2013-media-bypass-and-call-admission-control.md)

