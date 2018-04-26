---
title: 'Lync Server 2013: 프런트 엔드 풀과 연결된 에지 풀 변경'
TOCTitle: 프런트 엔드 풀과 연결된 에지 풀 변경
ms:assetid: 369468c7-2c0b-48cc-bbc3-825dad7b85aa
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688023(v=OCS.15)
ms:contentKeyID: 49885724
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 프런트 엔드 풀과 연결된 에지 풀 변경

 

_**마지막으로 수정된 항목:** 2012-09-21_

에지 풀이 다운되었는데 동일 사이트의 프런트 엔드 풀은 계속 실행되는 경우에는 오류가 발생한 에지 풀을 복원하는 동안 다른 사이트의 에지 풀을 사용하도록 프런트 엔드 풀을 설정해야 합니다.

## 프런트 엔드 풀과 연결된 에지 풀 변경

1.  토폴로지 작성기에서 변경해야 하는 프런트 엔드 풀의 이름을 탐색합니다.

2.  풀을 마우스 오른쪽 단추로 클릭한 다음 **속성 편집** 을 클릭합니다.

3.  **연결** 섹션의 **에지 풀 연결(미디어 구성 요소)** 에서 드롭다운 상자를 사용하여 이 프런트 엔드 풀과 연결할 에지 풀을 선택합니다.

4.  **확인** 을 클릭합니다.

## 참고 항목

#### 개념

[Lync Server 2013의 에지 서버 재해 복구](lync-server-2013-edge-server-disaster-recovery.md)

