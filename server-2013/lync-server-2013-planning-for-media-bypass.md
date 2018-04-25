---
title: 'Lync Server 2013: 미디어 바이패스 계획'
TOCTitle: 미디어 바이패스 계획
ms:assetid: 8ac732b6-8538-4d7b-b1a9-2035e419dac2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398703(v=OCS.15)
ms:contentKeyID: 49304310
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 미디어 바이패스 계획

 

_**마지막으로 수정된 항목:** 2012-09-21_

미디어 바이패스는 신호가 중재 서버를 트래버스하는 통화에 대해 가능할 때마다 미디어 경로에서 중재 서버를 제거하는 것을 가리킵니다.

미디어 바이패스는 대기 시간, 불필요한 변환, 패킷 손실 가능성 및 잠재적 오류 지점 수를 줄여 음성 품질을 향상시킬 수 있습니다. 바이패스된 통화에 대한 미디어 처리가 없으므로 중재 서버에 대한 부하가 줄어 들어 확장성이 향상될 수 있습니다. 이러한 부하의 감소가 여러 게이트웨이를 제어하는 중재 서버의 기능을 보완합니다.

중재 서버 없이 분기 사이트가 대역폭이 제한된 하나 이상의 WAN 링크에 의해 중앙 사이트에 연결된 경우 미디어 바이패스는 먼저 WAN 링크에서 중앙 사이트의 중재 서버로 그리고 역으로 흐를 필요 없이 분기 사이트의 클라이언트에서 미디어가 해당 로컬 게이트웨이로 직접 흐르도록 하여 대역폭 요구 사항을 줄입니다.

미디어 바이패스는 중재 서버가 미디어를 처리하지 않도록 하여 Enterprise Voice 인프라에 필요한 중재 서버 수도 줄일 수 있습니다.

다음 그림에서는 미디어 바이패스가 있는 경우와 없는 경우의 토폴로지의 기본 미디어 및 신호 경로를 보여 줍니다.

**미디어 바이패스가 있는 경우와 없는 경우의 미디어 및 신호 경로**

![음성 CAC 미디어 바이패스 연결 적용](images/Gg398703.4d66d529-0912-4de1-abec-266f54272eb3(OCS.15).jpg "음성 CAC 미디어 바이패스 연결 적용")

일반적으로 가능한 모든 곳에 미디어 바이패스를 사용합니다.

## 이 단원의 내용

  - [Lync Server 2013의 미디어 바이패스 개요](lync-server-2013-overview-of-media-bypass.md)

  - [Lync Server 2013의 미디어 바이패스 모드](lync-server-2013-media-bypass-modes.md)

  - [Lync Server 2013의 미디어 바이패스 및 통화 허용 제어 서비스](lync-server-2013-media-bypass-and-call-admission-control.md)

  - [Lync Server 2013의 미디어 바이패스에 대한 기술 요구 사항](lync-server-2013-technical-requirements-for-media-bypass.md)

## 관련 단원

[Lync Server 2013에서 고급 Enterprise Voice 기능 배포](lync-server-2013-deploying-advanced-enterprise-voice-features.md)

## 참고 항목

#### 작업

[Lync Server 2013에서 미디어 바이패스로 트렁크 구성](lync-server-2013-configure-a-trunk-with-media-bypass.md)  

#### 개념

[Lync Server 2013의 전역 미디어 바이패스 옵션](lync-server-2013-global-media-bypass-options.md)

