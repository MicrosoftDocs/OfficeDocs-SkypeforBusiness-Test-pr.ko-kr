---
title: 'Lync Server 2013: SIP 트렁크를 사용하여 E9-1-1 통화 라우팅'
TOCTitle: SIP 트렁크를 사용하여 E9-1-1 통화 라우팅
ms:assetid: 157753c3-fe74-4e2c-81da-ee06911d4cc2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204701(v=OCS.15)
ms:contentKeyID: 49302904
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 SIP 트렁크를 사용하여 E9-1-1 통화 라우팅

 

_**마지막으로 수정된 항목:** 2012-09-29_

E9-1-1을 배포하는 방법 중 하나는 SIP 트렁크를 사용하여 적격 E9-1-1 서비스 공급자에 연결하는 것입니다. ELIN 게이트웨이를 사용하여 공중 전화망(PSTN) 기반 E9-1-1 서비스 공급자에 연결하는 방법에 대한 자세한 내용은 [Lync Server 2013에서 ELIN 게이트웨이를 사용하여 E9-1-1 전화 라우팅](lync-server-2013-routing-e9-1-1-calls-by-using-an-elin-gateway.md)을 참조하십시오.

다음 다이어그램에서는 SIP 트렁크 및 적격 E9-1-1 서비스 공급자를 사용할 때 긴급 통화가 Lync Server에서 PSAP(Public Safety Answering Point)로 라우팅되는 방법을 보여 줍니다.

**SIP 트렁크를 통해 E9-1-1 라우팅**

![Lync Server에서 PSAP로의 긴급 통화 라우팅](images/JJ204701.0637a9d4-2ca7-438a-8ed0-19090a4b992d(OCS.15).jpg "Lync Server에서 PSAP로의 긴급 통화 라우팅")

호환 Lync Server 클라이언트에서 긴급 통화를 하는 경우

1.  위치, 발신자 콜백 번호 및 알림 URL과 회의 콜백 번호(선택 사항)가 포함된 SIP INVITE가 Lync Server로 라우팅됩니다.

2.  Lync Server는 긴급 번호의 일치 여부를 확인하여 해당하는 위치 정책에 정의된 **PSTN 사용** 값에 따라 통화를 중재 서버로 라우팅한 다음, 여기서 SIP 트렁크를 통해 E9-1-1 서비스 공급자로 라우팅합니다.

3.  E9-1-1 서비스 공급자는 통화에서 제공되는 위치에 따라 올바른 PSAP로 긴급 통화를 라우팅합니다. 클라이언트가 긴급 통화와 함께 확인된 ERL(Emergency Response Location)을 포함하는 경우 공급자가 해당하는 PSAP로 통화를 자동 라우팅합니다. 위치를 사용자가 수동으로 입력한 경우 ECRC(Emergency Call Response Center)는 긴급 통화를 PSAP로 라우팅하기 전에 발신자의 위치가 정확한지 구두로 먼저 확인합니다.

4.  알림에 대해 위치 정책을 구성한 경우에는 조직의 보안 담당자 한 명 이상에게 특수한 Lync 긴급 알림 인스턴트 메시지가 발송됩니다. 보안 담당자의 화면에 항상 팝업으로 표시되는 이 메시지에는 발신자 이름, 전화 번호, 시간, 및 위치가 포함되므로 보안 담당자가 인스턴트 메시지나 음성을 통해 긴급 발신자에게 빠르게 대응할 수 있습니다.

5.  회의에 대해 위치 정책을 구성한 경우 E9-1-1 서비스 공급자가 해당 정책을 지원하면 내부 보안 데스크가 단방향 오디오 또는 양방향 오디오를 사용하여 전화 회의에 참가하게 됩니다.

6.  통화가 중간에 끊어지면 PSAP는 콜백 번호를 사용하여 발신자에게 직접 연락합니다.

