---
title: 'Lync Server 2013: 영구 채팅 서버 정책 사용'
TOCTitle: 영구 채팅 서버 정책 사용
ms:assetid: 87063d6c-2e38-4970-b76d-2aa15f0de29e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205056(v=OCS.15)
ms:contentKeyID: 49304278
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 영구 채팅 서버 정책 사용

 

_**마지막으로 수정된 항목:** 2012-10-06_

Lync Server 2013 제어판에서는 **영구 채팅** 그룹의 **영구 채팅 정책** 페이지를 통해 기본 글로벌 정책 구성, 하나 이상의 추가 사용자 및 배포에 대한 사이트 정책 만들기 등을 포함하여 전역, 풀, 사이트 또는 사용자 수준에서 정책을 관리할 수 있습니다. 사용자가 정책에 의해 영구 채팅 서버에서 사용하도록 설정된 경우 영구 채팅 서버 환경이 해당 Lync 2013 클라이언트에 표시됩니다.


> [!NOTE]
> 토폴로지에서 영구 채팅 서버 사이트 정책은 전역, 사용자 풀 또는 사용자 사이트나 사용자별로 적용됩니다.



글로벌 정책은 영구 채팅 서버을 배포할 때 자동으로 만들어지며 구성할 수 있지만 삭제할 수는 없습니다. 글로벌 정책은 모든 사용자에게 적용되므로 사용자별로 설정할 필요가 없습니다.

글로벌 정책과 함께 영구 채팅 서버에 대해 사용자를 사용하도록 설정하는 여러 개의 사이트 및 사용자 정책을 만들고 구성할 수 있습니다. 풀 및 사이트 영구 채팅 서버 정책은 전역 영구 채팅 서버 정책을 재정의하지만 해당 사이트의 사용자로만 제한됩니다. 사용자 정책은 사용자 정책이 지정된 사용자에 대한 전역, 풀 및 사이트 정책을 모두 재정의합니다.


> [!NOTE]
> 영구 채팅 서버를 구성하고 사용하려면 먼저 토폴로지 작성기를 사용하여 토폴로지에 영구 채팅 서버 지원을 추가한 후에 토폴로지를 게시해야 합니다. 자세한 내용은 배포 설명서에서 <A href="lync-server-2013-adding-persistent-chat-server-to-your-deployment.md">Lync Server 2013에서 배포에 영구 채팅 서버 추가</A>를 참조하십시오.



## 이 섹션의 내용

  - [Lync Server 2013에서 영구 채팅에 대한 글로벌 정책 구성](lync-server-2013-configure-the-global-policy-for-persistent-chat.md)

  - [Lync Server 2013에서 영구 채팅에 대한 사이트 정책 만들기](lync-server-2013-create-a-site-policy-for-persistent-chat.md)

  - [Lync Server 2013에서 영구 채팅에 대한 사용자 정책 만들기](lync-server-2013-create-a-user-policy-for-persistent-chat.md)

  - [Lync Server 2013에서 사용자 또는 사용자 그룹에 영구 채팅 정책 적용](lync-server-2013-apply-a-persistent-chat-policy-to-a-user-or-user-group.md)

