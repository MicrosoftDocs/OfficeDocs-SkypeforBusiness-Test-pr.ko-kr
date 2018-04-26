---
title: 'Lync Server 2013: Lync Server와 함께 작동하도록 Microsoft Exchange Server의 통합 메시징 구성'
TOCTitle: Lync Server 2013과 함께 작동하도록 Microsoft Exchange Server의 통합 메시징 구성
ms:assetid: 058da9c4-23af-4ddb-9f63-70133a8aafc6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398106(v=OCS.15)
ms:contentKeyID: 49302681
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013과 함께 작동하도록 Microsoft Exchange Server의 통합 메시징 구성

 

_**마지막으로 수정된 항목:** 2012-10-11_


> [!IMPORTANT]
> Exchange 통합 메시징(UM)을 사용하여 통화 응답, Outlook Voice Access 또는 Enterprise Voice 사용자를 위한 자동 전화 교환 서비스를 제공하려면 계획 설명서에서 <A href="lync-server-2013-planning-for-exchange-unified-messaging-integration.md">Lync Server 2013의 Exchange 통합 메시징 통합 계획</A>을 읽은 후 이 섹션의 지침을 따르십시오.



Exchange 통합 메시징(UM)이 Enterprise Voice와 함께 작동하도록 구성하려면 다음 작업을 수행해야 합니다.

  - Exchange 통합 메시징(UM) 서비스를 실행하는 서버에서 인증서 구성
    

    > [!NOTE]
    > 모든 UM SIP URI 다이얼 플랜에 모든 클라이언트 액세스 및 사서함 서버 추가. 이렇게 하지 않으면 아웃바운드 통화 라우팅이 예상대로 작동하지 않습니다.



  - 하나 이상의 UM SIP URI 다이얼 플랜을 만들고 필요에 따라 구독자 액세스 전화 번호를 만든 다음 해당 Lync Server 다이얼 플랜 만들기

  - **exchucutil.ps1** 스크립트를 사용하여 다음 작업 수행
    
      - UM IP 게이트웨이 만들기
    
      - UM 헌트 그룹 만들기
    
      - UM Active Directory 도메인 서비스 개체를 읽을 수 있도록 Lync Server 2013 권한 부여

  - UM 자동 전화 교환 개체 만들기

  - 구독자 액세스 개체 만들기

  - 각 사용자에 대해 SIP URI를 만들고 UM SIP URI 다이얼 플랜에 사용자 연결

## 요구 사항 및 권장 사항

작업을 시작하기 전에, 이 섹션의 설명서에서는 Exchange 2013 역할인 클라이언트 액세스 및 사서함을 배포했다고 가정합니다. Microsoft Exchange Server 2013에서 Exchange UM은 이러한 서버의 서비스로 실행됩니다.

Exchange 2013을 배포하는 방법에 대한 자세한 내용은 Exchange 2013 TechNet 라이브러리( [http://go.microsoft.com/fwlink/?linkid=266637\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=266637%26clcid=0x412))를 참조하십시오.

또한 다음에 주의하십시오.

  - Exchange UM이 여러 포리스트에 설치되어 있으면 각 UM 포리스트에 대해 Exchange Server 통합 단계를 수행해야 합니다. 또한 각 UM 포리스트는 Lync Server 2013이 배포된 포리스트를 트러스트하도록 구성하고 Lync Server 2013이 배포된 포리스트는 각 UM 포리스트를 트러스트하도록 구성해야 합니다.

  - 통합 단계는 통합 메시징 서비스가 실행되는 Exchange Server 역할 및 Lync Server 2013을 실행하는 서버 둘 다에서 수행됩니다. Lync Server 2013 통합 단계를 수행하기 전에 Exchange Server 통합 메시징 통합 단계를 수행해야 합니다.
    

    > [!NOTE]
    > 각 서버에서 수행되는 통합 단계와 이때 사용되는 관리자 역할에 대한 자세한 내용은 <A href="lync-server-2013-deployment-process-for-integrating-on-premises-unified-messaging.md">온-프레미스 통합 메시징과 Lync Server 2013의 통합을 위한 배포 프로세스</A>를 참조하십시오.



Exchange UM을 실행하는 각 서버에서 다음 도구를 사용할 수 있어야 합니다.

  - Exchange 관리 셸

  - 다음 작업을 수행하는 스크립트 **exchucutil.ps1**
    
      - 각 Lync Server 2013에 대해 UM IP 게이트웨이 만들기
    
      - 각 게이트웨이에 대한 헌트 그룹 만들기. 각 헌트 그룹의 파일럿 식별자는 게이트웨이와 연결된 프런트 엔드 풀 또는 Standard Edition 서버에서 사용하는 UM SIP URI 다이얼 플랜을 지정합니다.
    
      - Active Directory 도메인 서비스에서 UM Exchange UM 개체를 읽을 수 있도록 Lync Server 2013 권한 부여

## 이 섹션의 내용

  - [Microsoft Exchange Server 통합 메시징을 실행하는 서버에서 인증서 구성](lync-server-2013-configure-certificates-on-the-server-running-microsoft-exchange-server-unified-messaging.md)

  - [Microsoft Exchange에서 Lync Server 2013용 통합 메시징 구성](lync-server-2013-configure-unified-messaging-on-microsoft-exchange.md)

