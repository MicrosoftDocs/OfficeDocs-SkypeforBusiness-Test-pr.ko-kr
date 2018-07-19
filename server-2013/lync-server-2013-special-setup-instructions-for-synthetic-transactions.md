---
title: 가상 트랜잭션에 대한 특별 설치 지침
TOCTitle: 가상 트랜잭션에 대한 특별 설치 지침
ms:assetid: 694cbe05-5dba-4035-a01c-c87ebfb0478b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688080(v=OCS.15)
ms:contentKeyID: 49885795
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 가상 트랜잭션에 대한 특별 설치 지침

 

_**마지막으로 수정된 항목:** 2013-01-22_

대부분의 가상 트랜잭션은 감시자 노드에서 있는 그대로 실행됩니다. 즉, 가상 트랜잭션이 감시자 노드 구성 설정에 추가되는 즉시, 감시자 노드가 테스트 진행 중 가상 트랜잭션을 즉시 사용할 수 있습니다. 하지만 이러한 방식이 모든 가상 트랜잭션에 적용되는 것은 아닙니다. 이러한 예외적인 특별한 설치 지침이 필요한 가상 트랜잭션은 다음 섹션에서 자세히 설명합니다.

## 데이터 회의 가상 트랜잭션

감시자 노드 컴퓨터가 경계 네트워크 외부에 있는 경우 네트워크 서비스 계정에 대해 먼저 Internet Explorer 프록시 설정을 사용하지 않도록 설정하지 않는 한 데이터 회의 가상 트랜잭션을 실행하지 못할 수 있습니다. 이 서비스에 대해 프록시 설정을 사용하지 않도록 설정하려면 다음 절차를 수행합니다.

1.  감시자 노드 컴퓨터에서 **시작**, **모든 프로그램**, **보조 프로그램**을 차례로 클릭하고 **명령 프롬프트**를 마우스 오른쪽 단추로 클릭한 후 **관리자로 실행**을 클릭합니다.

2.  콘솔 창에 다음 명령을 입력한 다음 Enter 키를 누릅니다.
    
        bitsadmin /util /SetIEProxy NetworkService NO_PROXY

명령 창에 다음 메시지가 표시됩니다.

    BITSAdmin is deprecated and is not guaranteed to be available in future versions of Windows. Administration tools for the BITS service are now provided by BITS PowerShell cmdlets.
    
    Internet proxy settings for account NetworkService set to NO_PROXY. 
    (connection = default)

이 메시지는 네트워크 서비스 계정에 대해 Internet Explorer 프록시 설정이 사용하지 않도록 설정되었다는 의미입니다.

## Exchange 통합 메시징 가상 트랜잭션

Exchange 통합 메시징(UM) 가상 트랜잭션은 테스트 사용자가 Exchange에 있는 음성 메일 계정에 연결할 수 있는지 확인합니다. 이러한 테스트 사용자는 Exchange UM 테스트를 사용하기 전에 음성 메일 계정으로 미리 구성되어 있어야 합니다.

## 영구 채팅 가상 트랜잭션

