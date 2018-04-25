---
title: Lync Server 2013 회의의 구성 요소 및 토폴로지
TOCTitle: 회의의 구성 요소 및 토폴로지
ms:assetid: eb83052a-3360-4ba1-a6a0-6ee419942809
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399061(v=OCS.15)
ms:contentKeyID: 49305424
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 회의의 구성 요소 및 토폴로지

 

_**마지막으로 수정된 항목:** 2013-02-04_

토폴로지 작성기에서 회의를 선택하면 회의가 프런트 엔드 서버 또는 Standard Edition 서버의 일부로 배포됩니다. 전화 접속 회의 및 PowerPoint 공유에는 추가 구성 요소 및 구성이 필요합니다. 다음 섹션에서는 웹 회의, A/V 회의 및 전화 접속 회의에 지원되는 구성 요소 및 토폴로지에 대해 설명합니다.

## 지원되는 구성 요소

웹 회의 및 A/V 회의에 필요한 유일한 구성 요소는 조직의 프런트 엔드 서버 또는 Standard Edition 서버뿐입니다. 프런트 엔드 서버 및 Standard Edition 서버에 대한 하드웨어 및 소프트웨어 요구 사항 목록은 [Lync Server 2013에서 지원되는 하드웨어](lync-server-2013-supported-hardware.md) 및 [Lync Server 2013의 서버 소프트웨어 및 인프라 지원](lync-server-2013-server-software-and-infrastructure-support.md)을 참조하십시오.

Lync Server 2013에서는 Office Web Apps 및 Office Web Apps 서버를 사용하여 PowerPoint 프레젠테이션의 공유 및 렌더링을 처리합니다. Office Web Apps 서버 설치 및 구성에 대한 자세한 내용은 [Office Online Server 및 Lync Server 2013과 통합 구성](lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md)를 참조하십시오.

