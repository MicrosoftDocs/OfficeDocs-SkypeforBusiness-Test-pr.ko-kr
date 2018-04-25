---
title: 'Lync Server 2013: 채팅방 비활성화 또는 활성화'
TOCTitle: 채팅방 비활성화 또는 활성화
ms:assetid: db0908fc-aae3-46e8-bc0b-245e9adfa1e2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ215883(v=OCS.15)
ms:contentKeyID: 49305216
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 채팅방 비활성화 또는 활성화

 

_**마지막으로 수정된 항목:** 2014-02-05_

영구 채팅 대화방의 주제가 더 이상 관련이 없는 경우 대화방을 사용하지 않도록 설정하여 사용자가 대화방을 사용할 수 없게 만들 수 있습니다.

사용하지 않도록 설정된 대화방은 나중에 영구 채팅 관리자가 사용하도록 설정할 수 있습니다. 대화방을 사용하지 않도록 설정하면 해당 구성원 자격 목록 및 기타 설정이 보존됩니다. 대화방을 다시 사용하도록 설정할 경우 설정을 수동으로 다시 만들 필요가 없습니다.

대화방 기록 보존은 범주 내 모든 대화방에 적용되는 범주에 대한 선택적 설정입니다. 기본 설정은 보존이지만 **채팅 기록 사용(Enable Chat History)**을 False로 설정하여 이 설정을 해제할 수 있습니다. 대화방의 기록이 보존되는 경우 대화방을 사용할 수 없어도 콘텐츠가 보존됩니다. 그러나 이러한 콘텐츠는 해당 대화방이 사용할 수 없는 상태로 유지되는 동안에는 검색 시 표시되지 않습니다. 나중에 대화방을 사용하도록 설정하면 대화방을 사용하지 않도록 설정하기 전에 게시되었던 메시지를 검색할 수 있습니다.

Windows PowerShell 명령줄 인터페이스로 대화방을 사용하거나 사용하지 않도록 설정하는 방법에 대한 자세한 내용은 [Windows PowerShell cmdlet으로 영구 채팅 서버 구성](configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md)의 "대화방 관리"를 참고하세요. 대화방을 사용하지 않도록 설정하려면 다음과 비슷한 명령을 사용합니다.

    Set-CsPersistentChatRoom -Identity "atl-cs-001.litwareinc.com\ITChatRoom" -Disabled $True

대화방을 사용하도록 설정하려면 사용 안 함 속성을 False로 설정합니다.

    Set-CsPersistentChatRoom -Identity "atl-cs-001.litwareinc.com\ITChatRoom" -Disabled $False

Lync Server 제어판을 사용하여 대화방을 사용하거나 사용하지 않도록 설정할 수는 없습니다.

대화방 구성에 대한 자세한 내용은 배포 설명서의 [Lync Server 2013에서 채팅방 구성](lync-server-2013-configure-rooms.md)을 참조하십시오.

