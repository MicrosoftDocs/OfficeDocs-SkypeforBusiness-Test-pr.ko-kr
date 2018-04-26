---
title: Office Communications Server 2007 R2 환경 확인
TOCTitle: Office Communications Server 2007 R2 환경 확인
ms:assetid: e051bdd5-e7ef-4754-8705-900b2c57f37c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721906(v=OCS.15)
ms:contentKeyID: 49886018
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Office Communications Server 2007 R2 환경 확인

 

_**마지막으로 수정된 항목:** 2012-10-16_

Office Communications Server 2007 R2와 함께 사용할 수 있도록 Lync Server 2013을 배포하려면 먼저 Office Communications Server 2007 R2 서비스가 구성되고 시작되었는지 확인해야 합니다.

**Office Communications Server 2007 R2 관리 도구를 사용하여 풀이 시작되었는지 확인**

1.  Office Communications Server 2007 R2 관리 도구를 엽니다.

2.  **Forest** 노드를 확장하고 **Standard Edition Server** 또는 **엔터프라이즈 풀** 노드를 확장한 다음 해당 풀 또는 서버 이름을 확장합니다.

3.  Standard Edition Server 또는 엔터프라이즈 풀에서 서비스가 실행 중인지 확인합니다.
    
    ![Office Communications Server 2007 R2 관리 콘솔](images/JJ721906.76897b6d-f433-47d2-930d-0816fc30a3c2(OCS.15).jpg "Office Communications Server 2007 R2 관리 콘솔")

**Office Communications Server 2007 R2에 대해 구성된 사용자 검토**

1.  Office Communications Server 2007 R2 관리 도구를 엽니다.

2.  **Forest** 노드를 확장하고 **Standard Edition Server** 또는 **엔터프라이즈 풀** 노드를 확장한 다음 해당 풀 또는 서버 이름을 확장합니다.

3.  **사용자**를 클릭합니다.

4.  Office Communications Server 2007 R2 사용자의 목록을 확인합니다.
    
    ![OCS 관리 도구의 사용자 목록](images/JJ721906.f6bb7c4f-cbed-4389-8d0a-69a28577f17a(OCS.15).jpg "OCS 관리 도구의 사용자 목록")

**레거시 XMPP 페더레이션 파트너 구성 확인**

1.  레거시 XMPP 서버에서 관리 도구\\서비스 애플릿을 이동합니다.

2.  Office Communications Server XMPP 게이트웨이 서비스가 시작되었는지 확인합니다.
    
    ![Office Communications Server XMPP 게이트웨이 서비스](images/JJ205231.23223724-3c4b-4cb9-ace2-1cab2c3c91c3(OCS.15).jpg "Office Communications Server XMPP 게이트웨이 서비스")

