---
title: 'Lync Server 2013: 데이터베이스 강화 및 보호'
TOCTitle: Lync Server 2013의 데이터베이스 강화 및 보호
ms:assetid: 6953e721-3511-4235-b848-51bab093dc89
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn518330(v=OCS.15)
ms:contentKeyID: 60504740
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 데이터베이스 강화 및 보호

 

_**마지막으로 수정된 항목:** 2013-12-05_

Microsoft Lync Server 2013은 또한 사용자 정보, 전화 회의 상태, 보관 데이터 및 CDR(통화 정보 기록)을 저장하기 위해 SQL Server 데이터베이스를 사용합니다. 내결함성이 향상되고 문제 해결 방식이 간단해질 수 있도록 응용 프로그램 데이터를 분할하여 Lync Server 백 엔드 데이터베이스에 대한 Lync Server 2013 데이터의 가용성을 극대화할 수 있습니다. 이러한 목표를 달성하려면 다음과 같은 방법으로 응용 프로그램을 분할합니다.

  - **유용한 서버 분할 방법 사용**   운영 체제, 응용 프로그램 및 프로그램 파일을 데이터 파일과 분리합니다.

  - **트랜잭션 로그 파일 및 데이터베이스 파일 저장**   이러한 파일을 별도로 저장하여 내결함성을 높이고, 복구를 최적화하고, 암호화된 디스크 또는 볼륨에 저장합니다.

  - **서버 클러스터링 사용**   백 엔드 서버를 클러스터링하여 Lync Server 2013 시스템 가용성을 최적화합니다.

  - **모든 데이터 백업이 암호화되고 올바르게 처리되었는지 보장**   분실, 폐기 또는 잘못 배치된 백업 미디어는 Lync Server 2013 배포의 데이터 보안에 중대한 위협을 일으킬 수 있습니다.

Standard Edition 서버를 제외한 모든 Lync Server 2013 서버에서 SQL Server Express 인스턴스(RTCLOCAL 인스턴스)는 원격으로 액세스할 수 없으며, Standard Edition 서버의 SQL Server Express를 제외하고 로컬 방화벽 예외가 만들어지지 않습니다. Standard Edition 서버에서는 백 엔드 데이터베이스 및 CMS(중앙 관리 저장소)가 모두 원격으로 액세스할 수 있도록 설정됩니다. SQL Server 데이터베이스를 강화하려면 다음을 수행할 수 있습니다.

  - Standard Edition 서버에서 SQL Server Express 방화벽을 사용자 지정하여 데이터베이스에 원격으로 액세스할 수 있는 서버 범위를 제한합니다. 기본적으로 모든 IP 주소가 데이터베이스에 원격으로 액세스할 수 있습니다.

  - SQL Server 구성 관리자를 사용하여 SQL Server 원격 액세스에 대한 프로토콜, IP 주소 및 포트를 지정합니다.
    
      - Lync Server 2013에는 TCP/IP 프로토콜이 사용됩니다. 여기에서 IPv4(IP 버전 4)는 지원되지만 IPv6(IP 버전 6)이 지원되지 않습니다.
        

        > [!NOTE]
        > Lync Server 2013은 이중 IP 스택이 설정된 네트워크에서 작동할 수 있습니다.

    
      - Lync Server 2013에서는 다중 IP 주소(다중 홈 네트워크 주소 카드)가 지원됩니다. SQL Server가 특정 IP 주소로만 수신 대기하고(개별 주소 또는 서브넷별) 특정 프로토콜만 사용하도록 지정할 수 있습니다.
    
      - Lync Server 2013에서는 정적 및 동적 SQL Server 포트가 지원됩니다.

  - 정적(기본값이 아님) 포트에서 SQL Server를 실행하고 수신 대기 포트를 클라이언트에 보고할 수 없도록 SQL Server 브라우저는 실행하지 않습니다. 이렇게 하려면 프런트 엔드 서버, 모니터링 서버, 보관 서버 및 관리 콘솔(Lync Server 관리 셸, Lync Server 제어판 또는 토폴로지 작성기 실행)을 포함하는 각 SQL Server 클라이언트와 Lync Server 데이터베이스를 실행하는 다른 모든 서버에서 사용자 지정 구성이 필요합니다.


> [!NOTE]
> 데이터베이스에 대한 액세스는 신뢰할 수 있는 데이터베이스 관리자로 제한해야 합니다. 악의적인 데이터베이스 관리자는 자신에게 Lync Server 2013 서버에 대한 제어 또는 직접 액세스 권한이 부여되어 있지 않더라도 Lync Server 2013 서버에 대한 권한을 획득하기 위해 또는 서비스에서 민감한 정보를 가져오기 위해 데이터베이스에서 데이터를 삽입하거나 수정할 수 있습니다.



사용자 지정 구성 및 SQL Server 데이터베이스 강화에 대한 자세한 내용은 NextHop 블로그 문서, "Lync Server 2010에서 사용자 지정 SQL Server 네트워크 구성 사용"([http://go.microsoft.com/fwlink/p/?LinkId=214008](http://go.microsoft.com/fwlink/p/?linkid=214008))을 참조하세요.


> [!NOTE]
> 또한 운영 체제 및 응용 프로그램 서버를 강화하고 그룹 정책을 사용하여 Lync Server 배포에서 보안 잠금을 구현할 수 있습니다. 자세한 내용은 <A href="lync-server-2013-hardening-and-protecting-servers-and-applications.md">Lync Server 2013에 대한 서버 및 응용 프로그램 강화 및 보호</A>을 참조하세요.


