---
title: 'Lync Server 2013: 푸시 알림 구성'
TOCTitle: 푸시 알림 구성
ms:assetid: d77f2c06-0fe6-45d5-8f08-808ab871b3e0
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh690047(v=OCS.15)
ms:contentKeyID: 49305194
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 푸시 알림 구성

 

_**마지막으로 수정된 항목:** 2013-02-12_

배지, 아이콘 또는 경고 형태의 푸시 알림은 모바일 응용 프로그램이 비활성 상태일 때도 모바일 장치로 발송될 수 있습니다. 푸시 알림은 신규/부재 중 메신저 초대, 음성 사서함 등의 이벤트를 사용자에게 알려 줍니다. Lync Server 2013 Mobility Service는 클라우드 기반 Lync Server 푸시 알림 서비스로 알림을 보내며, 이 서비스는 Lync 2010 Mobile 클라이언트를 실행 중인 Apple 장치의 경우 APNS(Apple 푸시 알림 서비스)로, Lync 2010 Mobile 또는 Lync 2013 모바일 클라이언트를 실행 중인 Windows Phone 장치의 경우 MPNS(Microsoft 푸시 알림 서비스)로 알림을 보냅니다.


> [!IMPORTANT]
> Lync 2010 Mobile 또는 Lync 2013 모바일 클라이언트가 설치된 Windows Phone을 사용하는 경우 푸시 알림은 중요한 고려 사항입니다.<BR>Apple 장치에서 Lync 2010 Mobile을 사용하는 경우에도 역시 푸시 알림은 중요한 고려 사항입니다.<BR>Apple 장치에서 Lync 2013 Mobile을 사용하는 경우에는 푸시 알림이 더 이상 필요하지 않습니다.



다음을 수행하여 푸시 알림을 지원하도록 토폴로지를 구성합니다.

  - 환경에 Lync Server 2010 또는 Lync Server 2013에지 서버가 있는 경우에는 새로운 호스팅 공급자(Microsoft Lync Online)를 추가한 다음 조직과 Lync Online 간에 호스팅 공급자 페더레이션을 설정해야 합니다.

  - 환경에 Office Communications Server 2007 R2에지 서버가 있는 경우에는 push.lync.com과의 직접 SIP 페더레이션을 설정해야 합니다.
    

    > [!NOTE]
    > Push.lync.com은 푸시 알림 서비스용 Microsoft Office 365 도메인입니다.



  - 푸시 알림을 사용하도록 설정하려면 **Set-CsPushNotificationConfiguration** cmdlet을 실행해야 합니다. 기본적으로 푸시 알림은 해제됩니다.

  - 페더레이션 구성 및 푸시 알림을 테스트합니다.

## Lync Server 2013 또는 Lync Server 2010  에지 서버에 대해 푸시 알림을 구성하려면

1.  Lync Server 관리 셸 및 Ocscore가 설치된 컴퓨터에 RtcUniversalServerAdmins 그룹의 구성원으로 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  명령줄에 다음을 입력하여 Lync Server 온라인 호스팅 공급자를 추가합니다.
    
        New-CsHostingProvider -Identity <unique identifier for Lync Online hosting provider> -Enabled $True -ProxyFqdn <FQDN for the Access Server used by the hosting provider> -VerificationLevel UseSourceVerification
    
    예를 들면 다음과 같습니다.
    
        New-CsHostingProvider -Identity "LyncOnline" -Enabled $True -ProxyFqdn "sipfed.online.lync.com" -VerificationLevel UseSourceVerification
    

    > [!NOTE]
    > 단일 호스팅 공급자와 둘 이상의 페더레이션 관계를 설정할 수는 없습니다. 즉, 이미 sipfed.online.lync.com과의 페더레이션 관계가 있는 호스팅 공급자를 설정한 경우에는 호스팅 공급자의 ID가 LyncOnline이 아니더라도 다른 호스팅 공급자를 추가해서는 안 됩니다.



4.  명령줄에 다음을 입력하여 Lync Online의 푸시 알림 서비스와 조직 간의 호스팅 공급자 페더레이션을 설정합니다.
    
        New-CsAllowedDomain -Identity "push.lync.com"

## Office Communications Server 2007 R2  에지 서버에 대해 푸시 알림을 구성하려면

1.  RtcUniversalServerAdmins 그룹의 구성원으로 에지 서버에 로그온합니다.

2.  **시작** 을 클릭하고 **모든 프로그램** 과 **관리 도구** 를 차례로 클릭한 다음 **컴퓨터 관리** 를 클릭합니다.

3.  콘솔 트리에서 **서비스 및 응용 프로그램** 을 확장하고 **Microsoft Office Communications Server 2007 R2** 를 마우스 오른쪽 단추로 클릭한 다음 **속성** 을 클릭합니다.

4.  **허용** 탭에서 **추가** 를 클릭합니다.

5.  **페더레이션 파트너 추가** 대화 상자에서 다음을 수행합니다.
    
      - **페더레이션 파트너 도메인 이름** 에 **push.lync.com** 을 입력합니다.
    
      - **페더레이션 파트너 액세스 에지 서버** 에 **sipfed.online.lync.com**을 입력합니다.
    
      - **확인** 을 클릭합니다.

## 푸시 알림을 사용하도록 설정하려면

1.  Lync Server 관리 셸 및 Ocscore가 설치되어 있는 컴퓨터에 CsAdministrator 역할의 구성원으로 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  명령줄에 다음을 입력하여 푸시 알림을 사용하도록 설정합니다.
    
        Set-CsPushNotificationConfiguration -EnableApplePushNotificationService $True -EnableMicrosoftPushNotificationService $True

4.  명령줄에 다음을 입력하여 페더레이션을 사용하도록 설정합니다.
    
        Set-CsAccessEdgeConfiguration -AllowFederatedUsers $True

## 페더레이션 및 푸시 알림을 테스트하려면

1.  Lync Server 관리 셸 및 Ocscore가 설치되어 있는 컴퓨터에 CsAdministrator 역할의 구성원으로 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  명령줄에 다음을 입력하여 페더레이션 구성을 테스트합니다.
    
        Test-CsFederatedPartner -TargetFqdn <FQDN of Access Edge server used for federated SIP traffic> -Domain <FQDN of federated domain> -ProxyFqdn <FQDN of the Access Edge server used by the federated organization>
    
    예를 들면 다음과 같습니다.
    
        Test-CsFederatedPartner -TargetFqdn accessproxy.contoso.com -Domain push.lync.com -ProxyFqdn sipfed.online.lync.com

4.  명령줄에 다음을 입력하여 푸시 알림을 테스트합니다.
    
        Test-CsMcxPushNotification -AccessEdgeFqdn <Access Edge service FQDN>
    
    예를 들면 다음과 같습니다.
    
        Test-CsMcxPushNotification -AccessEdgeFqdn accessproxy.contoso.com

## 참고 항목

#### 기타 리소스

[Test-CsFederatedPartner](https://docs.microsoft.com/en-us/powershell/module/skype/Test-CsFederatedPartner)  
[Test-CsMcxPushNotification](https://docs.microsoft.com/en-us/powershell/module/skype/Test-CsMcxPushNotification)

