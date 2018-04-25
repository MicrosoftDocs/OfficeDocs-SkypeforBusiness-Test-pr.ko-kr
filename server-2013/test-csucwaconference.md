---
title: Test-CsUcwaConference
TOCTitle: Test-CsUcwaConference
ms:assetid: 4e01c4d6-7b81-4932-a8e1-4d14989b71bd
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ619178(v=OCS.15)
ms:contentKeyID: 49303579
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsUcwaConference

 

_**마지막으로 수정된 항목:** 2015-03-09_

UCWA(통합 통신 웹 API)를 활용한 사용자 쌍의 온라인 회의 예약, 참가 및 진행 기능을 테스트합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Test-CsUcwaConference -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-OrganizerSipAddress <String>] [-ParticipantSipAddress <String>] [-RegistrarPort <Int32>] <COMMON PARAMETERS>

    Test-CsUcwaConference -OrganizerCredential <PSCredential> -OrganizerSipAddress <String> -ParticipantCredential <PSCredential> -ParticipantSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] <COMMON PARAMETERS>

    Test-CsUcwaConference [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>] [-ParticipantSipAddress <String>]

## 예제

## 예제 1

예제 1의 명령은 테스트 사용자 한 쌍이 풀 atl-cs-001.litwareinc.com에서 UCWA 회의에 참석할 수 있는지 확인합니다. 이 명령은 atl-cs-001.litwareinc.com에 대해 상태 모니터링 구성 테스트 사용자 쌍을 미리 정의하지 않으면 실패합니다.

    Test-CsUcwaConference -TargetFqdn "atl-cs-001.litwareinc.com"

## 예제 2

예제 2의 명령은 사용자 쌍(litwareinc\\pilar 및 litwareinc\\kenmyer)의 UCWA 회의 참석 기능을 테스트합니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 **Get-Credential** cmdlet을 사용하여 사용자 Pilar Ackerman의 이름과 암호가 들어 있는 Windows PowerShell 명령줄 인터페이스 자격 증명 개체를 만듭니다. 로그인 이름 litwareinc\\pilar는 매개 변수로 포함되기 때문에 Windows PowerShell 자격 증명 요청 대화 상자에서는 관리자에게 Pilar Ackerman 계정의 암호 입력만 요구합니다. 만들어진 자격 증명 개체는 $cred1이라는 변수에 저장됩니다. 두 번째 명령도 같은 작업을 수행하지만 이번에는 Ken Myer 계정의 자격 증명 개체를 반환합니다.

두 개의 자격 증명 개체를 확보했으므로 예제의 세 번째 명령은 두 사용자가 UCWA 회의에 참석할 수 있는지 확인합니다. 이 작업을 수행하기 위해 **Test-CsUcwaConference** cmdlet이 호출되며, 이때 TargetFqdn(등록자 풀의 FQDN), OrganizerSipAddress(모임 이끌이의 SIP 주소), OrganizerCredential(모임 이끌이의 자격 증명이 들어 있는 Windows PowerShell 개체), ParticipantSipAddress(나머지 테스트 사용자의 SIP 주소) 및 ParticipantCredential(나머지 테스트 사용자의 자격 증명이 들어 있는 Windows PowerShell 명령줄 인터페이스 개체) 매개 변수도 함께 호출됩니다.

    $cred1 = Get-Credential "litwareinc\pilar"
    $cred2 = Get-Credential "litwareinc\kenmyer"
    
    Test-CsUcwaConference -TargetFqdn atl-cs-001.litwareinc.com -OrganizerSipAddress "sip:pilar@litwareinc.com" -OrganizerCredential $cred1 -ParticipantSipAddress "sip:kenmyer@litwareinc.com" -ParticipantCredential $cred2

## 자세한 정보

**Test-CsUcwaConference** cmdlet은 테스트 사용자 쌍이 UCWA(통합 통신 웹 API)를 사용하여 온라인 회의를 예약하고, 온라인 회의에 참가하고, 회의를 진행할 수 있는지 확인합니다. 이 작업을 수행하기 위해 cmdlet은 Lync Server 웹 티켓 서비스를 사용하여 두 테스트 사용자를 인증하고 이들을 Lync Server에 등록합니다. 그 다음 cmdlet은 모임 이끌이 자격 증명을 사용하여 회의를 시작하고 참가자를 모임에 초대합니다. 참가자가 모임에 참석하면 **Test-CsUcwaConference** cmdlet이 메신저 대화 교환 및 풀 수행 등의 작업을 할 수 있는지 확인한 다음 회의를 끝내고 두 테스트 사용자 등록을 취소합니다. 테스트가 끝나면 예약된 회의도 삭제됩니다.

