---
title: 'Lync Server 2013: 채팅방 또는 범주 삭제'
TOCTitle: 채팅방 또는 범주 삭제
ms:assetid: adccb869-0015-4eba-ac73-718bac7843b5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ215881(v=OCS.15)
ms:contentKeyID: 49304714
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 채팅방 또는 범주 삭제

 

_**마지막으로 수정된 항목:** 2012-11-01_

영구 채팅 대화방은 삭제할 수 있습니다. 또한 더 이상 사용되지 않는 대화방이 있는 경우 사용하지 않도록 설정할 수 있습니다. 자세한 내용은 [Lync Server 2013에서 채팅방 비활성화 또는 활성화](lync-server-2013-disabling-or-enabling-a-chat-room.md)을 참조하십시오.

영구 채팅 관리자는 사용하지 않도록 설정된 대화방을 쿼리할 수 있으며, Windows PowerShell cmdlet인 **Remove-CsPersistentChatRoom**을 사용하여 대화방을 정기적으로 삭제하고 영구적으로 삭제할 수 있습니다.

범주는 삭제할 수 있습니다. 그러나 범주를 삭제하려면 먼저 범주 아래에 있는 모든 대화방을 삭제하거나 새 범주로 이동하여, 삭제 가능한 비어 있는 범주로 만들어야 합니다. 영구 채팅 서버에서는 대화방이 포함된 범주를 삭제할 수 없습니다. 자세한 내용은 [Lync Server 2013에서 범주 간 채팅방 이동](lync-server-2013-moving-a-chat-room-from-one-category-to-another.md)을 참조하십시오.

Windows PowerShell 명령줄 인터페이스을 사용하여 비어 있는 범주를 삭제하는 방법에 대한 자세한 내용은 [Windows PowerShell cmdlet으로 영구 채팅 서버 구성](configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md)에서 "대화방 관리"를 참조하십시오.

대화방과 범주에 대한 자세한 내용은 배포 설명서에서 [Lync Server 2013에서 채팅방 구성](lync-server-2013-configure-rooms.md) 및 [Lync Server 2013에서 범주 구성](lync-server-2013-configure-categories.md)을 참조하십시오.

