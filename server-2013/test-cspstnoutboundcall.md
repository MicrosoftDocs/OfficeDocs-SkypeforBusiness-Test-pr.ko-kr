---
title: Test-CsPstnOutboundCall
TOCTitle: Test-CsPstnOutboundCall
ms:assetid: 12d940c3-8526-4c8f-8dc1-3fe65a3211bc
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398207(v=OCS.15)
ms:contentKeyID: 49302872
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsPstnOutboundCall

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자가 PSTN(공중 전화망)에 있는 전화 번호로 전화를 걸 수 있는지 테스트합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Test-CsPstnOutboundCall -TargetPstnPhoneNumber <String> -UserCredential <PSCredential> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] <COMMON PARAMETERS>

    Test-CsPstnOutboundCall -TargetFqdn <String> -TargetPstnPhoneNumber <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-UserSipAddress <String>] <COMMON PARAMETERS>

    Test-CsPstnOutboundCall [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>]

## 예제

## 예제 1

예제 1은 미리 구성된 테스트 사용자가 atl-cs-001.litwareinc.com 풀에 로그온한 다음 PSTN 게이트웨이를 통해 전화를 걸 수 있는지 확인합니다. 이 명령은 atl-cs-001.litwareinc.com 풀에 대해 테스트 사용자가 정의된 경우에만 작동합니다. 정의되어 있는 경우 이 명령은 첫 번째 테스트 사용자가 시스템에 로그온할 수 있는지, 그리고 로그온할 수 있는 경우 PSTN 네트워크에 있는 전화로 전화를 걸 수 있는지 여부를 확인합니다.

등록자가 정의되어 있지 않으면 테스트를 수행할 때 이용할 사용자를 알 수 없으므로 명령이 실패합니다. 풀에 대해 테스트 사용자를 정의하지 않은 경우 UserSipAddress 매개 변수와 테스트에 관련된 사용자 계정의 자격 증명을 포함해야 합니다. 그러면 **Test-CsPstnOutboundCall** cmdlet이 지정된 사용자를 사용하여 검사를 수행합니다.

    Test-CsPstnOutboundCall -TargetFqdn atl-cs-001.litwareinc.com -TargetPstnPhoneNumber "+15551234567" 

## 예제 2

예제 2에 표시된 명령은 테스트 사용자(litwareinc\\kenmyer)가 Lync Server에 로그온한 다음 PSTN 게이트웨이를 통해 전화를 걸 수 있는지 테스트합니다. 이 작업을 수행하기 위해 이 예제의 첫 번째 명령은 **Get-Credential** cmdlet을 사용하여 사용자 Ken Myer의 이름 및 암호를 포함하는 Windows PowerShell 자격 증명 개체를 만듭니다. 로그온 이름 litwareinc\\kenmyer는 매개 변수로 포함되었으므로 관리자는 Windows PowerShell 자격 증명 요청 대화 상자에 Ken Myer 계정의 암호만 입력하면 됩니다. 이렇게 만들어진 자격 증명 개체는 $cred1이라는 변수에 저장됩니다.

자격 증명 개체가 준비되면 예제의 두 번째 명령에서 테스트 사용자가 Lync Server에 로그온한 다음 대상 전화 번호(+15551234567)로 전화를 걸 수 있는지 확인합니다. 이 작업을 수행하기 위해 **Test-CsPstnOutboundCall** cmdlet을 TargetFqdn(등록자 풀의 FQDN), UserSipAddress(전화를 거는 사용자의 SIP 주소), UserCredential(테스트 사용자의 자격 증명이 포함된 Windows PowerShell 개체) 및 TargetPstnPhoneNumber(대상 전화 번호) 매개 변수와 함께 호출합니다.

    $cred1 = Get-Credential "litwareinc\kenmyer"
    
    Test-CsPstnOutboundCall -TargetFqdn atl-cs-001.litwareinc.com -TargetPstnPhoneNumber "+15551234567" -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $cred1

## 예제 3

예제 3에서는 서버 플랫폼 모드로 **Test-CsPstnOutboundCall** cmdlet을 사용하는 방법을 보여 줍니다. 이 모드에서는 사용자의 SIP 주소를 지정하지만 사용자 자격 증명은 포함되지 않습니다. 이 방식으로 실행하면 Lync Server에서 인증서를 사용하여 테스트 사용자를 인증합니다.

    Test-CsPstnOutboundCall -TargetFqdn atl-cs-001.litwareinc.com -UserSipAddress sip:kenmyer@litwareinc.com -TargetPstnPhoneNumber "+15551234567"

## 자세한 정보

**Test-CsPstnOutboundCall** cmdlet은 Lync Server "가상 트랜잭션"의 한 예입니다. 가상 트랜잭션은 Lync Server에서 사용자가 시스템 로그온, 메신저 대화 교환 또는 PSTN(공중 전화망)의 전화로 전화 걸기와 같은 일반적인 작업을 성공적으로 수행할 수 있는지 확인하는 데 사용됩니다. 이러한 테스트는 관리자가 "수동으로" 수행하거나 Microsoft System Center Operations Manager(이전 Microsoft Operations Manager)와 같은 응용 프로그램에 의해 자동으로 실행될 수 있습니다.

