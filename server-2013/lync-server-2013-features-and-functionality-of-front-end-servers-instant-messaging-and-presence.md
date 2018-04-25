---
title: 'Lync Server 2013: 프런트 엔드 서버, 메신저, 현재 상태의 기능'
TOCTitle: 프런트 엔드 서버, 메신저, 현재 상태의 기능
ms:assetid: 05b29536-dcd7-49b5-934a-2ebf20ddc45c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398109(v=OCS.15)
ms:contentKeyID: 49302688
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 프런트 엔드 서버, 메신저, 현재 상태의 기능

 

_**마지막으로 수정된 항목:** 2013-03-17_

프런트 엔드 서버는 대부분의 Lync Server 기능을 제공합니다. 사용 가능한 버전은 Lync Server Enterprise Edition(주로 대규모 기업용으로 디자인됨) 및 Lync Server Standard Edition(주로 하드웨어 투자액이 적으며 고가용성이 필요하지 않은 소규모 조직용으로 디자인됨)의 두 가지입니다. 두 버전은 IM, 현재 상태, 회의 및 Enterprise Voice를 비롯한 모든 Lync Server 작업을 지원합니다.

IM(메신저 대화)은 사용자가 텍스트 기반 메시지를 사용하여 컴퓨터에서 실시간으로 다른 사용자와 통신할 수 있도록 합니다. 양방향 및 단체 메신저 세션이 모두 지원됩니다. 양방향 메신저 대화의 참가자는 언제든지 대화에 세 번째 참가자를 추가할 수 있습니다. 이 경우 대화 창이 회의 기능을 지원하도록 변경됩니다.


> [!IMPORTANT]
> Lync 및 Communicator 클라이언트는 일대일 통신에서 사용될 경우 주로 피어 투 피어라고 합니다. 엄밀히 말하면 두 개의 클라이언트가 일대일 대화에서 통신하고 그 중간에 IMMCU(Instant Messaging Multipoint Control Unit)가 있는 것입니다. IMMCU는 프런트 엔드 서버의 구성 요소입니다. 필수 통신 워크플로에 IMMCU가 있으면 통화 정보 기록과 그 밖에 프런트 엔드 서버에서 사용할 수 있는 기능이 허용됩니다. 통신은 클라이언트의 동적 원본 포트에서 시작되어 프런트 엔드 서버 포트 TLS/TCP/5061(권장 전송 계층 보안을 사용하는 경우)에서 끝납니다. 기본적으로 피어 투 피어 통신 및 다자간 메신저 대화는 Lync Server 및 IMMCU가 활성화되어 있고 사용 가능한 경우에만 해당됩니다.



*현재 상태* 는 네트워크에 있는 다른 사용자의 상태에 대한 정보를 제공합니다. 사용자의 현재 상태는 다른 사용자가 사용자와 대화를 시도해야 하는지 여부와 메신저 대화, 전화 또는 전자 메일 중 어떤 것을 사용할지 결정하는 데 유용한 정보를 제공합니다. 현재 상태는 가능한 경우 인스턴트 통신을 촉진하는 동시에, 사용자가 회의 중인지 또는 부재 중인지에 대한 정보를 제공하여 인스턴트 통신을 사용할 수 없다는 것도 표시합니다. 이 현재 상태는 Lync 및 현재 상태를 인식하는 기타 응용 프로그램(예: Microsoft Outlook 메시징 및 공동 작업 클라이언트, Microsoft SharePoint 기술, Microsoft Word, Microsoft Excel 스프레드시트 소프트웨어)에 현재 상태 아이콘으로 표시됩니다. 현재 상태 아이콘은 사용자의 현재 상태와 통신 가능 여부를 나타냅니다.

