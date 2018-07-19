---
title: Microsoft Lync Server 2013 음성 사서함에 대해 Microsoft Exchange Server 2013 통합 메시징 구성
TOCTitle: Microsoft Lync Server 2013 음성 사서함에 대해 Microsoft Exchange Server 2013 통합 메시징 구성
ms:assetid: 1be9c4f4-fd8e-4d64-9798-f8737b12e2ab
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ687983(v=OCS.15)
ms:contentKeyID: 49885668
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Microsoft Lync Server 2013 음성 사서함에 대해 Microsoft Exchange Server 2013 통합 메시징 구성

 

_**마지막으로 수정된 항목:** 2013-02-04_

Microsoft Lync Server 2013에서는 Microsoft Exchange Server 2013에 음성 메일 메시지를 저장할 수 있습니다. 저장된 음성 메일 메시지는 사용자의 받은 편지함에 전자 메일 메시지로 표시됩니다. 이 기능은 Lync Server 및 Exchange의 2010 버전에서도 제공되었습니다. 그러나 2013 버전에서는 UM Call Router 구성 요소가 도입되어 이 "통합 메시징"을 구성하는 프로세스가 간소화되었습니다. 이 구성 요소는 Exchange 2013 클라이언트 액세스 서버에 설치되며, 음성 메일 등 Exchange 통합 메시징에 대한 모든 호출은 먼저 Call Router를 통해 라우팅된 다음 적절한 사서함 서버로 리디렉션됩니다.

Lync Server 2013과 Exchange 2013 간에 서버 간 인증을 이미 구성한 경우에는 통합 메시징을 설정할 수 있습니다. 이렇게 하려면 먼저 Exchange 서버에서 새 통합 메시징 다이얼 플랜을 만들고 할당해야 합니다. 예를 들어 Exchange 관리 셸에서 실행할 수 있는 다음 두 명령은 Exchange용으로 3자리 다이얼 플랜을 새로 구성합니다.

    New-UMDialPlan -Name "RedmondDialPlan" -VoIPSecurity "Secured" -NumberOfDigitsInExtension 3 -URIType "SipName" -CountryOrRegionCode 1
    Set-UMDialPlan "RedmondDialPlan" -ConfiguredInCountryOrRegionGroups "Anywhere,*,*,*" -AllowedInCountryOrRegionGroups "Anywhere"

위 예의 첫 번째 명령에서 VoIPSecurity 매개 변수와 매개 변수의 값 "Secured"는 신호 채널이 TLS(전송 계층 보안)를 사용하여 암호화됨을 나타냅니다. URIType "SipName"은 메시지가 SIP 프로토콜을 사용하여 송/수신됨을 나타내고, CountryOrRegionCode 1은 다이얼 플랜이 미국에 적용됨을 나타냅니다.

두 번째 명령에서 ConfiguredInCountryOrRegionGroups 매개 변수로 전달되는 매개 변수 값은 이 다이얼 플랜에 사용할 수 있는 국가 내 그룹을 지정합니다. 매개 변수 값 "Anywhere,\*,\*,\*"는 다음을 설정합니다.

  - 그룹 이름("Anywhere")

  - AllowedNumberString(\* - 모든 숫자 문자열이 허용됨을 나타내는 와일드카드 문자)

  - DialNumberString(\* - 전화를 건 모든 번호가 허용됨을 나타내는 와일드카드 문자)

  - TextComment(\* - 모든 텍스트 명령이 허용됨을 나타내는 와일드카드 문자)

새 다이얼 플랜을 만들고 구성한 후에는 통합 메시징 서버에 새 다이얼 플랜을 추가한 다음 해당 서버의 시작 모드를 수정해야 합니다. 특히 시작 모드를 "Dual"로 설정해야 합니다. 이 두 작업은 모두 Exchange 관리 셸 내에서 수행할 수 있습니다.

    Set-UmServer -Identity "atl-exchangeum-001.litwareinc.com" -DialPlans "RedmondDialPlan" -UMStartupMode "Dual"

통합 메시징 서버를 구성한 다음에는 Enable-ExchangeCertificate cmdlet을 실행하여 Exchange 인증서가 통합 메시징 서비스에 적용되는지 확인해야 합니다.

    Enable-ExchangeCertificate -Server "atl-umserver-001.litwareinc.com" -Thumbprint "EA5A332496CC05DA69B75B66111C0F78A110D22d" -Services "SMTP","IIS","UM"

인증서가 올바르게 할당되고 나면 통합 메시징 서버에서 MsExchangeUM 서비스를 중지했다가 다시 시작해야 합니다. 시작 모드를 변경할 때마다 이 서비스를 중지한 후 다시 시작해야 합니다.

통합 메시징 서버 구성이 완료되면 UM Call Router를 구성할 수 있습니다.

    Set-CsUMCallRouterSettings -Server "atl-exchange-001.litwareinc.com" -UMStartupMode "Dual" -DialPlans "RedmondDialPlan" 
    Enable-ExchangeCertificate -Server "atl-umserver-001.litwareinc.com" -Thumbprint "45BAA32496CC891169B75B9811320F78A1075DDA" -Services "IIS","UMCallRouter"

시작 모드가 변경되었으므로 UM Call Router를 호스팅하는 컴퓨터에서 MsExchangeUMCR 서비스를 중지했다가 다시 시작해야 합니다.

통합 메시징 설정을 완료하려면 UM 사서함 정책을 만든 다음 해당 정책을 사용하여 사용자가 통합 메시징을 사용할 수 있도록 설정해야 합니다. 다음과 같은 명령을 사용하여 사서함 정책을 만들 수 있습니다.

    New-UMMailboxPolicy -ID "RedmondMailboxPolicy" -AllowedCountryOrRegionGroups "Anywhere"

그리고 다음과 같은 명령을 사용하면 사용자가 통합 메시징을 사용할 수 있도록 설정할 수 있습니다.

    Enable-UMMailbox -Extensions 100 -SIPResourceIdentifier "kenmyer@litwareinc.com" -Identity "litwareinc\kenmyer" -UMMailboxPolicy "RedmondMailboxPolicy"

위의 명령에서 Extensions 매개 변수는 사용자의 전화 내선 번호를 나타냅니다. 이 예에서 사용자의 내선 번호는 100입니다.

해당 사서함을 사용하도록 설정하고 나면 kenmyer@litwareinc.com 사용자가 Exchange 통합 메시징을 사용할 수 있게 됩니다. Lync Server 관리 셸 내에서 [Test-CsExUMConnectivity](https://docs.microsoft.com/en-us/powershell/module/skype/Test-CsExUMConnectivity) cmdlet을 실행하면 사용자가 Exchange UM에 연결할 수 있는지를 확인할 수 있습니다.

    $credential = Get-Credential "litwareinc\kenmyer"
    
    Test-CsExUMConnectivity -TargetFqdn "atl-cs-001.litwareinc.com" -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $credential

통합 메시징을 사용할 수 있도록 설정된 두 번째 사용자가 있는 경우 [Test-CsExUMVoiceMail](test-csexumvoicemail.md) cmdlet을 사용하여 두 번째 사용자가 첫 번째 사용자에게 음성 메일 메시지를 남길 수 있는지 확인할 수 있습니다.

    $credential = Get-Credential "litwareinc\pilar"
    
    Test-CsExUMVoiceMail -TargetFqdn "atl-cs-001.litwareinc.com" -ReceiverSipAddress "sip:kenmyer@litwareinc.com" -SenderSipAddress "sip:pilar@litwareinc.com" -SenderCredential $credential

