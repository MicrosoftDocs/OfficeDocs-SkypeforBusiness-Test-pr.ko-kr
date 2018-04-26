---
title: Lync Server 2013 지원되는 토폴로지
TOCTitle: 지원되는 토폴로지
ms:assetid: 3475d430-0394-491b-a09b-ba85bd62be70
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425833(v=OCS.15)
ms:contentKeyID: 49303261
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 지원되는 토폴로지

 

_**마지막으로 수정된 항목:** 2014-01-14_

Lync Server 2013에서는 조직에서 온-프레미스로 사이트를 배포하고 온-프레미스 배포를 비즈니스용 Skype Online 배포와 통합할 수 있도록 지원하며, 이러한 배포를 하이브리드 배포라고 합니다. 하이브리드 배포에서는 온-프레미스와 온라인에 각각 사용자가 있습니다.

온-프레미스 배포의 경우 Lync Server 2013에서는 고가용성 및 위치 요구 사항에 맞게 조정할 수 있는 하나 이상의 사이트 배포를 지원합니다. 이러한 사이트와 해당 구성 요소를 조직의 액세스 및 복구 요구 사항을 충족하도록 구성할 수 있습니다.

Lync Server 2013 온-프레미스 배포는 다음 항목으로 구성됩니다.

  - 배포에 중앙 사이트(데이터 센터라고도 함)가 하나 이상 포함되어야 합니다. 각 중앙 사이트는 하나 이상의 Enterprise Edition 프런트 엔드 풀 또는 하나의 Standard Edition 서버를 포함해야 합니다. 이러한 풀 또는 서버는 다음으로 구성됩니다.
    
      - Enterprise Edition 프런트 엔드 풀은 하나 이상의 프런트 엔드 서버와 별도의 백 엔드 서버로 구성되며, 일반적으로 확장성을 위해 둘 이상의 프런트 엔드 서버를 포함합니다. 프런트 엔드 풀 하나에 최대 12개의 프런트 엔드 서버를 포함할 수 있습니다. 프런트 엔드 서버가 여러 개인 경우 부하 분산이 필요합니다. SIP 트래픽의 경우 DNS 부하 분산이 권장되지만 하드웨어 부하 분산도 지원됩니다. SIP 트래픽에 DNS 부하 분산을 사용하는 경우에도 HTTP 트래픽에 대한 하드웨어 부하 분산 장치가 필요합니다. 또한 데이터베이스의 고가용성을 위해 SQL Server 미러링을 사용하는 것이 좋습니다. 백 엔드 데이터베이스에는 별도의 인스턴스가 필요하지만 보관 데이터베이스, 미러링 데이터베이스, 영구 채팅 데이터베이스 및 영구 채팅 준수 데이터베이스를 함께 배치할 수 있습니다. Lync Server 2013에서는 배포 시 공유 클러스터를 사용한 파일 공유를 지원합니다. 데이터베이스 저장소 요구 사항에 대한 자세한 내용은 [Lync Server 2013의 데이터베이스 소프트웨어 지원](lync-server-2013-database-software-support.md)을 참고하세요. 파일 저장소 요구 사항에 대한 자세한 내용은 [Lync Server 2013의 파일 저장소 지원](lync-server-2013-file-storage-support.md)을 참고하세요.
        

        > [!IMPORTANT]
        > 여러 Lync Server 데이터베이스를 배치하는 경우에는 가용성과 성능에 영향을 줄 수 있는 모든 요인을 평가하는 것이 좋습니다. 장애 조치(failover) 기능을 확인하려면 모든 장애 조치(failover) 시나리오를 테스트하는 것이 좋습니다.

    
      - Standard Edition 서버는 함께 배치된 SQL Server Express 데이터베이스를 포함합니다.

  - 배포에 중앙 사이트와 연결된 하나 이상의 분기 사이트를 포함할 수도 있습니다.

