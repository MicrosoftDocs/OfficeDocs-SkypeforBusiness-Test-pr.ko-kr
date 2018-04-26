---
title: 원격 통화 제어 사용
TOCTitle: 원격 통화 제어 사용
ms:assetid: 0b91d418-e6ed-4556-97af-e8523e01f249
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204664(v=OCS.15)
ms:contentKeyID: 49302770
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 원격 통화 제어 사용

 

_**마지막으로 수정된 항목:** 2012-10-02_

원격 통화 제어를 사용하면 사용자가 Lync Server 2013을 사용하여 자신의 데스크톱 PBX(private branch exchange) 전화를 제어할 수 있습니다. 레거시 환경에 원격 통화 제어를 배포했고 이를 Lync Server 2013으로 마이그레이션하려면 다음 작업을 수행해야 합니다.

1.  SIP/CSTA 게이트웨이를 설치하고 PBX와 통신하도록 구성합니다. Lync Server 2013 파일럿 풀을 배포할 때 이 단계를 수행해야 합니다.

2.  토폴로지를 병합하고 정책 및 설정을 마이그레이션한 후에는 CSTA 요청의 경로를 SIP/CSTA 게이트웨이로 지정하도록 Lync Server 2013을 구성합니다. 이 단계는 자동화된 마이그레이션 이후에 수행되는 수동 단계입니다. CSTA 요청의 라우팅을 구성하려면 다음을 수행합니다.
    
      - 권한이 부여된 레거시 호스트 항목( Lync Server 2013의 *트러스트된 서버 항목* )을 제거합니다. 레거시 배포로부터 사용자를 마이그레이션하는 경우 Lync Server 2013 파일럿 풀에서 새 트러스트된 응용 프로그램 항목을 구성하기 전에 SIP/CSTA 게이트웨이에 대해 만든 기존의 모든 권한이 부여된 호스트 항목을 제거해야 합니다. 권한이 부여된 레거시 호스트 항목을 제거하는 방법에 대한 자세한 내용은 [권한이 부여된 호스트 항목 제거](remove-an-authorized-host-entry.md)를 참조하십시오.
    
      - 원격 통화 제어를 위한 고정 경로 구성 원격 통화 제어를 지원하려는 개별 풀에 대한 고정 경로를 구성하거나 풀 수준의 고정 경로로 구성되지 않은 각 풀에 전역 고정 경로가 사용되도록 전역 고정 경로를 구성할 수 있습니다. 고정 경로를 구성하는 방법에 대한 자세한 내용은 배포 설명서에서 [Lync Server 2013에서 원격 통화 제어에 대한 고정 경로 구성](lync-server-2013-configure-a-static-route-for-remote-call-control.md)을 참조하십시오.
    
      - 원격 통화 제어를 지원하려는 각 풀에서 원격 통화 제어를 위한 트러스트된 응용 프로그램 항목을 구성합니다. 트러스트된 응용 프로그램 항목을 구성하는 방법에 대한 자세한 내용은 배포 설명서에서 [Lync Server 2013에서 원격 통화 제어를 위한 신뢰할 수 있는 응용 프로그램 항목 구성](lync-server-2013-configure-a-trusted-application-entry-for-remote-call-control.md)을 참조하십시오.

3.  TCP(Transmission Control Protocol)를 사용하여 Lync Server 2013에 연결하는 SIP/CSTA 게이트웨이를 배포한 경우 토폴로지 작성기에서 게이트웨이의 IP 주소를 정의합니다. IP 주소를 정의하는 방법에 대한 자세한 내용은 배포 설명서에서 [Lync Server 2013에서 SIP/CSTA 게이트웨이 IP 주소 정의](lync-server-2013-define-a-sip-csta-gateway-ip-address.md)를 참조하십시오.

4.  원격 통화 제어를 사용하도록 설정하고 회선 서버 URI(Uniform Resource Identifier) 및 회선 URI를 지정하여 원격 통화 제어에 맞게 Lync 2013 사용자를 구성합니다. 레거시 배포에서 Lync Server 2013로 사용자를 마이그레이션할 때 원격 통화 제어 설정은 다른 사용자 설정과 함께 마이그레이션됩니다.

5.  레거시 배포에서 주소록 전화 번호 정규화 규칙을 사용자 지정한 경우 정책 및 설정에 대한 자동화된 마이그레이션이 완료된 후 몇 가지 수동 작업을 수행하여 사용자 지정된 정규화 규칙을 마이그레이션해야 합니다. 정규화 규칙을 사용자 지정하지 않은 경우 주소록은 남은 토폴로지와 함께 마이그레이션됩니다. 사용자 지정된 정규화된 규칙을 수동으로 마이그레이션하는 방법에 대한 자세한 내용은 [주소록 마이그레이션](migrate-address-book_1.md)을 참조하십시오.

