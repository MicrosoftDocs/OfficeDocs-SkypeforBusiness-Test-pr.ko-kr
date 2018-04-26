---
title: 'Lync Server 2013: 영구 채팅에 대한 글로벌 정책 구성'
TOCTitle: 영구 채팅에 대한 글로벌 정책 구성
ms:assetid: 6176eb5c-19de-4c07-bcc0-2e38f8965966
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204951(v=OCS.15)
ms:contentKeyID: 49303805
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 영구 채팅에 대한 글로벌 정책 구성

 

_**마지막으로 수정된 항목:** 2012-10-06_

기본 글로벌 정책 자체를 사용해서 배포에 포함된 모든 사용자에 대해 영구 채팅 설정을 사용하도록 설정할 수 있습니다. 또한 영구 채팅이 특정 사용자 및 사이트에 대해 사용하거나 사용하지 않도록 설정되었는지 여부를 제어하기 위해 사이트 및 사용자에 대한 추가 정책을 지정할 수도 있습니다.

글로벌 정책은 삭제할 수 없습니다. 글로벌 정책을 삭제하려고 하면 구성이 기본값으로 다시 설정됩니다.


> [!NOTE]
> 영구 채팅 서버를 구성하고 사용하려면 먼저 토폴로지 작성기를 사용하여 토폴로지에 영구 채팅 서버 지원을 추가한 후에 토폴로지를 게시해야 합니다. 자세한 내용은 배포 설명서에서 <A href="lync-server-2013-adding-persistent-chat-server-to-your-deployment.md">Lync Server 2013에서 배포에 영구 채팅 서버 추가</A>를 참조하십시오.<BR>영구 채팅 서버 구성 설정을 구성하려면 배포 설명서에서 <A href="lync-server-2013-configure-persistent-chat-server-options-globally-or-for-persistent-chat-server-pool.md">Lync Server 2013에서 영구 채팅 서버 풀에 대해 또는 전역적으로 영구 채팅 서버 옵션 구성</A>을 참조하십시오.



## 영구 채팅용 글로벌 정책을 구성하려면

1.  CsPersistentChatAdministrator, CsAdministrator 또는 CsUserAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  **시작** 메뉴에서 Lync Server 제어판을 선택하거나 브라우저 창을 열고 관리 URL을 입력합니다. Lync Server 제어판을 시작하기 위해 사용할 수 있는 여러 방법들에 대한 자세한 내용은 작업 설명서에서 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하십시오.
    

    > [!IMPORTANT]
    > 또한 Windows PowerShell cmdlet을 사용할 수도 있습니다. 자세한 내용은 배포 설명서에서 <A href="configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md">Windows PowerShell cmdlet으로 영구 채팅 서버 구성</A>을 참조하십시오.



3.  Lync Server 제어판에서 **영구 채팅**을 클릭한 후 **영구 채팅 정책** 을 클릭합니다.

4.  정책 목록에서 **전역** 을 클릭하고 **편집** 을 클릭한 후에 **세부 정보 표시** 를 클릭합니다.

5.  **영구 채팅 정책 편집 - 전역**에서 다음을 수행합니다.
    
      - **이름** 에서 글로벌 정책의 새 이름을 지정합니다(기본값인 "전역"을 사용하지 않으려는 경우).
    
      - **설명** 에서 사용자 정책에 대한 자세한 설명을 입력합니다(예: *centralSiteName* 용 글로벌 정책).
    
      - 사이트 정책 또는 사용자 정책을 통해 제어되지 않는 모든 사이트 및 사용자에 대한 영구 채팅을 제어하려면 **영구 채팅 사용** 확인란을 선택하거나 선택을 취소합니다.

6.  **커밋** 을 클릭합니다.

