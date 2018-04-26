---
title: 'Lync Server 2013: 보관에 대한 기술 요구 사항'
TOCTitle: 보관에 대한 기술 요구 사항
ms:assetid: 896d60e2-be4b-462d-8357-4cd307ab7304
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205059(v=OCS.15)
ms:contentKeyID: 49304299
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 보관에 대한 기술 요구 사항

 

_**마지막으로 수정된 항목:** 2012-10-09_

Lync Server 2013 기술 요구 사항은 다음과 같습니다.

  - 인프라 요구 사항

  - 보관용으로 설치해야 하는 필수 구성 요소 소프트웨어

  - 보관용 데이터 저장소 요구 사항

  - 보관 배포에 대한 확장 요구 사항 및 고려 사항

  - 보관 데이터베이스에 대한 성능 요구 사항 및 고려 사항


> [!NOTE]
> 이 Lync Server 2013 릴리스에서는 확장 및 성능 정보를 사용할 수 없습니다.



## 인프라 요구 사항

Lync Server 2013 보관 인프라 요구 사항은 Lync Server 2013 배포와 동일합니다. 자세한 내용은 계획 설명서에서 [Lync Server 2013에 대한 인프라 요구 사항 확인](lync-server-2013-determining-your-infrastructure-requirements.md)을 참조하십시오.

## 보관 필요 조건

Lync Server 2013은 다음과 같은 이유로 보관에 대한 필요 조건이 효율적으로 개선되었습니다.

  - 보관 서버가 더 이상 서버 역할이 아닙니다. 대신 보관용 데이터를 캡처하기 위해 통합 데이터 컬렉션 에이전트가 풀의 프런트 엔드 서버 및 Standard Edition 서버에서 실행되므로 보관을 위한 별도의 시스템 플랫폼을 설정하지 않아도 됩니다.

  - 보관에는 모임 콘텐츠 파일의 임시 저장을 위한 Lync Server 2013 파일 저장소가 사용되므로 보관을 위한 별도의 파일 저장소를 설정할 필요가 없습니다.

  - Lync Server 2013에서는 메시지 큐가 필요하지 않습니다.

## 보관용 데이터 저장소 요구 사항

또한 보관 저장소에 대한 인프라를 설정할 필요가 없습니다. 여기에는 다음과 같은 항목 중 하나 또는 모두가 포함됩니다.

  - **Microsoft Exchange 저장소**. 모임 콘텐츠 파일(예: PowerPoint 프레젠테이션)이 첨부 파일로 보관됩니다. Lync 보관 데이터를 Exchange 준수 데이터와 함께 저장할 수 있도록 Microsoft Exchange 통합을 사용하려는 경우 해당 Exchange 배포에 대해 Exchange 2013을 사용하고 최대 저장소 크기로 모임 콘텐츠 파일의 저장이 지원되는지 확인해야 합니다. Microsoft Exchange 통합 옵션을 사용하여 보관을 배포할 경우 Exchange 2013 서버에 있는 사용자에 대해서만 Lync 보관 데이터가 Exchange 2013 준수 데이터와 함께 저장됩니다. Microsoft Exchange 통합 옵션을 사용해서 보관을 배포하고 사용하도록 설정하기 전에 Exchange 2013을 배포해야 합니다. Exchange 2013 저장소를 사용하도록 선택한 경우 Exchange 2013 서버에 없는 Lync 사용자가 있지 않은 한 별도의 보관용 SQL Server 데이터베이스를 배포할 필요가 없습니다.

  - **보관용 SQL Server 데이터베이스 저장소**. Exchange 2013 서버에 없는 사용자를 지원하기 위해 또는 Microsoft Exchange 통합 옵션을 사용하지 않으려는 경우에는 SQL Server 데이터베이스를 사용해서 보관 저장소를 배포해야 합니다. Lync Server 2013에서는 다음과 같은 64비트 버전의 SQL Server가 지원됩니다.
    
      - Microsoft SQL Server 2008 R2 Enterprise
    
      - Microsoft SQL Server 2008 R2 Standard
    
      - Microsoft SQL Server 2012 Enterprise
    
      - Microsoft SQL Server 2012 Standard
    

    > [!NOTE]
    > Microsoft SQL Server 2008 R2 Express 및 Microsoft SQL Server 2012 Express는 보관용으로 지원되지 않습니다. 32비트 버전의 SQL Server도 지원되지 않습니다. 자세한 SQL Server 요구 사항 및 제한 사항을 보려면 계획 설명서 또는 지원 가능성 설명서에서 <A href="lync-server-2013-database-software-support.md">Lync Server 2013의 데이터베이스 소프트웨어 지원</A>을 참조하십시오.

    
    보관을 배포 및 사용하도록 설정하기 전에 먼저 SQL Server 플랫폼을 설정해야 합니다. 토폴로지를 게시하는 데 사용될 계정에 적절한 관리자 권한 및 권한이 있는 경우 토폴로지를 게시할 때 보관 데이터베이스(LcsLog)를 만들 수 있습니다. 또한 설치 절차의 일부로 포함하는 등 나중에 데이터베이스를 만들 수도 있습니다. SQL Server에 대한 자세한 내용은 SQL Server TechCenter( [http://go.microsoft.com/fwlink/?linkid=129045\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=129045%26clcid=0x412))를 참조하십시오.

