---
title: Lync Server 2013, 영구 채팅 서버 관리
TOCTitle: Lync Server 2013, 영구 채팅 서버 관리
ms:assetid: 82befdc6-5d32-45f1-bfd7-aaedffed1ab8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398657(v=OCS.15)
ms:contentKeyID: 49304218
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013, 영구 채팅 서버 관리

 

_**마지막으로 수정된 항목:** 2012-10-11_

Lync Server 2013영구 채팅 서버를 사용하면 여러 사용자가 대화에 참가하여 텍스트, 링크, 파일 등의 특정 항목에 대한 콘텐츠를 게시하고 액세스할 수 있습니다. 사용자는 세션 중에 실시간으로 통신할 수 있지만 각 세션의 내용이 지속적으로 유지될 수 있습니다. 즉, 세션이 끝난 후에도 해당 내용을 계속 사용할 수 있습니다.

영구 채팅방 내용은 긴 메시지( *이야기* )와 하이퍼링크, 이모티콘 및 업로드한 문서를 포함할 수도 있지만 주로 짧은 텍스트 메시지로 구성됩니다.


> [!NOTE]
> 파일 업로드 및 다운로드는 Lync 2013 클라이언트에서 지원되지 않지만 Lync Server 2013, 영구 채팅 서버에서 계속 지원됩니다. 레거시 그룹 채팅 클라이언트는 파일을 게시하고 볼 수 있지만 동일 채팅방을 Lync 2013 클라이언트를 통해 액세스할 경우 파일에 액세스할 수 없습니다.



채팅방에 대한 액세스는 구성원 자격 목록에 의해 제어됩니다. 전체 채팅방 내용은 모든 구성원이 시간별 검토 또는 전체 텍스트 검색에 이용할 수 있습니다. 영구 채팅 클라이언트 사용에 대한 자세한 내용은 계획 설명서의 [Lync Server 2013의 클라이언트 계획](lync-server-2013-planning-for-clients.md) 및 배포 설명서의 [Lync Server 2013에서 클라이언트 및 장치 배포](lync-server-2013-deploying-clients-and-devices.md)를 참조하십시오.

조직에 대해 영구 채팅 서버를 설정할 경우, 배포 중 초기 구성을 지정합니다. 하지만 일부 경우에는 영구 채팅 서버 지원의 구현 방법을 변경해야 할 수 있습니다. 예를 들어 조직 내 특정 팀 또는 그룹에 대해 영구 채팅 서버 지원 및 제어를 다르게 설정해야 할 수 있습니다. 이 섹션에서는 영구 채팅 서버 배포를 사용자 지정하는 데 도움이 되는 정보 및 절차를 제공합니다. 영구 채팅 서버에 대해 구성할 수 있는 기능에 대한 자세한 내용은 계획 설명서의 [Lync Server 2013에서 영구 채팅 서버에 대한 조직 요구 사항 정의](lync-server-2013-defining-your-requirements-for-persistent-chat-server.md) 및 계획 설명서, 배포 설명서 또는 작업 설명서의 [Lync Server 2013에서 영구 채팅 서버의 작동 방법](lync-server-2013-how-persistent-chat-server-works.md)을 참조하십시오. Lync Server 2013용 영구 채팅 서버 배포에 대한 자세한 내용은 배포 설명서에서 [Lync Server 2013에서 영구 채팅 서버 배포](lync-server-2013-deploying-persistent-chat-server.md)를 참조하십시오.

## 이 단원의 내용

  - [Lync Server 2013에서 영구 채팅 서버의 작동 방법](lync-server-2013-how-persistent-chat-server-works.md)

  - [범주를 사용하여 영구 채팅 서버 관리](using-categories-to-administer-persistent-chat-server.md)

  - [영구 채팅 구성원 자격 이해](understanding-persistent-chat-membership.md)

  - [영구 채팅 서버 모범 사례](persistent-chat-server-best-practices.md)

  - [Lync Server 2013에서 범주, 채팅방 및 추가 기능 관리](lync-server-2013-managing-categories-rooms-and-add-ins.md)

  - [Lync Server 2013에서 영구 채팅 사용자 액세스 관리](lync-server-2013-managing-persistent-chat-user-access.md)

  - [Lync Server 2013에서 영구 채팅 시스템 운영 및 유지 관리](lync-server-2013-operating-and-maintaining-the-persistent-chat-system.md)

