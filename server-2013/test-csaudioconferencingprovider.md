---
title: Test-CsAudioConferencingProvider
TOCTitle: Test-CsAudioConferencingProvider
ms:assetid: 9e00081e-5825-4ee9-a838-3c91ad054589
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205117(v=OCS.15)
ms:contentKeyID: 49304540
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsAudioConferencingProvider

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자가 오디오 회의 공급자에 연결할 수 있는지 테스트합니다. 오디오 회의 공급자는 조직에 회의 서비스를 제공하는 타사입니다. 특히 외부에 있거나 회사 네트워크 또는 인터넷에 연결되지 않은 사용자는 오디오 회의 공급자를 통해 회의 또는 모임의 오디오 부분에 참여할 수 있습니다. 이 cmdlet은 Lync Server 2013에 도입되었습니다.

## 구문

    Test-CsAudioConferencingProvider -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-UserSipAddress <String>] <COMMON PARAMETERS>

    Test-CsAudioConferencingProvider -UserCredential <PSCredential> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] <COMMON PARAMETERS>

    Test-CsAudioConferencingProvider [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-DialoutUserCredential <PSCredential>] [-DialoutUserSipAddress <String>] [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>] [-TestJoinLauncher <SwitchParameter>]

## 예제

## 예제 1

예제 1에서는 atl-cs-001.litwareinc.com 풀에 대해 정의된 테스트 사용자가 오디오 회의 공급자에 연결할 수 있는지를 확인합니다. 이 명령을 실행하려면 풀에 대해 테스트 사용자를 한 명 이상 정의해야 합니다. atl-cs-001.litwareinc.com에 대해 테스트 사용자가 정의되지 않은 경우에는 **Test-CsAudioConferencingProvider** cmdlet이 테스트에서 사용할 사용자를 알 수 없으므로 명령이 실패합니다. 풀에 대해 테스트 사용자를 정의하지 않은 경우에는 오디오 회의 공급자와의 연결을 확인할 때 명령이 사용해야 하는 사용자 계정의 자격 증명과 UserSipAddress 매개 변수를 포함해야 합니다.

    Test-CsAudioConferencingProvider -TargetFqdn atl-cs-001.litwareinc.com

## 예제 2

예제 2에 표시된 명령은 특정 사용자(litwareinc\\kenmyer)가 오디오 회의 공급자에 연결할 수 있는지 테스트합니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 **Get-Credential** cmdlet을 사용하여 사용자 Ken Myer의 이름 및 암호를 포함하는 Windows PowerShell 명령줄 인터페이스 자격 증명 개체를 만듭니다. 로그온 이름 litwareinc\\kenmyer가 매개 변수로 포함되었으므로 관리자는 Windows PowerShell 자격 증명 요청 대화 상자에 Ken Myer 계정의 암호만 입력하면 됩니다. 이렇게 만들어진 자격 증명 개체는 $credential 변수에 저장됩니다.

두 번째 명령은 이 사용자가 오디오 회의 공급자에 연결할 수 있는지 확인합니다. 이 작업을 수행하기 위해 **Test-CsAudioConferencingProvider** cmdlet을 TargetFqdn(등록자 풀의 FQDN), UserCredential(Ken Myer의 사용자 자격 증명이 포함된 Windows PowerShell 개체) 및 UserSipAddress(제공된 사용자 자격 증명에 해당하는 SIP 주소)의 매개 변수와 함께 호출합니다.

    $credential = Get-Credential "litwareinc\kenmyer"
    
    Test-CsAudioConferencingProvider -TargetFqdn atl-cs-001.litwareinc.com -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $credential

## 자세한 정보

오디오 회의 공급자는 조직에 회의 서비스를 제공하는 타사입니다. 특히 외부에 있거나 회사 네트워크 또는 인터넷에 연결되지 않은 사용자는 오디오 회의 공급자를 통해 회의 또는 모임의 오디오 부분에 참여할 수 있습니다. 오디오 회의 공급자는 실시간 번역, 기록 및 회의별 실시간 운영자 지원과 같은 고급 서비스를 제공합니다.

