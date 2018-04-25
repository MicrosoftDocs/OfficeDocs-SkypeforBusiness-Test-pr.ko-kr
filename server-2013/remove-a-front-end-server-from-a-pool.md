---
title: 풀에서 프런트 엔드 서버 제거
TOCTitle: 풀에서 프런트 엔드 서버 제거
ms:assetid: 767225c9-7c0b-4d54-a407-d77134ba2abe
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688095(v=OCS.15)
ms:contentKeyID: 49885813
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 풀에서 프런트 엔드 서버 제거

 

_**마지막으로 수정된 항목:** 2012-10-04_

Microsoft Lync Server 2010 Enterprise Edition 프런트 엔드 서버는 독립 실행형 컴퓨터로 존재할 수 없습니다. 풀에서 단일 컴퓨터인 경우에도 프런트 엔드 풀로 정의되어야 합니다.

이 항목에서는 기존 프런트 엔드 풀로부터 개별 프런트 엔드 서버를 제거하는 프로세스에 대해 설명합니다. 프런트 엔드 서버가 풀에서 마지막 서버이거나 풀을 완전히 제거하는 경우, [프런트 엔드 풀 또는 Standard Edition 서버 제거](remove-front-end-pool-or-standard-edition-server.md)를 참조하십시오. 프런트 엔드 풀을 제거하기 전에는 개별 프런트 엔드 서버를 제거할 필요가 없습니다. 풀을 제거할 때는 각 프런트 엔드 서버를 제거합니다.

## 풀에서 프런트 엔드 서버를 제거하려면

1.  Lync Server 2013 프런트 엔드 서버를 열고 토폴로지 작성기를 엽니다.

2.  Lync Server 2010 노드로 이동합니다.

3.  **Enterprise Edition 프런트 엔드 풀** 을 확장하고, 제거하려는 프런트 엔드 서버가 포함된 프런트 엔드 풀을 확장하고, 제거하려는 프런트 엔드 서버를 마우스 오른쪽 단추로 클릭한 후 **삭제** 를 클릭합니다.

