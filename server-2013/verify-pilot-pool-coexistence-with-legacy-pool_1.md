---
title: 레거시 풀과 파일럿 풀 동시 사용 확인
TOCTitle: 레거시 풀과 파일럿 풀 동시 사용 확인
ms:assetid: 597d0fa6-ca04-4521-b1c2-72d7f35ecd08
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204914(v=OCS.15)
ms:contentKeyID: 49303725
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 레거시 풀과 파일럿 풀 동시 사용 확인

 

_**마지막으로 수정된 항목:** 2012-09-28_

## Office Communications Server 2007 R2 관리 도구에서 풀 확인

1.  Office Communications Server 2007 R2 관리 도구를 엽니다.

2.  **포리스트** 노드를 확장하고 **Standard Edition 서버** 또는 **엔터프라이즈 풀** 노드를 확장한 다음 해당 풀 또는 서버 이름을 확장합니다.

3.  Office Communications Server 2007 R2 서비스가 풀에서 실행되고 있는지 확인합니다.
    
    ![Office Communications Server 2007 R2 관리 콘솔](images/JJ721906.76897b6d-f433-47d2-930d-0816fc30a3c2(OCS.15).jpg "Office Communications Server 2007 R2 관리 콘솔")  

## Lync Server 2013 제어판에서 파일럿 풀 확인

1.  CsAdministrator 역할의 구성원인 사용자 계정에서 Lync Server 2013 프런트 엔드 서버에 로그인합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  **토폴로지** 를 클릭합니다.

4.  배포한 서버가 파일럿 풀에 있는지 확인합니다.
    
    ![Lync Server 제어판 토폴로지 페이지](images/JJ204914.a3d1ba5f-c1a7-45e8-b9a5-7cb07b01af8c(OCS.15).jpg "Lync Server 제어판 토폴로지 페이지")  

## Lync Server 2013 서비스가 시작되었는지 확인

1.  Lync Server 2013 프런트 엔드 서버의 **관리 도구** 그룹에서 **서비스** 애플릿을 엽니다.

2.  나열된 서비스가 다음 그림의 목록과 일치하는지 확인합니다.
    
    ![시작된 Lync 서비스를 보여 주는 서비스 페이지](images/JJ204914.fd35d54a-2ab6-4c09-b5e9-fd5bf10f6f51(OCS.15).jpg "시작된 Lync 서비스를 보여 주는 서비스 페이지")