가상 트랜잭션은 일반적으로 두 가지 방법으로 수행됩니다. 많은 관리자가 **CsHealthMonitoringConfiguration** cmdlet을 사용하여 각 등록자 풀의 테스트 사용자를 설정합니다. 이러한 테스트 사용자는 가상 트랜잭션에 사용하도록 미리 구성된 사용자 쌍입니다. 일반적으로 이는 테스트 계정이며 실제 사용자에게 속한 계정이 아닙니다. 풀에 테스트 사용자가 구성되면 관리자는 테스트에 참여한 사용자 계정의 ID 및 자격 증명을 지정하지 않고도 해당 풀에 대해 가상 트랜잭션을 실행할 수 있습니다.

또는 실제 사용자 계정을 사용하여 가상 트랜잭션을 실행할 수 있습니다. 예를 들어 두 사용자가 메신저 대화를 교환할 수 없는 경우 관리자는 이 두 사용자 계정(테스트 계정 쌍이 아님)을 사용하여 가상 트랜잭션을 실행하고 문제를 진단 및 해결할 수 있습니다. 실제 사용자 계정을 사용하여 가상 트랜잭션을 수행하도록 결정한 경우 각 사용자에 대한 로그온 이름 및 암호를 제공해야 합니다.

Test-CsPstnOutboundCall을 서버 플랫폼 모드로 사용할 수도 있습니다. 이 경우에는 사용자의 SIP 주소만 지정하면 Lync Server에서 인증서를 사용하여 해당 사용자를 인증합니다.

**Test-CsPstnOutboundCall** cmdlet을 실행하는 경우 이 cmdlet은 먼저 테스트 사용자를 Lync Server에 로그온하려고 합니다. 로그온이 성공하면 cmdlet은 PSTN 게이트웨이를 통해 전화를 걸려고 합니다. 이 전화를 걸 때는 테스트 계정에 할당된 다이얼 플랜, 음성 정책 및 기타 정책과 설정을 사용합니다. 전화를 받으면 cmdlet에서 미디어 연결을 확인하기 위해 네트워크를 통해 DTMF(Dual-Tone Multi-Frequency) 코드를 전송합니다.

**Test-CsPstnOutboundCall** cmdlet은 테스트 수행 시 실제로 전화를 겁니다. 테스트에 성공하려면 대상 전화가 울리고 전화를 받아야 합니다. 또한 관리자가 이 통화를 수동으로 종료해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsPstnOutboundCall"}

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
<td><p><em>TargetFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>문자열</p></td>
<td><p>테스트할 풀의 FQDN(정규화된 도메인 이름)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>TargetPstnPhoneNumber</em></p></td>
<td><p>필수</p></td>
<td><p>문자열</p></td>
<td><p>테스트를 수행할 때 전화를 걸 PSTN 전화 번호입니다. 대상 전화 번호는 E.164 형식을 사용하여 지정하는 것이 가장 좋습니다. 예를 들어 &quot;+14255551298&quot;이 이러한 형식의 번호에 해당하는데, 더하기(+) 기호가 맨 앞에 오고, 국가 번호(1), 지역 번호(425) 및 전화 번호(5551298)가 차례로 뒤에 오는 형식입니다. 전화 번호를 지정할 때는 대시, 괄호 또는 기타 문자를 사용하지 마십시오.</p>
<p>E.164 형식을 사용하지 않는 경우에는 테스트 사용자의 다이얼 플랜이 번호 뒤에 추가됩니다. 그러면 Lync Server에서 해당 다이얼 플랜을 사용하여 번호를 E.164 형식으로 정규화합니다. 번호를 정규화할 수 없는 경우에는 통화가 연결되지 않고 테스트에 실패합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserCredential</em></p></td>
<td><p>필수</p></td>
<td><p>PS 자격 증명</p></td>
<td><p>테스트할 계정의 사용자 자격 증명 개체입니다. UserCredential에 전달되는 값은 <strong>Get-Credential</strong> cmdlet을 사용하여 가져온 개체 참조여야 합니다. 예를 들어 다음 코드는 사용자 litwareinc\kenmyer의 자격 증명 개체를 반환하고 이 개체를 $x라는 변수에 저장합니다.</p>
<p>$x = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
<p>이 명령을 실행할 때는 사용자 암호를 제공해야 합니다.</p>
<p>명령에서 CsHealthMonitoringConfiguration cmdlet을 사용하여 구성된 테스트 사용자를 사용하는 경우에는 이 매개 변수가 필요하지 않습니다. 또한 서버 플랫폼 모드로 테스트를 수행하는 경우에도 이 매개 변수를 지정할 필요가 없습니다. 이 경우 Lync Server는 인증서를 사용하여 사용자를 인증합니다.</p></td>
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
<td><p>SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>OutLoggerVariable</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
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
<td><p><em>RegistrarPort</em></p></td>
<td><p>선택</p></td>
<td><p>Int32</p></td>
<td><p>등록자 서비스에서 사용하는 SIP 포트입니다. 등록자에서 기본 포트 5061을 사용하는 경우에는 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserSipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>테스트할 사용자 계정의 SIP 주소입니다(예: -SenderSipAddress &quot;sip:kenmyer@litwareinc.com&quot;). UserSipAddress 매개 변수는 UserCredential과 동일한 사용자 계정을 참조해야 합니다.</p>
<p>명령에서 CsHealthMonitoringConfiguration cmdlet을 사용하여 구성된 테스트 사용자를 사용하는 경우에는 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Test-CsPstnOutboundCall** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Test-CsPstnOutboundCall** cmdlet은 Microsoft.Rtc.SyntheticTransactions.TaskOutput 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Test-CsPstnPeerToPeerCall](test-cspstnpeertopeercall.md)

