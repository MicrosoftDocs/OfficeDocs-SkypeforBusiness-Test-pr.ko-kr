---
title: 파일럿 풀 배포를 위한 DNS 레코드 구성
TOCTitle: 파일럿 풀 배포를 위한 DNS 레코드 구성
ms:assetid: eb421bad-4bf1-4837-a077-7795094692d9
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721921(v=OCS.15)
ms:contentKeyID: 49886037
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 파일럿 풀 배포를 위한 DNS 레코드 구성

 

_**마지막으로 수정된 항목:** 2012-09-29_

Lync Server 2013 파일럿 풀을 배포하기 전에 파일럿 풀에 대한 DNS 호스트 A 항목을 업데이트해야 합니다. 이 절차를 성공적으로 완료하려면 서버 또는 도메인에 Domain Admins 그룹의 구성원 또는 DnsAdmins 그룹의 구성원으로 로그온해야 합니다.

**DNS 호스트 A 레코드를 구성하려면**

1.  DNS(Domain Name System) 서버에서 **시작** , **관리 도구** 및 **DNS** 를 차례로 클릭합니다.

2.  도메인에 대한 콘솔 트리에서 **정방향 조회 영역** 을 확장하고 Lync Server 2013이 설치될 도메인을 마우스 오른쪽 단추로 클릭합니다.

3.  **새 호스트(A 또는 AAAA)** 를 클릭합니다.

4.  **이름** 을 클릭하고 Lync Server 2013 풀의 호스트 이름을 입력합니다. 여기서는 도메인 이름을 레코드가 정의된 영역에서 가져온 것으로 가정하므로 A 레코드의 일부로 입력할 필요는 없습니다.

5.  **IP 주소** 를 클릭하고 프런트 엔드 풀의 IP 주소를 입력합니다.

6.  **호스트 추가** 를 클릭한 다음 **확인** 을 클릭합니다.

7.  마쳤으면 **완료** 를 클릭합니다.

