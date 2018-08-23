---
title: 'Lync Server 2013: Enterprise Voice 배포'
TOCTitle: Enterprise Voice 배포
ms:assetid: b5b593a6-ac30-461c-8c8c-0041e2c9ab04
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412876(v=OCS.15)
ms:contentKeyID: 49304788
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 Enterprise Voice 배포

 

_**마지막으로 수정된 항목:** 2012-10-03_

Lync Server 2013의 Enterprise Voice는 Lync Server 2013 인프라의 일부입니다.

Enterprise Voice를 배포하려면 다음 작업을 수행해야 합니다.

1.  계획 설명서에서 [Lync Server 2013의 Enterprise Voice 계획](lync-server-2013-planning-for-enterprise-voice.md) 섹션을 검토합니다.

2.  이 작업을 통해 배포할 기능 및 구성 요소에 대한 계획을 완료합니다.

3.  계획 도구를 실행하여 배포 결정을 반영하는 토폴로지를 설계합니다.

4.  배포 설명서의 [Lync Server 2013에서 토폴로지 정의 및 구성](lync-server-2013-defining-and-configuring-the-topology.md)에 설명된 대로 토폴로지 작성기에서 토폴로지 디자인을 엽니다.
    

    > [!NOTE]
    > 토폴로지 작성기 설치는 내부 풀의 배포 프로세스에 속합니다. 자세한 내용은 배포 설명서에서 <A href="lync-server-2013-install-lync-server-administrative-tools.md">Lync Server 2013 관리 도구 설치</A>를 참조하십시오.



또한 배포하도록 선택한 참조 토폴로지에 해당하는 중앙 사이트 및 분기 사이트에 Lync Server Enterprise Edition이 이미 배포되어 있어야 합니다. 하나 이상의 내부 풀에 대한 파일을 정의, 게시 및 설치해야만 Enterprise Voice 구성 요소를 배포할 수 있으며 토폴로지 작성기를 사용하여 내부 풀을 정의하고 게시해야 합니다.

Enterprise Voice 서버 역할을 배포하는 예와 해당 서버 역할과 다른 서버 역할 및 다른 Lync Server 2013 서버 역할에 대한 관계를 보여 주는 참조 토폴로지를 보려면 계획 설명서에서 [Lync Server 2013의 참조 토폴로지](lync-server-2013-reference-topologies.md)를 참조하십시오.

네트워크 지역, 네트워크 사이트 및 서브넷 등 샘플 통화 허용 제어 배포를 설명하는 참조 토폴로지를 보려면 계획 설명서에서 [예: Lync Server 2013에서 통화 허용 제어 서비스에 대한 요구 사항 수집](lync-server-2013-example-of-gathering-your-requirements-for-call-admission-control.md)을 참조하십시오.


> [!IMPORTANT]
> 중앙 사이트에 Enterprise Voice를 배포하려면 이 섹션의 항목을 계속 읽으십시오. 분기 사이트에 Enterprise Voice를 배포하려면 배포 설명서의 <A href="lync-server-2013-deploying-branch-sites.md">Lync Server 2013에서 분기 사이트 배포</A>로 건너뛰십시오.



이 섹션에는 각 프런트 엔드 서버 또는 Standard Edition Server에 중재 서버를 권장되는 방식으로 배치하는 배포 및 독립 실행형 중재 서버 풀의 배포와 관련된 절차가 포함되어 있습니다.

토폴로지 작성기를 사용하여 각 프런트 엔드 서버 또는 Standard Edition Server에 중재 서버를 배치하는 토폴로지를 정의하고 게시한 경우 프런트 엔드 서버 풀 또는 Standard Edition Server용 파일을 설치할 때 중재 서버용 파일을 배포 마법사가 이미 자동으로 설치했으므로 다음 콘텐츠를 건너뛸 수 있습니다.

  - [Lync Server 2013에서 트렁크 구성](lync-server-2013-configuring-trunks.md)

