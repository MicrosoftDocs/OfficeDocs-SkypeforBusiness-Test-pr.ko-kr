---
title: 보관용 저장소 설정
TOCTitle: 보관용 저장소 설정
ms:assetid: f751245c-743e-454f-8325-968ae5e3de71
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205392(v=OCS.15)
ms:contentKeyID: 49305558
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 보관용 저장소 설정

 

_**마지막으로 수정된 항목:** 2013-12-17_

Lync Server 2013의 보관 저장소에는 다음이 포함됩니다.

  - **데이터 저장소**   데이터 저장소는 IM 콘텐츠를 저장하는 데 필요합니다.

  - **파일 저장소**   파일 저장소는 회의(모임) 콘텐츠 데이터 저장소 및 파일 저장소를 저장하는 필요합니다.

## 데이터 저장소 설정

Lync Server 2013에서 보관용으로 데이터 저장소를 설정하기 위한 요구 사항은 보관 데이터를 저장하는 방법에 따라 달라집니다.

  - Exchange 저장소를 사용하여 보관 데이터를 저장하기 위해 Lync Server 2013 보관과 Exchange 배포를 통합합니다.

  - 보관 데이터를 저장할 개별 SQL Server 데이터베이스 서버를 설정합니다.

## Exchange 저장소를 데이터 보관용으로 설정

Exchange를 보관 데이터 저장소로 설정하려면 Exchange 배포가 Exchange 2013에서 실행 중이어야 합니다. 또한 사용자 사서함이 Exchange 2013 서버에 있어야 하며 이러한 사서함을 현재 위치 유지 상태로 전환해야 합니다. Exchange 2013 구성에 대한 자세한 내용은 Exchange 제품 설명서를 참조하십시오.

## SQL Server 데이터베이스 서버를 보관 데이터 저장소로 설정

Lync Server 2013에 보관하려면 Exchange와 배포를 통합하지 않은 경우 SQL Server 데이터베이스 소프트웨어에서 보관 데이터를 저장해야 합니다.

SQL Server 보관 데이터베이스의 경우 보관 데이터베이스를 호스팅할 컴퓨터에 SQL Server를 설치해야 합니다. 프런트 엔드 풀용 백엔드 데이터베이스에 사용하는 동일한 SQL 인스턴스를 사용할 수 있습니다. 성능을 최대화하려면 중앙 관리 저장소와는 분리된 컴퓨터에 보관 데이터베이스를 배포해야 합니다. Lync Server 2013 구성 요소 배치에 대한 자세한 내용은 지원 가능성 설명서에서 [Lync Server 2013의 지원되는 서버 배치](lync-server-2013-supported-server-collocation.md)를 참조하십시오.

각 데이터베이스 서버에서 SQL Server의 지원 버전이 실행되고 있어야 합니다. 지원 버전에 대한 자세한 내용은 계획 설명서에서 [Lync Server 2013의 보관에 대한 기술 요구 사항](lync-server-2013-technical-requirements-for-archiving.md)을 참조하십시오.

보관을 배포 및 사용하도록 설정하기 전에 먼저 SQL Server 플랫폼을 설정해야 합니다. 토폴로지를 게시하는 데 사용될 계정에 적절한 관리자 권한 및 권한이 있는 경우 토폴로지를 게시할 때 보관 데이터베이스(LcsLog)를 만들 수 있습니다. 또한 설치 절차의 일부로 포함하는 등 나중에 데이터베이스를 만들 수도 있습니다. SQL Server에 대한 자세한 내용은 SQL Server TechCenter([http://go.microsoft.com/fwlink/?linkid=129045\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=129045%26clcid=0x412))를 참조하십시오.


> [!NOTE]
> SQL Server 에이전트 서비스 시작 유형이 자동이며 SQL 인스턴스에 대해 보관 데이터베이스를 보유하고 있는 SQL Server 에이전트 서비스가 실행 중입니다. 따라서 기본 보관 SQL Server 유지 관리 작업을 SQL Server 에이전트 서비스의 통제 하에 예약된 기준에 따라 실행할 수 있습니다.



## 파일 저장소 설정

보관에서는 프런트 엔드 풀이나 Standard Edition Server를 설정할 때 지정한 Lync Server 2013 파일 공유를 사용합니다. 보관용으로 사용되는 파일 공유는 변경할 수 없습니다. 지원되는 파일 저장소 시스템에 대한 자세한 내용은 지원 가능성 설명서에서 [Lync Server 2013의 파일 저장소 지원](lync-server-2013-file-storage-support.md)을 참조하십시오.

