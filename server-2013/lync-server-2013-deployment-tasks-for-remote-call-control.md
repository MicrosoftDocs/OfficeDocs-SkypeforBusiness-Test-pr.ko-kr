---
title: 'Lync Server 2013: 원격 통화 제어에 대한 배포 작업'
TOCTitle: 원격 통화 제어에 대한 배포 작업
ms:assetid: 20218871-4f27-4611-9b7e-c0ca55908284
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg558624(v=OCS.15)
ms:contentKeyID: 49303025
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 원격 통화 제어에 대한 배포 작업

 

_**마지막으로 수정된 항목:** 2012-10-05_

이 항목에서는 Lync Server 환경에서 사용자에 대한 원격 통화 제어를 설정하기 위해 수행해야 하는 배포 작업에 대해 설명합니다.


> [!NOTE]
> 이전에 Microsoft Office Communicator 2007 R2에서 원격 통화 제어를 사용하도록 설정된 사용자를 마이그레이션하려면 이 항목에 설명된 원격 통화 제어 배포 작업을 시작하기 전에 추가 배포 작업을 수행해야 합니다. Lync Server로의 마이그레이션 프로세스 중에 Office Communications Server 2007 R2 관리 도구를 사용하여 신뢰할 수 있는 응용 프로그램 항목(이전에는 <EM>권한이 부여된 호스트 항목</EM> 이라고 함)을 제거해야 합니다.<BR>권한이 부여된 호스트를 제거하는 방법에 대한 자세한 내용은 <A href="lync-server-2013-remove-a-legacy-authorized-host-optional.md">Lync Server 2013에서 권한이 부여된 기존 호스트 제거(선택 사항)</A>를 참조하십시오.



## 1단계: PBX와 통신할 SIP/CSTA 게이트웨이 설치 및 구성

사용자에게 원격 통화 제어 기능을 제공하려면 환경 내의 Lync Server 및 기존 PBX(Private Branch Exchange)에 연결할 수 있는 SIP/CSTA 게이트웨이를 하나 이상 설치해야 합니다. SIP/CSTA 게이트웨이는 SIP와 CSTA(Computer-Supported Telecommunications Application) 사이에 있는 게이트웨이입니다. 게이트웨이를 여러 개 설치하든 하나만 설치하든 관계없이 하나의 게이트웨이 또는 PBX만 사용하여 각 사용자를 구성할 수 있습니다. 기존 PBX에 SIP/CSTA 인터페이스가 없는 경우에는 소유 PBX 공급업체별 신호 프로토콜에 대한 지원을 포함하여 PBX를 지원할 수 있는 SIP/CSTA 게이트웨이를 배포해야 합니다. 기능에 대한 자세한 내용은 각 공급업체에 직접 문의하십시오.

원격 통화 제어를 위해 Lync Server와 통합할 수 있는 SIP/CSTA 게이트웨이를 설치할 준비가 완료되었으면 게이트웨이 공급업체에 문의하거나 공급업체의 게이트웨이 설명서를 참조하여 다음 정보에 대해 게이트웨이에 필요한 구문을 확인합니다.

  - 게이트웨이의 회선 서버 URI

  - 게이트웨이에 할당할 사용자에 대한 줄 URI

위 설정은 사용자 구성 중에 필요하며, 게이트웨이에서 예상대로 지정해야 PBX를 올바르게 라우팅하고 연결할 수 있습니다.

