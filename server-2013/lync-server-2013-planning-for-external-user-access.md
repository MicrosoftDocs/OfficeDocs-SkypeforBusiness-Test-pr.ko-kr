---
title: 'Lync Server 2013: 외부 사용자 액세스 계획'
TOCTitle: 외부 사용자 액세스 계획
ms:assetid: ea098933-eff5-461e-aba3-e7f128784dc2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399048(v=OCS.15)
ms:contentKeyID: 49305408
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 외부 사용자 액세스 계획

 

_**마지막으로 수정된 항목:** 2013-01-19_

대부분 조직의 통신은 내부 네트워크 외부에 있는 서비스와 사용자를 포함합니다. 이러한 서비스와 사용자에는 임시로 또는 영구적으로 회사 외부에 있는 직원, 고객이나 파트너 조직의 직원, 공용 IM(인스턴트 메시징) 서비스를 사용하는 사용자, 잠재적인 고객, 파트너 및 모임과 프레젠테이션에 초대할 익명 사용자 등이 있습니다 이들 모두를 통칭하여 *외부 사용자* 라고 합니다.

Microsoft Lync Server 2013을 사용하면 조직의 사용자가 IM 및 현재 상태를 사용하여 외부 사용자와 통신할 수 있으며, 회사 외부 직원 및 기타 유형의 외부 사용자와 함께 A/V(오디오/비디오) 회의 및 웹 회의에 참가할 수 있습니다. 모바일 장치 및 Enterprise Voice를 통해서도 외부 액세스를 지원할 수 있습니다. 익명 참석자를 허용하므로 조직의 구성원이 아닌 외부 사용자가 Lync Server 2013 모임에 참가할 수 있습니다.

조직의 방화벽 전체에서 통신을 지원하려면 경계 네트워크(DMZ, 완충 영역 또는 스크린된 서브넷이라고도 함)에 Lync Server 2013 에지 서버를 배포합니다. 에지 서버는 방화벽 외부의 사용자가 내부 Lync Server 2013 배포에 연결할 수 있는 방법을 제어합니다. 또한 방화벽 내에서 보낸 외부 사용자와의 통신도 제어합니다.

요구 사항에 따라 하나 이상의 위치에 하나 이상의 에지 서버를 배포할 수 있습니다. 이 섹션에서는 Lync Server 2013의 외부 사용자 액세스에 대한 시나리오와 에지 및 역방향 프록시 토폴로지를 계획하는 방법에 대해 설명합니다.


> [!NOTE]
> Enterprise Voice와 외부 사용자 액세스를 지원하기 위해 에지 서버가 필요하지만 이 섹션에서는 IM, 현재 상태, A/V 회의, 페더레이션 및 Lync Mobile 지원에 대해 중점적으로 설명합니다. Enterprise Voice 지원에 대한 자세한 내용은 계획 설명서에서 <A href="lync-server-2013-planning-for-enterprise-voice.md">Lync Server 2013의 Enterprise Voice 계획</A>을 참조하십시오.



## 이 단원의 내용

  - [에지 서버 계획에 영향을 주는 Lync Server 2013의 변경 사항](lync-server-2013-changes-in-lync-server-that-affect-edge-server-planning.md)

  - [Lync Server 2013의 외부 사용자 액세스 구성 요소에 대한 시스템 요구 사항](lync-server-2013-system-requirements-for-external-user-access-components.md)

  - [Lync Server 2013의 외부 사용자 액세스 개요](lync-server-2013-overview-of-external-user-access.md)

  - [Lync Server 2013의 자동 검색 이해](lync-server-2013-understanding-autodiscover.md)

  - [Lync Server 2013에서 토폴로지 선택](lync-server-2013-choosing-a-topology.md)

  - [Lync Server 2013의 데이터 수집](lync-server-2013-data-collection.md)

  - [Lync Server 2013에 대한 DNS 요구 사항 확인](lync-server-2013-determine-dns-requirements.md)

  - [Lync Server 2013에 대한 외부 A/V 방화벽 및 포트 요구 사항 확인](lync-server-2013-determine-external-a-v-firewall-and-port-requirements.md)

  - [Lync Server 2013의 에지 서버 인증서 계획](lync-server-2013-plan-for-edge-server-certificates.md)

  - [Lync Server 2013의 외부 사용자 액세스에 대한 시나리오](lync-server-2013-scenarios-for-external-user-access.md)

