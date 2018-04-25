---
title: Lync Server 2013의 주요 보안 기능
TOCTitle: Lync Server 2013의 주요 보안 기능
ms:assetid: bf2a3b8f-73c6-47e1-8c9e-ca1dc1a502bf
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn342829(v=OCS.15)
ms:contentKeyID: 56270298
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 주요 보안 기능

 

_**마지막으로 수정된 항목:** 2013-07-18_

Lync Server 2013에는 서버 간 인증, 역할 기반 액세스 제어, 구성 데이터의 중앙 저장소를 비롯한 여러 가지 보안 기능이 있습니다.

이 문서에서는 Lync Server 2013 보안에 대한 높은 수준의 개요를 제공합니다.

## Lync Server 2013의 주요 보안 기능

보안은 매우 포괄적인 주제입니다. Lync Server 2013의 모든 기능은 물론 Lync 환경을 구성하는 데이터베이스, 서비스, 하드웨어까지 영향을 미칩니다. 이 문서에서는 보안을 위해 특별히 디자인된 Lync Server 2013의 몇 가지 기능에 대해 간략하게 설명합니다.

## 계획 및 디자인 도구

Lync Server 2013은 계획과 디자인을 용이하게 하고 Lync Server 구성 요소를 잘못 구성하는 실수를 방지하기 위해 두 가지 도구를 제공합니다.

  - **토폴로지 계획 도구**는 토폴로지 디자인 과정의 대부분을 자동화합니다. 계획 도구에서 Lync Server 2013을 실행하는 각 서버를 설치하기 위해 필요한 토폴로지 작성기로 결과를 내보낼 수 있습니다.

  - **토폴로지 작성기**는 중앙 관리 저장소에 모든 구성 정보를 저장합니다.

이러한 도구에 대한 자세한 내용은 [Lync Server 2013용 계획](lync-server-2013-planning.md)을 참고하세요.

## 중앙 관리 저장소

Lync Server 2013에서 서버 및 서비스에 대한 구성 데이터는 중앙 관리 저장소에 포함됩니다. 중앙 관리 저장소는 Lync Server 배포를 정의, 설정, 유지, 관리, 설명, 운영하는 데 필요한 강력하고 체계화된 데이터 저장 공간을 제공합니다. 또한 구성 일관성을 보장하기 위해 데이터의 유효성을 검사합니다. 이 구성 데이터에 대한 모든 변경 작업이 중앙 관리 저장소에서 발생하므로 "동기화되지 않는" 문제를 방지할 수 있습니다.

데이터의 읽기 전용 복사본이 에지 서버 및 SBA(Survivable Branch Appliance)를 비롯한 토폴로지의 모든 서버에 복제됩니다. 복제는 기본적으로 네트워크 서비스의 컨텍스트에서 실행되는 서비스에 의해 관리되므로 권한과 사용 권한이 컴퓨터에 있는 단순 사용자로 제한됩니다.

## 서버 간 인증

Lync Server 2013에서는 OAuth(Open Authorization) 프로토콜을 사용하여 서버 간에 인증을 구성할 수 있습니다. 예를 들어 Exchange Server 2013을 실행하는 서버를 사용하여 인증하도록 Lync Server 2013을 구성할 수 있습니다. OAuth 프로토콜을 사용하면 Lync Server와 Exchange Server가 서로를 신뢰할 수 있습니다. 따라서 제품을 원활하게 통합할 수 있습니다. 자세한 내용은 [Lync Server 2013에서 서버 간 인증(Oauth) 및 파트너 응용 프로그램 관리](lync-server-2013-managing-server-to-server-authentication-oauth-and-partner-applications.md)를 참고하세요.

## Windows PowerShell 기반 관리 및 웹 기반 관리 인터페이스

Lync Server 2013에는 Windows PowerShell 명령줄 인터페이스를 기반으로 한 강력한 관리 인터페이스가 제공됩니다. 여기에는 보안 관리를 위한 cmdlet이 포함되며, Windows PowerShell 보안 기능이 기본적으로 설정되어 있기 때문에 사용자가 모르는 상태에서 부주의하게 스크립트를 실행할 수 없습니다. 즉, 소프트웨어 기본값이 자동으로 보안을 극대화하고 공격 통로를 줄일 수 있도록 설정되어 있습니다. Lync Server 2013의 Windows PowerShell 관리 지원에 대한 자세한 내용은 [Lync Server 관리 셸](lync-server-2013-lync-server-management-shell.md)을 참고하세요.

## RBAC(역할 기반 액세스 제어)

