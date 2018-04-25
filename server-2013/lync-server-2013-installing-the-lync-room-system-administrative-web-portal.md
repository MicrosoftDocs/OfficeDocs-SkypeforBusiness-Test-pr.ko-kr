---
title: Lync 채팅방 시스템 관리 웹 포털 설치
TOCTitle: Lync 채팅방 시스템 관리 웹 포털 설치
ms:assetid: dd19e368-c338-4e21-a40d-6439d46a9748
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn436326(v=OCS.15)
ms:contentKeyID: 59602780
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync 채팅방 시스템 관리 웹 포털 설치

 

_**마지막으로 수정된 항목:** 2015-04-09_

Microsoft 다운로드 센터([http://go.microsoft.com/fwlink/p/?LinkId=324044](http://go.microsoft.com/fwlink/p/?linkid=324044))에서 Microsoft Lync 채팅방 시스템 관리 웹 포털을 다운로드할 수 있습니다.

Lync 채팅방 시스템 관리 웹 포털을 설치하려면 다음 단계를 사용합니다.

1.  Lync Server 관리 셸에서 다음 cmdlet을 실행하여 신뢰할 수 있는 응용 프로그램 포트를 구성합니다.
    
        Set-CsWebServer -Identity POOLFQDN -MeetingRoomAdminPortalInternalListeningPort 4456 -MeetingRoomAdminPortalExternalListeningPort 4457

2.  회의실 포털을 설치하려면 **LyncRoomAdminPortal.exe**를 다운로드한 다음 관리자 권한으로 실행합니다.

3.  다음 위치에서 Web.config 파일을 엽니다.
    
    %Program Files%\\Microsoft Lync Server 2013\\Web Components\\Meeting Room Portal\\Int\\Handler\\

4.  Web.Config 파일에서 PortalUserName을 “Lync 채팅방 시스템 관리 포털을 위한 필수 구성 요소 구성”(이 단계에서는 이름으로 LRSApp이 권장됨) 섹션의 2단계에서 만든 사용자 이름으로 변경합니다.
    
        <add key="PortalUserName" value="sip:LRSApp@domain.com" />

5.  LRS 관리 포털은 신뢰할 수 있는 응용 프로그램이기 때문에 포털 구성에 암호를 제공하지 않아도 됩니다. 이 사용자가 로컬 등록자가 아닌 다른 등록자를 사용할 경우 Web.Config 파일에 다음 줄을 추가해 이에 대한 등록자를 지정해야 합니다.
    
        <add key="PortalUserRegistrarFQDN" value="pool-xxxx.domain.com" />

6.  사용된 포트가 5061이 아닌 경우 Web.Config 파일에 다음 줄을 추가합니다.
    
        <add key="PortalUserRegistrarPort" value="5061" />

## Lync 채팅방 시스템 관리 웹 포털의 설치 확인

Lync 채팅방 시스템 관리 웹 포털 설치를 확인하려면 다음을 실행합니다.


1.  프런트 엔드 서버에서 다음 URL로 이동합니다.
    
    https://\<fe-server\>/lrs
    
    다음 이미지와 같이 오류가 나타나지 않아야 합니다.
    
    ![Lync Room System 관리 포털 로그인 화면](images/Dn436326.050bcf70-2f3b-46b2-9b96-ebd12679b713(OCS.15).png "Lync Room System 관리 포털 로그인 화면")

2.  오류가 나타나지 않으면 토폴로지의 다른 컴퓨터에서 다음 URL에 액세스합니다.
    
    https://\<fe-server\>/lrs
    
    페이지에 액세스하려면 "자동 클라이언트 로그인에 필요한 DNS 레코드"([http://go.microsoft.com/fwlink/p/?LinkId=318056](http://go.microsoft.com/fwlink/p/?linkid=318056))에 설명되어 있는 대로 DNS 레코드를 추가해야 합니다.

