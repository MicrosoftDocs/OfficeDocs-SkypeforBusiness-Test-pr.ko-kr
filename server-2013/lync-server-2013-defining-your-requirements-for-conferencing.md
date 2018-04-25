---
title: 'Lync Server 2013: 회의 요구 사항 정의'
TOCTitle: 회의 요구 사항 정의
ms:assetid: 5c83e268-22bf-42b2-bac3-3237b5e02e03
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204935(v=OCS.15)
ms:contentKeyID: 49303764
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 회의 요구 사항 정의

 

_**마지막으로 수정된 항목:** 2012-09-30_

배포할 회의 기능을 확인할 때는 사용자에게 제공하려는 기능 및 네트워크 대역폭 기능을 고려해야 합니다. 다음 질문 목록에 따라 회의 계획 프로세스에서 조직의 요구 사항을 기반으로 배포해야 하는 회의 기능을 확인하십시오.

  - **문서 공동 작업 및 응용 프로그램 공유가 포함된 웹 회의를 사용하려고 하십니까?**
    
    그렇다면 Microsoft Lync Server 2013, 계획 도구 또는 토폴로지 작성기에서 프런트 엔드 풀에 대해 회의를 사용하도록 설정해야 합니다. 회의를 사용하도록 설정할 때는 웹 회의와 A/V 회의를 모두 사용하도록 설정합니다.
    
    응용 프로그램 공유에는 문서 공동 작업보다 더 많은 네트워크 대역폭이 필요합니다. Lync Server 2013에서는 각 응용 프로그램 공유 세션을 제어하는 제한 메커니즘을 제공합니다. 기본적으로 대역폭 제한은 세션당 1.5KB/초로 설정됩니다.
    
    문서 공동 작업을 수행하되, 응용 프로그램 공유를 사용하지 않으려면 회의를 활성화하고 모임 정책을 사용하여 응용 프로그램 공유를 사용하지 않도록 설정하면 됩니다. 모임 정책 구성에 대한 자세한 내용은 [Lync Server 2013의 회의 정책](lync-server-2013-conferencing-policies.md)을 참조하십시오.
    
    사용자가 PowerPoint 프레젠테이션을 공유할 수 있도록 설정하려면 Office Web Apps 서버를 구성해야 합니다. Office Web Apps 서버 구성에 대한 자세한 내용은 [Office Online Server 및 Lync Server 2013과 통합 구성](lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md)을 참조하십시오.

  - **A/V 회의를 사용하려고 하십니까?**
    
    그렇다면 Lync Server 2013, 계획 도구 또는 토폴로지 작성기에서 프런트 엔드 풀에 대해 회의를 사용하도록 설정해야 합니다. 회의를 사용하도록 설정할 때는 웹 회의와 A/V 회의를 모두 사용하도록 설정합니다.
    
    A/V 회의에는 웹 회의(문서 공동 작업 및 응용 프로그램 공유 포함)보다 더 많은 네트워크 대역폭이 필요합니다. 웹 회의를 수행하되, A/V 회의를 사용하지 않으려면 회의를 활성화하고 모임 정책을 사용하여 A/V 전화 회의를 사용하지 않도록 설정하면 됩니다.
    
    화상 회의는 사용하지 않고 오디오 회의만 사용하려면 A/V 회의를 활성화하고 모임 정책을 사용하여 화상 회의를 사용할 수 없도록 설정하면 됩니다. 또는 A/V 회의를 사용하고 특정 사용자만 A/V 전화 회의를 시작하거나 A/V 전화 회의에 참가하도록 설정할 수 있습니다.
    

    > [!NOTE]
    > A/V 회의를 사용하기 위해서는 Enterprise Voice가 필요하지 않습니다. A/V 회의를 사용하도록 설정하면 전화 솔루션에 PBX를 사용하는 경우에도 오디오 장치가 있는 사용자는 자신의 전화 회의에 오디오를 추가할 수 있습니다.



  - **사용자가 PSTN 전화를 사용하여 전화 회의의 오디오 부분에 참가할 수 있도록 설정하시겠습니까?**
    
    그렇다면 전화 접속 회의를 배포하고 활성화해야 합니다. 그러면 조직 내부 및 외부의 초대 받은 사용자가 PSTN 전화를 사용하여 전화 회의의 오디오 부분에 참가할 수 있습니다.

  - **특정 전화 회의 유형을 사용하도록 설정한 경우 외부 사용자가 Lync Server 2013 클라이언트를 사용하여 이러한 전화 회의 유형에 참가하도록 설정하시겠습니까?**
    
    그렇다면 에지 서버를 배포해야 합니다. 외부 참가자가 모임에 참가하도록 허용하면 Lync Server 2013에 대한 투자가 극대화됩니다. 예를 들어 Lync Server 2013이 설치된 랩톱 사용자가 가정이나 공항 또는 고객 사이트 등 어디에서든 전화 회의에 참가할 수 있습니다.
    
    또한 에지 서버를 배포하면 고객 및 공급업체와 같은 다른 조직과 페더레이션 관계를 만들 수 있으며 이러한 조직의 사용자가 회사 내부의 사용자와 보다 쉽게 공동 작업할 수 있습니다.
    
    에지 서버 배포에 대한 자세한 내용은 [Lync Server 2013의 외부 사용자 액세스 계획](lync-server-2013-planning-for-external-user-access.md) 및 [Lync Server 2013에서 외부 사용자 액세스 배포](lync-server-2013-deploying-external-user-access.md)를 참조하십시오. Office Web Apps 서버에서 외부 액세스를 사용하도록 설정하는 방법에 대한 자세한 내용은 [역방향 프록시 서버를 사용하여 Lync Server 2013에서 Office Online Server 서버 게시](lync-server-2013-publishing-office-web-apps-server-using-a-reverse-proxy-server.md)를 참조하십시오.

  - **Lync Server 2013 모임에 참가할 수 있는 클라이언트를 제어하시겠습니까?**
    
    그렇다면 지원할 클라이언트 옵션만 사용할 수 있도록 모임 참가 페이지를 구성해야 합니다. 사용자가 예약된 모임에 참가하기 위해 링크를 클릭할 때마다 Lync Server 2013에서 클라이언트가 컴퓨터에 이미 설치되어 있는지 여부를 감지합니다. 그런 다음 기본 클라이언트를 시작하고 대체 클라이언트에 대한 링크가 포함된 모임 참가 페이지를 엽니다. 모임 참가 페이지에는 항상 Microsoft Lync Web App을 사용할 수 있는 옵션이 포함되어 있습니다. 이 옵션 외에 Attendee 및 이전 버전의 Communicator에 대한 링크를 포함할지 여부를 결정할 수 있습니다. 자세한 내용은 [Lync Server 2013에서 모임 참가 페이지 구성](lync-server-2013-configuring-the-meeting-join-page.md)을 참조하십시오.

## 이 단원의 내용

  - [웹 회의 요구 사항](lync-server-2013-web-conferencing-requirements.md)

  - [A/V 회의 요구 사항](lync-server-2013-a-v-conferencing-requirements.md)

  - [Lync Server 2013의 전화 접속 회의 요구 사항](lync-server-2013-dial-in-conferencing-requirements.md)

## 참고 항목

#### 기타 리소스

[Lync Server 2013의 회의 계획](lync-server-2013-planning-for-conferencing.md)  
[Lync Server 2013의 회의에 대한 배포 검사 목록](lync-server-2013-deployment-checklist-for-conferencing.md)