전화 접속 회의에는 웹 회의 및 A/V 회의에 대한 요구 사항 외에도 다음 Lync Server 2013 구성 요소가 사용됩니다.

  - **응용 프로그램 서비스**    응용 프로그램 서비스는 UC(통합 통신) 응용 프로그램의 배포, 호스트 및 관리를 위한 플랫폼을 제공합니다. 전화 접속 회의에서는 응용 프로그램 서비스가 필요한 두 UC(통합 통신) 응용 프로그램인 회의 길잡이 및 회의 알림을 사용합니다. 회의 작업을 배포하고 전화 접속 회의 옵션을 선택하면 프런트 엔드 풀의 프런트 엔드 서버와 Standard Edition 서버에서 응용 프로그램 서비스가 기본적으로 설치되고 활성화됩니다.

  - **회의 길잡이 응용 프로그램**    회의 길잡이 응용 프로그램는 PSTN(공중 전화망) 통화를 수락하고 프롬프트를 재생하고 통화를 A/V 회의에 참가시키는 통합 통신 응용 프로그램입니다. 회의 작업을 배포하고 전화 접속 회의 옵션을 선택하면 회의 길잡이 응용 프로그램가 기본적으로 설치되고 활성화됩니다.

  - **회의 알림 응용 프로그램**    회의 알림 응용 프로그램은 참가자가 회의에 참가하거나 회의에서 나가거나, 참가자가 음소거되거나 음소거 해제되거나, 누군가가 전화 회의 대기실에 들어오거나, 회의가 잠기거나 잠금 해제되는 등의 특정 동작에 대해 소리를 재생하고 PSTN 참가자에게 메시지를 표시하는 통합 통신 응용 프로그램입니다. 또한 회의 알림 응용 프로그램은 전화기 키패드의 DTMF(Dual-Tone Multifrequency) 명령을 지원합니다. 회의 작업을 배포하고 전화 접속 회의 옵션을 선택하면 회의 알림 응용 프로그램이 자동으로 설치되고 기본적으로 활성화됩니다.

  - **전화 접속 회의 설정 페이지**    전화 접속 회의 설정 페이지에는 사용 가능한 언어, 할당된 전화 회의 정보(즉, 예약할 필요가 없는 모임에 대한 정보) 및 전화 회의 내에서의 DTMF 제어와 함께 전화 회의 전화 접속 번호가 표시됩니다. 이 페이지에서 개인식별번호(PIN) 및 할당된 회의 정보를 관리할 수 있습니다. 전화 접속 회의 설정 페이지는 웹 서비스의 일부로서 자동으로 설치됩니다.

  - **Lync Server 2013, 중재 서버 및 중재 서버 및 PSTN 게이트웨이**   전화 접속 회의에는 Lync Server 2013과 PSTN 게이트웨이 간의 신호(일부 구성의 경우 미디어도 해당)를 변환하기 위한 중재 서버가 필요하며, 중재 서버와 PSTN 게이트웨이 간의 신호 및 미디어를 변환하기 위한 PSTN 게이트웨이도 필요합니다. 전화 접속 회의의 경우 하나 이상의 중재 서버와 다음 중 하나 이상을 배포해야 합니다.
    
      - PSTN 게이트웨이
    
      - IP-PBX
    
      - (SIP 트렁크를 구성하여 연결할 인터넷 전화 통신 서비스 공급자에 대한) SBC(세션 경계 컨트롤러)
    

    > [!NOTE]
    > 또한 Enterprise Voice를 배포하는 경우에도 중재 서버 및 PSTN 게이트웨이가 Enterprise Voice 베포에 포함됩니다. Enterprise Voice를 배포하지 않으려는 경우 전화 접속 회의용으로 하나 이상의 중재 서버와 하나 이상의 PSTN 게이트웨이, IP-PBX 또는 SBC를 배포해야 합니다.



  - **파일 저장소**   파일 저장소는 녹음된 이름 오디오 파일에 사용됩니다. 파일 저장소는 모든 Enterprise Edition 또는 Standard Edition 배포에서 표준 구성 요소입니다.

  - **사용자 저장소**   사용자 저장소는 사용자 Lync Server 2013 PIN을 저장하는 데 사용됩니다. PIN은 해시됩니다. 사용자 저장소는 모든 Enterprise Edition 또는 Standard Edition 배포에서 표준 구성 요소입니다.

  - **Lync Server 제어판**    Lync Server 제어판을 사용하여 일부 전화 접속 설정을 구성할 수 있습니다.

  - **Lync Server 관리 셸**   모든 전화 접속 설정은 Lync Server 관리 셸 cmdlet을 사용하여 구성할 수 있습니다. Lync Server 관리 셸 cmdlet은 회의 길잡이 응용 프로그램 및 회의 알림 응용 프로그램의 배포, 구성, 실행, 모니터링 및 문제 해결에 사용할 수 있습니다. 특정 cmdlet에 대한 자세한 내용은 Lync Server 관리 셸 설명서를 참조하십시오.

## 지원되는 토폴로지

Lync Server 2013에서는 회의 서비스를 실행하는 서버가 항상 프런트 엔드 서버 또는 Standard Edition 서버와 함께 배치됩니다. 초기 배포 중에 토폴로지 작성기는 토폴로지에 회의를 포함할 수 있는 옵션을 제공합니다. 또한 토폴로지 작성기를 사용하여 기존 배포에 회의를 추가할 수도 있습니다. 자세한 내용은 [Lync Server 2013에서 토폴로지 정의 및 구성](lync-server-2013-defining-and-configuring-the-topology.md)을 참조하십시오.

## 전화 접속 회의 토폴로지

다음 토폴로지 및 구성에 전화 접속 회의를 배포할 수 있습니다.

  - Lync Server 2013Standard Edition

  - Lync Server 2013Enterprise Edition

  - Enterprise Voice 사용/사용 안 함

중앙 사이트에는 응용 프로그램 서비스, 회의 길잡이 응용 프로그램 및 회의 알림 응용 프로그램을 배포할 수 있지만 분기 사이트에는 배포할 수 없습니다.


> [!NOTE]
> 전화 접속 회의를 배포하려면 Lync Server 2013 회의를 배포한 모든 풀에 배포해야 합니다. 풀마다 액세스 번호를 할당할 필요는 없지만 전화 접속 회의 기능은 모든 풀에 배포해야 합니다. 이 요구 사항은 사용자가 하나의 풀에서 액세스 번호로 전화를 걸어 다른 풀의 Lync Server 2013 전화 회의에 참가할 때 녹음된 이름 기능을 지원합니다.



