---
title: 가상 트랜잭션으로 영구 채팅 서버 테스트
TOCTitle: 가상 트랜잭션으로 영구 채팅 서버 테스트
ms:assetid: 414e43f3-0074-4ecf-a232-398de972cb24
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204837(v=OCS.15)
ms:contentKeyID: 49303436
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 가상 트랜잭션으로 영구 채팅 서버 테스트

 

_**마지막으로 수정된 항목:** 2012-09-21_

채팅방에서 두 사용자 간에 메시지를 전송 및 수신하기 위해 영구 채팅 서버를 테스트하려면

    Test-CsPersistentChatMessage [-Authentication <TrustedServer | Negotiate | ClientCertificate | 
        LiveID>] [-ReceiverSipAddress <String>] [-RegistrarPort <Int32>] [-SenderSipAddress <String>] -TargetFqdn <String> [-Force <SwitchParameter>] [-OutLoggerVariable <String>] 
        [-OutVerboseVariable <String>] [<CommonParameters>]

또는

    Test-CsPersistentChatMessage [-Authentication <TrustedServer | Negotiate | ClientCertificate | 
        LiveID>] -ReceiverCredential <PSCredential> -ReceiverSipAddress <String> [-RegistrarPort 
        <Int32>] -SenderCredential <PSCredential> -SenderSipAddress <String> [-TargetFqdn <String>] [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>] [<CommonParameters>]

또는

    Test-CsPersistentChatMessage [-Authentication <TrustedServer | Negotiate | ClientCertificate | 
        LiveID>] [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable 
        <String>] [<CommonParameters>]

