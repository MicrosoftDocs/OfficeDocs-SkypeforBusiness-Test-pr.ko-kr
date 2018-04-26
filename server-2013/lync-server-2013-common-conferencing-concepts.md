---
title: 공통 회의 개념
TOCTitle: 공통 회의 개념
ms:assetid: a21d4987-1c0a-44c8-8a39-9c17ffb57f3c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688158(v=OCS.15)
ms:contentKeyID: 49885904
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 공통 회의 개념

 

_**마지막으로 수정된 항목:** 2012-09-19_

모든 유형의 회의에는 몇 가지 공통적인 개념이 있습니다. 다음 섹션에서는 이러한 개념에 대해 설명합니다.

## 정책 및 대역폭 관리

Lync Server 2013을 통해 관리자는 사용자가 구성할 수 있는 모임 유형에 대한 정책을 설정할 수 있습니다. 이렇게 하면 조직 정책을 적용하고 대역폭 사용을 제어할 수 있습니다. 다양한 모임 정책을정의하여 개별 사용자 및 사용자 그룹에 할당할 수 있습니다. 또한 피어 투 피어 대화를 제어하는 정책을 설정할 수 있습니다. 회의 정책을 설정하는 방법에 대한 자세한 내용은 작업 설명서에서 [Lync Server 2013의 회의 정책](lync-server-2013-conferencing-policies.md)을 참조하십시오. 대역폭 관리에 대한 자세한 내용은 [Lync Server 2013의 통화 허용 제어 서비스 개요](lync-server-2013-overview-of-call-admission-control.md) 및 [Lync Server 2013에서 비디오 대역폭 구성](lync-server-2013-configuring-video-bandwidth.md)을 참조하십시오.

## 보관 및 준수 기능

Lync Server 2013에서는 조직이 준수 규정을 따라야 하는 경우 사용할 수 있는 기능을 제공합니다. 보관 기능을 사용하여 모임에서 제공된 내용과 IM(인스턴트 메시징) 대화 및 IM 회의의 내용을 모두 보관할 수 있습니다. 자세한 내용은 계획 설명서에서 [Lync Server 2013의 보관 계획](lync-server-2013-planning-for-archiving.md)을 참조하십시오. 영구 채팅 서버의 준수 기능을 사용하여 사용하여 오랜 시간 동안 지속되는 특정 주제에 대한 단체 대화를 보관할 수 있습니다.자세한 내용은 계획 설명서에서 [Lync Server 2013의 영구 채팅 서버 계획](lync-server-2013-planning-for-persistent-chat-server.md)을 참조하십시오.

## 모니터링 기능

모니터링 서버 기능은 CDR(통화 정보 기록)을 캡처할 수 있습니다. CDR은 Lync Server 2013을 사용하여 서로 대화하는 사용자를 추적하는 데 사용할 수 있습니다. 모니터링 배포 및 구성에 대한 자세한 내용은 [Lync Server 2013의 모니터링 배포](lync-server-2013-deploying-monitoring.md)를 참조하십시오.

## 외부 사용자의 전화 회의 참가 설정

초대 받은 외부 사용자가 전화 회의에 참가할 수 있도록 설정하여 Lync Server 2013 회의에 대한 투자 이익을 크게 증가시킬 수 있습니다. 외부 사용자에는 다음이 포함될 수 있습니다.

  - **원격 사용자**   방화벽 외부에서 랩톱 또는 다른 Lync Server 2013 장치를 사용하여 작업하는 조직의 사용자

  - **페더레이션 사용자**   Lync Server 2013을 실행하여 함께 작업하는 회사의 사용자. 조직의 사용자가 이러한 사용자에게 쉽게 연결할 수 있도록 하려면 이러한 회사와 페더레이션 관계를 만들면 됩니다.

  - **익명 사용자**   조직의 사용자가 특정 전화 회의에 참가하도록 특별히 초대한 다른 모든 외부 사용자. 회사의 모임 이끌이는 외부 사용자에게 전화 회의 초대 전자 메일을 보낼 수 있습니다. 이 전자 메일에는 외부 사용자가 클릭하여 전화 회의에 참가할 수 있는 링크가 포함됩니다.

이러한 시나리오의 전부 또는 일부를 적용하려면 에지 서버를 배포하여 Lync Server 2013 배포와 외부 사용자 간의 보안 통신을 설정해야 합니다. 에지 서버를 사용하는 Lync Server 2013 솔루션은 VPN(가상 사설망)과 같은 다른 솔루션보다 뛰어난 품질의 미디어를 제공합니다. 자세한 내용은 [Lync Server 2013의 외부 사용자 액세스 계획](lync-server-2013-planning-for-external-user-access.md)를 참조하십시오.

또한 에지 서버 배포 여부에 관계없이 사용자(조직 내부 또는 외부)가 표준 PSTN 전화에서 전화 접속을 통해 온-프레미스 오디오 회의에 참가하도록 설정할 수 있습니다. Lync Server 2013 전화 접속 회의를 배포하면 됩니다.

## 모임 유형 및 클라이언트 버전 간의 호환성

Lync Server 2013이 이전 버전의 Office Communications Server 및 해당 클라이언트와 상호 운용되도록 하려면 다음과 같은 문제를 알아야 합니다.

  - Lync Server 2013을 사용하는 사용자는 Live Meeting 회의를 예약하거나 이 유형의 마이그레이션된 모임을 수정할 수 없습니다.

  - Lync Server 2013을 사용하는 사용자가 Office Communications Server 2007 R2을 실행하는 서버에서 호스팅되는 Live Meeting 회의에 참석하려면 Lync Server 2013 외에 Live Meeting 클라이언트를 컴퓨터에 설치해야 합니다.

  - Live Meeting 회의를 Lync Server 2013으로 마이그레이션한 경우 모임 콘텐츠는 마이그레이션되지 않습니다. 이 콘텐츠가 필요한 경우 다시 업로드해야 합니다.