Microsoft Lync Server 2013은 높은 보안 기준을 유지하는 동시에 관리 작업을 위임할 수 있는 RBAC(역할 기반 액세스 제어)를 제공합니다. RBAC를 사용하면 업무에서 요구되는 경우에만 관리 권한이 사용자에게 부여되는 "최소 권한 부여" 원칙을 따를 수 있습니다. Lync Server 2013에는 새 역할을 만드는 기능과 기존 역할을 수정하는 기능이 도입되었습니다. 자세한 내용은 [Lync Server 2013의 역할 기반 액세스 제어 계획](lync-server-2013-planning-for-role-based-access-control.md)을 참고하세요.

## NAT(Network Address Translation)

Lync Server 2013에서는 에지 서버의 내부 인터페이스에서 NAT(Network Address Translation) 사용을 지원하지 않지만, 단일 및 확장된 통합 에지 서버 토폴로지를 위해 NAT(Network Address Translation)를 수행하는 라우터나 방화벽 뒤에 Access 에지 서비스, 웹 회의 에지 서비스, A/V 에지 서비스의 외부 인스턴스를 배치하는 것은 가능합니다. 하드웨어 부하 분산 장치 뒤에 있는 여러 에지 서버는 NAT를 사용할 수 없습니다. 여러 에지 서버가 외부 인터페이스에서 NAT를 사용할 경우 DNS(Domain Name System) 부하 분산 장치가 필요합니다. DNS 부하 분산 장치를 사용하면 에지 서버 풀 하나에 있는 에지 서버 한 대당 공용 IP 주소의 수를 줄일 수 있습니다. 자세한 내용은 [Lync Server 2013의 외부 사용자 액세스 계획](lync-server-2013-planning-for-external-user-access.md)을 참고하세요.


> [!NOTE]
> Microsoft Office Communications Server 2007 배포가 있는 기업과 페더레이션하는 경우 사용자의 기업과 페더레이션된 기업 간에 오디오/비디오가 필요하면 배포된 이전 버전의 에지 서버의 포트 요구 사항이 적용됩니다. 예를 들어 페더레이션 파트너가 에지 서버를 Lync Server 2013으로 업그레이드할 때까지 두 기업 모두 이전 버전에 필요한 포트 범위를 열어 두어야 합니다. 이때 포트 요구 사항을 검토하고 새 구성에 따라 줄일 수 있습니다.



## 에지 서버의 간편해진 인증서

배포 마법사가 자동으로 SN(주체 이름)과 SAN(주체 대체 이름)을 채우므로 불필요하고 잠재적으로 안전하지 않은 항목이 포함될 가능성이 낮아집니다.

## 신뢰할 수 있는 컴퓨팅 SDL(Security Development Lifecycle)

Lync Server 2013은 Microsoft 신뢰할 수 있는 컴퓨팅 SDL(Security Development Lifecycle)과 호환되도록 디자인 및 개발되었습니다. 이에 대한 설명은 <http://go.microsoft.com/fwlink/?linkid=68761>을 참고하세요.

  - **디자인에 따른 신뢰**   더욱 안전한 통합 커뮤니케이션 시스템을 만들기 위한 첫 번째 단계는 위협 모델을 디자인하고 디자인 과정에서 각 기능을 테스트하는 것이었습니다. 또한 Microsoft는 예기치 않은 제품 동작으로 인해 발생하는 보안 취약점을 찾기 위해 디자인된 동작 이외의 동작에 대한 테스트도 수행했습니다. 코딩 프로세스 및 실행에 다수의 개선된 보안 관련 기능이 적용되었습니다. 빌드 시간 도구는 코드가 최종 제품에 체크 인되기 전에 초과되는 버퍼와 기타 잠재적인 보안 위협을 발견합니다. 물론 알려지지 않은 모든 보안 위협에 맞서 디자인하는 것은 불가능합니다. 완벽한 보안을 보장할 수 있는 시스템은 없지만 제품을 개발할 때 처음부터 보안 디자인 원칙이 적용되므로 Lync Server 2013은 업계 표준 보안 기술을 아키텍처의 기본으로 통합합니다.

  - **기본적인 신뢰**   기본적으로 Lync Server 2013에서 네트워크 통신은 암호화됩니다. 모든 서버에서 인증서, Kerberos 인증, TLS, SRTP(Secure Real-Time Transport Protocol) 및 128비트 AES(고급 암호화 표준) 암호화를 비롯한 기타 업계 표준 암호화 기술을 사용하기 때문에 거의 모든 Lync Server 데이터가 네트워크에서 보호됩니다. 또한 역할 기반 액세스 제어 덕분에 Lync Server 2013을 실행하는 서버를 배포할 수 있어 각 서버 역할이 서비스만 실행하고 해당 서비스와 관련된 서버 역할에 해당하는 권한만 가집니다.

  - **개발에 따른 신뢰**   모든 Lync Server 2013 설명서에는 배포를 위한 최적의 보안 수준을 결정 및 구성하고 기본이 아닌 옵션을 활성화할 경우 따르는 위험을 평가하는 데 도움이 되는 모범 사례와 권장 사항이 포함되어 있습니다.

