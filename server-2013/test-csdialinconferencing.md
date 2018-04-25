---
title: Test-CsDialInConferencing
TOCTitle: Test-CsDialInConferencing
ms:assetid: e4aedf4f-77ac-4c8b-9613-07f8ea12c041
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399013(v=OCS.15)
ms:contentKeyID: 49305328
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsDialInConferencing

 

_**마지막으로 수정된 항목:** 2015-03-09_

**Test-CsDialInConferencing** cmdlet은 사용자가 전화 접속 회의 세션에 참가할 수 있는지 확인합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Test-CsDialInConferencing -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-TargetPstnPhoneNumber <String>] [-UserSipAddress <String>] [-VerifyConferenceJoin <$true | $false>] <COMMON PARAMETERS>

    Test-CsDialInConferencing -UserCredential <PSCredential> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] [-TargetPstnPhoneNumber <String>] [-VerifyConferenceJoin <$true | $false>] <COMMON PARAMETERS>

    Test-CsDialInConferencing [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>]

## 예제

## 예제 1

예제 1에서는 미리 구성된 테스트 사용자가 atl-cs-001.litwareinc.com 풀에서 전화 접속 회의에 참가할 수 있는지 확인합니다. 이 명령은 atl-cs-001.litwareinc.com 풀에 대해 테스트 사용자가 정의된 경우에만 작동합니다. 사용자가 정의된 경우 테스트 사용자가 Lync Server에 로그온할 수 있는지 여부를 확인합니다.

테스트 사용자가 정의되지 않은 경우 어떤 사용자로 로그온할지를 알 수 없기 때문에 명령이 실패합니다. 풀의 테스트 사용자를 정의하지 않은 경우 로그온을 시도할 때 사용할 사용자의 자격 증명을 UserCredential 매개 변수와 함께 포함해야 합니다.

    Test-CsDialInConferencing -TargetFqdn atl-cs-001.litwareinc.com 

## 예제 2

예제 2에 표시된 명령은 특정 사용자(litwareinc\\pilar)가 atl-cs-001.litwareinc.com 풀에서 전화 접속 회의에 참가할 수 있는지 테스트합니다. 이 작업을 수행하기 위해 이 예제의 첫 번째 명령은 **Get-Credential** cmdlet을 사용하여 사용자 Pilar Ackerman의 이름 및 암호를 포함하는 Windows PowerShell 자격 증명 개체를 만듭니다. 로그온 이름 –litwareinc\\pilar가 매개 변수로 포함되었으므로 관리자는 Windows PowerShell 자격 증명 요청 대화 상자에 Pilar Ackerman 계정의 암호를 입력하기만 하면 됩니다. 이렇게 만들어진 자격 증명 개체는 $cred1이라는 변수에 저장됩니다.

두 번째 명령은 사용자 Pilar Ackerman이 atl-cs-001.litwareinc.com 풀에 로그온하여 전화 접속 회의에 참가할 수 있는지 확인합니다. 이 작업을 수행하기 위해 **Test-CsDialInConferencing** cmdlet을 TargetFqdn(등록자 풀의 FQDN), UserCredential(Pilar Ackerman의 사용자 자격 증명이 포함된 Windows PowerShell 개체) 및 UserSipAddress(제공된 사용자 자격 증명에 해당하는 SIP 주소)의 매개 변수와 함께 호출합니다.

    $cred1 = Get-Credential "litwareinc\pilar"
    
    Test-CsDialInConferencing -TargetFqdn atl-cs-001.litwareinc.com -UserSipAddress "sip:pilar@litwareinc.com" -UserCredential $cred1

## 자세한 정보

**Test-CsDialInConferencing** cmdlet은 Lync Server "가상 트랜잭션"의 한 예입니다. 가상 트랜잭션은 Lync Server에서 사용자가 시스템 로그온, 메신저 대화 교환 또는 PSTN(공중 전화망)의 전화로 전화 걸기와 같은 일반적인 작업을 성공적으로 수행할 수 있는지 확인하는 데 사용됩니다. 이러한 테스트는 관리자가 "수동으로" 수행하거나 Microsoft System Center Operations Manager(이전 Microsoft Operations Manager)와 같은 응용 프로그램에 의해 자동으로 실행될 수 있습니다.

가상 트랜잭션은 일반적으로 두 가지 방법으로 수행됩니다. 많은 관리자가 **CsHealthMonitoringConfiguration** cmdlet을 사용하여 각 등록자 풀의 테스트 사용자를 설정합니다. 이러한 테스트 사용자는 가상 트랜잭션에 사용하도록 미리 구성된 사용자 쌍입니다. 일반적으로 이러한 계정은 테스트 계정이며 실제 사용자가 소유한 계정은 아닙니다. 풀에 테스트 사용자가 구성되면 관리자는 테스트에 참여한 사용자 계정의 ID 및 자격 증명을 지정하지 않고도 해당 풀에 대해 가상 트랜잭션을 실행할 수 있습니다.

