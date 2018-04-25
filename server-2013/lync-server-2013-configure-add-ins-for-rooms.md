---
title: 'Lync Server 2013: 채팅방을 위한 추가 기능 구성'
TOCTitle: 채팅방을 위한 추가 기능 구성
ms:assetid: 4eeaf19e-8369-4f6f-af65-a283cf7daa1c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204878(v=OCS.15)
ms:contentKeyID: 49303599
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 채팅방을 위한 추가 기능 구성

 

_**마지막으로 수정된 항목:** 2013-02-21_

Lync Server 2013 제어판에서는 **영구 채팅** 페이지의 **추가 기능** 섹션을 사용하여 URL을 영구 채팅방과 연결할 수 있습니다. 이러한 URL은 대화 확장성 창의 채팅방에 있는 Lync 2013 클라이언트에 표시됩니다. 관리자가 등록된 추가 기능 목록에 추가 기능을 추가하고 채팅방 관리자/작성자가 등록된 추가 기능 중 하나와 방을 연결해야 사용자가 자신의 Lync 2013 클라이언트에서 이러한 업그레이드를 볼 수 있습니다.

추가 기능은 채팅방 내 환경을 확장하기 위해 사용됩니다. 일반적인 추가 기능에는 주식 시세 표시기를 채팅방에 게시할 때 이를 노출해서 주식 기록을 확장성 창에 표시하는 Silverlight 응용프로그램을 가리키는 URL이 포함될 수 있습니다. 다른 예로는 "Top of mind" 또는 "Topic of the day"와 같이 몇 가지 공유 컨텍스트를 포함하도록 채팅방에 OneNote 2013 URL을 추가 기능으로 포함하는 것을 들 수 있습니다.

## 채팅방의 추가 기능을 구성하려면

1.  CsPersistentChatAdministrator 또는 CsAdministrator 역할에 지정된 사용자 계정에서 내부 배포의 임의 컴퓨터에 로그온합니다.

2.  **시작** 메뉴에서 Lync Server 제어판을 선택하거나 브라우저 창을 열어 Admin URL을 입력합니다. Lync Server 제어판을 사용하여 시작할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하십시오.
    

    > [!IMPORTANT]
    > 또한 Windows PowerShell cmdlet을 사용할 수도 있습니다. 자세한 내용은 배포 설명서에서 <A href="configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md">Windows PowerShell cmdlet으로 영구 채팅 서버 구성</A>을 참조하십시오.



3.  왼쪽 탐색 모음에서 **영구 채팅**을 클릭한 후 **추가 기능** 을 클릭합니다.
    
    다중 영구 채팅 서버 풀 배포의 경우 드롭다운 목록에서 적합한 풀을 선택합니다.

4.  **추가 기능** 페이지에서 **새로 만들기** 를 클릭합니다.

5.  **서비스 선택** 에서 추가 기능을 만들려는 영구 채팅 서버 풀에 따라 서비스를 선택합니다. 추가 기능은 한 풀에서 다른 풀로 이동하거나 여러 풀 간에 공유할 수 없습니다.

6.  **새 추가 기능** 에서 다음을 수행합니다.
    
      - **이름** 에 새 추가 기능 이름을 지정합니다.
    
      - **URL** 에 추가 기능과 연결할 URL을 지정합니다. URL은 http 및 https 프로토콜로 제한됩니다.

7.  **커밋** 을 클릭합니다.

## 참고 항목

#### 작업

[Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)  

#### 개념

[Windows PowerShell cmdlet으로 영구 채팅 서버 구성](configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md)

