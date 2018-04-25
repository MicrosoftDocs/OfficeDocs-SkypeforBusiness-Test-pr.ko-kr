---
title: 'Lync Server 2013: Lync 채팅방 시스템 관리 웹 포털에 대한 환경 구성'
TOCTitle: Lync 채팅방 시스템 관리 웹 포털에 대한 환경 구성
ms:assetid: 1bf3cc55-cfa8-46ee-a8bc-6dab3bff76b2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn436325(v=OCS.15)
ms:contentKeyID: 59602767
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync 채팅방 시스템 관리 웹 포털에 대한 Lync Server 2013 환경 구성

 

_**마지막으로 수정된 항목:** 2014-05-22_

LRS(Lync 채팅방 시스템) 관리 웹 포털을 사용하려면 다음 필수 구성 요소를 설치 또는 구성해야 합니다.


> [!IMPORTANT]
> 서버가 Kerberos 및 NTLM 인증을 모두 사용하여 구성되고 LRS가 도메인에 가입하지 않은 컴퓨터에서 실행 중인 경우, Kerberos 인증은 실패하고 사용자는 관리 포털에서 LRS의 상태를 볼 수 없습니다. 이 문제를 해결하려면 NTLM 인증이나 NTLM 및 TLS-DSK 인증(Kerberos 없음)을 모두 사용하여 서버를 구성하거나 LRS 컴퓨터를 도메인에 가입합니다.



1.  Lync Server 토폴로지에 Lync Server 2013 누적 업데이트: 2013년 7월을 설치합니다.
    
    업데이트를 받거나 업데이트에 포함된 항목을 확인하려면 [Lync Server 2013에 대한 업데이트](http://go.microsoft.com/fwlink/p/?linkid=323959)를 참고하세요.

2.  SIP 사용 Active Directory 사용자를 만듭니다.
    
    LRS 관리 웹 포털에서는 이러한 자격 증명을 사용하여 Lync Server에서 정보를 쿼리합니다. 권장 사용자 이름은 LRSApp입니다.

3.  LRSSupportAdminGroup이라는 이름의 Active Directory 보안 그룹을 만듭니다.
    
    해당 그룹의 그룹 범위를 전역으로 지정하고 그룹 종류를 보안으로 지정합니다. 이 그룹에 추가된 SIP 사용 사용자에게는 채팅방 목록을 보고 로그 수집 등의 특정 명령을 실행할 수 있는 권한이 부여됩니다.

4.  LRSFullAccessAdminGroup이라는 이름의 Active Directory 보안 그룹을 만듭니다.
    
    해당 그룹의 그룹 범위를 전역으로 지정하고 그룹 종류를 보안으로 지정합니다. 이 그룹에 추가된 SIP 사용 사용자에게는 모든 관리 포털 기능을 사용할 수 있는 권한이 부여됩니다.
    
     
    
    ![보안 그룹 역할이 있는 관리 그룹 목록](images/Dn436325.5d432819-a2e2-452c-bc2a-5d4ee79d8c33(OCS.15).png "보안 그룹 역할이 있는 관리 그룹 목록")  
    
     

5.  LRSFullAccessAdminGroup을 LRSSupportAdminGroup의 구성원으로 추가합니다.
    
    ![LRSSupportAdminGroup 속성 구성원 페이지](images/Dn436325.91a4a28a-cacf-4ef6-aac1-915ec41c9648(OCS.15).png "LRSSupportAdminGroup 속성 구성원 페이지")  
    
     

6.  LRSSupport라는 이름의 SIP 사용 Active Directory 사용자를 만듭니다. 이 사용자를 LRSSupportAdminGroup에 추가합니다.
    
    ![LRSSupportAdminGroup 속성 구성원 페이지](images/Dn436325.7638055d-22ac-4909-914d-1966f5623909(OCS.15).png "LRSSupportAdminGroup 속성 구성원 페이지")  
    
     

7.  Microsoft 다운로드 센터([http://go.microsoft.com/fwlink/p/?LinkId=323967](http://go.microsoft.com/fwlink/p/?linkid=323967))에서 제공하는 Visual Studio 2010 SP1 및 Visual Web Developer 2010 SP1용 ASP.NET MVC 4를 설치하세요.

