---
title: 'Lync Server 2013: 원격 통화 제어 계획'
TOCTitle: 원격 통화 제어 계획
ms:assetid: 688a0328-1aa7-449f-b5f7-98c876112ed2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg558658(v=OCS.15)
ms:contentKeyID: 49303905
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 원격 통화 제어 계획

 

_**마지막으로 수정된 항목:** 2012-09-05_

Lync Server 2013에서는 원격 통화 제어 시나리오가 지원되므로 사용자가 데스크톱 컴퓨터에서 Lync 2013을 사용하여 PBX(Private Branch Exchange) 전화를 제어할 수 있습니다. 이 섹션에서는 원격 통화 제어 기능과 원격 통화 제어 배포를 위한 요구 사항에 대해 설명합니다.

PBX와 Lync Server 2013을 통합하면 원격 통화 제어를 사용할 수 있도록 설정된 사용자가 Lync 2013 UI(사용자 인터페이스)를 사용하여 다음과 같은 방식으로 PBX 전화에서 통화를 제어할 수 있습니다.


> [!NOTE]
> 궁극적으로, 사용자에게 제공되는 원격 통화 제어 기능은 해당 사용자의 PBX 전화를 호스팅하는 PBX 기능을 통해 결정됩니다.



  - 발신 전화 걸기

  - 수신 전화에 응답

  - 수신 전화에 인스턴트 메시지로 응답하기
    

    > [!NOTE]
    > 발신자의 전화 번호를 조직의 GAL(전체 주소 목록), 수신자의 Lync 연락처 목록 또는 페더레이션 파트너의 조직에서 인스턴트 메시지 주소에 연결할 수 있는 경우입니다.



  - 통화 전송

  - 수신 전화 착신 전환

  - 통화 대기

  - 여러 동시 통화 번갈아 받기

  - 통화 중인 상태에서 두 번째 전화 받기(통화 대기)

  - DTMF(Dual-tone Multifrequency) 번호로 전화 걸기

  - 대화 창에서 Microsoft Office OneNote 메모 작성 프로그램에서 메모 작성

또한, 사용자가 원격 통화 제어를 사용할 수 있도록 설정된 경우 Lync 2013에서는 다음과 같은 통화 정보를 사용자에게 제공합니다.

  - 발신자 전화 번호가 원격 통화 제어를 사용하도록 설정된 사용자의 Microsoft Office Outlook 메시징 및 공동 작업 클라이언트, Lync 연락처 목록 또는 조직의 GAL에 있는 경우 이름별 발신자 번호

  - Outlook의 대화 내용 폴더에 저장된 과거의 수신 및 발신 전화

  - 사용자의 Outlook 받은 편지함 폴더로 전송되지만 수신 전화를 받을 때 Lync가 실행 중인 경우에만 생성되는 부재 중 전화 알림

## 원격 통화 제어 및 Enterprise Voice

원격 통화 제어 기능은 Enterprise Voice 기능과는 다른 별도의 기능이며 사용자가 두 기능을 모두 사용하도록 설정할 수는 없지만, Enterprise Voice는 원격 통화 제어를 사용하도록 설정된 사용자도 사용 가능한 기능 하위 집합을 제공합니다. Enterprise Voice가 배포된 경우 원격 통화 제어를 사용하도록 설정된 사용자는 Lync를 사용하여 다음의 Enterprise Voice 기능에 액세스할 수 있습니다.

  - 다른 Lync 클라이언트와 음성 전화 걸기/받기

  - Enterprise Voice를 사용하도록 설정된 사용자가 만든 회의의 오디오 부분에 참가

## 이 섹션의 내용

  - [Lync Server 2013의 원격 통화 제어에 대한 배포 작업](lync-server-2013-deployment-tasks-for-remote-call-control.md)

