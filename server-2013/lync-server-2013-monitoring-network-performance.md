---
title: 'Lync Server 2013: 네트워크 성능 모니터링'
TOCTitle: 네트워크 성능 모니터링
ms:assetid: bc3a01da-91eb-4c0c-9598-35e5e46b00f6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn720923(v=OCS.15)
ms:contentKeyID: 62240125
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 네트워크 성능 모니터링

 

_**마지막으로 수정된 항목:** 2015-08-17_

Lync Server 2013은 사용자가 메신저, 음성 통화 또는 비디오 통신을 통해 서로 통신할 수 있도록 많은 양의 네트워크를 사용하는 실시간 통신 기술입니다. 따라서 사용자가 선택한 통신 형식을 통해 가능한 최상의 환경을 활용할 수 있도록 하려면 네트워크 성능을 지속적으로 모니터링하는 것이 중요합니다.

네트워크 성능은 다음 두 가지 수준으로 측정할 수 있습니다.

  - **전체 네트워크 성능**   이 성능 측정 수준에서는 조직이 해당 네트워크를 대략적으로 볼 수 있으며, 이 성능 측정 수준은 대개 타사 네트워크 모니터링 시스템을 통해 구현됩니다. 이러한 시스템은 라우터와 같은 원격 네트워크 장치에서 성능 및 용량 데이터를 받고 네트워크 전체에서 전환되어 관리자가 일과 중 언제든지 주어진 모든 네트워크의 상태를 확인할 수 있도록 합니다.

  - **개별 서버 성능**   이 성능 측정 수준은 특정 서버로 제한되며, 관리자가 특정한 성능 문제를 해결하거나 용량 계획 프로세스의 일환으로 주어진 기간 동안 해당 서버의 성능을 평가할 수 있도록 특정 서버의 네트워크 성능을 평가하는 데 도움이 됩니다.

다음 섹션에 설명된 도구를 사용하여 네트워크를 모니터링할 수 있습니다.

## 전체 네트워크 성능 모니터링을 위한 도구

## System Center Operations Manager 2012

System Center Operations Manager는 IT 환경 전체에서 서비스 수준을 높이기 위해 손쉽게 사용자 지정하고 확장할 수 있는 종단 간 서비스 관리를 제공합니다. 이를 통해 운영 및 IT 관리 팀에서는 배포된 IT 서비스의 상태에 영향을 미치는 문제를 식별하고 해결할 수 있습니다. 종단 간 서비스 관리는 Microsoft 기반 환경에만 국한되지 않습니다. WS-Management(Web Services for Management), SNMP(Simple Network Management Protocol), 파트너 솔루션이 지원되므로 Microsoft 운영 체제 및 하드웨어를 실행하지 않는 시스템이 System Center Operations Manager 2012 내의 서비스 모니터링에 포함될 수 있습니다.

## System Center Operations Manager 2012 및 타사 네트워크 관리 솔루션

**EMC Smarts**   EMC Solutions for Operations Manager를 통해 서비스 수준 전반에 영향을 미치는 문제를 빠르게 해결할 수 있습니다. EMC Solutions for Operations Manager를 사용하면 자동화된 통합 솔루션 하나로 전체 IT 서비스 체인을 관리하고 모니터링할 수 있습니다. 성능 및 가용성 문제의 근본 원인을 손쉽게 식별하고 신속하게 해결함으로써 효율성이 높아집니다. 주요 이점은 다음과 같습니다.

  - 사용이 쉬운 고급 관리   다양한 경고를 수동으로 정렬하고 필터링하는 대신 전략적 비즈니스 가치를 제공하는 데 중점을 둡니다.

  - **신속한 해결**   IT 문제를 해결하고 비즈니스 요구 사항을 빠르게 충족하여 효율성을 높입니다.

  - **간소화된 작업**   여러 관리 도구, 응용 프로그램, 터미널을 결합하여 IT 복잡성을 방지합니다.

자세한 내용은 다음 항목에서 확인할 수 있습니다.

