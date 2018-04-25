---
title: Windows PowerShell 및 Lync Online 소개
TOCTitle: Windows PowerShell 및 Lync Online 소개
ms:assetid: 4b4cf534-c950-4d6c-abd9-d3d0e6f53bb7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Dn362785(v=OCS.15)
ms:contentKeyID: 56270234
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Windows PowerShell 및 Lync Online 소개

 

_**마지막으로 수정된 항목:** 2015-06-22_

Windows PowerShell은 비즈니스용 Skype Online을 관리하는 데 사용할 수 있는 명령 셸 및 스크립팅 언어입니다. 그래픽 비즈니스용 Skype Online 관리 센터를 사용하여 비즈니스용 Skype Online을 관리하는 대신 다음과 같은 명령줄 명령을 사용하여 제품을 관리할 수 있습니다.

    Get-CsOnlineUser -Identity "kenmyer@litwareinc.com"

UPN kenmyer@litwareinc.com 사용자에 대한 정보를 반환하는 선행 예제와 같이 단순한 명령을 실행하는 것 외에도 Windows PowerShell에 익숙한 사용자는 이러한 명령을 스크립트로 구성할 수도 있습니다. 이러한 스크립트는 프로세스 자동화 및 반복 작업 수행에 사용될 수 있습니다.

일반적으로 비즈니스용 Skype Online 관리 센터를 사용하여 수행할 수 있는 모든 작업은 Windows PowerShell을 사용해서 수행할 수 있습니다. 예를 들어 관리 센터를 사용하여 휴대폰 알림(*푸시 알림*)을 관리할 수 있습니다. 푸시 알림을 사용하면 이벤트(예: 새 메신저 대화 또는 새 음성 메일)에 대한 알림을 iPhone 및 Windows Phone 등의 모바일 장치로 보낼 수 있습니다. 모바일 장치의 백그라운드에서 Lync 응용 프로그램이 실행 중인 경우에도 해당 장치에서 이러한 알림을 받을 수 있습니다.

푸시 알림을 관리하는 한 가지 방법은 비즈니스용 Skype Online 관리 센터를 사용하는 것입니다. 이곳에서 **조직** 탭의 적절한 옵션을 선택하여 푸시 알림을 설정하거나 해제할 수 있습니다.

![LyncOnlinePowerShell\_Push\_Notifications](images/Dn362807.0a6ec1f5-1999-427f-880b-0587c98d7670(OCS.15).png "LyncOnlinePowerShell_Push_Notifications")

원격 Windows PowerShell 세션 및 [Set-CsPushNotificationConfiguration](set-cspushnotificationconfiguration.md) cmdlet을 사용하여 푸시 알림을 설정하거나 해제할 수도 있습니다. 예를 들어 다음 명령을 사용하면 iPhone 및 Windows Phone에서 푸시 알림을 해제할 수 있습니다.

    Set-CsPushNotificationConfiguration -EnableApplePushNotificationService $False -EnableMicrosoftPushNotificationService $False

보다시피 **Set-CsPushNotificationConfiguration** cmdlet에서 사용되는 매개 변수(EnableApplePushNotificationService 및 EnableMicrosoftPushNotificationService)는 비즈니스용 Skype Online 관리 센터에서도 사용할 수 있는 옵션입니다.

![Lync 옵션/PS cmdlet 간에 나타나는 연결](images/Dn362785.f20086fd-3b51-4bbf-8d81-e643d9bf3a2e(OCS.15).png "Lync 옵션/PS cmdlet 간에 나타나는 연결")

요약하면, 관리 센터 또는 Windows PowerShell cmdlet과 적절한 매개 변수를 사용하여 푸시 알림을 관리할 수 있습니다. 두 방법 모두 유효하며 동일하게 작동합니다.


> [!NOTE]
> <EM>cmdlet</EM>, <EM>매개 변수</EM>, <EM>매개 변수 값</EM>, <EM>인수</EM> 등의 특정 Windows PowerShell 용어에 대한 정의는 <A href="windows-powershell-cmdlets-parameters-and-parameter-values-in-skype-for-business-online.md">Windows PowerShell Cmdlet, 매개 변수, 매개 변수 값</A>을 참고하세요.



그렇다면 다음과 같은 의문이 생깁니다. 비즈니스용 Skype Online 관리 센터와 Windows PowerShell이 동일한 기능을 제공한다면 왜 둘 중 하나를 사용해야 할까요? 마찬가지로, 단순히 관리 센터에서 확인란을 선택하거나 선택 해제하는 대신 Windows PowerShell에서 명령을 입력해야 할까요?

이전 예제와 같은 단순한 경우에는 개인적인 선호에 따라 방식을 선택하면 됩니다. 어떤 사람은 그래픽 사용자 인터페이스를 선호하고, 또 어떤 사람은 Windows PowerShell과 같은 명령줄 도구를 선호합니다. 하지만 어떤 경우에는, Windows PowerShell에서 관리 작업을 수행하는 것이 가장 효율적이거나, 어쩌면 유일한 방법이 되기도 합니다. 예를 들어 비즈니스용 Skype Online 관리 센터를 사용하면 모임 초대를 사용자 지정할 수 있습니다.

![Lync 관리 센터 모임 초대 설정](images/Dn362785.3fb00c33-0bd4-46dd-beb1-8f71e24cf630(OCS.15).png "Lync 관리 센터 모임 초대 설정")

[Set-CsMeetingConfiguration](set-csmeetingconfiguration.md) cmdlet을 사용하여 동일하게 사용자 지정 작업을 수행할 수 있습니다. 하지만 **Set-CsMeetingConfiguration** cmdlet에는 비즈니스용 Skype Online 관리 센터에서 제공하지 않는 옵션이 포함되어 있습니다. 예를 들어 조직의 한 사용자가 모임에 참가하면 해당 사용자는 자동으로 모임 발표자로 구성됩니다. 이 설정은 비즈니스용 Skype Online 관리 센터를 사용하여 변경할 수 없고, Windows PowerShell 및 **Set-CsMeetingConfiguration** cmdlet을 사용해야지만 변경이 가능합니다. 특별히, 이 명령은 DesignateAsPresenter 속성을 None으로 설정하는데, 이는 모임 이끌이가 모임에 참가할 때에만 발표자로 구성되도록 하는 설정입니다.

    Set-CsMeetingConfiguration -DesignateAsPresenter "Everyone"

Windows PowerShell 사용에 대한 자세한 내용은 다음 항목을 참고하세요.

  - [Windows PowerShell Cmdlet, 매개 변수, 매개 변수 값](windows-powershell-cmdlets-parameters-and-parameter-values-in-skype-for-business-online.md)

  - [매개 변수 사용](working-with-parameters-in-skype-for-business-online.md)

  - [필수 및 선택적 매개 변수](mandatory-and-optional-parameters-in-skype-for-business-online.md)

  - [매개 변수와 속성](parameters-vs-properties-in-skype-for-business-online.md)

  - [Lync Online Cmdlet과 기타 Windows PowerShell Cmdlet 결합](combining-skype-for-business-online-cmdlets-with-other-windows-powershell-cmdlets-in.md)

  - [Windows PowerShell 사용에 대한 추가 도움말](more-help-for-using-windows-powershell-in-skype-for-business-online.md)

