---
title: 프런트 엔드 풀 또는 Standard Edition 서버 제거
TOCTitle: 프런트 엔드 풀 또는 Standard Edition 서버 제거
ms:assetid: 83c39a36-49a1-4ac6-9cc5-b0e441b1fdec
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688115(v=OCS.15)
ms:contentKeyID: 49885850
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 프런트 엔드 풀 또는 Standard Edition 서버 제거

 

_**마지막으로 수정된 항목:** 2012-10-04_

이 항목에서는 프런트 엔드 풀 또는 Standard Edition 프런트 엔드 서버를 제거하는 프로세스에 대해 설명합니다. 프런트 엔드 풀을 제거할 때는 풀 제거 프로세스 중에 풀에 속하는 각 프런트 엔드 서버를 제거합니다. Standard Edition 프런트 엔드 서버를 제거할 경우 토폴로지 작성기에서 SQL 저장소 정의를 제거해야 합니다.

## 프런트 엔드 서버 풀을 제거하려면

1.  토폴로지 작성기을 엽니다.

2.  Lync Server 2010 노드로 이동합니다.

3.  **Enterprise Edition 프런트 엔드 풀** 및 프런트 엔드 풀을 차례로 확장하고 제거하려는 프런트 엔드 풀을 마우스 오른쪽 단추로 클릭한 후 **삭제** 를 클릭합니다.

4.  토폴로지를 게시하고, 복제 상태를 확인하고 필요에 따라 Lync Server 배포 마법사를 실행합니다.

## Standard Edition 프런트 엔드 서버를 제거하려면

1.  토폴로지 작성기을 엽니다.

2.  Lync Server 2010 노드로 이동합니다.

3.  **Standard Edition 프런트 엔드 서버** 를 확장하고, 제거하려는 프런트 엔드 서버를 마우스 오른쪽 단추로 클릭한 후 **삭제** 를 클릭합니다.

4.  **SQL 저장소** 를 확장하고 Standard Edition 프런트 엔드 서버와 연결된 SQL Server 데이터베이스를 마우스 오른쪽 단추로 클릭한 후 **삭제** 를 클릭합니다.
    

    > [!IMPORTANT]
    > Standard Edition 프런트 엔드 서버에서 배치된 SQL Server 데이터베이스의 정의를 제거해야 합니다.



5.  토폴로지를 게시하고, 복제 상태를 확인하고 필요에 따라 Lync Server 배포 마법사를 실행합니다.