**Test-CsAudioConferencingProvider** cmdlet은 사용자가 오디오 회의 공급자에 연결할 수 있는지를 확인하는 데 사용됩니다. 이 cmdlet은 두 가지 방법 중 하나로 실행할 수 있습니다. 대부분의 관리자는 CsHealthMonitoringConfiguration cmdlet을 사용하여 각각의 해당 등록자 풀에 대해 테스트 사용자를 설정합니다. 이러한 테스트 사용자는 가상 트랜잭션에 사용하도록 미리 구성된 한 쌍의 사용자 계정을 나타냅니다. 일반적으로 이러한 계정은 테스트 계정이며 실제 사용자가 소유한 계정은 아닙니다. 테스트 사용자가 풀에 대해 구성된 경우 관리자는 테스트에 참여한 사용자 계정의 ID를 지정하고 자격 증명을 제공할 필요 없이 해당 풀에 대해 **Test-CsAudioConferencingProvider** cmdlet을 실행할 수 있습니다.

또는 실제 사용자 계정을 사용하여 **Test-CsAudioConferencingProvider** cmdlet을 실행할 수도 있습니다. 실제 사용자 계정을 사용하여 테스트를 수행하려는 경우 해당 계정에 대한 로그온 이름 및 암호를 제공해야 합니다.

**Test-CsAudioConferencingProvider** cmdlet에서 사용하는 사용자에게 오디오 회의 공급자가 할당되지 않은 경우에는 테스트가 실패합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Test-CsAudioConferencingProvider** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsAudioConferencingProvider"}

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
<td><p>테스트할 풀의 FQDN(정규화된 도메인 이름)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>UserCredential</em></p></td>
<td><p>필수</p></td>
<td><p>PS 자격 증명</p></td>
<td><p>테스트할 계정의 사용자 자격 증명 개체입니다. UserCredential에 전달되는 값은 <strong>Get-Credential</strong> cmdlet을 사용하여 가져온 개체 참조여야 합니다. 예를 들어 이 코드는 사용자 litwareinc\kenmyer에 대한 자격 증명 개체를 반환하고 해당 개체를 $x 변수에 저장합니다.</p>
<p>$x = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
<p>이 명령을 실행할 때는 사용자 암호를 제공해야 합니다.</p>
<p>명령에서 CsHealthMonitoringConfiguration cmdlet을 사용하여 구성된 테스트 사용자를 사용하는 경우에는 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Authentication</em></p></td>
<td><p>선택</p></td>
<td><p>SIP 가상 트랜잭션 인증 메커니즘</p></td>
<td><p>테스트 실행 시 사용되는 인증 유형입니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>* TrustedServer</p>
<p>* Negotiate</p>
<p>* ClientCertificate</p>
<p>* LiveID</p></td>
</tr>
<tr class="even">
<td><p><em>DialoutUserCredential</em></p></td>
<td><p>선택</p></td>
<td><p>PS 자격 증명</p></td>
<td><p>테스트할 외부로 전화 접속 사용자 계정의 사용자 자격 증명 개체입니다 DialoutUserCredential에 전달되는 값은 <strong>Get-Credential</strong> cmdlet을 사용하여 가져온 개체 참조여야 합니다. 예를 들어 다음 코드는 사용자 litwareinc\pilar의 자격 증명 개체를 반환하고 이 개체를 $x라는 변수에 저장합니다.</p>
<p>$x = Get-Credential &quot;litwareinc\pilar&quot;</p>
<p>이 명령을 실행할 때는 사용자 암호를 제공해야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DialoutUserSipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>테스트할 외부로 전화 접속 사용자 계정의 SIP 주소입니다(예: -DialoutUserSipAddress &quot;sip:pilar@litwareinc.com&quot;). DialoutUserSipAddress 매개 변수는 DialoutUserCredential과 동일한 사용자 계정을 참조해야 합니다.</p></td>
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
<td><p><em>TestJoinLauncher</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>이 매개 변수가 있으면 참가 시작 관리자를 사용하여 AV 회의에 참가할 수 있는지를 테스트합니다. 참가 시작 관리자는 모바일 장치 사용자(모바일 서비스 사용자)가 회의에 참가할 수 있도록 하는 데 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserSipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>테스트할 사용자 계정의 SIP 주소입니다(예: -UserSipAddress &quot;sip:kenmyer@litwareinc.com&quot;). UserSipAddress 매개 변수는 UserCredential과 동일한 사용자 계정을 참조해야 합니다.</p>
<p>명령에서 CsHealthMonitoringConfiguration cmdlet을 사용하여 구성된 테스트 사용자를 사용하는 경우에는 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Test-CsAudioConferencingProvider** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Test-CsAudioConferencingProvider** cmdlet은 Microsoft.Rtc.SyntheticTransactions.TaskOutput 개체의 인스턴스를 반환합니다.

