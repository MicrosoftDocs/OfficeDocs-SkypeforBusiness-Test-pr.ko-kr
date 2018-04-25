---
title: Test-CsMcxConference
TOCTitle: Test-CsMcxConference
ms:assetid: c6ca9019-1535-489d-a42e-1a50070b2f67
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh690045(v=OCS.15)
ms:contentKeyID: 49304989
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsMcxConference

 

_**마지막으로 수정된 항목:** 2015-03-09_

세 명의 사용자가 Lync Server 2013 Mobility Service 전화 회의에 참가할 수 있는지를 테스트할 수 있습니다. iPhone 및 Windows Phone 같은 휴대폰 사용자는 Mobility Service를 통해 메신저 대화 및 현재 상태 정보를 교환하고, 음성 메일을 해당 무선 공급자를 통해서가 아닌 내부에서 저장 및 검색하고, 회사번호로 전화 기능 및 외부 전화 접속 회의 같은 Lync Server 기능을 활용하는 등의 작업을 수행할 수 있습니다. 이 cmdlet은 Lync Server 2010용 2011년 11월 누적 업데이트에서 도입되었습니다.

## 구문

    Test-CsMcxConference -OrganizerCredential <PSCredential> -OrganizerSipAddress <String> -User2Credential <PSCredential> -User2SipAddress <String> -UserCredential <PSCredential> -UserSipAddress <String> <COMMON PARAMETERS>

    Test-CsMcxConference -OrganizerSipAddress <String> -User2SipAddress <String> -UserSipAddress <String> <COMMON PARAMETERS>

    COMMON PARAMETERS: -Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID> -TargetFqdn <String> [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>] [-RegistrarPort <Int32>]

## 예제

## 예제 1

예제 1의 명령은 세 개의 사용자 계정 Ken Myer(모임 이끌이), Pilar Ackerman 및 Aidan Delaney를 사용하여 Mobility Service 전화 회의를 진행할 수 있는지 여부를 확인합니다. 이 테스트를 실행하기 위해 가장 먼저 해야 할 일은 각 사용자 계정에 대한 자격 증명 개체를 만드는 것입니다. 이러한 개체는 코드의 처음 세 줄에 만들며 변수 $organizerCred(Ken Myer), $user1Cred(Pilar Ackerman) 및 $user2Cred(Aidan Delaney)에 저장됩니다.

자격 증명 개체가 만들어진 후에는 **Test-CsMcxConference** cmdlet을 호출하여 대상 등록자 풀(atl-cs-001.litwareinc,com), 인증 유형(Negotiate), 전화 회의 참가자 역할을 하는 세 사용자의 SIP 주소 및 자격 증명을 지정해야 합니다.

    $organizerCred = Get-Credential "litwareinc\kenmyer"
    $user1Cred = Get-Credential "litwareinc\packerman"
    $user2Cred = Get-Credential "litwareinc\adelaney"
    
    Test-CsMcxConference -TargetFqdn "atl-cs-001.litwareinc.com" -Authentication Negotiate -OrganizerSipAddress "sip:kenmyer@litwareinc.com" -OrganizerCredential $organizerCred -UserSipAddress "sip:pilar@litwareinc.com" -UserCredential $user1Cred -User2SipAddress "sip:adelaney@litwareinc.com" -User2Credential $user2Cred

## 자세한 정보

Mobility Service는 Lync Server의 많은 기능을 Apple iPhone, Windows Phone, Android 전화, Nokia 전화 같은 모바일 장치로 확장합니다. 무엇보다도 사용자는 이러한 전화를 사용하여 메신저 대화 및 현재 상태 정보를 교환하고, 새 음성 메일에 대한 알림을 수신할 수 있습니다. iPhone 또는 Windows Phone 사용자는 푸시 알림 서비스(Apple 푸시 알림 서비스 및 Microsoft 푸시 알림 서비스) 덕분에 Lync가 백그라운드에서 실행 중이더라도 이러한 알림을 수신할 수 있습니다. 또한 Mobility Service를 사용하면 조직에서 회사번호로 전화 기능을 사용할 수 있습니다. 회사번호로 전화 기능을 사용하면 휴대폰에서 전화를 걸지만 회사 전화 번호에서 전화가 걸려 온 것처럼 보이게 할 수 있습니다. 예를 들어 발신자 번호 시스템에서 사용자의 휴대폰 번호 대신 회사 전화 번호를 표시합니다.

