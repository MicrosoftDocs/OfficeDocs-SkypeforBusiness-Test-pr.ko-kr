---
title: 감시자 노드 테스트 사용자 및 구성 설정 구성
TOCTitle: 감시자 노드 테스트 사용자 및 구성 설정 구성
ms:assetid: ab00e9cb-f539-4aa6-bcb4-5533fbe7bc44
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205152(v=OCS.15)
ms:contentKeyID: 49304680
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 감시자 노드 테스트 사용자 및 구성 설정 구성

 

_**마지막으로 수정된 항목:** 2013-07-29_

감시자 노드로 작동할 컴퓨터를 구성한 후에는 다음을 수행해야 합니다.

1.  이러한 감시자 노드에서 사용할 테스트 계정을 만듭니다. 또한 협상 인증 방법을 사용하는 경우에는 [Set-CsTestUserCredential](set-cstestusercredential.md) cmdlet을 사용해서 감시자 노드에 이러한 테스트 계정을 사용하도록 설정해야 합니다.

2.  감시자 노드 구성 설정을 업데이트합니다.

이 섹션에서는 다음 항목에 대해 설명합니다.

  - 테스트 사용자 계정 구성

  - 기본 가상 트랜잭션을 사용하여 기본적인 감시자 노드 구성

  - 확장 테스트 구성

  - 가상 트랜잭션 추가 및 제거

  - 감시자 노드 구성 보기 및 테스트

## 테스트 사용자 계정 구성

테스트 사용자는 실제 사람을 나타내지 않아도 되지만 올바른 Active Directory 도메인 서비스 계정이어야 하며 Lync Server 2013에 이러한 계정을 사용하도록 설정해야 합니다. 이러한 계정은 올바른 SIP 주소를 가져야 하며 Test-CsPstnPeerToPeerCall 가상 트랜잭션을 사용하기 위해 Enterprise Voice에 이러한 계정을 사용하도록 설정해야 합니다. TrustedServer 인증 방법을 사용하는 경우에는 이러한 계정이 존재하고 여기에 명시된 대로 구성되었는지 확인하기만 하면 됩니다. 테스트할 각 풀에 대해 3명 이상의 테스트 사용자를 할당해야 합니다.

또한 협상 인증 방법을 사용하는 경우에는 **Set-CsTestUserCredential** cmdlet 및 Lync Server 관리 셸을 사용하여 가상 트랜잭션에 이러한 테스트 계정을 사용하도록 설정해야 합니다. 이렇게 하려면 다음과 같은 명령을 실행하면 됩니다. 이러한 명령은 세 Active Directory 사용자 계정을 이미 만들었고 이러한 계정을 Lync Server 2013에 사용하도록 설정한 것으로 가정합니다.

    Set-CsTestUserCredential -SipAddress "sip:watcher1@litwareinc.com" -UserName "litwareinc\watcher1" -Password "P@ssw0rd"
    Set-CsTestUserCredential -SipAddress "sip:watcher2@litwareinc.com" -UserName "litwareinc\watcher2" -Password "P@ssw0rd"
    Set-CsTestUserCredential -SipAddress "sip:watcher3@litwareinc.com" -UserName "litwareinc\watcher3" -Password "P@ssw0rd"

SIP 주소뿐만 아니라 사용자 이름과 암호도 명령에 포함해야 합니다. 암호를 포함하지 않을 경우 Set-CsTestUserCredential에서 해당 정보 입력을 요청하는 메시지를 표시합니다. 사용자 이름은 위와 같이 도메인 이름\\사용자 이름 형식이나 사용자 이름@도메인 이름 형식을 사용하여 지정할 수 있습니다. 예를 들면 다음과 같습니다.

    -UserName "watcher3@litwareinc.com"

테스트 사용자 자격 증명이 만들어졌는지 확인하려면 Lync Server 관리 셸 내에서 다음 명령을 실행합니다.

    Get-CsTestUserCredential -SipAddress "sip:watcher1@litwareinc.com"
    Get-CsTestUserCredential -SipAddress "sip:watcher2@litwareinc.com"
    Get-CsTestUserCredential -SipAddress "sip:watcher3@litwareinc.com"

각 사용자에 대해 다음과 같은 정보가 반환됩니다.

    UserName                        Password
    --------                        --------
    Litwareinc\watcher1              System.Security.SecureString

## 기본 가상 트랜잭션을 사용하여 기본적인 감시자 노드 구성

