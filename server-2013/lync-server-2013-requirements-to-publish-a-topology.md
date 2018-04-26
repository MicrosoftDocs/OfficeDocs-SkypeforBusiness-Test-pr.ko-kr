---
title: 'Lync Server 2013: 토폴로지 게시 요구 사항'
TOCTitle: 토폴로지 게시 요구 사항
ms:assetid: 841cdf5d-d884-414d-ab50-3bb681b622ed
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg195733(v=OCS.15)
ms:contentKeyID: 49304237
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 토폴로지 게시 요구 사항

 

_**마지막으로 수정된 항목:** 2013-02-21_

이 항목에서는 토폴로지 작성기 또는 Lync Server 2013 관리 셸 명령줄 인터페이스를 사용하여 토폴로지를 게시할 때와 관련된 인프라 및 소프트웨어 요구 사항에 대해 설명합니다. 이러한 요구 사항은 모든 Lync Server 2013 관리 도구에 적용할 수 있는 일반적인 운영 체제, 소프트웨어 및 권한 요구 사항에 대해 추가로 적용됩니다. 토폴로지를 게시하기 전에 모든 관리 도구 요구 사항을 충족하는지 확인하세요.

  - Active Directory 도메인 서비스 준비 단계가 이미 완료되어 해당 컴퓨터에서 관리 도구를 사용하여 토폴로지를 성공적으로 게시할 수 있도록 작성 중인 Lync Server 2013 배포의 포리스트 또는 동일 도메인에 참여한 컴퓨터에서 토폴로지 작성기를 실행해야 합니다.

  - 토폴로지에 정의된 컴퓨터는 에지 서버를 제외하고 도메인 및 AD DS에 참여해야 합니다. 하지만 토폴로지를 게시할 때 컴퓨터가 온라인 상태일 필요는 없습니다.

  - 풀에 대한 파일 공유를 만들고 원격 사용자에게 제공해야 합니다.

  - Enterprise Edition 프런트 엔드 풀을 게시하려면 사용자가 서버를 배포 중인 도메인에 SQL Server 기반 백 엔드 서버가 참여해야 하며 온라인 상태여야 하며, 원격 사용자가 사용할 수 있도록 적합한 방화벽 규칙으로 구성되어 있어야 합니다. 방화벽 예외를 지정하는 방법에 대한 자세한 내용은 [Lync Server 2013의 SQL Server에 대한 방화벽 요구 사항 이해](lync-server-2013-understanding-firewall-requirements-for-sql-server.md)를 참조하십시오. SQL Server 구성에 대한 자세한 내용은 [Lync Server 2013에 대해 SQL Server 구성](lync-server-2013-configure-sql-server-for-lync-server.md)을 참조하십시오.
    

    > [!NOTE]
    > Standard Edition 서버에는 게시된 구성을 수락하는 배치된 데이터베이스가 있습니다. Lync Server 배포 마법사에서 먼저 <STRONG>첫 번째 Standard Edition 서버 준비</STRONG> 설정 작업을 실행해야 합니다.



## 참고 항목

#### 작업

[Lync Server 2013에서 토폴로지 게시](lync-server-2013-publish-the-topology.md)  
[Lync Server 2013에서 설치 권한 위임](lync-server-2013-delegate-setup-permissions.md)  

#### 개념

[Lync Server 2013의 관리 도구 소프트웨어 요구 사항](lync-server-2013-administrative-tools-software-requirements.md)  
[Lync Server 2013의 서버 및 도구 운영 체제 지원](lync-server-2013-server-and-tools-operating-system-support.md)  

#### 기타 리소스

[Lync Server 2013의 설정 및 관리에 필요한 관리자 권한](lync-server-2013-administrator-rights-and-permissions-required-for-setup-and-administration.md)

