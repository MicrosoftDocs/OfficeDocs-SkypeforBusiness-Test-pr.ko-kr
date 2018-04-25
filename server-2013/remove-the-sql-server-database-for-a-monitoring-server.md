---
title: 모니터링 서버용 SQL Server 데이터베이스 제거
TOCTitle: 모니터링 서버용 SQL Server 데이터베이스 제거
ms:assetid: aed5e394-d63e-4ad4-af40-f12d3a044344
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721848(v=OCS.15)
ms:contentKeyID: 49885929
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 모니터링 서버용 SQL Server 데이터베이스 제거

 

_**마지막으로 수정된 항목:** 2012-10-04_

Microsoft Lync Server 2010  모니터링 서버를 제거한 후에는 서버 데이터를 호스팅한 SQL Server 데이터베이스를 제거할 수 있습니다. 토폴로지 작성기에서 정의를 제거한 후 데이터베이스 서버에서 데이터베이스 및 로그 파일을 제거하려면 다음 절차를 따르십시오.

## 토폴로지 작성기를 사용하여 SQL Server 데이터베이스를 제거하려면

1.  Lync Server 2013 프런트 엔드 서버에서 토폴로지 작성기를 엽니다.

2.  토폴로지 작성기에서 **공유 구성 요소**, **SQL Server 저장소** 로 이동한 후 제거되었거나 다시 구성된 모니터링 서버와 연결된 SQL Server 인스턴스를 마우스 오른쪽 단추로 클릭한 후 **삭제** 를 클릭합니다.

3.  토폴로지를 게시한 후 복제 상태를 확인합니다.

## SQL Server에서 데이터베이스 파일을 제거하려면

1.  SQL Server 기반 서버에서 데이터베이스를 제거하려면 사용자가 데이터베이스 파일을 제거하려는 SQL Server 서버에 대해 SQL Server sysadmins 그룹의 구성원이어야 합니다.

2.  Lync Server 관리 셸를 엽니다.

3.  명령줄에 다음을 입력합니다.
    
        Uninstall-CsDataBase -DatabaseType Monitoring -SqlServerFqdn <FQDN> [-SqlInstanceName <instance>]
    
    여기서 *\<FQDN\>* 은 데이터베이스 서버의 FQDN(정규화된 도메인 이름)이며, *\<인스턴스\>* 는 선택적인 명명된 데이터베이스 인스턴스입니다.

4.  **Uninstall-CsDataBase** cmdlet에서 작업을 확인하라는 메시지가 표시되면 해당 정보를 읽고, 계속하려면 **Y** (또는 Enter 키)를 누르고, cmdlet을 중지하려면 **N** 을 누른 후 Enter 키를 누릅니다(즉, 오류가 있을 경우에 대비하여).

