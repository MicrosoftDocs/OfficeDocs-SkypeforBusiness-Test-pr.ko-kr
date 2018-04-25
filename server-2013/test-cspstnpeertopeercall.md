---
title: Test-CsPstnPeerToPeerCall
TOCTitle: Test-CsPstnPeerToPeerCall
ms:assetid: 839cf83f-b667-4cbe-b1ab-28f54a8a9d0b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398662(v=OCS.15)
ms:contentKeyID: 49304238
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsPstnPeerToPeerCall

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자 쌍이 PSTN(공중 전화망) 게이트웨이를 통해 피어-투-피어 통화를 수행할 수 있는지 테스트합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Test-CsPstnPeerToPeerCall -ReceiverCredential <PSCredential> -ReceiverSipAddress <String> -SenderCredential <PSCredential> -SenderSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] <COMMON PARAMETERS>

    Test-CsPstnPeerToPeerCall -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-ReceiverSipAddress <String>] [-RegistrarPort <Int32>] [-SenderSipAddress <String>] <COMMON PARAMETERS>

    Test-CsPstnPeerToPeerCall [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>]

## 예제

## 예제 1

예제 1에서는 미리 구성된 테스트 사용자 쌍이 atl-cs-001 풀에 로그온할 수 있는지 확인합니다. 테스트 사용자가 로그온되면 **Test-CsPstnPeerToPeerCall** cmdlet이 두 사용자가 PSTN 게이트웨이를 통해 피어 투 피어 통화를 수행할 수 있는지 확인합니다. 이 명령은 atl-cs-001.litwareinc.com 풀에 대해 테스트 사용자가 정의된 경우에만 작동합니다. 정의된 경우 첫 번째 테스트 사용자가 시스템에 로그온할 수 있는지 확인한 다음 이 사용자가 풀에 정의된 두 번째 사용자에게 전화를 걸 수 있는지 확인합니다.

테스트 사용자가 정의되어 있지 않으면 테스트를 수행할 때 사용할 사용자를 알 수 없으므로 명령이 실패합니다. 풀에 대해 테스트 사용자를 정의하지 않았거나 서버 플랫폼 모드로 실행 중이지 않은 경우에는 SenderSipAddress 및 ReceiverSipAddress 매개 변수를 포함하고 사용자의 해당 자격 증명을 테스트 계정으로 사용해야 합니다. 그런 다음 **Test-CsPstnPeerToPeerCall** cmdlet은 지정된 두 사용자를 사용하여 검사를 수행합니다.

    Test-CsPstnPeerToPeerCall -TargetFqdn atl-cs-001.litwareinc.com 

## 예제 2

예제 2에 표시된 명령은 사용자 쌍(litwareinc\\pilar 및 litwareinc\\kenmyer)이 Lync Server에 로그온한 다음 PSTN 게이트웨이를 통해 피어-투-피어 통화를 수행할 수 있는지 테스트합니다. 이 작업을 수행하기 위해 이 예제의 첫 번째 명령은 **Get-Credential** cmdlet을 사용하여 사용자 Pilar Ackerman의 이름 및 암호를 포함하는 Windows PowerShell 자격 증명 개체를 만듭니다. 로그온 이름 litwareinc\\pilar는 매개 변수로 포함되었으므로 관리자는 Windows PowerShell 자격 증명 요청 대화 상자에 Pilar Ackerman 계정의 암호만 입력하면 됩니다. 이렇게 만들어진 자격 증명 개체는 $cred1이라는 변수에 저장됩니다. 두 번째 명령도 같은 작업을 수행하지만 이번에는 Ken Myer 계정의 자격 증명 개체를 반환합니다.

두 자격 증명 개체를 얻은 상태에서 예제의 세 번째 명령은 두 사용자가 Lync Server에 로그온한 다음 PSTN 게이트웨이를 통해 피어 투 피어 통화를 수행할 수 있는지 확인합니다. 이 작업을 수행하기 위해 **Test-CsPstnPeerToPeerCall** cmdlet을 TargetFqdn(등록자 풀의 FQDN), SenderSipAddress(첫 번째 테스트 사용자의 SIP 주소), SenderCredential(이 사용자의 자격 증명을 포함하는 Windows PowerShell 개체), ReceiverSipAddress(다른 테스트 사용자의 SIP 주소) 및 ReceiverCredential(다른 사용자의 자격 증명을 포함하는 Windows PowerShell 개체) 매개 변수와 함께 호출합니다.

    $cred1 = Get-Credential "litwareinc\pilar"
    $cred2 = Get-Credential "litwareinc\kenmyer"
    
    Test-CsPstnPeerToPeerCall -TargetFqdn atl-cs-001.litwareinc.com -SenderSipAddress "sip:jhaas@litwareinc.com" -SenderCredential $cred1 -ReceiverSipAddress "sip:kenmyer@litwareinc.com" -ReceiverCredential $cred2