## Lync Server 2013 및 Office Web Apps에 지원되는 토폴로지

Lync Server 2013에서는 Office Web Apps 서버를 구성할 수 있는 다음 방법을 제공합니다. 필요에 따라 다음을 수행할 수 있습니다.

  - **Lync Server 2013 및 Office Web Apps 서버 모두를 조직의 방화벽 뒤와 동일 네트워크 영역 내에 온-프레미스로 설치합니다.** 이 토폴로지를 사용하면 Office Web Apps 서버에 대한 외부 액세스가 역방향 프록시 서버를 통해 제공됩니다. Lync Server 2013 및 Office Web Apps 서버(또는 Office Web Apps 서버 팜)가 모두 온-프레미스로 조직의 방화벽 뒤에 설치됩니다. 되도록 Lync Server와 동일한 네트워크 영역 안에 Office Web Apps 서버를 설치하는 것이 좋습니다.
    
    외부 Lync 클라이언트는 역방향 프록시 서버를 사용하여 Lync Server 2013와 Office Web Apps 서버에 연결할 수 있는데, 역방향 프록시 서버란 인터넷에서 요청을 받아서 내부 네트워크로 전달하는 서버를 말합니다. 내부 클라이언트는 Office Web Apps 서버에 직접 연결할 수 있으므로 역방향 프록시 서버를 사용할 필요가 없습니다. 이 토폴로지는 Lync Server 2013에만 사용되는 전용 Office Web Apps 서버를 사용하려는 경우에 매우 적합합니다.

  - **외부적으로 배포된 Office Web Apps 서버 사용**
    
    이 토폴로지에서는 Lync Server 2013이 온-프레미스로 배포되며 Lync Server 네트워크 영역 외부에 배포되는 Office Web Apps 서버를 사용합니다. Office Web Apps 서버가 기업의 여러 응용 프로그램 간에 공유되고 Lync Server가 있어야만 Office Web Apps 서버의 외부 인터페이스를 사용할 수 있는(반대의 경우도 포함) 네트워크에 배포되는 경우가 여기에 해당합니다.
    
    역방향 프록시 서버는 설치할 필요가 없습니다. 대신 Office Web Apps 서버에서 Lync Server 2013으로 전송되는 모든 요청이 에지 서버를 통해 라우팅됩니다. 내부 및 외부 Lync 클라이언트가 모두 외부 URL을 사용하여 Office Web Apps 서버에 연결됩니다.
    
    Office Web Apps 서버를 내부 방화벽의 외부에 배포하는 경우 토폴로지 작성기에서 **Office Web Apps 서버가 외부 네트워크(경계/인터넷)에 배포됨(Office Web Apps Server is deployed in an external network (that is, perimeter/Internet))** 옵션을 선택합니다. 자세한 내용은 [Office Online Server 및 Lync Server 2013과 통합 구성](lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md)을 참조하십시오.

선택하는 토폴로지와 관계 없이 올바른 방화벽 포트를 열어야 하며 Office Web Apps 서버, 부하 분산 또는 Lync Server에서 DNS 이름, IP 주소 및 포트가 방화벽에 의해 차단되지 않는지 확인해야 합니다.


> [!NOTE]
> Office Web Apps 서버에 대한 외부 액세스를 제공할 수 있는 또 한 가지 옵션은 경계 네트워크에 서버를 배포하는 것입니다. 이 방법을 선택할 경우 Office Web Apps 서버 설정 시 서버 컴퓨터가 Active Directory 도메인의 구성원이어야 합니다. 네트워크 정책에서 경계 네트워크의 컴퓨터가 Active Directory 도메인에 가입하는 것을 허용하지 않을 경우에는 경계 네트워크에 Office Web Apps 서버를 설치하지 않는 것이 좋습니다. 대신 내부 네트워크에 Office Web Apps 서버를 설치하고 역방향 프록시 서버를 통해 외부 사용자 액세스를 제공해야 합니다.


