---
title: 'Lync Server 2013: 사용자 또는 사용자 그룹에 영구 채팅 정책 적용'
TOCTitle: 사용자 또는 사용자 그룹에 영구 채팅 정책 적용
ms:assetid: 809ef4e0-8d42-4feb-b7c0-3995f39867a7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205038(v=OCS.15)
ms:contentKeyID: 49304194
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 사용자 또는 사용자 그룹에 영구 채팅 정책 적용

 

_**마지막으로 수정된 항목:** 2012-10-06_

사용자가 Lync Server 2013에 대해 설정된 경우 영구 채팅 서버에 대해 사용하거나 사용하지 않도록 설정하기 위해 특정 사용자에게 적절한 정책을 적용할 수 있습니다.


> [!NOTE]
> 영구 채팅 서버를 구성하고 사용하려면 먼저 토폴로지 작성기를 사용하여 토폴로지에 영구 채팅 서버 지원을 추가한 후에 토폴로지를 게시해야 합니다. 자세한 내용은 배포 설명서에서 <A href="lync-server-2013-adding-persistent-chat-server-to-your-deployment.md">Lync Server 2013에서 배포에 영구 채팅 서버 추가</A>를 참조하십시오.<BR>영구 채팅 서버 구성 설정을 구성하려면 배포 설명서에서 <A href="lync-server-2013-configure-persistent-chat-server-options-globally-or-for-persistent-chat-server-pool.md">Lync Server 2013에서 영구 채팅 서버 풀에 대해 또는 전역적으로 영구 채팅 서버 옵션 구성</A>을 참조하십시오.



이 항목의 절차를 사용하여 이전에 만든 영구 채팅 사용자 정책을 하나 이상의 사용자 계정 또는 사용자 그룹에 적용합니다.

## 사용자 계정에 영구 채팅 사용자 정책을 적용하려면

1.  CsPersistentChatAdministrator, CsAdministrator 또는 CsUserAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  **시작** 메뉴에서 Lync Server 제어판을 선택하거나 브라우저 창을 열어 Admin URL을 입력합니다. Lync Server 제어판을 사용하여 시작할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하십시오.

3.  왼쪽 탐색 모음에서 **사용자** 를 클릭하고 구성할 사용자 계정을 검색합니다.

4.  검색 결과가 나열된 표에서 사용자 계정을 클릭하고 **편집** 을 클릭한 후에 **자세한 정보 표시** 를 클릭합니다.

5.  **Lync Server 사용자 편집** 의 **영구 채팅 정책** 에서 적용할 영구 채팅 사용자 정책을 선택합니다.
    

    > [!NOTE]
    > <STRONG>&lt;자동&gt;</STRONG> 설정을 선택하면 기본 유효 정책이 적용됩니다. 이러한 설정은 서버에 의해 자동으로 적용됩니다.



6.  **커밋** 을 클릭합니다.

