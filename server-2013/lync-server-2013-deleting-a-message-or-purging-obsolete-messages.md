---
title: 'Lync Server 2013: 메시지 삭제 또는 오래된 메시지 제거'
TOCTitle: 메시지 삭제 또는 오래된 메시지 제거
ms:assetid: 3f0c612d-6dfd-41a4-a5fe-5ff3448eb0ce
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ215874(v=OCS.15)
ms:contentKeyID: 49303412
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 메시지 삭제 또는 오래된 메시지 제거

 

_**마지막으로 수정된 항목:** 2014-02-05_

영구 채팅 관리자는 영구 채팅 방에서 메시지를 삭제할 수 있고, 선택적으로 이를 다른 메시지로 바꿀 수 있습니다. 관리자는 또한 지속적인 유지 관리의 일환으로 오래된 메시지를 삭제하여 데이터베이스 증가를 최소화할 수 있습니다. 예를 들어, 다음과 같은 Windows PowerShell 명령을 실행하면 ITChatRoom 채팅방에서 사용자 kenmyer@litwareinc.com이 게시한 모든 메시지가 제거됩니다.

    Remove-CsPersistentChatMessage -Identity "atl-persistentchat-001.litwareinc.com\ITChatRoom" -UserUri "sip:kenmyer@litwareinc.com"

또한 아래 예제의 명령을 실행하면 제거된 모든 메시지가 해당 메시지를 더 이상 사용할 수 없다는 알림으로 바뀝니다.

    Remove-CsPersistentChatMessage -Identity "atl-persistentchat-001.litwareinc.com\ITChatRoom" -UserUri "sip:kenmyer@litwareinc.com" -ReplaceMessage "This message is no longer available."

자세한 내용은 [Remove-CsPersistentChatMessage](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsPersistentChatMessage) cmdlet 관련 도움말 항목을 참고하세요.

