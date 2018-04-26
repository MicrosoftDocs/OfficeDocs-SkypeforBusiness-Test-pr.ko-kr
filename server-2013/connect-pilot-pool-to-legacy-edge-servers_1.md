---
title: 레거시 에지 서버에 파일럿 풀 연결
TOCTitle: 레거시 에지 서버에 파일럿 풀 연결
ms:assetid: 9ed13c41-f3ab-4e1d-beb6-a00152c541e2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205136(v=OCS.15)
ms:contentKeyID: 49304551
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 레거시 에지 서버에 파일럿 풀 연결

 

_**마지막으로 수정된 항목:** 2012-10-02_

Lync Server 2013을 배포한 후 이 사이트에 대한 페더레이션 경로가 구성되지 않았습니다. Office Communications Server 2007 R2에서 사용 중인 페더레이션 경로를 사용하려면 이 경로를 사용하도록 Lync Server 2013을 구성해야 합니다.

Lync Server 2013 사이트가 BackCompatSite의 디렉터 및 에지 서버를 사용하도록 설정하려면 토폴로지 작성기를 사용하여 레거시 에지 풀을 연결합니다.

## 토폴로지 작성기를 사용하여 레거시 에지 풀을 연결하려면

1.  토폴로지 작성기에서 파일럿 풀을 열려면

2.  Lync Server 2013 사이트를 선택합니다.

3.  **동작** 메뉴에서 **속성 편집** 을 클릭합니다.

4.  **사이트 페더레이션 경로 지정**에서 **SIP 페더레이션 사용**을 선택한 후 Office Communications Server 2007 R2 디렉터를 선택하고, 디렉터가 나열되지 않은 경우 Office Communications Server 2007 R2 에지 서버를 선택합니다.
    
    ![속성 편집 대화 상자, 페더레이션 경로 페이지](images/JJ205136.bc13014b-3578-4d9e-9ff7-bdd09130b676(OCS.15).jpg "속성 편집 대화 상자, 페더레이션 경로 페이지")  

5.  **확인** 을 클릭하여 **속성 편집** 페이지를 닫습니다.

6.  토폴로지 작성기의 Lync Server 2013 노드에서 **Standard Edition Server** 또는 **Enterprise Edition 프런트 엔드 풀** 로 이동하고, 풀을 마우스 오른쪽 단추로 클릭한 후 **속성 편집** 을 클릭합니다.

7.  **연결** 에서 **에지 풀 연결(미디어 구성 요소)** 옆의 확인란을 선택합니다.

8.  목록에서 BackCompatSite에 대한 에지 서버 인터페이스를 선택합니다.
    
    ![속성 편집 대화 상자, 일반 페이지](images/JJ205136.75045212-03ca-4b82-8337-5dacb487094f(OCS.15).jpg "속성 편집 대화 상자, 일반 페이지")  

9.  **확인** 을 클릭하여 **속성 편집** 페이지를 닫습니다.

10. **토폴로지 작성기** 에서 맨 위에 있는 **Lync Server** 노드를 선택합니다.

11. **동작** 메뉴에서 **토폴로지 게시** 를 클릭하고 **다음** 을 클릭합니다.

12. **게시 마법사** 가 완료되면 **마침** 을 클릭합니다.

