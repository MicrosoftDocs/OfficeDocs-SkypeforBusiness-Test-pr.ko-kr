---
title: 'Lync Server 2013: 범주 간 채팅방 이동'
TOCTitle: 범주 간 채팅방 이동
ms:assetid: 7e93b8f6-5a18-4476-a432-3918e01bcfa6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ215877(v=OCS.15)
ms:contentKeyID: 49304173
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 범주 간 채팅방 이동

 

_**마지막으로 수정된 항목:** 2012-11-01_

채팅방을 만든 후에는 영구 채팅방의 범주를 변경하지 않는 것이 좋습니다. 하지만 채팅방 관리자가 다른 범주에 대해 **작성자** 권한을 갖고 있는 경우 방을 한 범주에서 다른 범주로 이동할 수 있습니다. 방은 삭제되지 않고 다시 만들어집니다. 데이터베이스 내의 연결에 대한 변경입니다.

채팅방 범주 변경은 드물게 수행됩니다. 범주는 해당 채팅방에 대해 허용되는 구성원 자격을 결정하므로 채팅방을 다른 범주로 이동하면 새 범주에 따라 더 이상 지원되지 않는 모든 SACL(시스템 액세스 제어 목록)이 삭제됩니다. 예를 들어 사용자가 특정 방의 구성원이었는데 새 범주에서는 더 이상 **AllowedMember**가 아닌 경우 방 구성원 자격이 수정되어 이 사용자가 방에서 제거됩니다.

Windows PowerShell 명령줄 인터페이스를 사용하여 채팅방을 이동하는 방법에 대한 자세한 내용은 [Windows PowerShell cmdlet으로 영구 채팅 서버 구성](configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md)에서 "방 관리"를 참조하십시오.

대화방 구성에 대한 자세한 내용은 배포 설명서의 [Lync Server 2013에서 채팅방 구성](lync-server-2013-configure-rooms.md)을 참조하십시오.

