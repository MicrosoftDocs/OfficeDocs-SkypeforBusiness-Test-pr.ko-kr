---
title: "Lync Server 2013: 기존 Lync Server Enterprise에 Lync Server Standard Edition 배포"
TOCTitle: 기존 Lync Server 2013 Enterprise에 Lync Server 2013 Standard Edition 배포
ms:assetid: 05ea128d-6c94-49b3-b28b-477367196425
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398112(v=OCS.15)
ms:contentKeyID: 49302684
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 기존 Lync Server 2013 Enterprise에 Lync Server 2013 Standard Edition 배포

 

_**마지막으로 수정된 항목:** 2012-10-01_

기존 Enterprise Edition 배포에 Standard Edition 서버를 배포하는 과정은 추가 서버 역할을 배포하는 과정과 비슷합니다. Standard Edition 서버는 다른 사이트에 배포하여 해당 사이트의 사용자가 WAN(광역 네트워크)에서 프런트 엔드 풀이 아닌 Standard Edition 서버로 이동하도록 허용할 수 있습니다. 새 사이트를 설치하고 해당 사이트에 서버를 설치하는 절차는 이미 [Lync Server 2013 배포](lync-server-2013-deploying-lync-server.md) 설명서의 다른 섹션에 정의되어 있습니다.

**새 사이트를 정의하려면**

1.  토폴로지 작성기 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 토폴로지 작성기**를 클릭합니다.

2.  콘솔 트리에서 **Lync Server 2013**을 마우스 오른쪽 단추로 클릭하고 **새 중앙 사이트** 를 클릭합니다.

3.  **사이트 지정** 페이지에서 사이트 이름을 지정하고 원하는 경우 설명을 입력합니다.

4.  절차에 따라 사이트 토폴로지의 나머지 부분을 정의합니다. 자세한 내용은 [Lync Server 2013에서 토폴로지 정의 및 구성](lync-server-2013-defining-and-configuring-the-topology.md)을 참조하십시오.

5.  업데이트된 토폴로지를 게시합니다. 자세한 내용은 [Lync Server 2013에서 토폴로지 게시](lync-server-2013-publish-the-topology.md)를 참조하십시오.

6.  Standard Edition 서버를 설정 및 설치합니다.
    

    > [!WARNING]
    > Standard Edition 서버만 포함된 환경을 배포한 경우에는 Lync Server 배포 마법사에서 설치 프로세스를 시작했으며, <STRONG>첫 번째 Standard Edition 서버 준비</STRONG> 링크를 사용하여 새 Standard Edition 서버에 초기 데이터베이스 파일을 설치한 것입니다. 기존 Lync Server 2013 배포에 Standard Edition 서버를 설치할 때는 해당 프로세스를 따르지 <STRONG>마십시오</STRONG>.


