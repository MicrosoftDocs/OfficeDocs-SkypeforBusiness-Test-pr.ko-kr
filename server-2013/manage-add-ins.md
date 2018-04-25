---
title: 추가 기능 관리
TOCTitle: 추가 기능 관리
ms:assetid: b84f868e-b36e-4ab4-b284-7db212d401c3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205193(v=OCS.15)
ms:contentKeyID: 49304822
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 추가 기능 관리

 

_**마지막으로 수정된 항목:** 2012-10-06_

새로운 영구 채팅 서버 추가 기능을 만들려면

    New-CsPersistentChatAddin -Name Contoso -PersistentChatPoolFqdn client.contoso.com -Url http://contoso.com 

## 추가 기능 만들기, 가져오기, 설정 또는 제거

새로운 추가 기능을 만들려면

    New-CsPersistentChatAddin -PersistentChatPoolFqdn <String> -Name <String> -Url<String>


> [!IMPORTANT]
> PersistentChatPoolFqdn &lt;문자열&gt;은 영구 채팅 서버 풀이 두 개 이상 있는 경우에만 필요합니다.



추가 기능을 가져오려면

    Get-CsPersistentChatAddin -Identity <String>]

또는

    Get-CsPersistentChatAddin -PersistentChatPoolFqdn <String>

추가 기능을 설정하려면

    Set-CsPersistentChatAddIn -Instance <AddinObject> [-Force <Switch Parameter>] [-Confirm <Switch Parameter>]

또는

    Set-CsPersistentChatAddIn -Identity <String> [-Name <String>] [-Url<String>] [-Force <Switch Parameter>] [-Confirm <Switch Parameter>]

추가 기능을 제거하려면

    Remove-CsPersistentChatAddIn -Instance <AddinObject> [-Force <Switch Parameter>] [-Confirm <Switch Parameter>]

또는

    Remove-CsPersistentChatAddIn -Identity <String> [-Force <Switch Parameter>] [-Confirm <Switch Parameter>]