Microsoft Unified Communications Open Interoperability Program 웹 사이트( [http://go.microsoft.com/fwlink/?linkid=203309\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=203309%26clcid=0x412))에서 공급업체를 참조할 수 있습니다.

## 2단계: CSTA 요청을 SIP/CSTA 게이트웨이로 라우팅하도록 Lync Server 구성

Lync Server 풀에서 배포에 포함된 모든 SIP/CSTA 게이트웨이에 대해 원격 통화 제어 요청을 라우팅할 대상 주소(서버 URI)에 대한 고정 경로를 만들어야 합니다. 또한 각 대상 주소에 해당하는 신뢰할 수 있는 응용 프로그램 항목을 만들어야 합니다. 게이트웨이를 신뢰할 수 있는 응용 프로그램으로 지정하면 타사에서 개발한 응용 프로그램(제품에 기본 제공되는 일부가 아닌 서비스이므로 *외부 서비스* 라는 서비스를 실행함)인 경우에도 Lync Server 환경의 일부로 실행되도록 신뢰할 수 있는 상태가 지정됩니다. 끝으로, Lync Server에서 TLS(전송 계층 보안) 연결 대신 TCP(Transmission Control Protocol) 연결을 사용하여 SIP/CSTA 게이트웨이에 연결하는 경우 토폴로지 작성기를 사용하여 게이트웨이 IP 주소를 정의해야 합니다.

고정 경로를 구성하는 방법에 대한 자세한 내용은 [Lync Server 2013에서 원격 통화 제어에 대한 고정 경로 구성](lync-server-2013-configure-a-static-route-for-remote-call-control.md)을 참조하십시오.

신뢰할 수 있는 응용 프로그램 항목을 구성하는 방법에 대한 자세한 내용은 [Lync Server 2013에서 원격 통화 제어를 위한 신뢰할 수 있는 응용 프로그램 항목 구성](lync-server-2013-configure-a-trusted-application-entry-for-remote-call-control.md)을 참조하십시오.

토폴로지 작성기에서 SIP/CSTA 게이트웨이 IP 주소를 정의하는 방법에 대한 자세한 내용은 [Lync Server 2013에서 SIP/CSTA 게이트웨이 IP 주소 정의](lync-server-2013-define-a-sip-csta-gateway-ip-address.md)를 참조하십시오.

## 3단계: 원격 통화 제어에 대한 Lync 사용자 구성

Lync Server를 사용하도록 사용자를 설정한 경우 Lync Server 제어판 또는 Lync Server 관리 셸을 사용하여 원격 통화 제어를 사용하도록 사용자를 설정할 수 있습니다. 이 작업은 각 사용자에게 회선 서버 URI 및 줄 URI를 할당하는 배포 단계에 속합니다. 회선 서버 URI는 사용자에게 할당할 SIP/CSTA 게이트웨이의 SIP URI입니다. 줄 URI는 사용자에게 할당된 고유 전화 번호입니다.

원격 통화 제어에 대해 사용자를 구성하는 방법에 대한 자세한 내용은 [Lync Server 2013에서 Lync 사용자가 원격 통화 제어를 사용하도록 설정](lync-server-2013-enable-lync-users-for-remote-call-control.md)을 참조하십시오.

## 4단계: Lync Server 전화 번호 정규화 규칙 정의

원격 통화 제어 시나리오에서는 Lync Server에서 전화 번호 정규화 규칙을 사용하여 SIP/CSTA 게이트웨이로부터 받은 전화 번호를 E.164 형식으로 변환합니다. 특정 원격 통화 제어 기능이 제대로 작동하려면 전화 번호가 이 표준화된 형식이어야 합니다. 원격 통화 제어에서는 주소록 서비스 전화 번호 정규화에 대해 구성한 전화 번호 정규화 규칙을 사용합니다. 이 규칙은 Enterprise Voice에 사용되는 전화 번호 정규화 규칙과 다릅니다.

원격 통화 제어에서 전화 번호 정규화 규칙을 사용하는 방법에 대한 자세한 내용은 [Lync Server 2013의 원격 통화 제어 및 전화 번호 정규화](lync-server-2013-remote-call-control-and-phone-number-normalization.md)를 참조하십시오. 주소록 서비스의 전화 번호 정규화 규칙에 대한 자세한 내용은 작업 설명서에서 [Lync Server 2013에서 주소록 서비스 관리](lync-server-2013-administering-the-address-book-service.md)를 참조하십시오.

