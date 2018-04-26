---
title: 'Lync Server 2013: 외부 사용자 액세스 배포'
TOCTitle: 외부 사용자 액세스 배포
ms:assetid: d40c9574-c16b-4fe6-b848-21ae0b7e4f0e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398918(v=OCS.15)
ms:contentKeyID: 49305147
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 외부 사용자 액세스 배포

 

_**마지막으로 수정된 항목:** 2013-09-23_

Microsoft Lync Server 2013에 대한 에지 구성 요소를 배포하면 인증된 원격 사용자 및 익명 원격 사용자, 페더레이션 파트너(XMPP 파트너 포함), 모바일 클라이언트, 공용 메신저 서비스 사용자 등을 비롯한 조직의 내부 네트워크에 로그인하지 않은 외부 사용자가 Lync Server를 사용하여 조직의 다른 사용자와 통신할 수 있습니다. Lync Server 2013 배포 및 구성 프로세스는 Lync Server 2010과 많이 다르지 않습니다. 설치 및 관리 도구가 Lync Server 2010과 거의 동일합니다.


> [!IMPORTANT]
> Microsoft Lync Server 2013에지 서버 설치 및 구성은 보안, 네트워킹, 방화벽, DNS(Domain Name System), 부하 분산 장치, PKI(공개 키 인프라) 등의 고려 사항을 포함하여 내부 팀과 상당히 많은 계획 및 조율이 필요한 꽤 복잡한 프로세스일 수 있습니다. 외부 액세스 구성 요소를 배포하기 전에 제공된 계획 프로세스 및 문서를 검토하고 활용하는 것이 가장 좋습니다. 그러면 배포 프로세스를 진행하면서 원치 않는 변경 사항이나 문제가 더 적게, 더 드물게 발생하는 데 도움이 됩니다. 외부 사용자 액세스를 계획하는 방법에 대한 자세한 내용은 <A href="lync-server-2013-planning-for-external-user-access.md">Lync Server 2013의 외부 사용자 액세스 계획</A>을 참조하십시오.



## 이 단원의 내용

  - [Lync Server 2013의 외부 사용자 액세스를 위한 배포 검사 목록](lync-server-2013-deployment-checklist-for-external-user-access.md)

  - [Lync Server 2013의 외부 사용자 액세스 구성 요소에 대한 시스템 요구 사항](lync-server-2013-system-requirements-for-external-user-access-components.md)

  - [Lync Server 2013의 경계 네트워크에 서버 설치 준비](lync-server-2013-preparing-for-installation-of-servers-in-the-perimeter-network.md)

  - [Lync Server 2013에서 에지 및 디렉터 토폴로지 구성](lync-server-2013-building-an-edge-and-director-topology.md)

  - [Lync Server 2013에서 디렉터 설치](lync-server-2013-setting-up-the-director.md)(선택 사항)

  - [Lync Server 2013에서 에지 서버 설정](lync-server-2013-setting-up-edge-servers.md)

  - [Lync Server 2013에 대한 역방향 프록시 서버 설치](lync-server-2013-setting-up-reverse-proxy-servers.md)

  - [Lync Server 2013에서 외부 사용자 액세스에 대한 지원 구성](lync-server-2013-configuring-support-for-external-user-access.md)

  - [Lync Server 2013의 Lync-Skype 연결에 대한 프로비전 가이드](lync-server-2013-provisioning-guide-for-lync-skype-connectivity.md)

  - [Lync Server 2013에서 SIP 페더레이션, XMPP 페더레이션 및 공용 메신저 구성](lync-server-2013-configuring-sip-federation-xmpp-federation-and-public-instant-messaging.md)

  - [Lync Server 2013에서 모바일 기능 배포](lync-server-2013-deploying-mobility.md)

  - [Lync Server 2013에서 에지 배포 확인](lync-server-2013-verifying-your-edge-deployment.md)

