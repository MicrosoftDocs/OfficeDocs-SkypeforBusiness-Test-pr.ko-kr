---
title: 'Lync Server 2013: 하드웨어 설치'
TOCTitle: 하드웨어 설치
ms:assetid: 37a9f295-cde3-4beb-9a6a-2580082798ab
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425852(v=OCS.15)
ms:contentKeyID: 49303312
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 하드웨어 설치

 

_**마지막으로 수정된 항목:** 2013-02-21_

토폴로지를 구현하는 데 필요한 인프라에서 필요한 하드웨어 및 기타 구성 요소를 설치하려면 토폴로지 작성기에서 토폴로지를 게시하기 전에 다음을 수행해야 합니다.

  - 필요한 모든 컴퓨터(Lync Server 2013 실행 서버, 데이터베이스 서버, IIS(인터넷 정보 서비스)를 실행하는 서버, 역방향 프록시 서버 중 해당하는 서버), 네트워크 어댑터, 하드웨어 부하 분산 장치 및 저장소 장치(예: 파일 서버)를 비롯해 토폴로지 작성기를 사용하여 만들고 저장한 토폴로지 디자인 내의 각 구성 요소에 대해 하드웨어를 설치합니다. 네트워크 어댑터 수 및 속도에 대해 권장 사항을 준수했는지 확인합니다. 하드웨어 부하 분산 장치를 사용하려는 경우 Lync Server 2013에서 하드웨어 부하 분산 장치를 사용하도록 구성하기 위해 적절한 정보를 공급업체로부터 받아야 합니다. 파일 서버 또는 기타 서버를 사용하여 Lync Server에 필요한 파일 공유를 배치하려는 경우에는 해당 서버가 파일 공유 구성용으로 사용 가능하며 준비되어 있는지 확인합니다. 배포에 필요한 구성 요소를 지정하는 토폴로지를 정의하는 방법에 대한 자세한 내용은 [Lync Server 2013에서 토폴로지 정의 및 구성](lync-server-2013-defining-and-configuring-the-topology.md)을 참고하세요. 서버의 하드웨어 요구 사항에 대한 자세한 내용은 지원 가능성 설명서에서 [Lync Server 2013에서 지원되는 하드웨어](lync-server-2013-supported-hardware.md)를 참고하세요.

  - 네트워킹 인프라가 요구 사항을 충족하는지 확인합니다. 자세한 내용은 계획 설명서에서 [Lync Server 2013용 네트워크 인프라 요구 사항](lync-server-2013-network-infrastructure-requirements.md)을 참고하세요.

  - Active Directory 도메인 서비스를 설치합니다. AD DS 설치 작업에는 AD DS를 준비하는 작업과 AD DS에서 배포할 모든 구성 요소를 정의하는 작업이 포함됩니다. AD DS를 준비하는 방법에 대한 자세한 내용은 배포 설명서에서 [Lync Server 2013에 대한 Active Directory 도메인 서비스 준비](lync-server-2013-preparing-active-directory-domain-services.md)를 참조하십시오.

  - 파일 공유를 만드는 데 필요한 권한을 설정합니다. Lync Server 2013에서 파일 공유를 사용하기 위한 권한은 토폴로지를 게시할 때 토폴로지 작성기를 통해 자동으로 구성됩니다. 그러나 토폴로지 작성기에서 필요한 권한을 구성하려면 토폴로지를 게시하는 데 사용되는 사용자 계정에 파일 공유에 대한 모든 권한(읽기/쓰기/수정)이 있어야 합니다. 토폴로지 작성기 게시 프로세스 중에 파일 공유를 적절하게 관리하려면, 사용자 또는 사용자가 구성원으로 속한 도메인 그룹이 파일 공유가 있는 컴퓨터의 로컬 Administrators 그룹 구성원이어야 합니다. 다중 도메인 시나리오에서 도메인 A 사용자나 그룹은 파일 공유가 있는 도메인 B의 컴퓨터에서 로컬 Administrators 그룹의 구성원으로 지정되어야 합니다.
    
    DFS(분산 파일 시스템)에서 파일 공유를 사용하여 업데이트하는 방법에 대한 자세한 내용은 [Lync Server 2013의 파일 저장소 구성](lync-server-2013-configure-dfs-file-storage.md)를 참조하십시오.
    

    > [!WARNING]
    > Lync Server 2013 Enterprise Edition용 파일 공유는 프런트 엔드 서버에 배치할 수 없습니다.



  - 웹 서비스용 하드웨어 부하 분산 장치를 설치 및 설정합니다. DNS(Domain Name System) 부하 분산 기능이 배포되어 있는 경우에도, HTTP/HTTPS 트래픽에 한해 이러한 풀에서 하드웨어 부하 분산 장치 역시 사용해야 합니다. 하드웨어 부하 분산 장치는 클라이언트에서 포트 443 및 80을 통한 HTTPS 트래픽에 사용됩니다. 이러한 풀에 대해서도 하드웨어 부하 분산 장치가 필요하지만, 이러한 설치 및 관리 작업은 HTTP/HTTPS에 한해서만 수행하면 됩니다. 이는 하드웨어 부하 분산 장치 관리자에게는 익숙한 일입니다.

이 항목에서 설명하는 모든 준비 작업을 완료한 후에는 토폴로지를 게시하기 전에 다음 작업도 수행해야 합니다.

  - [Lync Server 2013의 서버에 운영 체제 및 필수 구성 요소 소프트웨어 설치](lync-server-2013-install-operating-systems-and-prerequisite-software-on-servers.md)

  - [Lync Server 2013에 대한 IIS 구성](lync-server-2013-configure-iis.md)

  - [Lync Server 2013에 대해 SQL Server 구성](lync-server-2013-configure-sql-server-for-lync-server.md)

  - [프런트 엔드 풀 또는 Standard Edition 서버에 대한 Lync Server 2013의 DNS 레코드 구성](lync-server-2013-configure-dns-records-for-a-front-end-pool-or-standard-edition-server.md)