영구 채팅 가상 트랜잭션을 사용하려면 관리자가 먼저 채널을 만들고 테스트 사용자에게 이를 사용할 수 있는 권한을 부여해야 합니다. [Test-CsPersistentChatMessage](https://docs.microsoft.com/en-us/powershell/module/skype/Test-CsPersistentChatMessage) cmdlet은 이러한 테스트 사용자를 올바르게 구성하는 데 사용할 수 있습니다.

    $cred1 = Get-Credential "litwareinc\kenmyer"
    $cred2 = Get-Credential "litwareinc\pilar"
    
    Test-CsPersistentChatMessage -TargetFqdn atl-cs-001.litwareinc.com -SenderSipAddress sip:kenmyer@litwareinc.com -SenderCredential $cred1 -ReceiverSipAddress sip:pilar@litwareinc.com -ReceiverCredential $cred2 -TestUser1SipAddress sip:kenmyer@litwareinc.com -TestUser2SipAddress sip:pilar@litwareinc.com -Setup $True

이 설정 작업은 엔터프라이즈 내부에서 실행해야 합니다.

  - 서버가 아닌 컴퓨터에서 실행할 경우 cmdlet을 실행하는 사용자는 RBAC(역할 기반 액세스 제어)에 대한 PersistentChatAdministrators 역할의 구성원이어야 합니다.

  - 서버 자체에서 실행할 경우 cmdlet을 실행하는 사용자는 RTCUniversalServerAdmins 그룹의 구성원이어야 합니다.

위 명령에서는 Setup 매개 변수가 포함되었으며 True($True)로 설정되었습니다. Setup 매개 변수를 포함하면 Test-CsPersistentChatMessage가 특별한 영구 채팅방을 만들고 이 방에 테스트 사용자를 채웁니다. 이러한 방식은 테스트 목적으로 사용할 수 있는 채팅방을 실제로 만드는 데 도움이 됩니다. Setup 매개 변수는 프런트 엔드 서버에서만 실행해야 합니다.

Test-CsPersistentChatMessage로 만든 채팅방은 관리자만 삭제할 수 있습니다.

## PSTN 피어 투 피어 통화 가상 트랜잭션

[Test-CsPstnPeerToPeerCall](https://docs.microsoft.com/en-us/powershell/module/skype/Test-CsPstnPeerToPeerCall) 가상 트랜잭션은 PSTN(공중 전화망)을 통해 통화를 걸고 받는 기능을 확인합니다.

이 가상 트랜잭션을 실행하려면 관리자가 다음을 구성해야 합니다.

  - Enterprise Voice에 대해 설정된 두 명의 테스트 사용자(발신자와 수신자)

  - 각 사용자 계정에 대한 DID(Direct Inward Dialing) 번호

  - 수신자 번호에 대한 통화가 PSTN 게이트웨이에 연결되도록 하는 음성 정책 및 음성 경로

  - 통화를 허용하는 PSTN 게이트웨이 및 사용된 번호를 기반으로 수신자의 홈 풀로 통화를 라우팅하는 미디어

## 통합 연락처 저장소 가상 트랜잭션

통합 연락처 저장소 가상 트랜잭션은 Lync Server 2013이 Microsoft Exchange Server 2013에서 사용자 대신 연락처를 검색할 수 있는지 확인합니다.

이 가상 트랜잭션을 사용하려면 다음 조건을 충족해야 합니다.

  - Lync Server 2013 및 Exchange 2013 사이에 [Lync Server 2013에서 서버 간 인증(Oauth) 및 파트너 응용 프로그램 관리](lync-server-2013-managing-server-to-server-authentication-oauth-and-partner-applications.md)를 구성해야 합니다.

  - 테스트 사용자는 유효한 Exchange 2013 사서함을 갖고 있어야 합니다.

이러한 조건이 충족되었으면 관리자가 다음 명령을 실행하여 SIP 주소 kenmyer@litwareinc.com의 사용자가 통합 연락처 저장소에서 자신의 연락처를 검색할 수 있는지 확인할 수 있습니다.

    Test-CsUnifiedContactStore -TargetFqdn atl-cs-001.litwareinc.com -UserSipAddress "sip:kenmyer@litwareinc.com" -RegistrarPort 5061 -Authentication TrustedServer -Setup

이전 명령에서는 Setup 매개 변수가 사용되었습니다. Test-CsUnifiedContactStore를 실행할 때 Setup 매개 변수가 포함되었으면 지정된 사용자의 연락처(이 경우 sip:kenmyer@litwareinc.com)가 통합 연락처 저장소로 이동됩니다. (물론 사용자의 연락처가 이미 통합 연락처 저장소에 있으면 이동할 필요가 없습니다.) Setup 매개 변수는 일반적으로 한 번만(Test-CsUnifiedContactStore를 처음 실행할 때) 사용되며 테스트 사용자에 대해서만 사용해야 합니다. 즉, 실제로 Lync Server에 로그온하지 않는 사용자 계정에서만 사용해야 합니다. 테스트 사용자가 통합 연락처 저장소로 마이그레이션된 후에는 Setup 매개 변수 없이 Test-CsUnifiedContactStore를 호출하여 사용자의 연락처를 검색할 수 있는지 확인할 수 있습니다.

    Test-CsUnifiedContactStore -TargetFqdn atl-cs-001.litwareinc.com -UserSipAddress "sip:kenmyer@litwareinc.com" -RegistrarPort 5061 -Authentication TrustedServer

## XMPP 가상 트랜잭션

XMPP(Extensible Messaging and Presence Protocol) IM 가상 트랜잭션을 사용하려면 하나 이상의 페더레이션 도메인에 XMPP 기능이 구성되어 있어야 합니다.

XMPP 가상 트랜잭션을 사용하도록 설정하려면 라우팅 가능한 XMPP 도메인의 사용자 계정을 XmppTestReceiverMailAddress 매개 변수에 제공해야 합니다. 예:

    Set-CsWatcherNodeConfiguration -Identity pool0.contoso.com -Tests @{Add="XmppIM"} -XmppTestReceiverMailAddress user1@litwareinc.com

이 예에서 메시지를 litwareinc.com에서 XMPP 게이트웨이로 라우팅하려면 Lync Server 2013 규칙이 존재해야 합니다.

