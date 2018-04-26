---
title: 'Lync Server 2013: Enterprise Voice 배포 지침'
TOCTitle: Enterprise Voice 배포 지침
ms:assetid: 8985bd93-7613-4cef-9c89-51df6049ed9b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398694(v=OCS.15)
ms:contentKeyID: 49304302
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 Enterprise Voice 배포 지침

 

_**마지막으로 수정된 항목:** 2012-09-21_

이 항목에서는 Lync Server 2013 및 Enterprise Voice 작업 부하를 배포하려고 계획할 때 고려해야 할 필요 조건 및 기타 지침에 대해 설명합니다.

## 배포 필요 조건

Enterprise Voice 배포 환경을 최적화하려면 IT 인프라, 네트워크 및 시스템이 다음 필요 조건을 충족하는지 확인합니다.

  - Lync Server 2013 Standard Edition 또는 Enterprise Edition이 네트워크에 설치되어 있으며 작동합니다.

  - 경계 네트워크에 모든 에지 서버가 배포되어 작동 중이어야 합니다( 액세스 에지 서비스, A/V 에지 서비스, 웹 회의 에지 서비스 및 역방향 프록시가 있는 에지 서버 포함).

  - Lync Server에 대해 한 명 이상의 사용자를 만들고 사용하도록 설정했습니다.

  - Microsoft Exchange Server 2007 SP1(서비스 팩 1) 또는 최신 서비스 팩 또는 Microsoft Exchange Server 2010이 설치되어 있어야 합니다. Exchange 통합 메시징(UM)을 Lync Server와 통합하고 다양한 알림 및 통화 기록 정보를 클라이언트 끝점에 제공하려면 이들 중 하나가 필요합니다.

  - Enterprise Voice를 사용할 수 있는 각 사용자의 고유한 기본 전화 번호가 지정되고 정규화되어 **msRTCSIP-line** 특성에 복사되어 있어야 합니다.
    

    > [!NOTE]
    > Lync Server는 E.164 번호 및 DID(Direct Inward Dialing)가 아닌 번호를 지원합니다. DID가 아닌 번호는 <STRONG>&lt;E.164&gt;;ext=&lt;extension&gt;</STRONG> 형식 또는 숫자 문자열로 나타낼 수 있습니다. 단, 개인 내선 번호는 엔터프라이즈 전체에서 고유해야 합니다. 예를 들어 개인 번호 1001은 <STRONG>+1425550100;ext=1001</STRONG> 또는 <STRONG>1001</STRONG>로 나타낼 수 있습니다. <STRONG>1001</STRONG>로 나타낼 경우 이 개인 번호는 엔터프라이즈 전체에서 고유한 번호로 간주됩니다.



  - Enterprise Voice를 배포하는 관리자는 RTCUniversalServerAdmins 그룹의 구성원이어야 합니다.

  - 적어도 Office Communicator 2007은 성공적으로 배포되어 있어야 합니다. 이 버전의 새 기능을 사용하려면 Lync 2013이 배포되어 있어야 합니다.

  - Microsoft 또는 타사 CA(인증 기관) 인프라를 사용하여 MKI(관리 키 인프라)가 배포 및 구성되었습니다.

  - 중재 서버를 설치하는 각 컴퓨터는 다음 요구 사항을 충족해야 합니다.
    
      - 도메인의 구성원 서버이며 Active Directory 도메인 서비스에 대해 준비되어야 합니다. Active Directory 도메인 서비스 준비 절차에 대해서는 배포 설명서의 [Lync Server 2013에 대한 Active Directory 도메인 서비스 준비](lync-server-2013-preparing-active-directory-domain-services.md)를 참조하십시오.
    
      - 다음 운영 체제 중 하나를 실행합니다.
        
          -   
            Windows Server 2008 Standard 운영 체제 64비트 버전
        
          -   
            Windows Server 2008 Enterprise 운영 체제 64비트 버전

  - TDM(Time Division Multiplexing) 연결을 통해 PSTN(공중 전화망) 또는 PBX(Private Branch Exchange)에 연결된 경우에는 하나 이상의 PSTN 게이트웨이를 배포에 사용할 수 있습니다. SIP 트렁크를 통해 연결된 경우에는 PSTN 게이트웨이가 필요하지 않습니다.

## 전원, 네트워크 또는 전화 서비스 중단

사용 지역에서 정전, 방해 또는 기타 전원, 네트워크, 전화 서비스 저하가 발생할 경우 Lync Server의 음성, 인스턴트 메시징, 현재 상태 및 기타 기능과 Lync Server에 연결된 장치가 제대로 작동하지 않을 수 있습니다.

## Enterprise Voice는 서버 가용성과 음성 클라이언트 및 하드웨어 운용성에 의존함

Lync Server를 통해 음성으로 통신하려면 서버 소프트웨어를 사용할 수 있고 음성 클라이언트 또는 서버 소프트웨어에 연결하는 하드웨어 전화 장치가 제대로 작동해야 합니다.

## 긴급 서비스에 액세스하기 위한 대체 수단

음성 클라이언트(예: Lync 클라이언트 또는 Lync Phone Edition 장치를 실행 중인 PC)를 설치하는 위치에 대해서는 정전, 네트워크 연결 저하, 전화 서비스 중단 또는 Lync Server, Lync 또는 Lync Phone Edition 장치의 작동을 제지할 수 있는 기타 문제에 대비하여 사용자가 긴급 서비스(예: 119 등)에 통화할 수 있는 백업 옵션을 유지 관리하는 것이 좋습니다. 이러한 대체 옵션은 표준 PSTN(공중 전화망) 회선이나 휴대폰에 연결된 전화기를 포함할 수 있습니다.

## 긴급 통화 및 다중 회선 전화 시스템

MLTS(다중 회선 전화 시스템)를 사용할 경우 미국의 주법이나 연방법 또는 기타 국가/지역의 법률을 따라야 합니다. 해당 법률은 긴급 서비스에 전화를 걸 때(예: 119와 같은 긴급 전화 번호로 전화를 걸 때) MLTS가 발신자의 전화 번호, 내선 번호 및/또는 실제 위치를 해당 긴급 서비스에 제공하도록 요구합니다. 이 릴리스에서는 [Lync Server 2013의 응급 서비스 계획(E9-1-1)](lync-server-2013-planning-for-emergency-services-e9-1-1.md)에 설명된 대로 발신자의 실제 위치를 긴급 서비스 공급자에 제공하도록 Lync Server을 구성할 수 있습니다. MLTS 법률을 준수하는 것은 전적으로 Lync Server, Lync 클라이언트 및 Lync Phone Edition 장치를 구입한 사람의 책임입니다.