[Microsoft System Center Operations Manager](http://go.microsoft.com/fwlink/p/?linkid=243651)

[System Center Operations Manager의 솔루션](http://www.emc.com/collateral/software/data-sheet/h6135-server-manager-ds.pdf)

## 타사 솔루션

**HP Network Management Center(이전의 HP OpenView)**   [HP Network Management Center](https://h10078.www1.hp.com/cda/hpms/display/main/hpms_content.jsp?zn=bto%26cp=1-11-15-119_4000_100__)는 네트워크 가용성 및 성능을 높이기 위해 통합된 결함 및 성능 관리를 제공합니다. Network Management Center는 결함, 성능, 구성, 변경 관리를 통합하는 HP 자동 네트워크 관리 솔루션의 일부입니다.

**Cisco Network Management 및 자동화 제품**   CiscoWorks LAN Management Solution 및 Cisco Network Analysis Module을 비롯한 Cisco의 여러 가지 기업용 관리 제품을 사용하여 운영 효율성을 높이고 네트워크 가동 중지 시간은 줄일 수 있습니다. 이러한 제품에 대한 추가 데이터는 Cisco 웹 사이트([http://www.cisco.com/en/US/products/sw/netmgtsw/index.html](http://www.cisco.com/en/us/products/sw/netmgtsw/index.html))를 참조하세요.

SNMP(Simple Network Management Protocol)   SNMP(Simple Network Management Protocol)는 TCP/IP 네트워크 관리 전략을 정의하는 네트워크 관리 표준입니다. SNMP를 사용하면 네트워크에 대한 구성 및 상태 정보를 캡처하여 이벤트 모니터링을 위해 이 정보를 지정된 컴퓨터로 보낼 수 있습니다. 이 표준 기반 네트워크 관리 프로토콜은 다음을 포함한 배포된 아키텍처를 사용합니다.

  - 여러 관리되는 노드. 각각 관리 인프라에 대한 원격 액세스 권한을 부여하는 에이전트라는 SNMP 엔터티를 포함합니다.

  - 관리 응용 프로그램을 실행하여 관리되는 요소를 모니터링 및 제어하는 하나 이상의 SNMP 엔터티('관리자'라고 함). 관리되는 요소는 호스트, 라우터 등의 장치이며 해당 관리 정보에 액세스하여 모니터링 및 제어합니다.

  - 관리 프로토콜인 SNMP는 관리 스테이션과 에이전트 간에 관리 정보를 전달하는 데 사용됩니다. 관리 정보는 MIB(관리 정보 데이터베이스)라고 하는 가상 정보 저장소에 있는 관리 개체 컬렉션을 참조합니다.


> [!NOTE]
> 타사 네트워크 모니터링 솔루션의 예는 위에 나와 있습니다. 이 목록은 확정적이지 않으며 Microsoft가 특정 공급업체 솔루션을 선호하지는 않습니다. 조직에 가장 적합한 네트워크 모니터링 솔루션을 확인하려면 네트워크 서비스 공급자 및/또는 해당 기술 제공자에게 문의하세요.



## 개별 서버 네트워크 성능을 모니터링하기 위한 도구

## System Center Operations Manager 2012

System Center Operations Manager 2012를 사용하여 관리자는 Windows Server 2012 관리 팩: Windows Server 운영 체제 관리 팩을 통해 개별 서버의 네트워크 성능을 볼 수 있습니다. 이 관리 팩에는 관리자가 네트워크 어댑터 성능과 어댑터 상태를 모니터링할 수 있도록 하는 "성능" 관리 팩이 포함되어 있습니다.

## Windows 네트워크 모니터

서버의 리소스 사용량을 수집, 표시, 분석하고 네트워크 트래픽을 측정합니다. 네트워크 모니터는 네트워크 활동만 모니터링합니다. 네트워크 데이터를 캡처하여 분석하고 이 데이터를 성능 로그와 함께 사용하면 네트워크 사용을 확인하고, 네트워크 문제를 식별하고, 향후의 네트워크 요구 사항을 예측할 수 있습니다.

Network Monitor 3.4에 대한 자세한 내용과 네트워크 모니터를 설치 및 구성하고 데이터를 캡처하여 분석하는 방법을 알아보려면 Network Monitor 3.3 개요 세션을 검토하세요. 네트워크 모니터 블로그(<http://blogs.technet.com/b/netmon/>)에서도 유용한 정보를 확인할 수 있습니다.

