---
title: Lync Server 2013 초기 계획 결정
TOCTitle: 초기 계획 결정
ms:assetid: cbaa5cb3-2b00-4b9f-952d-986a0c9f160b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398855(v=OCS.15)
ms:contentKeyID: 49305048
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에 대한 초기 계획 결정

 

_**마지막으로 수정된 항목:** 2012-10-01_

계획 프로세스의 처음 부분에서는 조직에 필요한 Lync Server 작업 및 주요 기능을 결정합니다.

1.  **원하는 배포가 온-프레미스 배포인가, 온라인 배포인가?**    Lync Server에서는 두 배포 시나리오를 모두 지원합니다. 이 결정에 대한 자세한 내용은 이 섹션의 초반부에 있는 [Lync Server 2013 배포 방법 결정](lync-server-2013-deciding-how-to-deploy-microsoft-lync.md)을 참조하십시오.

2.  **실제 토폴로지가 필요한가, 가상화 토폴로지가 필요한가?**    Lync Server은 실제 토폴로지와 가상화 토폴로지에서 모든 작업 부하 및 서버 역할을 지원합니다. 사용자 용량 및 확장성은 실제 토폴로지와 가상화 토폴로지 간에 차이가 납니다. 자세한 내용은 [가상 서버에서 Lync Server 실행](lync-server-2013-running-lync-server-on-virtual-servers.md)을 참조하십시오.

3.  ***메신저* 및 *현재 상태*는 항상 사용하도록 설정됩니다.**   모든 Lync Server 배포에서 메신저 및 현재 상태 작업이 기본적으로 설치되고 사용하도록 설정됩니다. 메신저는 사용자들이 실시간 텍스트 메시지를 사용하여 커뮤니케이션하는 데 사용되며, 현재 상태는 네트워크에 있는 다른 사용자들의 상태를 보는 데 사용됩니다. 사용자의 현재 상태는 다른 사람들이 사용자에게 연락할지 여부와 연락 방법을 결정하는 데 도움이 되는 정보를 제공합니다. 자세한 내용은 계획 설명서에서 [Lync Server 2013의 프런트 엔드 서버, 메신저 및 현재 상태 계획](lync-server-2013-planning-for-front-end-servers-instant-messaging-and-presence.md)을 참고하세요.

4.  **회의 모드를 배포할 것인가?**   회의는 Lync Server의 또 다른 핵심 기능입니다. 몇 가지 회의 모드가 지원됩니다. 지원되는 모든 회의 유형을 배포하거나 일부만 배포하도록 선택할 수 있습니다. *웹 회의* 는 사용자가 Microsoft PowerPoint 프레젠테이션 그래픽 프로그램으로 만든 슬라이드 카드와 같이 프레젠테이션할 파일을 보는 데 사용됩니다. *응용 프로그램 공유* 는 사용자들이 실시간으로 서로 데스크톱의 일부 또는 전부를 공유하는 데 사용됩니다. 사용자들은 *A/V 회의* 를 사용하여 회의 및 피어 투 피어 통신에 오디오(및 비디오)를 추가할 수 있습니다. *전화 접속 회의* 는 사용자가 표준 PSTN 전화를 사용하여 조직에서 호스팅되는 회의의 오디오 부분에 참가하는 데 사용됩니다. 자세한 내용은 계획 설명서에서 [Lync Server 2013의 회의 계획](lync-server-2013-planning-for-conferencing.md)를 참조하십시오.
    
    Lync Server 2013에서 웹 회의를 배포하면 모임에서 Powerpoint를 공유하고 볼 수 있도록 Office Web Apps Server와의 통합도 계획해야 합니다. 자세한 내용은 [Office Online Server 및 Lync Server 2013과 통합 구성](lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md)을 참조하십시오.

5.  **A/V 회의를 배포하는 경우 이러한 회의의 오디오 품질도 모니터링해야 합니다.**    Lync Server A/V 회의의 오디오 및 비디오 품질에 영향을 주는 요소는 많습니다. 모니터링을 사용하면 통화 및 회의의 A/V 품질을 모니터링할 수 있습니다. 미디어 품질에 영향을 주는 문제를 탐지하고 사용자의 미디어 환경이 최적의 상태인지 확인할 수 있습니다. 자세한 내용은 [Lync Server 2013의 모니터링 계획](lync-server-2013-planning-for-monitoring.md)을 참조하십시오.

6.  **메신저, 현재 상태 및 회의 서버에 고가용성이 필요한가?**   사이트에 메신저, 현재 상태 및 회의 기능을 제공하는 서버가 한 대만 있는 경우 서버가 중단되면 사용자의 생산성이 크게 저하됩니다. 이러한 기능을 위해 여러 대의 서버로 구성된 Enterprise Edition*풀* 을 배포하면 서버를 사용할 수 없는 경우에도 Lync Server가 이러한 모든 기능이 유지된 상태로 작동을 계속할 수 있습니다.
    
    또 다른 옵션으로, 5000명 이하의 사용자가 있는 조직에서 고가용성을 원하는 경우 Lync ServerStandard Edition을 실행하는 두 서버를 배포하여 이들 서버를 쌍으로 연결할 수 있습니다. 자세한 내용은 [Lync Server 2013의 고가용성 및 재해 복구 계획](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md)을 참조하십시오.

