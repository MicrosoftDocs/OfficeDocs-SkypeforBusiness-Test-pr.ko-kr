---
title: iPhone에 푸시 알림 사용 또는 사용 안 함
TOCTitle: iPhone에 푸시 알림 사용 또는 사용 안 함
ms:assetid: 8bbf531a-807f-4a8f-814a-94bfed8f97ef
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688122(v=OCS.15)
ms:contentKeyID: 49885860
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# iPhone에 푸시 알림 사용 또는 사용 안 함

 

_**마지막으로 수정된 항목:** 2013-02-23_

모바일 응용 프로그램이 비활성 상태일 때에도 배지, 아이콘 또는 경고 형태의 푸시 알림을 iPhone에 전송할 수 있습니다. 푸시 알림은 IM 초대 및 음성 메일의 신규 또는 누락과 같은 이벤트를 사용자에게 알립니다. Lync Server 2013 제어판 또는 Lync Server 2013 관리 셸을 사용해서 iPhone에 대한 푸시 알림을 사용하거나 사용하지 않도록 설정할 수 있습니다.

## Lync Server 제어판에서 iPhone에 대한 푸시 알림을 사용하도록 설정하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **클라이언트**를 클릭하고 **푸시 알림 구성** 탐색 단추를 클릭합니다.

4.  **푸시 알림 구성** 페이지에서 편집하려는 사이트를 클릭하고 **편집**을 클릭한 후 **세부 정보 표시**를 클릭합니다.

5.  **Apple 푸시 알림 사용** 확인란을 클릭합니다.

6.  **커밋**을 클릭합니다.

## Lync Server 제어판에서 iPhone에 대한 푸시 알림을 사용하지 않도록 설정하려면

1.  CsUserAdministrator 역할 또는 CsAdministrator 역할에 할당된 사용자 계정에서 내부 배포된 컴퓨터에 로그온합니다.

2.  브라우저 창을 연 다음 Admin URL을 입력하여 Lync Server 제어판을 엽니다. Lync Server 제어판을 시작하는 데 사용할 수 있는 다양한 방법에 대한 자세한 내용은 [Lync Server 관리 도구 열기](lync-server-2013-open-lync-server-administrative-tools.md)를 참조하세요.

3.  왼쪽 탐색 모음에서 **클라이언트**를 클릭하고 **푸시 알림 구성** 탐색 단추를 클릭합니다.

4.  **푸시 알림 구성** 페이지에서 편집하려는 사이트를 클릭하고 **편집**을 클릭한 후 **세부 정보 표시**를 클릭합니다.

5.  **Apple 푸시 알림 사용** 확인란의 선택을 취소합니다.

6.  **커밋**을 클릭합니다.

## Windows PowerShell cmdlet을 사용하여 iPhone에 대한 푸시 알림을 사용하거나 사용하지 않도록 설정하려면

**Set-CsPushNotificationConfiguration** cmdlet을 사용해서 Apple iPhone에 대한 푸시 알림을 사용하거나 사용하지 않도록 설정할 수 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## iPhone에 대해 푸시 알림을 사용하도록 설정하려면

  - iPhone에 대해 푸시 알림을 사용하도록 설정하려면 EnableApplePushNotificationService 속성 값을 True($True)로 설정합니다. 예:
    
        Set-CsPushNotificationConfiguration -Identity "site:Redmond" -EnableApplePushNotificationService $True

## iPhone에 대해 푸시 알림을 사용하지 않도록 설정하려면

  - iPhone에 대해 푸시 알림을 사용하지 않도록 설정하려면 EnableApplePushNotificationService 속성 값을 False($False)로 설정합니다. 예:
    
        Set-CsPushNotificationConfiguration -Identity "site:Redmond" -EnableApplePushNotificationService $False

자세한 내용은 [Set-CsPushNotificationConfiguration](set-cspushnotificationconfiguration.md) cmdlet의 도움말 항목을 참조하십시오.

## 참고 항목

#### 작업

[Lync Server 2013의 푸시 알림 구성](lync-server-2013-configuring-for-push-notifications.md)

