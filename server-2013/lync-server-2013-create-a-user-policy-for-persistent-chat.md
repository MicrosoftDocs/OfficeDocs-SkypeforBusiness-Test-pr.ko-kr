---
title: 'Lync Server 2013: 영구 채팅에 대한 사용자 정책 만들기'
TOCTitle: 영구 채팅에 대한 사용자 정책 만들기
ms:assetid: aa3774af-d442-4206-8a68-2fbb9102e9d6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205170(v=OCS.15)
ms:contentKeyID: 49304669
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 영구 채팅에 대한 사용자 정책 만들기

 

_**마지막으로 수정된 항목:** 2012-10-06_

Lync Server 제어판에서는 **사용자** 에서 사용자에게 할당할 수 있는 사용자 정책을 정의합니다.

사용자 정책은 해당 정책이 할당된 특정 사용자에 한해 전역 정책 및 사이트 정책을 재정의합니다.


> [!NOTE]
> 영구 채팅 서버를 구성하고 사용하려면 먼저 토폴로지 작성기를 사용하여 토폴로지에 영구 채팅 서버 지원을 추가한 후에 토폴로지를 게시해야 합니다. 자세한 내용은 배포 설명서에서 <A href="lync-server-2013-adding-persistent-chat-server-to-your-deployment.md">Lync Server 2013에서 배포에 영구 채팅 서버 추가</A>를 참조하십시오.<BR>영구 채팅 서버 구성 설정을 구성하려면 배포 설명서에서 <A href="lync-server-2013-configure-persistent-chat-server-options-globally-or-for-persistent-chat-server-pool.md">Lync Server 2013에서 영구 채팅 서버 풀에 대해 또는 전역적으로 영구 채팅 서버 옵션 구성</A>을 참조하십시오.



## 영구 채팅에 대한 사용자 정책을 만들려면

1.  CsPersistentChatAdministrator, CsAdministrator 또는 CsUserAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  **시작** 메뉴에서 Lync Server 제어판을 선택하거나 브라우저 창을 열어 Admin URL을 입력합니다. Lync Server 제어판을 사용하여 시작할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하십시오.
    

    > [!IMPORTANT]
    > 또한 Windows PowerShell cmdlet을 사용할 수도 있습니다. 배포 설명서에서 <A href="configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md">Windows PowerShell cmdlet으로 영구 채팅 서버 구성</A>을 참조하십시오.



3.  왼쪽 탐색 모음에서 **영구 채팅**을 클릭하고 **영구 채팅 정책** 을 클릭합니다.

4.  **새로 만들기** 를 클릭하고 **사용자 정책** 을 클릭합니다.

5.  **새 영구 채팅 정책**에서 다음을 수행합니다.
    
      - **이름** 에 새 사용자 정책의 이름을 지정합니다.
    
      - **설명** 에 사용자 정책에 대한 자세한 설명을 입력합니다(예: 특정 사용자에 대한 영구 채팅 정책).
    
      - 사용자 정책을 통해 특별히 제어되지 않는 모든 사용자에 대해 영구 채팅을 제어하려면 **영구 채팅 사용** 확인란을 선택하거나 선택 취소합니다.

6.  **커밋** 을 클릭합니다.