## 예제 3

예제 3에서는 서버 플랫폼 모드로 Test-CsPstnPeerToPeerCall cmdlet을 사용하는 방법을 보여 줍니다. 이 모드에서는 테스트 사용자의 SIP 주소를 지정하지만 사용자 자격 증명은 포함되지 않습니다. 이 방식으로 실행하면 Lync Server에서 인증서를 사용하여 두 테스트 사용자를 인증합니다.

    Test-CsPstnPeerToPeerCall -TargetFqdn atl-cs-001.litwareinc.com -SenderSipAddress "sip:jhaas@litwareinc.com" -ReceiverSipAddress "sip:kenmyer@litwareinc.com" 

## 자세한 정보

**Test-CsPstnPeerToPeerCall** cmdlet은 Lync Server "가상 트랜잭션"의 한 예입니다. 가상 트랜잭션은 Lync Server에서 사용자가 시스템 로그온, 메신저 대화 교환 또는 PSTN(공중 전화망)의 전화로 전화 걸기와 같은 일반적인 작업을 성공적으로 수행할 수 있는지 확인하는 데 사용됩니다. 이러한 테스트는 관리자가 "수동으로" 수행하거나 Microsoft System Center Operations Manager(이전 Microsoft Operations Manager)와 같은 응용 프로그램에 의해 자동으로 실행될 수 있습니다.

가상 트랜잭션은 일반적으로 두 가지 방법으로 수행됩니다. 많은 관리자가 **CsHealthMonitoringConfiguration** cmdlet을 사용하여 각 등록자 풀의 테스트 사용자를 설정합니다. 이러한 테스트 사용자는 가상 트랜잭션에 사용하도록 미리 구성된 사용자 쌍입니다. 일반적으로 이러한 계정은 테스트 계정이며 실제 사용자가 소유한 계정은 아닙니다. 풀에 테스트 사용자가 구성되면 관리자는 테스트에 참여한 사용자 계정의 ID 및 자격 증명을 지정하지 않고도 해당 풀에 대해 가상 트랜잭션을 실행할 수 있습니다.

또는 실제 사용자 계정을 사용하여 가상 트랜잭션을 실행할 수 있습니다. 예를 들어 두 사용자가 메신저 대화를 교환할 수 없는 경우 관리자는 이 두 사용자 계정(테스트 계정 쌍이 아님)을 사용하여 가상 트랜잭션을 실행하고 문제를 진단 및 해결할 수 있습니다. 실제 사용자 계정을 사용하여 가상 트랜잭션을 수행하도록 결정한 경우 각 사용자에 대한 로그온 이름 및 암호를 제공해야 합니다.

**Test-CsPstnPeerToPeerCall** cmdlet을 서버 플랫폼 모드로 사용할 수도 있습니다. 이 경우에는 사용자의 SIP 주소만 지정하면 Lync Server에서 인증서를 사용하여 해당 사용자를 인증합니다.

**Test-CsPstnPeerToPeerCall**을 호출하면 이 cmdlet은 먼저 두 테스트 사용자를 Lync Server에 로그온시키려고 합니다. 이 로그온이 성공한 경우 cmdlet은 사용자 1이 PSTN 게이트웨이를 통해 사용자 2에게 전화를 걸도록 합니다. **Test-CsPstnPeerToPeerCall** cmdlet은 다이얼 플랜, 음성 정책 및 기타 테스트 사용자에게 할당된 정책 및 구성을 사용하여 이 전화를 겁니다. 테스트가 계획대로 진행될 경우 cmdlet은 사용자 2가 전화를 받았는지 확인한 다음 두 테스트 계정을 모두 시스템에서 로그오프합니다.

**Test-CsPstnPeerToPeerCall** cmdlet은 실제로 전화를 걸어 연결을 설정할 수 있는지 확인한 다음 네트워크를 통해 DTMF(Dual-Tone Multifrequency)를 전송하여 이 연결을 통해 미디어를 전송할 수 있는지 확인합니다. 그러나 이 통화에 cmdlet 자체에서 응답한 경우 통화를 수동으로 종료할 필요가 없습니다. 즉, 이 전화에 아무도 응답할 필요가 없습니다.

이 cmdlet을 실행할 수 있는 사용자: 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsPstnPeerToPeerCall"}

