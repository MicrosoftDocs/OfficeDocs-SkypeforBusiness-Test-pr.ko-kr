---
title: 'Lync Server 2013: 경계 네트워크 VoIP 구성 요소'
TOCTitle: 경계 네트워크 VoIP 구성 요소
ms:assetid: 74230008-695d-436a-90b9-9cd060c70f7b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398559(v=OCS.15)
ms:contentKeyID: 49304055
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에 대한 경계 네트워크 VoIP 구성 요소

 

_**마지막으로 수정된 항목:** 2012-09-21_

개인적인 통화나 전화 회의를 위해 Unified Communications 클라이언트를 사용하는 외부 발신자는 동료들과의 음성 통신을 위해 에지 서버를 사용합니다.

에지 서버에서 액세스 에지 서비스는 조직 방화벽 외부에 있는 Lync 사용자의 통화에 대해 SIP 신호를 제공합니다. A/V 에지 서비스를 사용하면 미디어가 NAT 및 방화벽을 트래버스할 수 있습니다. 회사 방화벽 외부에서 UC(통합 통신) 클라이언트를 사용하는 발신자는 개인적인 통화와 전화 회의 모두에 A/V 에지 서비스를 사용합니다.

A/V 에지 서비스와 함께 A/V 인증 서비스가 배치되어 인증 서비스를 제공합니다. A/V 에지 서비스에 연결하려는 외부 사용자는 A/V 인증 서비스에서 제공한 인증 토큰이 있어야 통화할 수 있습니다.

