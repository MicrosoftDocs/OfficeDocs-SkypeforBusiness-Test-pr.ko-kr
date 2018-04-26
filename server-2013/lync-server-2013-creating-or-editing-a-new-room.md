---
title: 'Lync Server 2013: 새 채팅방 만들기 및 편집'
TOCTitle: 새 채팅방 만들기 및 편집
ms:assetid: aa8f4349-cfd9-4036-9c4d-de8fb2c4c8a4
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ215880(v=OCS.15)
ms:contentKeyID: 49304674
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 새 채팅방 만들기 및 편집

 

_**마지막으로 수정된 항목:** 2015-03-19_

영구 채팅 대화방 구성은 일반적으로 사용자가 처리하며 영구 채팅 관리자는 대개 대화방을 구성하거나 관리하지 않습니다. 대화방을 관리하는 Windows PowerShell cmdlet은 **CsPersistentChatAdministrator** 관리자만 사용할 수 있습니다.

특정 범주의 **만든 이**인 사용자는 Lync 클라이언트를 사용하여 대화방을 만들고 관리할 수 있습니다. 특정 대화방의 관리자로 지정된 사용자도 대화방 속성 또는 구성원과 같은 대화방의 지속적인 관리를 수행할 수 있습니다.


> [!TIP]
> 영구 채팅 관리자도 만든 이가 될 수 있으며 만든 이에게 부과되는 제한이 적용되지 않습니다.



영구 채팅 관리자는 원할 경우 Windows PowerShell cmdlet 대신에 사용자 인터페이스를 사용하여 대화방을 만들고 관리할 수 있습니다. 이를 위해 관리자가 영구 채팅 서버에서 SIP를 사용할 수 있도록 설정해야 합니다. 그러면 관리자가 Lync 클라이언트를 사용하여 대화방을 만들고 관리할 수 있습니다.

사용자에 대한 사용자 지정 대화방 관리 워크플로를 만들려는 경우 사용자를 Lync 클라이언트에서 해당 사용자 지정 솔루션으로 리디렉션하도록 영구 채팅 서버 구성의 **RoomManagementUrl** 속성을 설정할 수 있습니다.

Windows PowerShell 명령줄 인터페이스을 사용하여 대화방을 구성하는 방법에 대한 자세한 내용은 [Windows PowerShell cmdlet으로 영구 채팅 서버 구성](configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md)에서 "대화방 관리"를 참조하십시오.

대화방 구성에 대한 자세한 내용은 배포 설명서의 [Lync Server 2013에서 채팅방 구성](lync-server-2013-configure-rooms.md)을 참조하십시오.