**Test-CsMcxConference** cmdlet은 일련의 세 사용자가 Mobility Service를 사용하여 전화 회의에 참가할 수 있는지 여부를 확인하는 데 사용합니다. 이 cmdlet을 실행하기 위해 휴대폰을 사용하거나 실제 전화 회의에 참가해야 하는 것은 아닙니다. 대신 이 cmdlet은 세 명의 사용자가 Lync Server에 로그온할 수 있으며 Mobility Service가 전화 회의를 수행하는 데 필요한 연결을 설정할 수 있는지를 확인합니다. 또한 전화 회의 이끌이가 다른 두 전화 회의 참가자에게 메신저 대화를 보낼 수 있는지도 확인합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Test-CsMcxConference** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsMcxConference"}

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
<td><p><em>Authentication</em></p></td>
<td><p>필수</p></td>
<td><p>SIP 가상 트랜잭션 인증 메커니즘</p></td>
<td><p>허용되는 값은 TrustedServer, Negotiate, ClientCertificate 및 LiveID입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>OrganizerCredential</em></p></td>
<td><p>필수</p></td>
<td><p>PS 자격 증명</p></td>
<td><p>모임 이끌이 역할을 할 사용자 계정의 사용자 자격 증명 개체입니다. OrganizerCredential에 전달되는 값은 <strong>Get-Credential</strong> cmdlet을 사용하여 가져온 개체 참조여야 합니다. 예를 들어 다음 코드는 사용자 litwareinc\adelaney의 자격 증명 개체를 반환하고 이 개체를 $z라는 변수에 저장합니다.</p>
<p>$z = Get-Credential &quot;litwareinc\adelaney&quot;</p>
<p>이 명령을 실행할 때는 사용자 암호를 제공해야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>OrganizerSipAddress</em></p></td>
<td><p>필수</p></td>
<td><p>문자열</p></td>
<td><p>모임 이끌이 역할을 할 사용자 계정의 SIP 주소입니다. 예를 들면 다음과 같습니다.</p>
<p>-OrganizerSipAddress &quot;sip:adelaney@litwareinc.com&quot;</p>
<p>OrganizerSipAddress 매개 변수는 OrganizerCredential 매개 변수와 동일한 사용자 계정을 참조해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>TargetFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>문자열</p></td>
<td><p>테스트할 풀의 FQDN(정규화된 도메인 이름)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>User2Credential</em></p></td>
<td><p>필수</p></td>
<td><p>PS 자격 증명</p></td>
<td><p>테스트할 두 사용자 계정 중 두 번째 사용자 계정의 사용자 자격 증명 개체입니다. Use2rCredential에 전달되는 값은 <strong>Get-Credential</strong> cmdlet을 사용하여 가져온 개체 참조여야 합니다. 예를 들어 다음 코드는 사용자 litwareinc\kenmyer의 자격 증명 개체를 반환하고 이 개체를 $y라는 변수에 저장합니다.</p>
<p>$y = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
<p>이 명령을 실행할 때는 사용자 암호를 제공해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>User2SipAddress</em></p></td>
<td><p>필수</p></td>
<td><p>문자열</p></td>
<td><p>테스트할 두 사용자 계정 중 두 번째 사용자 계정의 SIP 주소입니다. 예를 들면 다음과 같습니다.</p>
<p>-User2SipAddress &quot;sip:pilar@litwareinc.com&quot;</p>
<p>User2SipAddress 매개 변수는 User2Credential 매개 변수와 동일한 사용자 계정을 참조해야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserCredential</em></p></td>
<td><p>필수</p></td>
<td><p>PS 자격 증명</p></td>
<td><p>테스트할 두 사용자 계정 중 첫 번째 사용자 계정의 사용자 자격 증명 개체입니다. UserCredential에 전달되는 값은 <strong>Get-Credential</strong> cmdlet을 사용하여 가져온 개체 참조여야 합니다. 예를 들어 다음 코드는 사용자 litwareinc\pilar의 자격 증명 개체를 반환하고 이 개체를 $x라는 변수에 저장합니다.</p>
<p>$x = Get-Credential &quot;litwareinc\pilar&quot;</p>
<p>이 명령을 실행할 때는 사용자 암호를 제공해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>UserSipAddress</em></p></td>
<td><p>필수</p></td>
<td><p>문자열</p></td>
<td><p>테스트할 두 사용자 계정 중 첫 번째 사용자 계정의 SIP 주소입니다. 예를 들면 다음과 같습니다.</p>
<p>-UserSipAddress &quot;sip:kenmyer@litwareinc.com&quot;</p>
<p>UserSipAddress 매개 변수는 UserCredential 매개 변수와 동일한 사용자 계정을 참조해야 합니다.</p></td>
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
<p>참고: 변수 이름을 지정할 때 $ 문자를 추가해서는 안 됩니다.</p>
<p>로거 변수에 저장된 정보를 HTML 파일에 저장하려면 다음 명령을 사용합니다.</p>
<p>$TestOutput.ToHTML() &gt; C:\Logs\TestOutput.html</p>
<p>로거 변수에 저장된 정보를 XML 파일에 저장하려면 다음 명령을 사용합니다.</p>
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
</tbody>
</table>


## 입력 형식

없음. **Test-CsMcxConference** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Test-CsMcxConference** cmdlet은 Microsoft.Rtc.SyntheticTransactions.TaskOutput 개체의 인스턴스를 반환합니다.

