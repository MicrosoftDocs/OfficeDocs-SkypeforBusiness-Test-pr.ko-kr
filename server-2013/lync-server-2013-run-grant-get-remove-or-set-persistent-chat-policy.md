---
title: 'Lync Server 2013: 영구 채팅 정책 실행, 부여, 가져오기, 제거 또는 설정'
TOCTitle: 영구 채팅 정책 실행, 부여, 가져오기, 제거 또는 설정
ms:assetid: 39ccdbe8-fb3d-47bc-96e2-9486b6d317e0
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204810(v=OCS.15)
ms:contentKeyID: 49303342
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 영구 채팅 정책 실행, 부여, 가져오기, 제거 또는 설정

 

_**마지막으로 수정된 항목:** 2012-10-01_

새 영구 채팅 정책을 만들려면

    New-CsPersistentChatPolicy -Identity <XdsIdentity> [-Enable <Switch Parameter>] [-Confirm <Switch Parameter>] [-Force <Switch Parameter>] [-WhatIf <Switch Parameter>] [-InMemory <Switch Parameter>]

영구 채팅 정책을 부여하려면

    Grant-CsPersistentChatPolicy -Identity <UserIdParameter> -PolicyName <String> [-Confirm <Switch Parameter>] [-WhatIf <Switch Parameter>]

영구 채팅 정책을 가져오려면

    Get-CsPersistentChatPolicy [-Identity <XdsIdentity>] [-Filter <String>] [-LocalStore <Switch Parameter>]

영구 채팅 정책을 제거하려면

    Remove-CsPersistentChatPolicy -Identity <XdsIdentity> [-Confirm <Switch Parameter>] [-Force <Switch Parameter>] [-WhatIf <Switch Parameter>]

영구 채팅 정책을 설정하려면

    Set-CsPersistentChatPolicy [-Identity <XdsIdentity>] [-Instance < PSObject>]

