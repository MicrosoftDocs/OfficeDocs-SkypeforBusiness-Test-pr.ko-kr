---
title: Test-CsWebAppAnonymous
TOCTitle: Test-CsWebAppAnonymous
ms:assetid: acfb28c1-8db6-4d2b-95ad-5c824660ea71
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh690041(v=OCS.15)
ms:contentKeyID: 49304709
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsWebAppAnonymous

 

_**마지막으로 수정된 항목:** 2015-03-09_

익명 사용자가 Lync Web App을 사용하여 Lync Server 전화 회의에 참가할 수 있는지 여부를 확인할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

이 cmdlet은 온-프레미스 버전의 Lync Server 2013에서는 더 이상 사용되지 않습니다. 대신 관리자가 [Test-CsUcwaConference](test-csucwaconference.md) cmdlet을 사용하여 이러한 테스트를 수행해야 합니다.

## 구문

    Test-CsWebAppAnonymous -UserCredential <PSCredential> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-External <SwitchParameter>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] <COMMON PARAMETERS>

    Test-CsWebAppAnonymous -TargetUri <String> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-WebCredential <PSCredential>] <COMMON PARAMETERS>

    Test-CsWebAppAnonymous -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-External <SwitchParameter>] [-RegistrarPort <Int32>] [-UserSipAddress <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>]

## 예제

## 예제 1

예제 1에 표시된 명령에서는 atl-cs-001.litwareinc.com 풀에 대해 구성된 테스트 사용자가 Lync Web App을 사용하여 전화 회의에 익명으로 참가할 수 있는지 여부를 확인합니다. 이 명령은 **CsHealthMonitoringConfiguration** cmdlet을 사용하여 풀에 대해 테스트 사용자를 구성한 경우에만 성공합니다.

    Test-CsWebAppAnonymous -TargetFqdn atl-cs-001.litwareinc.com

## 예제 2

예제 2에 표시된 명령은 사용자 Ken Myer가 Lync Web App을 사용하여 전화 회의에 익명으로 참가할 수 있는지 여부를 확인합니다. 실제 사용자 계정을 사용하기 위해 예제의 첫 번째 명령에서는 **Get-Credential** cmdlet을 사용하여 사용자 litwareinc\\kenmyer에 대한 Windows PowerShell 자격 증명 개체를 만듭니다. 그런 다음 이 자격 증명 개체(변수 $cred1에 저장)는 예제의 두 번째 명령에 있는 UserCredential 매개 변수로 전달됩니다. UserCredential 매개 변수 외에 Ken Myer의 SIP 주소와 함께 UserSipAddress 매개 변수도 포함됩니다.

    $cred1 = Get-Credential "litwareinc\kenmyer"
    
    Test-CsWebApp -TargetFqdn atl-cs-001.litwareinc.com -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $cred1 

## 자세한 정보

관리자는 **Test-CsWebAppAnonymous** cmdlet을 사용하여 익명 사용자가 Microsoft Exchange Server 2013을 통해 전화 회의에 참가할 수 있는지 여부를 확인할 수 있습니다. **Test-CsWebAppAnonymous** cmdlet을 실행하면 웹 티켓 서비스를 사용하여 익명 웹 티켓 가져오기를 시도합니다. 티켓을 가져올 수 있으면 **Test-CsWebAppAnonymous** cmdlet은 Lync Web App을 사용하여 Lync Server에 연결을 시도합니다. 연결이 설정되면 이 cmdlet은 메신저 대화, 응용 프로그램 공유 및 데이터 공동 작업을 위한 별도의 전화 회의를 설정합니다.

많은 관리자는 **CsHealthMonitoringConfiguration** cmdlet을 사용하여 각각의 해당 등록자 풀에 대해 테스트 사용자를 설정합니다. 이러한 테스트 사용자는 가상 트랜잭션에 사용하도록 미리 구성된 한 쌍의 사용자 계정을 나타냅니다. 일반적으로 이러한 계정은 테스트 계정이며 실제 사용자가 소유한 계정은 아닙니다. 테스트 사용자가 풀에 대해 구성된 경우 관리자는 테스트에 참여한 사용자 계정의 ID를 지정하거나 자격 증명을 제공할 필요 없이 해당 풀에 대해 **Test-CsWebAppAnonymous** cmdlet을 실행할 수 있습니다.

또는 실제 사용자 계정을 사용하여 **Test-CsWebAppAnonymous** cmdlet을 실행할 수도 있습니다. 실제 사용자 계정을 사용하여 테스트를 수행하려는 경우 해당 계정에 대한 로그온 이름 및 암호를 제공해야 합니다.

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
<th>형식</th>
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
<td><p><em>UserCredential</em></p></td>
<td><p>필수</p></td>
<td><p>PS 자격 증명</p></td>
<td><p>테스트할 두 사용자 계정 중 첫 번째 사용자 계정의 사용자 자격 증명 개체입니다. UserCredential에 전달되는 값은 <strong>Get-Credential</strong> cmdlet을 사용하여 가져온 개체 참조여야 합니다. 예를 들어 다음 코드는 사용자 litwareinc\pilar의 자격 증명 개체를 반환하고 이 개체를 $x라는 변수에 저장합니다.</p>
<p>$x = Get-Credential &quot;litwareinc\pilar&quot;</p>
<p>이 명령을 실행할 때는 사용자 암호를 제공해야 합니다.</p>
<p><strong>CsHealthMonitoringConfiguration</strong> cmdlet을 통해 구성된 테스트 사용자를 사용하여 테스트를 실행하는 경우에는 이 매개 변수가 필요 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Authentication</em></p></td>
<td><p>선택</p></td>
<td><p>SIP 가상 트랜잭션 인증 메커니즘</p></td>
<td><p>테스트 실행 시 사용되는 인증 유형입니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>* TrustedServer</p>
<p>* Negotiate</p>
<p>* ClientCertificate</p>
<p>* LiveID</p></td>
</tr>
<tr class="odd">
<td><p><em>External</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>이 매개 변수가 있으면 <strong>Test-CsWebAppAnonymous</strong> cmdlet에서 Reach 서버의 외부 웹 릴레이를 테스트합니다. 이 매개 변수가 없는 경우 이 cmdlet은 내부 웹 릴레이를 테스트합니다. 웹 릴레이는 내부 네트워크와 인터넷 간의 중계자 역할을 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
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
<td><p>PS 자격 증명</p></td>
<td><p>테스트에서 사용할 사용자 계정의 사용자 자격 증명 개체입니다. UserCredential에 전달되는 값은 <strong>Get-Credential</strong> cmdlet을 사용하여 가져온 개체 참조여야 합니다. 예를 들어 다음 코드는 사용자 litwareinc\kenmyer의 자격 증명 개체를 반환하고 이 개체를 $x라는 변수에 저장합니다.</p>
<p>$x = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
<p>TargetUri 매개 변수나 UserSipAddress 매개 변수를 지정한 경우 명령을 실행하는 컴퓨터에 서버 인증서가 없으면 이 매개 변수가 필요합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

**Test-CsWebAppAnonymous** cmdlet은 Microsoft.Rtc.SyntheticTransactions.TaskOutput 개체의 인스턴스를 반환합니다.