7.  **재해 복구 옵션이 필요한가?**   두 군데의 데이터 센터가 있는 경우 재해 복구 옵션을 사용하여 한 데이터 센터의 모든 또는 일부 서버의 가동이 중단해도 사용자가 작업을 계속 진행할 수 있도록 하려면 재해 복구 기능을 사용하여 서버를 배포할 수 있음을 기억하십시오. 이러한 배포에서는 한 데이터 센터의 서버 풀을 다른 데이터 센터의 상대 풀과 쌍으로 연결할 수 있습니다. 한 데이터 센터의 가동이 중단되는 경우 쌍으로 연결된 다른 풀이 최소한의 서비스 중단만으로 두 풀의 사용자 모두에게 서비스를 제공할 수 있습니다. 자세한 내용은 [Lync Server 2013의 고가용성 및 재해 복구 계획](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md)을 참조하십시오.

8.  **사용자가 외부 사용자와 커뮤니케이션하고 공동 작업하도록 지원할 것인가?**   외부 사용자와의 커뮤니케이션 및 공동 작업을 지원하면 Lync Server의 투자 수익률을 높일 수 있습니다. 이렇게 하면 조직의 사용자들이 조직의 방화벽 외부에서 일할 때도 Lync Server 기능을 활용할 수 있습니다. 또한 Lync Server를 실행하는 파트너 또는 고객 조직과 페더레이션할 수도 있습니다. 이렇게 하면 사용자 및 페더레이션된 파트너 사용자가 쉽게 메신저 메시지를 주고받고, 서로 모임에 초대하고, 상대방의 현재 상태를 볼 수 있습니다. 또한 사용자는 전자 메일 메시지를 사용하여 자신이 이끄는 회의에 특정 외부 사용자를 초대할 수 있습니다. 자세한 내용은 [Lync Server 2013의 외부 사용자 액세스 계획](lync-server-2013-planning-for-external-user-access.md)을 참조하십시오.

9.  **Enterprise Voice를 배포할 것인가?**    *Enterprise Voice* 는 Lync Server가 제공하는 VoIP(Voice over IP) 솔루션입니다. 기존의 PBX 기반 전화 통신에 대한 매력적인 대안을 제공합니다. Enterprise Voice는 사용자가 컴퓨터 또는 VoIP 전화를 통해 Outlook 또는 Lync Server에서 대화 상대를 클릭하여 전화를 걸 수 있도록 지원합니다. IP 네트워크를 통해 컴퓨터 간, 컴퓨터에서 전화로 또는 전화에서 컴퓨터로 통화를 할 수 있습니다. 사용자가 자신의 컴퓨터에서 통합하고 사용할 수 있는 모든 통신 옵션(음성, 전자 메일, 메신저 및 회의)을 모두 활용할 수 있습니다. 자세한 내용은 계획 설명서에서 [Lync Server 2013의 Enterprise Voice 계획](lync-server-2013-planning-for-enterprise-voice.md)을 참조하십시오.

10. **Enterprise Voice를 배포하는 경우 이러한 통화의 오디오 품질도 모니터링해야 합니다.**   Enterprise Voice를 배포하는 경우 모니터링 서버를 사용하여 Enterprise Voice 통화의 오디오 품질을 확인하는 것이 좋습니다. 자세한 내용은 [Lync Server 2013의 모니터링 계획](lync-server-2013-planning-for-monitoring.md)을 참조하십시오.

11. **요구 사항을 준수하기 위해 메신저 콘텐츠 또는 모임 콘텐츠를 보관해야 하는가?**   조직에서 요구 사항을 준수하기 위해 메신저 콘텐츠 또는 모임 콘텐츠를 보관해야 하는 경우 보관을 배포할 수 있습니다. 자세한 내용은 [Lync Server 2013의 보관 계획](lync-server-2013-planning-for-archiving.md)을 참조하십시오.

12. **영구 채팅을 배포할 것인가?**   사용자가 시간이 경과해도 유지할 수 있는 실시간 대화를 나눌 수 있도록 하려면 영구 채팅을 배포할 수 있습니다. 자세한 내용은 [Lync Server 2013의 영구 채팅 서버 계획](lync-server-2013-planning-for-persistent-chat-server.md)을 참조하십시오.

13. **Microsoft Exchange를 배포할 것인가?**   조직에서 전자 메일 서비스를 위해 Microsoft Exchange Server를 사용하는 경우 Lync Server 및 Microsoft Exchange Server를 효과적으로 개선하는 여러 기능을 사용할 수 있습니다. Exchange 통합 메시징(UM)이라는 이러한 기능의 일부로는 Outlook 또는 Outlook Web Access의 음성 메일 공지 수신, 음성 메일 수신 대기, 전화를 통해 Microsoft Exchange 사서함 액세스 및 Microsoft Exchange 사서함에 팩스 수신 기능이 포함됩니다. 또한 Exchange 2013을 배포한 경우 두 시스템 간의 사용자에 대해 대화 상대 저장소를 통합하고, Exchange를 사용하여 고해상도 대화 상대 사진을 저장하며, 전자 메일 및 메신저 대화의 보관 파일을 통합할 수 있습니다. 자세한 내용은 [Lync Server 2013과 Exchange Server 통합 계획](lync-server-2013-planning-for-exchange-server-integration.md)을 참조하십시오.

14. **조직에 지사가 있는가?**   조직에 지사가 있는 경우 Lync Server는 지사를 지원하기 위한 다양한 방법을 제공하고 음성 및 기타 기능에 대한 복구를 보장합니다. 특히 데이터 센터에 대한 복구 가능한 WAN 연결이 없는 지사에 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버를 설치하여 WAN(광역 네트워크) 연결이 중단될 경우 Enterprise Voice 지원을 유지할 수 있습니다. 자세한 내용은 [Lync Server 2013의 분기 사이트 음성 복구 계획](lync-server-2013-planning-for-branch-site-voice-resiliency.md)을 참조하십시오.

