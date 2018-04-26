---
title: 'Lync Server 2013: 영구 채팅 서버 구성'
TOCTitle: 영구 채팅 서버 구성
ms:assetid: 85028aff-a38e-4748-958e-59e707a47532
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205054(v=OCS.15)
ms:contentKeyID: 49304256
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 영구 채팅 서버 구성

 

_**마지막으로 수정된 항목:** 2012-10-06_

새로운 영구 채팅 구성을 만들려면

    New-CsPersistentChatConfiguration -Identity <XdsIdentity> [-DefaultChatHistory <Integer>] [-MaxChatContentSizeMB <Integer>] [-MaxFileSizeKB <Integer>] [-ParticipantUpdateLimit <Integer>] [-FileServiceUrl <UrlForFileUpload>] [-RoomManagementUrl <RoomManagementUrl>] [-Instance <PSObject>] [-Force <Switch Parameter>] [-Confirm <Switch Parameter>] [-WhatIf <Switch Parameter>]

영구 채팅 구성을 가져오려면

    Get-CsPersistentChatConfiguration [-LocalStore <Switch Parameter>] [-Identity <XdsIdentity>]

영구 채팅 구성을 제거하려면

    Remove-CsPersistentChatConfiguration -Identity <XdsIdentity>

영구 채팅 구성을 설정하려면

    Set-CsPersistentChatConfiguration [-DefaultChatHistory <Integer>] [-MaxChatContentSizeMB <Integer>] [-MaxFileSizeKB <Integer>] [-ParticipantUpdateLimit <Integer>] [-FileServiceUrl <UrlForFileUpload>] [-RoomManagementUrl <RoomManagementUrl>] [-Instance <PSObject >] [-Force <Switch Parameter>] [-Confirm <Switch Parameter>] [-WhatIf <Switch Parameter>]

Lync Server 2013의 경우 모든 웹 서비스 트래픽이 Lync Server 2013, 프런트 엔드 서버에 대해 지원됩니다. 따라서 영구 채팅 서버의 gcweb01 주소는 필요하지 않습니다. 원격 사용자의 *외부* 웹 사이트가 아니라 *내부* 웹 사이트에 대해서만 파일 업로드/다운로드 웹 서비스를 제공하기 때문에 내부 웹 서비스 액세스도 계속 지원됩니다.

