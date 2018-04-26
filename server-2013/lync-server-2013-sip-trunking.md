---
title: 'Lync Server 2013: SIP 트렁크'
TOCTitle: SIP 트렁크
ms:assetid: 7c586401-d0e5-4017-b3e1-fe5e7f8fc6db
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398619(v=OCS.15)
ms:contentKeyID: 49304156
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 SIP 트렁크

 

_**마지막으로 수정된 항목:** 2012-08-13_

SIP(Session Initiation Protocol)는 기본 전화 서비스 및 인스턴트 메시징, 회의, 현재 상태 감지, 멀티미디어 등의 추가 실시간 통신 서비스에 대한 VoIP(Voice over IP) 통신 세션을 시작 및 관리하는 데 사용됩니다. 이 섹션에서는 로컬 네트워크의 경계를 넘어 확장되는 SIP 연결 유형인 *SIP 트렁크* 를 구현하기 위한 계획 정보를 제공합니다.

## SIP 트렁크란?

SIP 트렁크는 조직과 방화벽 너머의 ITSP(인터넷 전화 통신 서비스 공급자) 간의 SIP 통신 링크를 설정하는 IP 연결입니다. 일반적으로 SIP 트렁크는 조직의 중앙 사이트를 ITSP에 연결하는 데 사용됩니다. 일부의 경우 분기 사이트를 ITSP에 연결하는 데에도 SIP 트렁크를 사용하도록 선택할 수 있습니다.

## SIP 트렁크와 Direct SIP 연결

*트렁크*라는 용어는 회로 전환 기술에서 파생된 것으로, 전화 전환 장비를 연결하는 물리적 전용 회선을 가리킵니다. 이전 TDM(Time Division Multiplexing) 트렁크와 마찬가지로 SIP 트렁크는 두 개의 별개 SIP 네트워크인 Lync Server 2013 엔터프라이즈와 ITSP 간의 연결입니다. 회로 전환 트렁크와는 달리 SIP 트렁크는 지원되는 모든 SIP 트렁크 연결 유형에 대해 설정할 수 있는 가상 연결입니다. 지원되는 연결 유형에 대한 자세한 내용은 [Lync Server 2013에서 SIP 트렁크를 구현하는 방법](lync-server-2013-how-do-i-implement-sip-trunking.md)을 참고하세요.

반면에 Direct SIP 연결은 로컬 네트워크 경계를 가로지르지 않는 SIP 연결입니다(즉, 내부 네트워크 내에서 PSTN(공중 전화망) 게이트웨이 또는 PBX(Private Branch Exchange)에 연결됨). Lync Server 2013과의 직접 SIP 연결을 사용하는 방법에 대한 자세한 내용은 [Lync Server 2013의 직접 SIP 연결](lync-server-2013-direct-sip-connections.md)을 참조하십시오.

## 이 섹션의 내용

  - [Lync Server 2013의 SIP 트렁크 개요](lync-server-2013-overview-of-sip-trunking.md)

  - [Lync Server 2013에서 SIP 트렁크를 구현하는 방법](lync-server-2013-how-do-i-implement-sip-trunking.md)

  - [Lync Server 2013의 SIP 트렁크에 대한 구성 요소 및 토폴로지](lync-server-2013-components-and-topologies-for-sip-trunking.md)

  - [Lync Server 2013의 분기 사이트 SIP 트렁크](lync-server-2013-branch-site-sip-trunking.md)

  - [Lync Server 2013에 대한 SIP 트렁크 배포 검사 목록](lync-server-2013-sip-trunk-deployment-checklist.md)