**Test-CsUcwaConference** cmdlet을 사용하면 익명 사용자가 온라인 회의에 참가할 수 있는지 여부도 확인할 수 있습니다.

**Test-CsUcwaConference** cmdlet은 UCWA가 설치되어 있는 Microsoft Lync Server 2010 풀에 대해서만 실행해야 합니다. UCWA가 설치되어 있지 않으면 **Test-CsUcwaConference** cmdlet 호출이 실패합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsUcwaConference"}

**Lync Server 제어판:** **Test-CsUcwaConference** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>OrganizerCredential</em></p></td>
<td><p>필수</p></td>
<td><p>PS 자격 증명</p></td>
<td><p>모임 이끌이 역할을 하는 사용자 계정의 사용자 자격 증명 개체입니다. OrganizerCredential에 전달되는 값은 <strong>Get-Credential</strong> cmdlet을 사용할 때 가져온 개체 참조여야 합니다. 예를 들어 이 코드는 사용자 litwareinc\kenmyer의 자격 증명 개체를 반환하고 이 개체를 $x라는 변수에 저장합니다.</p>
<p>$x = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
<p>이 명령을 실행할 때는 사용자 암호를 제공해야 합니다.</p>
<p>풀의 상태 모니터링 구성 설정에 따라 테스트를 실행하는 경우에는 모임 이끌이 자격 증명이 필요하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ParticipantCredential</em></p></td>
<td><p>필수</p></td>
<td><p>PS 자격 증명</p></td>
<td><p>모임 참가자 역할을 하는 사용자 계정의 사용자 자격 증명 개체입니다. ParticipantCredential에 전달되는 값은 <strong>Get-Credential</strong> cmdlet을 사용할 때 가져온 개체 참조여야 합니다. 예를 들어 이 코드는 사용자 litwareinc\pilar의 자격 증명 개체를 반환하고 이 개체를 변수 $y에 저장합니다.</p>
<p>$y = Get-Credential &quot;litwareinc\pilar&quot;</p>
<p>이 명령을 실행할 때는 사용자 암호를 제공해야 합니다.</p>
<p>풀의 상태 모니터링 구성 설정에 따라 테스트를 실행하는 경우에는 참가자 자격 증명이 필요하지 않습니다.</p></td>
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
<td><p>테스트 실행 시 사용되는 인증 유형입니다. 사용 가능한 값은 다음과 같습니다.</p>
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
<td><p><em>OrganizerSipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>모임 이끌이의 SIP 주소입니다. 예: -OrganizerSipAddress &quot;sip:pilar@litwareinc.com&quot;. OrganizerSIPAddress 매개 변수는 OrganizerCredential과 동일한 사용자 계정을 참조해야 합니다.</p>
<p>풀의 상태 모니터링 구성 설정에 따라 테스트를 실행하는 경우에는 SIP 주소가 필요하지 않습니다.</p></td>
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
<td><p><em>ParticipantSipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>모임 참가자의 SIP 주소입니다. 예: -ParticipantSipAddress &quot;sip:kenmyer@litwareinc.com&quot;. ParticipantSIPAddress 매개 변수는 ParticipantCredential과 같은 사용자 계정을 참조해야 합니다.</p>
<p>풀의 상태 모니터링 구성 설정에 따라 테스트를 실행하는 경우에는 SIP 주소가 필요하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>RegistrarPort</em></p></td>
<td><p>선택</p></td>
<td><p>Int32</p></td>
<td><p>등록자 서비스에서 사용하는 SIP 포트입니다. 등록자에서 기본 포트 5061을 사용하는 경우에는 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Test-CsUcwaConference** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Test-CsUcwaConference** cmdlet은 Microsoft.Rtc.SyntheticTransactions.WebTaskOutput 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Test-CsASConference](test-csasconference.md)  
[Test-CsDataConference](test-csdataconference.md)  
[Test-CsAVConference](test-csavconference.md)