이 섹션에서는 Lync Server 2013 배포의 사이트 및 구성 요소에 대해 설명합니다. Lync Server 2013 사이트, 토폴로지 및 구성 요소 계획에 대한 자세한 내용은 계획 설명서에서 [Lync Server 2013의 계획하기 전에 알아야 할 토폴로지 기본 사항](lync-server-2013-topology-basics-you-must-know-before-planning.md) 및 [Lync Server 2013의 참조 토폴로지](lync-server-2013-reference-topologies.md)를 참조하십시오. 이전 릴리스 구성 요소의 통합에 대한 자세한 내용은 [Lync Server 2013의 지원되는 마이그레이션 경로 및 동시 사용 시나리오](lync-server-2013-supported-migration-paths-and-coexistence-scenarios.md)를 참조하십시오.


> [!NOTE]
> 확대된 풀은 프런트 엔드, 에지, 중재, 디렉터 서버 역할에는 지원되지 않습니다.



## 중앙 사이트 토폴로지 및 구성 요소(온-프레미스)

중앙 사이트 토폴로지는 하나의 프런트 엔드 풀 또는 하나의 Standard Edition 서버를 포함해야 하지만 각 중앙 사이트는 다음을 포함할 수도 있습니다.

  - 같은 도메인 또는 다른 도메인에 있을 수 있는 여러 프런트 엔드 풀. 그러나 프런트 엔드 풀의 모든 프런트 엔드 서버와 해당 풀에 대한 백 엔드 서버는 같은 도메인에 있어야 합니다.

  - 여러 Standard Edition 서버

  - Office Web Apps 서버: Lync Server 2013의 Office 웹 응용 프로그램에서 Microsoft PowerPoint 프레젠테이션 공유 및 렌더링을 처리하는 데 사용됨

  - 경계 네트워크의 에지 서버 또는 에지 풀(페더레이션 파트너, 공용 IM 연결, XMPP(Extensible Messaging and Presence Protocol) 게이트웨이, 원격 사용자 액세스, 익명 사용자의 모임 참가 또는 Exchange 통합 메시징(UM)을 지원하도록 배포하려는 경우). 다른 서버 역할을 에지 서버와 함께 배치할 수 없습니다. 해당되는 경우 DNS 부하 분산이 권장되지만 하드웨어 부하 분산도 지원됩니다. 내부 에지 인터페이스와 외부 에지 인터페이스는 같은 유형의 부하 분산을 사용해야 합니다. 즉, 한 에지 인터페이스에서는 DNS 부하 분산을 사용하고 다른 에지 인터페이스에서는 하드웨어 부하 분산을 사용할 수는 없습니다. 부하 분산 요구 사항 및 지원에 대한 자세한 내용은 계획 설명서의 [Lync Server 2013의 외부 사용자 액세스 계획](lync-server-2013-planning-for-external-user-access.md) 및 배포 설명서의 [Lync Server 2013에서 외부 사용자 액세스 배포](lync-server-2013-deploying-external-user-access.md)를 참조하십시오.

  - 중재 서버 또는 풀(중앙 사이트의 프런트 엔드 풀에서 Enterprise Voice 또는 전화 접속 회의를 지원하려는 경우). Enterprise Voice 지원을 배포하는 방법에 따라 프런트 엔드 풀에 중재 서버를 배치(기본값)하거나 독립 실행형 중재 서버 또는 풀을 배포할 수 있습니다. DNS, 하드웨어 또는 응용 프로그램 부하 분산(해당되는 경우)을 사용하여 중재 서버 풀의 게이트웨이 피어(PSTN 게이트웨이, IP-PBX 또는 SIP 트렁크 SBC(Session Border Control) 등)에서 트래픽을 분산시킬 수 있습니다. 적절한 중재 서버 토폴로지를 계획하는 방법에 대한 자세한 내용은 계획 설명서에서 [Lync Server 2013의 중재 서버 배포 지침](lync-server-2013-deployment-guidelines-for-mediation-server.md)을 참조하십시오.

  - 영구 채팅 서버(사용자가 오랜 시간 동안 계속되는 주제 기반 단체 대화에 참가할 수 있도록 하려는 경우). 더 많은 용량을 제공하고 안정성을 높이려면 토폴로지에 영구 채팅 서버를 실행하는 여러 컴퓨터를 포함할 수 있습니다. 영구 채팅 서버는 엔터프라이즈 풀에서 다른 서버 역할과 함께 배치할 수 없습니다. 그러나 Standard Edition 서버에 영구 채팅 서버를 배치할 수는 있습니다. 영구 채팅에는 데이터베이스가 필요하며, 영구 채팅 준수를 구현하는 경우에는 영구 채팅 준수 데이터베이스도 필요하지만 이러한 데이터베이스는 보관 데이터베이스/모니터링 데이터베이스와 함께 배치하거나 Enterprise Edition 프런트 엔드 풀의 백 엔드 서버에 배치할 수 있습니다. 적절한 영구 채팅 서버 토폴로지를 계획하는 방법에 대한 자세한 내용은 [Lync Server 2013의 영구 채팅 서버 계획](lync-server-2013-planning-for-persistent-chat-server.md)을 참조하십시오.

  - 모니터링(배포에 포함된 Enterprise Voice 및 A/V 회의의 CDR(통화 정보 기록) 및 오디오/비디오 QoE(체감 품질)에 대한 데이터 수집을 지원하려는 경우). 필요한 경우 모니터링 CDR 및 QoE 데이터를 사용하여 통화 안정성 및 미디어 품질의 상태를 보여 주는 알림을 거의 실시간으로 생성하는 Microsoft System Center Operations Manager(이전 Microsoft Operations Manager)를 설치할 수도 있습니다. 모니터링은 배포하는 경우 프런트 엔드 서버 또는 Standard Edition 서버에 배치됩니다. 모니터링에는 데이터베이스가 필요하지만 해당 데이터베이스는 보관 데이터베이스/영구 채팅 데이터베이스/영구 채팅 준수 데이터베이스와 함께 배치하거나 Enterprise Edition 프런트 엔드 풀의 백 엔드 서버에 배치할 수 있습니다.

  - 보관(준수용으로 배포의 IM 통신 및 모임 콘텐츠를 보관하려는 경우). 보관은 배포하는 경우 프런트 엔드 서버 또는 Standard Edition 서버에 배치됩니다. 보관 저장소에는 보관 데이터베이스를 배포해야 하거나 Exchange 2013 저장소를 통합해야 합니다. 두 방법을 모두 사용하는 경우('혼합 모드'라고 함) Exchange 2013 저장소를 사용하여 Exchange 2013에 있는 사용자의 보관 데이터를 저장하고 보관 데이터베이스를 사용하여 배포에 포함된 다른 모든 사용자의 데이터를 보관합니다. 보관 데이터베이스가 필요한 경우 해당 데이터베이스는 모니터링 데이터베이스/영구 채팅 데이터베이스/영구 채팅 준수 데이터베이스와 함께 배치하거나 프런트 엔드 풀의 백 엔드 서버에 배치할 수 있습니다. 적절한 보관 토폴로지를 계획하는 방법에 대한 자세한 내용은 계획 설명서에서 [Lync Server 2013의 보관 계획](lync-server-2013-planning-for-archiving.md)을 참조하십시오 *.*

  - 디렉터 또는 디렉터 풀(사용자의 홈 풀(Enterprise Edition 프런트 엔드 풀 또는 Standard Edition 서버일 수 있음)로의 Lync Server 2013 사용자 요청 리디렉션 및 탄성을 용이하게 하려는 경우). 외부 사용자 액세스를 지원하는 각 중앙 사이트 및 하나 이상의 프런트 엔드 풀을 배포한 각 중앙 사이트에 디렉터 또는 디렉터 풀을 배포하는 것이 좋습니다. 각 디렉터 풀은 최대 10개의 디렉터를 포함할 수 있습니다. 디렉터를 다른 서버 역할과 함께 배치할 수는 없습니다. 적절한 디렉터 토폴로지를 계획하는 방법에 대한 자세한 내용은 계획 설명서에서 [Lync Server 2013의 디렉터 시나리오](lync-server-2013-scenarios-for-the-director.md)을 참조하십시오.

  - 역방향 프록시( Lync Server 2013 구성 요소는 아니지만 페더레이션 사용자의 웹 콘텐츠 공유를 지원하거나 모바일 트래픽을 지원하려는 경우에 필요함). 역방향 프록시 서버는 어떤 Lync Server 2013 서버 역할과도 함께 배치할 수 없지만 다른 응용 프로그램에 사용되는 조직 내의 기존 역방향 프록시 서버에 지원을 구성하여 Lync Server 2013 배포에 대한 역방향 프록시 지원을 구현할 수 있습니다. 역방향 프록시 서버에 대한 자세한 내용은 배포 설명서에서 [Lync Server 2013에 대한 역방향 프록시 서버 설치](lync-server-2013-setting-up-reverse-proxy-servers.md)을 참조하십시오.


