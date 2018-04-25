---
title: 'Lync Server 2013: 인프라 및 시스템 준비'
TOCTitle: 인프라 및 시스템 준비
ms:assetid: 1254ee38-0679-4714-b293-1050f107c158
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398205(v=OCS.15)
ms:contentKeyID: 49302866
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에 대한 인프라 및 시스템 준비

 

_**마지막으로 수정된 항목:** 2013-02-21_

Lync Server 2013을 배포하려면 토폴로지 작성기를 사용하여 토폴로지 디자인을 정의하고 게시해야 합니다. 토폴로지에 필요한 구성 요소를 파악하려면 토폴로지 작성기를 사용하여 토폴로지 디자인을 만들고 저장합니다. 토폴로지 작성기에서 토폴로지를 게시하기 전에 다음을 수행합니다.

  - 필요한 모든 컴퓨터( Lync Server 2013을 실행하는 서버, 데이터베이스 서버, IIS(인터넷 정보 서비스)를 실행하는 서버, 역방향 프록시 서버 중 해당하는 서버), 네트워크 어댑터, 하드웨어 부하 분산 장치 및 저장소 장치(예: 파일 서버)를 비롯해 토폴로지 작성기를 사용하여 만들고 저장한 토폴로지 디자인 내의 각 구성 요소에 대해 하드웨어를 얻어 설치합니다. 배포에 필요한 구성 요소를 지정하는 토폴로지를 정의하는 방법에 대한 자세한 내용은 [Lync Server 2013에서 토폴로지 정의 및 구성](lync-server-2013-defining-and-configuring-the-topology.md)을 참조하십시오. 서버의 하드웨어 요구 사항에 대한 자세한 내용은 지원 가능성 설명서에서 [Lync Server 2013에서 지원되는 하드웨어](lync-server-2013-supported-hardware.md)를 참조하십시오.

  - 네트워킹 인프라가 요구 사항을 충족하는지 확인합니다. 자세한 내용은 계획 설명서에서 [Lync Server 2013용 네트워크 인프라 요구 사항](lync-server-2013-network-infrastructure-requirements.md)을 참고하세요.

  - Active Directory 도메인 서비스를 설치합니다. 토폴로지를 게시하고 사용하도록 설정하려면 AD DS의 컴퓨터 계정을 통해 내부 서버를 표시해야 합니다. 이렇게 하려면 컴퓨터를 AD DS에 연결합니다. AD DS를 준비하는 방법에 대한 자세한 내용은 [Lync Server 2013에 대한 Active Directory 도메인 서비스 준비](lync-server-2013-preparing-active-directory-domain-services.md)를 참조하십시오.

  - 파일 공유를 만듭니다. Standard Edition 서버에서는 필수 파일 저장소에 대한 파일 공유를 호스팅할 수 있는 반면, 엔터프라이즈 배포에서는 파일 공유를 프런트 엔드 서버에서 호스팅할 수 없습니다. 파일 공유를 호스팅하려면 토폴로지 작성기에 대해 폴더 및 공유에 ACL(액세스 제어 목록)을 배포하고 설정하는 데 필요한 사용 권한 및 그룹 구성원 자격을 제대로 설정해야 합니다. 토폴로지 작성기를 실행하는 사용자에게 다음 사용 권한 및 그룹 구성원 자격이 있는지 확인해야 합니다.
    
      - 로컬 Administrators 그룹의 구성원
    
      - Domain Users의 구성원
    
      - 파일 저장소의 공유 및 폴더에 대한 모든 권한

  - Enterprise Edition의 경우 SQL Server를 설치 및 구성합니다. SQL Server 설치를 정상적으로 수행하려면 SQL Server 기반 서버가 온라인 상태여야 하며, 토폴로지 게시자는 SQL Server의 로컬 관리자인 동시에 SQL Server 인스턴스의 SQL Server sysadmin 그룹 구성원이어야 합니다.

이 항목에서 설명된 준비 작업을 모두 완료한 후 토폴로지를 게시하기 전에 Windows 운영 체제 및 기타 필수 구성 요소 소프트웨어를 설치하고, IIS를 설정하고, DNS를 구성하는 등의 기타 준비 작업을 수행해야 합니다. 이러한 작업에 대한 자세한 내용은 [Lync Server 2013을 실행하는 서버의 시스템 요구 사항](lync-server-2013-system-requirements-for-servers-running-lync-server-2013.md), [Lync Server 2013에 대한 IIS 구성](lync-server-2013-configure-iis.md) 및 [Lync Server 2013에 대한 인프라 및 시스템 준비](lync-server-2013-preparing-the-infrastructure-and-systems.md)를 참조하십시오. 또한 클라이언트 및 클라이언트 요구 사항에 대해서도 잘 알고 있어야 합니다. 자세한 내용은 [Lync Server 2013에서 클라이언트 및 장치 배포](lync-server-2013-deploying-clients-and-devices.md)를 참조하십시오.

## 이 단원의 내용

  - [Lync Server 2013의 하드웨어 설치](lync-server-2013-hardware-setup.md)

  - [Lync Server 2013의 소프트웨어 설치](lync-server-2013-software-setup.md)

  - [Lync Server 2013에 대한 Active Directory 도메인 서비스 준비](lync-server-2013-preparing-active-directory-domain-services.md)

  - [Lync Server 2013에 대해 SQL Server 구성](lync-server-2013-configure-sql-server-for-lync-server.md)

  - [프런트 엔드 풀 또는 Standard Edition 서버에 대한 Lync Server 2013의 DNS 레코드 구성](lync-server-2013-configure-dns-records-for-a-front-end-pool-or-standard-edition-server.md)

  - [Lync Server 2013 관리 도구 설치](lync-server-2013-install-lync-server-administrative-tools.md)

