---
title: 'Lync Server 2013: ELIN 게이트웨이를 사용하여 E9-1-1 전화 라우팅'
TOCTitle: ELIN 게이트웨이를 사용하여 E9-1-1 전화 라우팅
ms:assetid: 5a3997e3-898d-49cb-922a-4184c3373350
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204919(v=OCS.15)
ms:contentKeyID: 49303733
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 ELIN 게이트웨이를 사용하여 E9-1-1 전화 라우팅

 

_**마지막으로 수정된 항목:** 2013-02-05_

Unified Communications Open Interoperability Program의 일부 파트너는 자격이 있는 E9-1-1 서비스 공급자에 대한 SIP 트렁크 연결의 대안으로 사용할 수 있는 자격이 있는 ELIN(Emergency Location Identification Number) 지원 게이트웨이를 제공합니다. ELIN 게이트웨이는 PSTN(공중 전화망) 기반의 E9-1-1 서비스에 대한 ISDN 또는 CAMA(Centralized Automatic Message Accounting) 연결을 지원합니다. ELIN 게이트웨이를 제공하는 파트너에 대한 자세한 내용 및 해당 설명서에 대한 링크는 <http://go.microsoft.com/fwlink/?linkid=248425>를 참조하십시오.

E9-1-1 서비스 공급자에 대한 SIP 트렁크 연결과 마찬가지로 ELIN 게이트웨이는 긴급 통화를 발신자의 가장 적합한 PSAP(Public Safety Answering Point)로 라우팅할 수 있는 방법을 제공하지만, 이러한 게이트웨이는 ELIN을 위치 식별자로 사용합니다. 조직 내 각 ERL(Emergency Response Location)에 대한 ELIN을 정의합니다(자세한 내용은 [Lync Server 2013에서 ELIN 게이트웨이 위치 관리](lync-server-2013-managing-locations-for-elin-gateways.md) 참조).

긴급 통화를 위해 ELIN 게이트웨이를 사용할 때는 SIP 트렁크 연결에 사용하는 것과 동일한 Lync Server E9-1-1 인프라를 사용합니다. 즉, 위치 정보 서비스 데이터베이스는 위치를 Lync Server 클라이언트에 제공하고, 위치 정책은 기능을 사용하도록 설정하고 라우팅을 정의합니다. 하지만 ELIN 게이트웨이를 사용하려면 위치 정보 서비스 데이터베이스에 ELIN을 추가하고 PSTN 통신 사업자가 이를 ALI(Automatic Location Identification) 데이터베이스에 업로드하도록 해야 합니다.

Lync 클라이언트가 위치 정보 서비스에서 해당 위치를 가져올 때, 위치에는 ELIN이 포함됩니다. 긴급 통화 중 ELIN에는 ELIN 게이트웨이에 전송된 위치가 포함됩니다. ELIN 게이트웨이는 통화를 긴급 통화로 식별하고 통화 당사자의 번호를 ELIN으로 전환합니다. 그런 후 ELIN 게이트웨이는 호출 번호로 ELIN을 사용해서 통화를 PSTN으로 라우팅합니다. PSTN E9-1-1 공급자는 MSAG(Master Street Address Guide) 데이터베이스의 부속 데이터베이스인 ALI 데이터베이스에서 ELIN을 조회합니다. 그런 후 PSTN은 ALI 조회를 기반으로 가장 적합한 PSAP로 통화를 전송하고, PSAP는 ALI 조회를 기반으로 첫 번째 응답자를 발신자의 위치로 보냅니다. 호출 중인 번호는 콜백을 위해 미리 정의된 일정 기간 동안 ELIN 게이트웨이에 캐시로 저장됩니다. 콜백 중에는 PSAP가 ELIN 게이트웨이에 연결하여 발신자의 DID(direct inward dialing) 번호를 얻기 위해 ELIN으로 전환합니다.

ELIN 게이트웨이는 조직 내 네트워크 내부에서만 긴급 통화를 지원합니다. 네트워크 외부로부터의 긴급 통화는 지원하지 않습니다.


> [!NOTE]
> 긴급 통화를 위해 SIP 트렁크 연결을 사용하는 방법에 대한 자세한 내용은 <A href="lync-server-2013-routing-e9-1-1-calls-by-using-a-sip-trunk.md">Lync Server 2013에서 SIP 트렁크를 사용하여 E9-1-1 통화 라우팅</A>을 참조하십시오.



다음 다이어그램에서는 ELIN 게이트웨이를 사용할 때 긴급 통화가 Lync Server에서 PSAP로 라우팅되는 방법을 보여줍니다.

**ELIN 게이트웨이로 E9-1-1 통화 라우팅**

![ELIN 통화 라우팅](images/JJ204919.ea68f88a-0fc4-43d4-9660-79a7e8936df1(OCS.15).jpg "ELIN 통화 라우팅")

1.  위치, 발신자의 콜백 번호, 선택적인 알림 URL 및 회의 콜백 번호를 포함하는 SIP INVITE는 Lync Server로 라우팅됩니다.

2.  Lync Server가 긴급 번호를 일치시키고 통화를 적용 가능한 위치 정책에 정의된 **PSTN 사용** 값에 따라 중재 서버로 라우팅하고, 여기에서 ELIN 게이트웨이로 라우팅합니다.

3.  ELIN 게이트웨이는 ISDN 또는 CAMA 트렁크를 통해 통화를 PSTN으로 라우팅합니다.

4.  PSTN은 통화를 긴급 통화로 식별하고 이를 네트워크에서 E9-1-1 선택적 라우터로 라우팅합니다. E9-1-1 선택적 라우터는 지리적 위치 정보를 가져오기 위해 ALI 데이터베이스에서 발신자의 번호를 조회합니다. E9-1-1 선택적 라우터는 ALI 데이터베이스에서 검색된 위치 정보를 기반으로 가장 적합한 PSAP에 통화를 전송합니다.

5.  알림에 대해 위치 정책을 구성한 경우에는 조직의 보안 담당자 한 명 이상에게 특수한 Lync 긴급 알림 인스턴트 메시지가 발송됩니다. 보안 담당자의 화면에 항상 팝업으로 표시되는 이 메시지에는 발신자 이름, 전화 번호, 시간, 및 위치가 포함되므로 보안 담당자가 인스턴트 메시지나 음성을 통해 긴급 발신자에게 빠르게 대응할 수 있습니다.

6.  통화가 중간에 끊어지면 PSAP는 ELIN을 사용해서 발신자에게 직접 연락합니다. ELIN 게이트웨이는 발신자의 DID를 위해 ELIN을 전환합니다.