테스트 사용자를 만들었으면 다음과 같은 명령을 사용하여 감시자 노드를 만들 수 있습니다.

    New-CsWatcherNodeConfiguration -TargetFqdn "atl-cs-001.litwareinc.com" -PortNumber 5061 -TestUsers @{Add= "sip:watcher1@litwareinc.com","sip:watcher2@litwareinc.com", "sip:watcher3@litwareinc.com"}

이 명령은 기본 설정을 사용하고 기본 가상 트랜잭션 집합을 실행하는 새 감시자 노드를 만듭니다. 또한 새 감시자 노드는 테스트 사용자 watcher1@litwareinc.com, watcher2@litwareinc.com 및 watcher3@litwareinc.com을 사용합니다. 감시자 노드에 TrustedServer 인증을 사용하는 경우 세 테스트 계정은 Active Directory 및 Lync Server를 사용하도록 설정된 올바른 사용자 계정이면 됩니다. 또한 감시자 노드에 협상 인증 방법을 사용하는 경우에는 **Set-CsTestUserCredential** cmdlet으로 감시자 노드에 이러한 사용자 계정을 사용하도록 설정해야 합니다.

## 확장 테스트 구성

PSTN(공중 전화망)과의 연결을 확인하는 PSTN 테스트를 사용하려는 경우 감시자 노드를 설정할 때 몇 가지 추가적인 구성이 필요합니다. 첫째, 테스트 사용자를 PSTN 테스트 유형에 연결해야 합니다. 이렇게 하려면 Lync Server 관리 셸 내에서 다음과 같은 명령을 실행합니다.

    $pstnTest = New-CsExtendedTest -TestUsers "sip:watcher1@litwareinc.com", "sip:watcher2@litwareinc.com", "sip:watcher3@litwareinc.com"  -Name "Contoso Provider Test" -TestType PSTN

이 명령의 결과는 변수에 저장되어야 합니다. 이 예에 사용된 변수 이름은 $pstnTest입니다.

이제 **New-CsWatcherNodeConfiguration** cmdlet을 사용하여 $pstnTest 변수에 저장된 테스트 유형을 Lync Server 2013 풀에 연결할 수 있습니다. 예를 들어 다음 명령은 atl-cs-001.litwareinc.com 풀에 대한 새 감시자 노드 구성을 만들고 앞에서 만든 세 테스트 사용자를 추가한 후 PSTN 테스트 유형을 추가합니다.

    New-CsWatcherNodeConfiguration -TargetFqdn "atl-cs-001.litwareinc.com" -PortNumber 5061 -TestUsers @{Add= "sip:watcher1@litwareinc.com","sip:watcher2@litwareinc.com", "sip:watcher3@litwareinc.com"} -ExtendedTests @{Add=$pstnTest}

Lync Server 코어 파일과 RTCLocal 데이터베이스를 감시자 노드 컴퓨터에 설치하지 않은 경우 위의 명령이 실패합니다.

여러 음성 정책을 테스트하려면 **New-CsExtendedTest** cmdlet을 사용하여 각 정책에 대한 확장 테스트를 만들고 이 테스트에 할당된 사용자를 원하는 음성 정책으로 구성해야 합니다. 그런 후에 다음과 같은 명령을 사용하여 확장 테스트를 **New-CsWatcherNodeConfiguration** cmdlet에 전달해야 합니다.

    -ExtendedTests @{Add=$pstnTest1,$pstnTest2,$pstnTest3}

Tests 매개 변수를 사용하지 않고 New-CsWatcherNodeConfiguration을 호출할 경우 새 감시자 노드에 기본 가상 트랜잭션(및 지정된 확장 가상 트랜잭션)만 사용하도록 설정됩니다. 그 결과 감시자 노드는 다음 구성 요소를 테스트하게 됩니다.

  - 등록

  - 메신저

  - GroupIM

  - P2PAV(피어 투 피어 오디오/비디오 세션)

  - AvConference(오디오/회의)

  - 현재 상태

  - ABS(주소록 서비스)

  - ABWQ(주소록 웹 서비스)

  - PSTN(확장 테스트로 지정된 PSTN 게이트웨이 통화. 기본적으로 PSTN은 사용하지 않도록 설정됩니다. 이 경우에는 이 테스트가 사용하도록 설정되었는데, 그 이유는 단지 명령에 ExtendedTests 매개 변수를 사용하여 PSTN을 사용하도록 설정했기 때문입니다.)

또한 결과적으로 다음 구성 요소가 기본적으로 테스트되지 않습니다.

  - AVEdgeConnectivity

  - MCXP2PIM(모바일 장치 메신저)

  - ExumConnectivity(Exchange 통합 메시징)

  - JoinLauncher

  - PersistentChatMessage

  - DataConference

  - XmppIM

  - UnifiedContactStore