> [!NOTE]
> Lync Server 2013에서 A/V 회의, 모니터링 및 보관은 더 이상 별도의 서버 역할이 아니며 프런트 엔드 서버에서 실행됩니다.



중앙 사이트에 배포한 모든 프런트 엔드 풀 및 Standard Edition 서버는 중앙 사이트용으로 배포한 다음 항목을 공유합니다.

  - 디렉터 또는 디렉터 풀

  - 독립 실행형 중재 서버 또는 풀

  - Office Web Apps 서버

  - 에지 서버 또는 에지 풀

  - 영구 채팅 서버 또는 풀

  - 모니터링

  - 보관


> [!NOTE]
> Exchange 2013 통합 메시징 통합을 지원하려는 경우에는 Exchange UM 서버를 Lync Server 2013 배포와 함께 구현할 수 있지만, Exchange UM 서버는 Lync Server 2013 사이트의 구성 요소가 아닙니다.



또한 하나의 중앙 사이트에 배포한 다음 항목을 여러 중앙 사이트에서 공유할 수 있습니다.

  - 독립 실행형 중재 서버 또는 풀

  - 에지 서버 또는 에지 풀

  - 영구 채팅 서버 또는 풀

  - 보관

  - 모니터링


> [!NOTE]
> Exchange UM 서버를 Lync Server 2013 배포와 함께 구현하고 여러 중앙 사이트에서 공유할 수 있지만, Exchange UM 서버는 Lync Server 2013 사이트의 구성 요소가 아닙니다.



