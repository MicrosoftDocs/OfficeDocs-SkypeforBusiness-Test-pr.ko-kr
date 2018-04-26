---
title: 'Lync Server 2013: 채팅방 범주에 사용자 및 사용자 그룹의 도메인 추가'
TOCTitle: 채팅방 범주에 사용자 및 사용자 그룹의 도메인 추가
ms:assetid: ee03f2cf-1c84-41c4-b524-d0729be33b8c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ215884(v=OCS.15)
ms:contentKeyID: 49305447
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 채팅방 범주에 사용자 및 사용자 그룹의 도메인 추가

 

_**마지막으로 수정된 항목:** 2014-02-07_

큰 그룹의 사용자를 채팅방에 추가하려면 배포 설명서에서 [Lync Server 2013에서 범주 구성](lync-server-2013-configure-categories.md) 및 [범주 관리](manage-categories.md)를 참고하세요. 예를 들어 다음 명령을 실행하면 Active Directory의 NorthAmericaUsers OU에 있는 모든 사용자가 NorthAmerica 채팅방에 추가됩니다.

    Set-CsPersistentChatRoom -PersistentChatPoolFqdn "atl-cs-001.litwareinc.com\NorthAmerica" -Members @{Add="OU=NorthAmericaUsers,DC=litwareinc,DC=com"}

이 명령을 실행하면 재무 메일 그룹의 모든 구성원이 같은 채팅방에 추가됩니다.

    Set-CsPersistentChatRoom -PersistentChatPoolFqdn "atl-cs-001.litwareinc.com\NorthAmerica" -Members @{Add="CN=Finance,OU=ExternalUsers,DC=litwareinc,DC=com"}