## 가상 트랜잭션 추가 및 제거

감시자 노드가 구성된 후에는 **Set-CsWatcherNodeConfiguration** cmdlet을 사용하여 이 노드에서 가상 트랜잭션을 추가하거나 제거할 수 있습니다. 예를 들어 감시자 노드에 PersistentChatMessage 테스트를 추가하려면 Add 메서드를 사용하는 다음과 같은 명령을 실행합니다.

    Set-CsWatcherNodeConfiguration -Identity "atl-cs-001.litwareinc.com" -Tests @{Add="PersistentChatMessage"}

테스트 이름을 쉼표로 구분하여 여러 테스트를 추가할 수 있습니다. 예를 들면 다음과 같습니다.

    Set-CsWatcherNodeConfiguration -Identity "atl-cs-001.litwareinc.com" -Tests @{Add="PersistentChatMessage","DataConference","UnifiedContactStore"}

감시자 노드에서 이미 이러한 테스트(예: DataConference)를 하나 이상 사용하도록 설정한 경우 다음과 같은 오류 메시지가 표시됩니다.

    Set-CsWatcherNodeConfiguration : 'urn:schema:Microsoft.Rtc.Management.Settings.WatcherNode.2010:TestName' 키 또는 고유한 identity 제약 조건에 중복 키 시퀀스 'DataConference'이(가) 있습니다.

이 오류가 발생하는 경우 변경 내용이 적용되지 않습니다. 중복 테스트를 제거한 후 명령을 다시 실행해야 합니다.

감시자 노드에서 가상 트랜잭션을 제거하려면 Add 메서드 대신 Remove 메서드를 사용합니다. 예를 들어 다음 명령은 감시자 노드에서 ABWQ 테스트를 제거합니다.

    Set-CsWatcherNodeConfiguration -Identity "atl-cs-001.litwareinc.com" -Tests @{Remove="ABWQ"}

또한 Replace 메서드를 사용하여 현재 사용하도록 설정된 모든 테스트를 하나 이상의 새 테스트로 바꿀 수 있습니다. 예를 들어 한 감시자 노드로 메신저 테스트를 실행하려면 다음 명령을 사용하여 그렇게 구성할 수 있습니다.

    Set-CsWatcherNodeConfiguration -Identity "atl-cs-001.litwareinc.com" -Tests @{Replace="IM"}

위의 명령을 실행하면 지정된 감시자 노드에서 IM을 제외한 모든 가상 트랜잭션이 사용하지 않도록 설정됩니다.

## 감시자 노드 구성 보기 및 테스트

감시자 노드에 할당된 테스트를 보려면 다음과 같은 명령을 사용합니다.

    Get-CsWatcherNodeConfiguration -Identity "atl-cs-001.litwareinc.com" | Select-Object -ExpandProperty Tests

위의 명령은 노드에 할당된 가상 트랜잭션에 따라 다음과 같은 정보를 반환합니다.

    Registration
    IM
    GroupIM
    P2PAV
    AvConference
    Presence
    PersistentChatMessage
    DataConference


> [!TIP]
> 사전순으로 가상 트랜잭션을 보려면 다음 명령을 대신 사용합니다.<BR>Get-CsWatcherNodeConfiguration –Identity "atl-cs-001.litwareinc.com" | Select-Object –ExpandProperty Tests | Sort-Object



감시자 노드가 만들어졌는지 확인하려면 Lync Server 관리 셸 내에서 다음 명령을 입력합니다.

    Get-CsWatcherNodeConfiguration

그러면 다음과 같은 정보가 표시됩니다.

    Identity      : atl-cs-001.litwareinc.com
    TestUsers     : {sip:watcher1@litwareinc.com, sip:watcher2@litwareinc.com ...}
    ExtendedTests : {TestUsers=IList<System.String>;Name=PSTN Test; Te...}
    TargetFqdn    : atl-cs-001.litwareinc.com
    PortNumber    : 5061

감시자 노드가 올바르게 구성되었는지 확인하려면 Lync Server 관리 셸 내에서 다음 명령을 입력합니다.

    Test-CsWatcherNodeConfiguration

위의 명령은 배포의 각 감시자 노드를 테스트하여 다음과 같은 정보를 표시합니다.

  - 필요한 등록자 역할이 설치되었는지 여부

  - Set-CsWatcherNodeConfiguration을 실행했을 때 필요한 레지스트리 키가 만들어졌는지 여부

  - 서버에서 올바른 버전의 Lync Server가 실행되고 있는지 여부

  - 포트가 올바르게 구성되었는지 여부

  - 할당된 테스트 사용자에게 필요한 자격 증명이 있는지 여부