Lync Server 2013 서버 역할 및 기능에 대한 자세한 내용은 계획 설명서에서 [Lync Server 2013의 서버 역할](lync-server-2013-server-roles.md)을 참조하십시오.

Lync Server 2013 서버 배치 지원에 대한 요약은 [Lync Server 2013의 지원되는 서버 배치](lync-server-2013-supported-server-collocation.md)를 참조하십시오.

이 섹션의 앞부분에서 다룬 서버 역할 및 기능 외에 Lync Server 2013에는 다음 중 일부 또는 전부를 포함할 수 있는 추가 구성 요소 및 옵션이 있습니다.

  - 방화벽

  - PSTN 게이트웨이(Enterprise Voice를 배포하는 경우)

  - Exchange UM 서버

  - DNS 부하 분산

  - 하드웨어 부하 분산 장치

  - SQL Server 데이터베이스

  - 파일 공유

모든 Lync Server 2013 기능, 구성 요소 및 옵션에 대한 자세한 내용은 계획 설명서를 참조하십시오.

## 분기 사이트 토폴로지 및 구성 요소(온-프레미스)

분기 사이트는 중앙 사이트와 연결되며, 분기 사이트의 각 SBA(Survivable Branch Appliance)는 연결된 중앙 사이트의 Enterprise Edition 프런트 엔드 풀 또는 Standard Edition 서버와 연결됩니다. 분기 사이트는 대부분의 기능을 중앙 사이트에 의존하므로 다음 구성 요소만 포함합니다.

  - SBA(Survivable Branch Appliance) - 공중 전화망(PSTN) 게이트웨이를 일부 Lync Server 기능과 결합합니다. 중재 서버를 SBA(Survivable Branch Appliance)의 등록자 인스턴스와 함께 배치할 수 있으며 독립 실행형 중재 서버 또는 중재 서버 풀을 배포할 수 있습니다.

  - 지속 가능 분기 서버 - Lync Server 2013 등록자 및 중재 서버 소프트웨어가 설치된 Windows Server 실행 서버입니다.

  - 독립 실행형 PSTN 게이트웨이(SBA(Survivable Branch Appliance)의 일부가 아님) 및 독립 실행형 중재 서버

지속 가능 분기 서버에 대한 요구 사항은 Lync Server 2013 서버 역할에 대한 요구 사항과 같습니다.

