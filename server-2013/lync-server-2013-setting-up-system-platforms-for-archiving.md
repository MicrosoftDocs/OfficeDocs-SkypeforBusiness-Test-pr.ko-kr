---
title: 보관을 위해 시스템 플랫폼 설정
TOCTitle: 보관을 위해 시스템 플랫폼 설정
ms:assetid: 2df40fdf-0e32-46d4-9fb2-1ce1d7bfa328
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204768(v=OCS.15)
ms:contentKeyID: 49303173
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 보관을 위해 시스템 플랫폼 설정

 

_**마지막으로 수정된 항목:** 2012-10-09_

보관 배포를 시작하기 전에 시스템 요구 사항을 충족하는 하드웨어에 필요한 운영 체제 및 기타 필수 구성 요소 소프트웨어를 설치해야 합니다.

  - **Lync Server 2013 플랫폼**   Lync Server 2013 배포에는 보관 서버가 없습니다. 대신 통합 데이터 수집 에이전트가 프런트 엔드 서버 및 Standard Edition 서버에서 실행되어 보관할 데이터를 캡처하므로 보관을 호스팅하기 위해 별도로 필요한 시스템 플랫폼은 없습니다.

  - **데이터 저장 플랫폼**   Lync Server 2013에서는 다음 중 하나를 사용하여 데이터를 저장할 수 있습니다.
    
      - **Microsoft Exchange 통합**   보관 데이터 저장용으로 별도의 데이터베이스를 설정하는 대신/설정함과 동시에 Exchange 2013 배포를 사용하여 Lync Server 2013 보관 데이터를 저장하려는 경우에는 Exchange 배포에서 Exchange 2013을 실행해야 합니다. Exchange 2013용 시스템 플랫폼을 설정하는 방법에 대한 자세한 내용은 Exchange 제품 설명서를 참조하십시오.
    
      - **SQL Server**   Microsoft Exchange 통합을 사용하는 대신/사용함과 동시에 보관 데이터 저장용으로 별도의 SQL Server 데이터베이스를 사용하려는 경우에는 보관 배포 전에 데이터베이스용 시스템 플랫폼을 설정해야 합니다. 특정 시스템 플랫폼 요구 사항은 보관 데이터베이스에 대해 사용하는 플랫폼(Microsoft SQL Server 2008 R2 또는 Microsoft SQL Server 2012)에 따라 다릅니다. 이러한 데이터베이스용 시스템 플랫폼을 설정하는 방법에 대한 자세한 내용은 Microsoft SQL Server 2008 R2 및 Microsoft SQL Server 2012 제품 설명서를 참조하십시오.

  - **파일 서버 플랫폼**   Lync Server 2013에서는 프런트 엔드 서버 또는 Standard Edition 서버를 설정할 때 파일 저장소에 대해 지정하는 것과 같은 위치에 Lync Server 보관 파일을 저장합니다. 보관 파일 저장용으로 별도의 위치를 지정할 수는 없으므로, 보관 파일 저장을 위해 별도의 시스템 플랫폼이 필요하지는 않습니다. Microsoft Exchange 통합을 사용하는 경우 Exchange 2013에 있는 보관된 Lync 통신의 파일이 해당 Exchange 서버에 있는 사용자에 대해 Exchange 2013에 저장됩니다.