## 매개 변수


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>매개 변수</th>
<th>필수</th>
<th>유형</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>ReceiverCredential</em></p></td>
<td><p>필수</p></td>
<td><p>PS 자격 증명</p></td>
<td><p>테스트할 두 사용자 계정 중 첫 번째 사용자 계정의 사용자 자격 증명 개체입니다. ReceiverCredential에 전달되는 값은 <strong>Get-Credential</strong> cmdlet을 사용하여 가져온 개체 참조여야 합니다. 예를 들어 다음 코드는 사용자 litwareinc\pilar의 자격 증명 개체를 반환하고 이 개체를 $y라는 변수에 저장합니다.</p>
<p>$y = Get-Credential &quot;litwareinc\pilar&quot;</p>
<p>이 명령을 실행할 때는 사용자 암호를 제공해야 합니다.</p>
<p>풀의 상태 모니터링 구성 설정에 따라 테스트를 실행하거나 서버 플랫폼 모드로 실행 중인 경우에는 받는 사람 자격 증명이 필요하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SenderCredential</em></p></td>
<td><p>필수</p></td>
<td><p>PS 자격 증명</p></td>
<td><p>테스트할 두 사용자 계정 중 두 번째 사용자 계정의 사용자 자격 증명 개체입니다. SenderCredential에 전달되는 값은 <strong>Get-Credential</strong> cmdlet을 사용하여 가져온 개체 참조여야 합니다. 예를 들어 다음 코드는 사용자 litwareinc\kenmyer의 자격 증명 개체를 반환하고 이 개체를 $x라는 변수에 저장합니다.</p>
<p>$x = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
<p>이 명령을 실행할 때는 사용자 암호를 제공해야 합니다.</p>
<p>풀의 상태 모니터링 구성 설정에 따라 테스트를 실행하거나 서버 플랫폼 모드로 실행 중인 경우에는 보낸 사람 자격 증명이 필요하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>TargetFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>문자열</p></td>
<td><p>테스트할 풀의 FQDN(정규화된 도메인 이름)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Authentication</em></p></td>
<td><p>선택</p></td>
<td><p>SIP 가상 트랜잭션 인증 메커니즘</p></td>
<td><p>테스트에서 사용되는 인증 유형입니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>* TrustedServer</p>
<p>* Negotiate</p>
<p>* ClientCertificate</p>
<p>* LiveID</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>OutLoggerVariable</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>이 매개 변수가 있으면 cmdlet을 실행하여 얻은 자세한 출력이 지정된 변수에 저장됩니다. 이 변수에 포함된 메서드 쌍(ToHTML 및 ToXML)은 이러한 출력을 HTML 또는 XML 파일에 저장하는 데 사용할 수 있습니다.</p>
<p>출력을 $TestOutput이라는 로거 변수에 저장하려면 다음과 같은 구문을 사용합니다.</p>
<p>-OutLoggerVariable TestOutput</p>
<p>참고: 변수 이름을 지정할 때 $ 문자를 추가해서는 안 됩니다. 로거 변수에 저장된 정보를 HTML 파일에 저장하려면 다음 명령을 사용합니다.</p>
<p>$TestOutput.ToHTML() &gt; C:\Logs\TestOutput.html</p>
<p>로거 변수에 저장된 정보를 XML 파일에 저장하려면 다음 명령을 사용합니다.</p>
<p></p>
<p>$TestOutput.ToXML() &gt; C:\Logs\TestOutput.xml</p></td>
</tr>
<tr class="odd">
<td><p><em>OutVerboseVariable</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>이 매개 변수가 있으면 cmdlet을 실행하여 얻은 자세한 출력이 지정된 변수에 저장됩니다. 예를 들어 출력을 $TestOutput이라는 변수에 저장하려면 다음과 같은 구문을 사용합니다.</p>
<p>-OutVerboseVariable TestOutput</p>
<p>변수 이름을 지정할 때 $ 문자를 추가해서는 안 됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ReceiverSipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>테스트할 두 사용자 계정 중 첫 번째 사용자 계정의 SIP 주소입니다(예: -ReceiverSipAddress &quot;sip:pilar@litwareinc.com&quot;). ReceiverSipAddress 매개 변수는 ReceiverCredential과 동일한 사용자 계정을 참조해야 합니다.</p>
<p>풀의 상태 모니터링 구성 설정에 따라 테스트를 실행하는 경우에는 SIP 주소가 필요하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>RegistrarPort</em></p></td>
<td><p>선택</p></td>
<td><p>Int32</p></td>
<td><p>등록자 서비스에서 사용하는 SIP 포트입니다. 등록자에서 기본 포트 5061을 사용하는 경우에는 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SenderSipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>테스트할 두 사용자 계정 중 두 번째 사용자 계정의 SIP 주소입니다(예: -SenderSipAddress &quot;sip:kenmyer@litwareinc.com&quot;). SenderSipAddress 매개 변수는 SenderCredential과 동일한 사용자 계정을 참조해야 합니다.</p>
<p>풀의 상태 모니터링 구성 설정에 따라 테스트를 실행하는 경우에는 SIP 주소가 필요하지 않습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Test-CsPstnPeerToPeerCall** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Test-CsPstnPeerToPeerCall** cmdlet은 Microsoft.Rtc.SyntheticTransactions.TaskOutput 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Test-CsPstnOutboundCall](test-cspstnoutboundcall.md)

