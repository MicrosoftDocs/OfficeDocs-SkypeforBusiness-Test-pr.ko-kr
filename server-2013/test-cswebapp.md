---
title: Test-CsWebApp
TOCTitle: Test-CsWebApp
ms:assetid: 0333a4a5-9bd5-4a45-aea8-e7af1a394ec3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh689989(v=OCS.15)
ms:contentKeyID: 49302641
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsWebApp

 

_**마지막으로 수정된 항목:** 2015-03-09_

인증된 사용자가 Lync Web App을 사용하여 Lync Server 전화 회의에 참가할 수 있는지 여부를 확인할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

이 cmdlet은 온-프레미스 버전의 Lync Server 2013에서는 더 이상 사용되지 않습니다. 대신 관리자가 [Test-CsUcwaConference](test-csucwaconference.md) cmdlet을 사용하여 이러한 테스트를 수행해야 합니다.

## 구문

    Test-CsWebApp -User2Credential <PSCredential> -User2SipAddress <String> -UserCredential <PSCredential> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-External <SwitchParameter>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] <COMMON PARAMETERS>

    Test-CsWebApp -TargetUri <String> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-WebCredential <PSCredential>] <COMMON PARAMETERS>

    Test-CsWebApp -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-External <SwitchParameter>] [-RegistrarPort <Int32>] [-UserSipAddress <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>]

## 예제

## 예제 1

예제 1에서는 atl-cs-001.litwareinc.com 풀에 대해 구성된 한 쌍의 테스트 사용자가 Lync Web App을 사용하여 전화 회의에 참가할 수 있는지 여부를 확인합니다. 이 명령은 **CsHealthMonitoringConfiguration** cmdlet을 사용하여 풀에 대해 테스트 사용자를 구성한 경우에만 성공합니다.

    Test-CsWebApp -TargetFqdn atl-cs-001.litwareinc.com

## 예제 2

예제 2에 표시된 명령에서는 두 명의 사용자(Ken Myer 및 Pilar Ackerman)가 Lync Web App을 사용하여 전화 회의에 참가할 수 있는지 여부를 확인합니다. 실제 사용자 계정을 사용하기 위해 예제의 처음 두 명령에서는 Get-Credential cmdlet을 사용하여 두 사용자(litwareinc\\kenmyer 및 litwareinc\\pilar)에 대한 Windows PowerShell 명령줄 인터페이스 자격 증명 개체를 만듭니다. 그런 다음 이러한 자격 증명 개체(변수 $cred1 및 $cred2에 저장)는 예제의 마지막 명령에서 UserCredential 및 User2Credential 매개 변수에 대한 매개 변수 값으로 사용됩니다. 사용자 자격 증명 매개 변수 외에 UserSipAddress 및 User2SipAddress 매개 변수를 비롯해 테스트에 사용된 두 사용자 계정의 SIP 주소가 함께 포함됩니다.

    $cred1 = Get-Credential "litwareinc\kenmyer"
    $cred2 = Get-Credential "litwareinc\pilar"
    
    Test-CsWebApp -TargetFqdn atl-cs-001.litwareinc.com -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $cred1 -User2SipAddress "sip:pilar@litwareinc.com" -User2Credential $cred2

## 자세한 정보

관리자는 **Test-CsWebApp** cmdlet을 사용하여 인증된 사용자가 Lync Web App을 통해 전화 회의에 참가할 수 있는지 여부를 확인할 수 있습니다. **Test-CsWebApp** cmdlet을 실행하면 웹 티켓 서비스를 사용하여 한 쌍의 테스트 사용자에 대한 웹 티켓 가져오기를 시도합니다. 티켓을 가져올 수 있고 테스트 사용자가 인증되면 **Test-CsWebApp** cmdlet은 Lync Web App을 사용하여 Lync Server에 연결을 시도합니다. 연결이 설정되면 이 cmdlet은 메신저 대화, 응용 프로그램 공유 및 데이터 공동 작업을 위한 별도의 전화 회의를 설정합니다.

