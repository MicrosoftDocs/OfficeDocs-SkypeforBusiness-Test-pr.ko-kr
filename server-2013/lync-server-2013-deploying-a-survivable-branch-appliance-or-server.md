---
title: 'Lync Server 2013: SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버 배포'
TOCTitle: SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버 배포
ms:assetid: cb780c14-dc5f-41ba-8092-f20ae905bd16
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398849(v=OCS.15)
ms:contentKeyID: 49305044
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013을 통해 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버 배포

 

_**마지막으로 수정된 항목:** 2014-12-10_

복구 Enterprise Voice는 분기 사이트 복구 즉 중앙 사이트에 대한 링크를 사용할 수 없는 경우 분기 사이트 사용자에게 중단 없이 Enterprise Voice 서비스를 제공하는 기능을 의미합니다.

25-1,000명의 사용자가 있는 중소 규모의 분기 사이트에서는 전화 통신 서비스 공급자에 대해 기본 제공되는 PSTN 게이트웨이나 SIP 트렁크를 사용하여 PSTN(공중 전화망) 통화를 종료하는 SBA(Survivable Branch Appliance)를 배포하는 것이 좋습니다. SBA(Survivable Branch Appliance)는 단일 어플라이언스 섀시에서 Windows Server 2008 R2 운영 체제, Lync Server 2013 등록자, 중재 서버 소프트웨어 및 PSTN 게이트웨이를 모두 실행하는 블레이드 서버가 포함된 타사 장치입니다.

1,000 ~ 5,000의 사용자가 있고 복구 WAN이 없는 분기 사이트에서는 전화 통신 서비스 공급자에 대해 PSTN 게이트웨이나 SIP 트렁크에 연결된 지속 가능 분기 서버를 배포하는 것이 좋습니다. 지속 가능 분기 서버는 등록자 및 중재 서버 소프트웨어가 설치된 Windows Server 기반 컴퓨터입니다.


> [!NOTE]
> 5,000명 이상의 사용자 및 전용 Lync Server 관리자가 있는 분기 사이트에서는 중앙 사이트의 배포와는 별개로 전체 Lync Server 2013 배포를 수행하는 것이 좋습니다.<BR>사전 요구 사항 및 계획 고려 사항을 포함하여 조직의 분기 사이트에 대한 최상의 복구 솔루션을 선택하는 방법에 대한 자세한 내용은 계획 설명서에서 <A href="lync-server-2013-branch-site-resiliency-requirements.md">Lync Server 2013에 대한 분기 사이트 복구 요구 사항</A> 섹션을 참조하십시오.



## 이 단원의 내용

  - [Lync Server 2013을 통해 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버 배포 - 중앙 사이트 작업](lync-server-2013-deploying-a-survivable-branch-appliance-or-server-central-site-tasks.md)

  - [Lync Server 2013을 통해 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버 배포 - 분기 사이트 작업](lync-server-2013-deploy-a-survivable-branch-appliance-or-server-branch-site-task.md)

  - [Lync Server 2013에서 분기 사이트 복원을 위한 사용자 구성](lync-server-2013-configuring-users-for-branch-site-resiliency.md)

  - [Lync Server 2013의 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버에 사용자 두기](lync-server-2013-home-users-on-a-survivable-branch-appliance-or-server.md)

  - [부록: Lync Server 2013의 SBA(Survivable Branch Appliance) 및 지속 가능 분기 서버](lync-server-2013-appendices-survivable-branch-appliances-and-servers.md)

## 참고 항목

#### 기타 리소스

[Lync Server 2013 배포](lync-server-2013-deploying-lync-server.md)

