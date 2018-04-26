---
title: 매개 변수와 속성
TOCTitle: 매개 변수와 속성
ms:assetid: 65348f95-f4d4-40cd-8869-f9d72643792d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362796(v=OCS.15)
ms:contentKeyID: 56270244
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 매개 변수와 속성

 

_**마지막으로 수정된 항목:** 2015-06-22_

비즈니스용 Skype Online cmdlet에 대한 도움말 항목을 검토하다 보면 *매개 변수*와 *속성*이라는 용어가 혼용되는 경우가 있습니다. 용어 때문에 헷갈릴 필요가 없습니다. 엄밀히 따지면 다른 용어지만 비즈니스용 Skype Online에서 이 용어는 기본적으로 동일한 의미입니다.

엄밀히 말해서, 매개 변수는 cmdlet을 실행할 때 사용됩니다. 예를 들어, 다음 Windows PowerShell 명령에서 EnableMicrosoftPushNotificationService 및 EnableApplePushNotificationService는 [Set-CsPushNotificationConfiguration](set-cspushnotificationconfiguration.md) cmdlet의 매개 변수입니다.

    Set-CsPushNotificationConfiguration -EnableMicrosoftPushNotificationService -EnableApplePushNotificationService $True

속성은 비즈니스용 Skype Online 개체의 특성입니다. 예를 들어, 푸시 알림 구성 설정 모음이 이에 해당합니다. 다음 명령을 실행한다고 가정해 보겠습니다.

    Set-CsPushNotificationConfiguration

이 명령을 실행하면 속성 모음 및 관련된 값을 얻게 됩니다. 여기에는 다음 항목들이 포함됩니다.

    EnableMicrosoftPushNotificationService : True
    EnableApplePushNotificationService     : True

보다시피 속성 및 매개 변수는 같은 이름을 공유합니다. EnableMicrosoftPushNotificationService 매개 변수를 사용하여 EnableMicrosoftPushNotificationService 속성 값을 구성할 수 있습니다.

## 참고 항목

#### 개념

[Windows PowerShell 및 Lync Online 소개](an-introduction-to-windows-powershell-and-skype-for-business-online.md)