많은 관리자는 **CsHealthMonitoringConfiguration** cmdlet을 사용하여 각각의 해당 등록자 풀에 대해 테스트 사용자를 설정합니다. 이러한 테스트 사용자는 가상 트랜잭션에 사용하도록 미리 구성된 한 쌍의 사용자 계정을 나타냅니다. 일반적으로 이러한 계정은 테스트 계정이며 실제 사용자가 소유한 계정은 아닙니다. 테스트 사용자가 풀에 대해 구성된 경우 관리자는 테스트에 참여한 사용자 계정의 ID를 지정하거나 자격 증명을 제공할 필요 없이 해당 풀에 대해 **Test-CsWebApp** cmdlet을 실행할 수 있습니다.

또는 실제 사용자 계정을 사용하여 **Test-CsWebApp** cmdlet을 실행할 수도 있습니다. 실제 사용자 계정을 사용하여 테스트를 수행하려는 경우 각 계정에 대한 로그온 이름 및 암호를 제공해야 합니다.

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
<td><p>테스트할 풀의 FQDN(정규화된 도메인 이름)입니다. 예를 들면 다음과 같습니다.</p>
<p>-TargetFqdn atl-cs-001.litwareinc.com</p></td>
</tr>
<tr class="even">
<td><p><em>TargetUri</em></p></td>
<td><p>필수</p></td>
<td><p>문자열</p></td>
<td><p>Reach 서버의 URI(Uniform Resource Identifier)입니다. 예를 들면 다음과 같습니다.</p>
<p>-TargetUri &quot;https://atl-cs-001.litwareinc.com/reach&quot;</p>
<p>같은 명령에서 TargetUri 매개 변수와 TargetFqdn 매개 변수를 함께 사용할 수는 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>User2Credential</em></p></td>
<td><p>필수</p></td>
<td><p>PSCredential</p></td>
<td><p>테스트할 두 사용자 계정 중 두 번째 사용자 계정의 사용자 자격 증명 개체입니다. User2Credential에 전달되는 값은 <strong>Get-Credential</strong> cmdlet을 사용하여 가져온 개체 참조여야 합니다. 예를 들어 다음 코드는 사용자 litwareinc\kenmyer의 자격 증명 개체를 반환하고 이 개체를 $y라는 변수에 저장합니다.</p>
<p>$y = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
<p>이 명령을 실행할 때는 사용자 암호를 제공해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>User2SipAddress</em></p></td>
<td><p>필수</p></td>
<td><p>문자열</p></td>
<td><p>테스트할 두 사용자 계정 중 두 번째 사용자 계정의 SIP 주소입니다. 예를 들면 다음과 같습니다.</p>
<p>-User2SipAddress &quot;sip:pilar@litwareinc.com&quot;</p>
<p><strong>CsHealthMonitoringConfiguration</strong> cmdlet을 통해 구성된 테스트 사용자를 사용하여 테스트를 실행하는 경우에는 이 매개 변수가 필요 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserCredential</em></p></td>
<td><p>필수</p></td>
<td><p>PSCredential</p></td>
<td><p>테스트할 두 사용자 계정 중 첫 번째 사용자 계정의 사용자 자격 증명 개체입니다. UserCredential에 전달되는 값은 <strong>Get-Credential</strong> cmdlet을 사용하여 가져온 개체 참조여야 합니다. 예를 들어 다음 코드는 사용자 litwareinc\pilar의 자격 증명 개체를 반환하고 이 개체를 $x라는 변수에 저장합니다.</p>
<p>$x = Get-Credential &quot;litwareinc\pilar&quot;</p>
<p>이 명령을 실행할 때는 사용자 암호를 제공해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Authentication</em></p></td>
<td><p>선택</p></td>
<td><p>SipSyntheticTransaction + AuthenticationMechanism</p></td>
<td><p>테스트 실행 시 사용되는 인증 유형입니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>* TrustedServer</p>
<p>* Negotiate</p>
<p>* ClientCertificate</p>
<p>* LiveID</p></td>
</tr>
<tr class="odd">
<td><p><em>External</em></p></td>
<td><p>선택</p></td>
<td><p>SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 <strong>Test-CsWebApp</strong> cmdlet에서 Reach 서버의 외부 웹 릴레이를 테스트합니다. 이 매개 변수가 없는 경우 이 cmdlet은 내부 웹 릴레이를 테스트합니다. 웹 릴레이는 내부 네트워크와 인터넷 간의 중계자 역할을 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>OutLoggerVariable</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>이 매개 변수가 있으면 cmdlet을 실행하여 얻은 자세한 출력이 지정된 변수에 저장됩니다. 이 변수에 포함된 메서드 쌍(ToHTML 및 ToXML)은 이러한 출력을 HTML 또는 XML 파일에 저장하는 데 사용할 수 있습니다.</p>
<p>출력을 $TestOutput이라는 로거 변수에 저장하려면 다음과 같은 구문을 사용합니다.</p>
<p>-OutLoggerVariable TestOutput</p>
<p>참고: 변수 이름을 지정할 때 $ 문자를 추가해서는 안 됩니다.</p>
<p>로거 변수에 저장된 정보를 HTML 파일에 저장하려면 다음 명령을 사용합니다.</p>
<p>$TestOutput.ToHTML() &gt; C:\Logs\TestOutput.html</p>
<p>로거 변수에 저장된 정보를 XML 파일에 저장하려면 다음 명령을 사용합니다.</p>
<p>$TestOutput.ToXML() &gt; C:\Logs\TestOutput.xml</p></td>
</tr>
<tr class="even">
<td><p><em>OutVerboseVariable</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>이 매개 변수가 있으면 cmdlet을 실행하여 얻은 자세한 출력이 지정된 변수에 저장됩니다. 예를 들어 출력을 $TestOutput이라는 변수에 저장하려면 다음과 같은 구문을 사용합니다.</p>
<p>-OutVerboseVariable TestOutput</p>
<p>변수 이름을 지정할 때 $ 문자를 추가해서는 안 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>RegistrarPort</em></p></td>
<td><p>선택</p></td>
<td><p>Int32</p></td>
<td><p>등록자 서비스에서 사용하는 SIP 포트입니다. 등록자에서 기본 포트 5061을 사용하는 경우에는 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>UserSipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>테스트할 두 사용자 계정 중 첫 번째 사용자 계정의 SIP 주소입니다. 예를 들면 다음과 같습니다.</p>
<p>-UserSipAddress &quot;sip:kenmyer@litwareinc.com&quot;</p>
<p>CsHealthMonitoringConfiguration cmdlet을 통해 구성된 테스트 사용자를 사용하여 테스트를 실행하는 경우에는 이 매개 변수가 필요 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WebCredential</em></p></td>
<td><p>선택</p></td>
<td><p>PSCredential</p></td>
<td><p>테스트에서 사용할 사용자 계정의 사용자 자격 증명 개체입니다. UserCredential에 전달되는 값은 <strong>Get-Credential</strong> cmdlet을 사용하여 가져온 개체 참조여야 합니다. 예를 들어 다음 코드는 사용자 litwareinc\kenmyer의 자격 증명 개체를 반환하고 이 개체를 $x라는 변수에 저장합니다.</p>
<p>$x = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
<p>TargetUri 매개 변수나 UserSipAddress/User2SipAddress 매개 변수를 지정한 경우 명령을 실행하는 컴퓨터에 서버 인증서가 없으면 이 매개 변수가 필요합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

**Test-CsWebApp** cmdlet은 Microsoft.Rtc.SyntheticTransactions.TaskOutput 개체의 인스턴스를 반환합니다.

