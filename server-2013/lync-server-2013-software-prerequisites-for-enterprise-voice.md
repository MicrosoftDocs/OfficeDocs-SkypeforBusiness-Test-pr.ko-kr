---
title: 'Lync Server 2013: Enterprise Voice에 대한 소프트웨어 필수 구성 요소'
TOCTitle: Enterprise Voice에 대한 소프트웨어 필수 구성 요소
ms:assetid: 41172119-9631-46c7-9d9f-386d951c650b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425916(v=OCS.15)
ms:contentKeyID: 49303429
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 Enterprise Voice에 대한 소프트웨어 필수 구성 요소

 

_**마지막으로 수정된 항목:** 2012-10-03_

Enterprise Voice를 배포하려는 인프라가 다음의 소프트웨어 필수 구성 요소를 충족하는지 확인하십시오.

  - Lync Server 2013 Standard Edition 또는 Enterprise Edition이 네트워크에 설치되어 있으며 작동합니다.

  - 액세스 에지 서비스 실행 에지 서버, A/V 에지 서비스, 웹 회의 에지 서비스 및 역방향 프록시를 포함하여 경계 네트워크에 모든 에지 서버가 배포되어 있고 작동합니다.

  - Exchange 통합 메시징을 Lync Server와 통합하고 다양한 알림 및 통화 로그 정보를 Lync 끝점에 제공하기 위해서는 Microsoft Exchange Server 2007 서비스 팩 3(SP3), Microsoft Exchange Server 2010 또는 Microsoft Exchange Server 2013이 필요합니다.

  - Lync Server에 대해 한 명 이상의 사용자를 만들고 사용하도록 설정했습니다.

  - Lync 클라이언트 및 장치를 배포했습니다.

  - 토폴로지 작성기가 네트워크의 서버에 설치되어 있습니다.

## 다음 단계: 보안 및 구성 필수 구성 요소 확인

Enterprise Voice에 대한 소프트웨어 필수 구성 요소를 확인한 후에는 설명서를 사용하여 Enterprise Voice 배포 준비를 계속할 수 있습니다.

1.  [Lync Server 2013의 Enterprise Voice에 대한 보안 및 구성 필수 구성 요소](lync-server-2013-security-and-configuration-prerequisites-for-enterprise-voice.md)에 설명된 대로 보안, 사용자 구성 및 하드웨어 필수 구성 요소를 확인합니다.

2.  [Lync Server 2013에서 중재 서버용 파일 설치](lync-server-2013-install-the-files-for-mediation-server.md)에 설명된 대로 중재 서버를 설치하지만 독립 실행형 중재 서버 또는 풀을 배포하는 *경우에만* 설치합니다. 중재 서버는 함께 배치될 경우 프런트 엔드 풀 또는 Standard Edition 서버 배포 프로세스의 일부로 설치됩니다.

3.  [Lync Server 2013에서 트렁크 구성](lync-server-2013-configuring-trunks.md)에 설명된 대로 사용자에게 PSTN 연결을 제공할 수 있도록 트렁크 연결을 구성합니다.

