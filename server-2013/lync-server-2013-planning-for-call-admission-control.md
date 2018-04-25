---
title: 'Lync Server 2013: 통화 허용 제어 서비스 계획'
TOCTitle: CAC(통화 허용 제어 서비스) 계획
ms:assetid: ca367138-adf5-4119-bc40-5ddf335ed22f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398842(v=OCS.15)
ms:contentKeyID: 49305025
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 통화 허용 제어 서비스 계획

 

_**마지막으로 수정된 항목:** 2012-09-21_

전화 통신, 비디오, 응용 프로그램 공유 등과 같은 IP 기반 UC(통합 통신) 응용 프로그램에서 사용 가능한 엔터프라이즈 네트워크 대역폭은 일반적으로 LAN 환경에서는 제한 요소로 간주되지 않지만 사이트, 네트워크 대역폭이 교차되는 WAL 링크에서는 제한될 수 있습니다. 네트워크 트래픽량이 WAN 링크를 초과 구독할 경우 이러한 정체를 해결하기 위해 큐, 버퍼링 및 패킷 삭제 등과 같은 현재 메커니즘이 사용됩니다. 추가 트래픽은 일반적으로 네트워크 정체가 해결되거나 필요한 경우 트래픽이 삭제될 때까지 지연됩니다. 이러한 상황에서 일반적인 데이터 트래픽에 대해서는 수신 클라이언트가 복구할 수 있습니다. 하지만 통합 통신과 같은 실시간 트래픽의 경우 통합 통신이 대기 시간 및 패킷 손실 모두에 민감하므로 이 방법으로 네트워크 정체를 해결할 수 없으며, WAN의 정체로 인해 사용자의 QoE(체감 품질)가 저하될 수 있습니다. 정체된 상황에서의 실시간 트래픽에 대해 품질이 낮은 연결을 제공하는 것보다 통화를 지연시키는 것이 더 나은 선택입니다.

CAC(통화 허용 제어)는 허용 가능한 품질의 실시간 세션을 설정하기 위해 충분한 네트워크 대역폭이 있는지 여부를 확인합니다. Lync Server 2013에서 CAC는 오디오 및 비디오에 대해서만 실시간 트래픽을 제어하며 데이터 트래픽에는 영향을 미치지 않습니다. 기본 WAN 경로에 필요한 대역폭이 없는 경우 CAC는 인터넷 경로나 PSTN(공중 전화망)을 통해 통화를 라우팅할 수 있습니다. CAC는 Lync Server에서만 사용할 수 있습니다.

이 섹션에서는 통화 허용 제어 기능과 CAC를 계획하는 방법에 대해서 설명합니다.


> [!NOTE]
> Lync Server에 포함된 세 가지 고급 Enterprise Voice 기능은 통화 허용 제어, 긴급 서비스(E9-1-1) 및 미디어 바이패스입니다. 이 세 기능에 공통적으로 적용되는 계획 정보의 개요는 <A href="lync-server-2013-network-settings-for-the-advanced-enterprise-voice-features.md">Lync Server 2013의 고급 Enterprise Voice 기능에 대한 네트워크 설정</A> 섹션을 참조하십시오.



## 이 단원의 내용

  - [Lync Server 2013의 통화 허용 제어 서비스 개요](lync-server-2013-overview-of-call-admission-control.md)

  - [Lync Server 2013에서 통화 허용 제어 서비스에 대한 요구 사항 정의](lync-server-2013-defining-your-requirements-for-call-admission-control.md)

  - [예: Lync Server 2013에서 통화 허용 제어 서비스에 대한 요구 사항 수집](lync-server-2013-example-of-gathering-your-requirements-for-call-admission-control.md)

  - [Lync Server 2013의 CAC의 구성 요소 및 토폴로지](lync-server-2013-components-and-topologies-for-cac.md)

  - [Lync Server 2013의 통화 허용 제어 서비스 모범 사례](lync-server-2013-best-practices-for-call-admission-control.md)

  - [Lync Server 2013의 통화 허용 제어 서비스에 대한 배포 검사 목록](lync-server-2013-deployment-checklist-for-call-admission-control.md)

