---
title: 'Lync Server 2013: 전화 접속 회의 구성 필수 구성 요소 및 권한'
TOCTitle: 전화 접속 회의 구성 필수 구성 요소 및 권한
ms:assetid: b3b251e5-78ac-44a2-8c36-2a061c9b2314
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412865(v=OCS.15)
ms:contentKeyID: 49304775
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 전화 접속 회의 구성 필수 구성 요소 및 권한

 

_**마지막으로 수정된 항목:** 2012-06-20_

전화 접속 회의는 Lync Server 2013 회의 작업의 선택적인 구성 요소입니다. 토폴로지 작성기를 사용하여 토폴로지를 설계한 다음 프런트 엔드 풀 또는 Standard Edition Server를 설정하는 경우 전화 접속 회의를 구성하기 전에 설치해야 하는 구성 요소가 배포됩니다. 이 항목에서는 전화 접속 회의를 구성하기 전에 완료해야 하는 작업에 대해 설명합니다.

이 섹션에서는 회의 작업 및 전화 접속 회의와 관련된 계획 섹션을 자세히 읽어 보았다고 가정합니다.

## 전화 접속 회의 구성 필요 조건

전화 접속 회의에는 다음과 같은 Lync Server 2013 구성 요소가 필요합니다.

  - UCAS(통합 통신 응용 프로그램 서비스)( *응용 프로그램 서비스* 라고 함)

  - 회의 길잡이 응용 프로그램

  - 회의 알림 응용 프로그램

  - 전화 접속 회의 설정 웹 페이지

  - Lync Server 2013 중재 서버와 PSTN 게이트웨이 각각 하나 이상

토폴로지 작성기를 사용하여 토폴로지를 정의하고 게시한 다음 프런트 엔드 풀 또는 Standard Edition Server를 배포하는 경우 이러한 구성 요소를 배포합니다. Enterprise Voice를 배포하는 경우 전화 접속 회의를 구성하기 전에 배포해야 합니다. Enterprise Voice를 배포하지 않는 경우 프런트 엔드 풀 또는 Standard Edition Server를 배포할 때 중재 서버 및 PSTN(공중 전화망) 게이트웨이를 배포할 수 있습니다.


> [!NOTE]
> Office Communications Server 2007 R2를 Lync Server 2013으로 업그레이드하는 경우 Lync Server 2013 회의를 호스팅하는 데 사용할 모든 풀에 전화 접속 회의를 배포합니다. 전화 접속 회의 마이그레이션에 대한 자세한 내용은 <A href="migration-from-office-communications-server-2007-r2-to-lync-server-2013.md">Office Communications Server 2007 R2에서 Lync Server 2013으로 마이그레이션</A>을 참조하십시오.



이 섹션에서는 다음을 완료했다고 가정합니다.

  - Office Communications Server 2007 R2 환경에 최신 업데이트를 적용했습니다( Lync Server 2013으로 마이그레이션하는 경우).

  - 토폴로지 작성기를 사용하여 토폴로지를 설계하고 구성했습니다. 회의 작업을 지정할 때 전화 접속 회의 옵션을 선택했습니다. 토폴로지 정의에 대한 자세한 내용은 배포 설명서에서 [Lync Server 2013에서 토폴로지 정의 및 구성](lync-server-2013-defining-and-configuring-the-topology.md)을 참조하십시오.

  - 토폴로지를 게시하고 프런트 엔드 풀 또는 Standard Edition Server를 설정했습니다. 토폴로지 게시 및 Lync Server 2013 설치에 대한 자세한 내용은 배포 설명서에서 [Lync Server 2013 배포](lync-server-2013-deploying-lync-server.md)를 참조하십시오.
    

    > [!NOTE]
    > 게시된 토폴로지를 설치하면 프런트 엔드 서버 또는 Standard Edition Server에 웹 서비스의 일부로 전화 접속 회의 설정 웹 페이지가 설치됩니다.

    

    > [!IMPORTANT]
    > Lync Server 2013을 배포한 후 토폴로지 작성기에서 파일 저장소의 경로를 변경한 경우 새 경로를 사용하도록 회의 길잡이 및 회의 알림 응용 프로그램을 재시작해야 합니다.



  - Enterprise Voice를 배포했습니다. Enterprise Voice를 배포하지 않는 경우 Enterprise Edition 프런트 엔드 서버 또는 Standard Edition Server에 중재 서버를 배포하거나 독립 실행형 중재 서버 및 PSTN 게이트웨이를 배포했습니다. Enterprise Voice 배포에 대한 자세한 내용은 배포 설명서에서 [Lync Server 2013에서 Enterprise Voice 배포](lync-server-2013-deploying-enterprise-voice.md)를 참조하십시오. 독립 실행형 중재 서버 및 PSTN 게이트웨이 설치에 대한 자세한 내용은 배포 설명서에서 [Lync Server 2013에서 중재 서버 배포 및 피어 정의](lync-server-2013-deploying-mediation-servers-and-defining-peers.md)를 참조하십시오.

다음 순서도에서는 전화 접속 회의를 구성하기 전에 수행해야 하는 단계 및 전화 접속 회의를 구성하기 위해 수행하는 단계를 보여 줍니다.

**전화 접속 회의 배포**

![전화 접속 회의 배포 순서도](images/Gg412865.fde8c246-b5ed-4323-a6e7-af1983a5ec86(OCS.15).jpg "전화 접속 회의 배포 순서도")

## 전화 접속 회의 권한

전화 접속 회의를 구성하려면 다음과 같은 관리 도구를 사용해야 합니다.

  - Lync Server 2013 제어판

  - Lync Server 관리 셸

이러한 관리 도구를 사용하여 전화 접속 회의 설정 및 다이얼 플랜, 정책 및 기타 전화 접속 회의에 필요한 설정을 구성합니다.

전화 접속 회의를 구성하려면 작업에 따라 다음과 같은 관리 역할이 필요합니다.

  - **CsVoiceAdministrator**   이 관리자 역할은 음성 관련 설정 및 정책을 만들고 구성하고 관리할 수 있습니다.

  - **CsUserAdministrator**   이 관리자 역할은 사용자가 Lync Server를 사용하거나 사용하지 않도록 설정하고, 회의 정책 및 PIN 정책과 같은 기존 정책을 사용자에게 할당할 수 있습니다.

  - **CsAdministrator**   이 관리자 역할은 CsVoiceAdministrator 및 CsUserAdministrator의 모든 작업을 수행할 수 있습니다.

## 참고 항목

#### 개념

[Lync Server 2013에서 Enterprise Voice 배포](lync-server-2013-deploying-enterprise-voice.md)

