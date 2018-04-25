---
title: Lync Server 2013 소규모 조직용 참조 토폴로지
TOCTitle: 소규모 조직용 참조 토폴로지
ms:assetid: 0453aeee-c41f-44e6-a6e0-aaace526ca08
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398095(v=OCS.15)
ms:contentKeyID: 49302660
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 소규모 조직의 Lync Server 2013에 대한 참조 토폴로지

 

_**마지막으로 수정된 항목:** 2013-10-07_

소규모 조직용 참조 토폴로지는 Lync Server를 실행하는 3개 서버만 배포하여 강력하고 가용성이 뛰어난 솔루션을 배포할 수 있는 방법을 보여줍니다.

**소규모 조직용 참조 토폴로지**

![세 개의 서버를 배포하는 참조 토폴로지 다이어그램](images/Gg398095.25196d0d-dd07-451b-83ba-94c0ddf59030(OCS.15).jpg "세 개의 서버를 배포하는 참조 토폴로지 다이어그램")

  - **배포되는 Standard Edition 서버 쌍**     이 조직에는 중앙 사이트에 4천 명의 사용자가 있습니다. 조직은 고가용성 및 재해 복구를 위해 Standard Edition 서버 두 개를 배포한 다음 쌍으로 묶었습니다. 각 서버에는 2천 명의 사용자가 있지만, 모든 사용자에 대한 정보는 두 서버 간에 동기화됩니다. 따라서 서버 하나가 다운되면 관리자는 사용자의 작업 중단을 최소화하면서 다른 서버에서 작업이 처리되도록 장애 조치(failover)를 수행할 수 있습니다. Lync Server 2013의 고가용성 및 재해 복구 기능에 대한 자세한 내용은 [Lync Server 2013의 고가용성 및 재해 복구 계획](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md)을 참고하세요.

  - **에지 서버 배포 권장.**    내부 IM, 현재 상태 및 회의에는 에지 서버를 배포하지 않아도 되지만 소규모 배포에도 에지 서버를 배포하는 것이 좋습니다. 에지 서버를 배포하여 현재 조직 방화벽 외부에 있는 사용자에게 서비스를 제공하면 Lync Server 투자를 극대화할 수 있습니다. 이 경우의 이점은 다음과 같습니다.
    
      - 조직의 사용자가 집에서 일하거나 외근 시 Lync Server 기능을 사용할 수 있습니다.
    
      - 사용자가 외부 사용자를 모임에 초대할 수 있습니다.
    
      - 파트너, 공급업체 또는 고객 조직에서도 Lync Server를 사용하는 경우 해당 조직과 *페더레이션 관계* 를 구축할 수 있습니다. 그러면 Lync Server 배포에서 페더레이션 조직의 사용자를 인식하므로 공동 작업의 효율이 향상됩니다.
    
      - 사용자가 Windows Live, AOL, Yahoo\!, Google Talk 등의 공용 IM 서비스 사용자와 메신저 대화를 주고받을 수 있습니다. 이러한 서비스와의 공용 IM 연결에는 별도의 라이선스가 필요할 수도 있습니다.
        

        > [!IMPORTANT]
        > <UL>
        > <LI>
        > <P>2012년 9월 1일 현재 신규 또는 갱신 계약에 대해 Microsoft Lync "PIC USL"(공용 메신저 연결 사용자 구독 라이선스)을 더 이상 구입할 수 없습니다. 유효 라이선스를 보유한 고객은 서비스 종료 날짜까지 Yahoo! Messenger와 계속 페더레이션할 수 있습니다. AOL 및 Yahoo!는 서비스 종료 날짜를 2014년 6월로 발표했습니다. 자세한 내용은 <A href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Lync Server 2013의 공용 메신저 연결 지원</A>을 참고하세요.</P>
        > <LI>
        > <P>PIC USL은 Lync Server 또는 Office Communications Server가 Yahoo! Messenger와 페더레이션하는 데 필요한 월별 사용자 단위 구독 라이선스입니다. Microsoft는 Yahoo!의 지원 여부에 따라 이 서비스를 제공할 수 있었으며 해당 서비스의 기본 계약은 곧 종료될 예정입니다.</P>
        > <LI>
        > <P>Lync는 전 세계의 여러 조직과 개별 사용자를 연결해 주는 매우 효율적인 도구입니다. Lync Standard CAL 외의 추가 사용자/장치 라이선스가 없어도 Windows Live Messenger와의 페더레이션이 가능합니다. Skype 페더레이션도 이 목록에 추가될 예정이므로 Lync 사용자는 메신저 및 음성을 통해 수많은 사람들과 연결할 수 있습니다.</P></LI></UL>



  - **분기 사이트 지속 가능성.**    이 조직에서는 Lync Server Enterprise Voice 기능의 파일럿 프로그램을 실행합니다. 일부 사용자는 음성 솔루션으로 Lync Server만 사용합니다. 이러한 Voice 파일럿 사용자 중 일부는 분기 사이트에 있습니다. 분기 사이트에는 중앙 사이트에 대한 안정적인 WAN(Wide Area Network) 링크가 없으므로 SBA(Survivable Branch Appliance)가 배포되어 있습니다. SBA가 배포되어 있으면 WAN 링크가 다운된 경우에도 분기 사이트의 사용자가 계속 전화(조직 내의 통화 및 PSTN 통화 모두 가능)를 걸고 받을 수 있으며 음성 메일 기능을 사용하고 두 사용자 간에 IM(메신저 대화)으로 통신할 수 있습니다. 또한 WAN 링크를 사용할 수 없는 경우에도 사용자가 인증을 받을 수 있습니다.

  - **Exchange UM 배포.** 이 참조 토폴로지에는 Lync Server가 아니라 Microsoft Exchange Server를 실행하는 Exchange 통합 메시징(UM) 서버가 포함되어 있습니다.
    
    Exchange UM에 대한 자세한 내용은 계획 설명서에서 [Lync Server 2013의 Exchange 통합 메시징 통합 계획](lync-server-2013-planning-for-exchange-unified-messaging-integration.md) 및 [Lync Server 2013의 호스팅된 Exchange 통합 메시징 통합](lync-server-2013-hosted-exchange-unified-messaging-integration.md)을 참고하세요.

  - **Office Web Apps Server.** 웹 회의를 사용하는 모든 조직에서 Office Web Apps Server 또는 Office Web Apps Server 팜을 배포하는 것이 좋습니다. Office Web Apps Server를 사용하면 웹 회의에서 PowerPoint 슬라이드를 제공할 수 있습니다. 자세한 내용은 [Office Online Server 및 Lync Server 2013과 통합 구성](lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md)을 참고하세요.