또는 실제 사용자 계정을 사용하여 가상 트랜잭션을 실행할 수 있습니다. 예를 들어 두 사용자가 메신저 대화를 교환할 수 없는 경우 관리자는 이 두 사용자 계정(테스트 계정 쌍이 아님)을 사용하여 가상 트랜잭션을 실행하고 문제를 진단 및 해결할 수 있습니다. 실제 사용자 계정을 사용하여 가상 트랜잭션을 수행하도록 결정한 경우 각 사용자에 대한 로그온 이름 및 암호를 제공해야 합니다.

**Test-CsDialInConferencing** cmdlet은 테스트 사용자를 시스템에 로그온시키는 방식으로 작동합니다. 테스트 사용자를 사용하는 경우 **Test-CsDialInConferencing** cmdlet은 해당 풀에 구성된 첫 번째 테스트 계정을 사용합니다. 로그온에 성공하면 이 cmdlet은 사용자 자격 증명 및 권한을 사용하여 사용 가능한 전화 접속 회의 액세스 번호로 연결을 시도합니다. 각 전화 접속 시도의 성공 또는 실패가 기록되면 테스트 사용자가 Lync Server에서 로그오프됩니다.

**Test-CsDialInConferencing** cmdlet은 해당 연결을 설정할 수 있는지만 확인합니다. 이 cmdlet은 실제로 전화를 걸거나 다른 사용자가 참가할 수 있는 전화 접속 회의를 만들지 않습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Test-CsDialInConferencing** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsDialInConferencing"}

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
<td><p>System.String</p></td>
<td><p>테스트할 풀의 FQDN(정규화된 도메인 이름)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>UserCredential</em></p></td>
<td><p>필수</p></td>
<td><p>System.Management.Automation.PSCredential</p></td>
<td><p>테스트할 사용자 계정의 사용자 자격 증명 개체입니다 UserCredential에 전달되는 값은 <strong>Get-Credential</strong> cmdlet을 사용하여 가져온 개체 참조여야 합니다. 예를 들어 다음 코드는 사용자 litwareinc\kenmyer의 자격 증명 개체를 반환하고 이 개체를 $x라는 변수에 저장합니다.</p>
<p>$x = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
<p>이 명령을 실행할 때는 사용자 암호를 제공해야 합니다. 상태 모니터링 구성 설정을 사용하여 테스트를 수행하는 경우 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Authentication</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction+AuthenticationMechanism</p></td>
<td><p>테스트에서 사용되는 인증 유형입니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>* TrustedServer</p>
<p>* Negotiate</p>
<p>* ClientCertificate</p>
<p>* LiveID</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
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
<tr class="even">
<td><p><em>OutVerboseVariable</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 매개 변수가 있으면 cmdlet을 실행하여 얻은 자세한 출력이 지정된 변수에 저장됩니다. 예를 들어 출력을 $TestOutput이라는 변수에 저장하려면 다음과 같은 구문을 사용합니다.</p>
<p>-OutVerboseVariable TestOutput</p>
<p>변수 이름을 지정할 때 $ 문자를 추가해서는 안 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>RegistrarPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>등록자 서비스에서 사용하는 SIP 포트입니다. 등록자에서 기본 포트 5061을 사용하는 경우에는 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>TargetPstnPhoneNumber</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>PSTN 사용자가 전화 접속 회의에 참가할 수 있는지를 확인하는 데 사용할 PSTN 전화의 전화 번호입니다. 예를 들면 다음과 같습니다.</p>
<p>-TargetPstnPhoneNumber &quot;+12065551219&quot;</p>
<p>VerifyConferenceJoinType 매개 변수를 사용할 때만 TargetPstnPhoneNumber를 포함해야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserSipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>테스트할 사용자 계정의 SIP 주소입니다(예: -UserSipAddress &quot;sip:kenmyer@litwareinc.com&quot;). UserSipAddress 매개 변수는 UserCredential과 동일한 사용자 계정을 참조해야 합니다. 상태 모니터링 구성 설정을 사용하여 테스트를 수행하는 경우 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>VerifyConferenceJoin</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 PSTN 전화를 통해 전화 접속 회의에 참가할 수 있음을 확인합니다. 이 테스트를 수행할 때는 필요에 따라 TargetPstnPhoneNumber를 포함할 수 있습니다. TargetPstnPhoneNumber를 포함하는 경우에는 회의 참가 시 사용할 PSTN 전화를 지정해야 합니다. TargetPstnPhoneNumber를 포함하지 않으면 <strong>Test-CsDialInConferencing</strong> cmdlet은 해당하는 전화 접속 회의 지역에 미리 할당된 전화 접속 전화 번호를 사용합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Test-CsDialInConferencing** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Test-CsDialInConferencing** cmdlet은 Microsoft.Rtc.SyntheticTransactions.TaskOutput 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Test-CsAVConference](test-csavconference.md)

