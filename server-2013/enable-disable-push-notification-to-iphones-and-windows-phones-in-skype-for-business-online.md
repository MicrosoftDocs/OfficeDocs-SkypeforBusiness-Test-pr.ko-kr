---
title: iPhone 및 Windows Phone에 푸시 알림 설정/해제
TOCTitle: iPhone 및 Windows Phone에 푸시 알림 설정/해제
ms:assetid: 64482dcb-6354-4fb5-a2e4-1564b3d0e047
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362792(v=OCS.15)
ms:contentKeyID: 56270243
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# iPhone 및 Windows Phone에 푸시 알림 설정/해제

 

_**마지막으로 수정된 항목:** 2015-06-22_

iPhone 또는 Windows Phone으로 전송되는 푸시 알림을 해제하려면 [Set-CsPushNotificationConfiguration](set-cspushnotificationconfiguration.md) cmdlet을 사용하여 EnableApplePushNotificationService 및 EnableMicrosoftPushNotificationService 속성 값을 False($False)로 설정합니다.

    Set-CsPushNotificationConfiguration -EnableApplePushNotificationService $False -EnableMicrosoftPushNotificationService $False

iPhone 및 Windows Phone은 개별적으로 설정될 수 있습니다. 예를 들어, 다음 명령은 iPhone의 푸시 알림은 해제하고, Windows Phone의 알림은 설정합니다.

    Set-CsPushNotificationConfiguration -EnableApplePushNotificationService $False -EnableMicrosoftPushNotificationService $True

## 참고 항목

#### 개념

[빠른 참조: Windows PowerShell을 사용하여 일반적인 Lync Online 관리 작업 수행](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