토폴로지 작성기를 사용하여 독립 실행형 풀에 중재 서버를 정의하고 게시한 경우 다음과 같은 콘텐츠를 사용할 수 있습니다.

  - [Lync Server 2013에 대한 Enterprise Voice 필수 구성 요소](lync-server-2013-enterprise-voice-prerequisites.md)에 설명된 대로 토폴로지가 소프트웨어 및 환경 필수 구성 요소를 충족하는지 확인합니다.

## 이 섹션의 내용

   [Lync Server 2013에 대한 Enterprise Voice 필수 구성 요소](lync-server-2013-enterprise-voice-prerequisites.md)

   [Lync Server 2013에서 중재 서버 배포 및 피어 정의](lync-server-2013-deploying-mediation-servers-and-defining-peers.md)

   [Lync Server 2013에서 트렁크 구성](lync-server-2013-configuring-trunks.md)

   [Lync Server 2013에서 다이얼 플랜 구성](lync-server-2013-configuring-dial-plans.md)

   [Lync Server 2013에서 음성 정책, PSTN 사용 레코드 및 음성 경로 구성](lync-server-2013-configuring-voice-policies-pstn-usage-records-and-voice-routes.md)

   [Lync Server 2013에서 음성 라우팅 구성 내보내기 및 가져오기](lync-server-2013-exporting-and-importing-voice-routing-configuration.md)

   [Lync Server 2013에서 음성 라우팅 테스트](lync-server-2013-test-voice-routing.md)

   [Lync Server 2013에서 음성 라우팅 구성에 보류 중인 변경 사항 게시](lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md)

   [Lync Server 2013 음성 메일을 제공하도록 온-프레미스 Exchange UM 배포](lync-server-2013-deploying-on-premises-exchange-um-to-provide-lync-server-2013-voice-mail.md)

   [호스팅된 Exchange UM에서 Lync Server 2013 사용자 음성 메일 제공](lync-server-2013-providing-lync-server-users-voice-mail-on-hosted-exchange-um.md)

   [Exchange Online과 온-프레미스 Lync Server 2013 통합 구성](lync-server-2013-configuring-on-premises-lync-server-integration-with-exchange-online.md)

   [Lync Server 2013에서 고급 Enterprise Voice 기능 배포](lync-server-2013-deploying-advanced-enterprise-voice-features.md)
    
  - [Lync Server 2013의 네트워크 지역, 사이트 및 서브넷 정보](lync-server-2013-about-network-regions-sites-and-subnets.md)
  
  - [Lync Server 2013에서 네트워크 지역 만들기 또는 수정](lync-server-2013-create-or-modify-a-network-region.md)
  
  - [Lync Server 2013에서 네트워크 사이트 만들기 또는 수정](lync-server-2013-create-or-modify-a-network-site.md)
  
  - [Lync Server 2013 에서 네트워크 사이트에 서브넷 연결](lync-server-2013-associate-a-subnet-with-a-network-site.md)
  
  - [Lync Server 2013에서 통화 허용 제어 서비스 구성](lync-server-2013-configure-call-admission-control.md)
  
  - [Lync Server 2013에서 고급 9-1-1 구성](lync-server-2013-configure-enhanced-9-1-1.md)
  
  - [Lync Server 2013에서 미디어 바이패스 구성](lync-server-2013-configure-media-bypass.md)

   [Lync Server 2013에서 사용자가 Enterprise Voice를 사용할 수 있도록 설정](lync-server-2013-enable-users-for-enterprise-voice.md)

## 참고 항목

#### 기타 리소스

[Lync Server 2013에서 분기 사이트 배포](lync-server-2013-deploying-branch-sites.md)  
[Lync Server 2013에서 전화 접속 회의 구성](lync-server-2013-configuring-dial-in-conferencing.md)  
[Lync Server 2013에서 통화 대기 구성](lync-server-2013-configuring-call-park.md)  
[Lync Server 2013에서 지정되지 않은 번호에 대한 알림 구성](lync-server-2013-configuring-announcements-for-unassigned-numbers.md)  
[Lync Server 2013의 모니터링 배포](lync-server-2013-deploying-monitoring.md)

