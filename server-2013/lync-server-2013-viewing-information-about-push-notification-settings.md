---
title: 푸시 알림 설정에 대한 정보 보기
TOCTitle: 푸시 알림 설정에 대한 정보 보기
ms:assetid: be5c6b01-4294-4d17-9772-fed40201e8a5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721868(v=OCS.15)
ms:contentKeyID: 49885954
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 푸시 알림 설정에 대한 정보 보기

 

_**마지막으로 수정된 항목:** 2013-02-23_

배지, 아이콘 또는 경고 형태의 푸시 알림은 모바일 응용 프로그램이 비활성 상태일 때도 모바일 장치로 발송될 수 있습니다. 푸시 알림은 신규/부재 중 IM 초대 및 음성 메일 등의 이벤트를 사용자에게 알려 줍니다. Lync Server 2013 제어판 또는 Lync Server 2013 관리 셸을 사용하여 모바일 장치에 대한 푸시 알림 설정 정보를 볼 수 있습니다.

## Lync Server 제어판에서 푸시 알림 정보를 보려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **클라이언트**를 클릭하고 **푸시 알림 구성**을 클릭합니다.

4.  **푸시 알림 구성** 페이지에서 보려는 사이트를 클릭하고 **편집** 메뉴를 클릭한 후 **자세한 정보 표시**를 클릭합니다.

## Windows PowerShell cmdlet을 사용하여 푸시 알림 구성 정보를 보려면

또한 Lync Server 관리 셸 및 **Get-CsPushNotificationConfiguration** cmdlet을 사용하여 푸시 알림 구성 설정을 볼 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## 푸시 알림 구성 정보를 보려면

  - 모든 푸시 알림 구성 설정에 대한 정보를 보려면 Lync Server 관리 셸에서 다음 명령을 입력한 후 Enter 키를 누릅니다.
    
        Get-CsPushNotificationConfiguration
    
    그러면 다음과 같은 정보가 반환됩니다.
    
        Identity                               : Global
        EnableApplePushNotificationService     : False
        EnableMicrosoftPushNotificationService : False

자세한 내용은 [Get-CsPushNotificationConfiguration](get-cspushnotificationconfiguration.md) cmdlet에 대한 도움말 항목을 참조하십시오.

## 참고 항목

#### 작업

[Lync Server 2013의 푸시 알림 구성](lync-server-2013-configuring-for-push-notifications.md)

