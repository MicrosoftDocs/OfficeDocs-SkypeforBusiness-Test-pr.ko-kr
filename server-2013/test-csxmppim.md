---
title: Test-CsXmppIM
TOCTitle: Test-CsXmppIM
ms:assetid: ffeb05a7-141d-46dc-936f-1f7218521ff8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205423(v=OCS.15)
ms:contentKeyID: 49305651
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsXmppIM

 

_**마지막으로 수정된 항목:** 2015-03-09_

XMPP(Extensible Messaging and Presence Protocol) 게이트웨이를 통해 메신저 대화를 보낼 수 있는지를 확인합니다. Lync Server 2013 사용자는 XMPP 게이트웨이를 통해 XMPP를 사용하는 메신저 및 현재 상태 공급자에 속하는 사용자와 메신저 대화 및 현재 상태 정보를 교환할 수 있습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Test-CsXmppIM -UserCredential <PSCredential> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] <COMMON PARAMETERS>

    Test-CsXmppIM -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-UserSipAddress <String>] <COMMON PARAMETERS>

    Test-CsXmppIM [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] <COMMON PARAMETERS>

    COMMON PARAMETERS: -Receiver <String> [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>]

## 예제

## 예제 1

위 예제에서는 atl-cs-001.litwareinc.com 풀에 대해 XMPP 메신저 기능을 테스트합니다. 이 명령은 atl-cs-001.litwareinc.com 풀에 대해 테스트 사용자가 정의된 경우에만 작동합니다. 사용자가 정의된 경우 명령은 첫 번째 테스트 사용자가 SIP 주소가 adelaney@contoso.com인 사용자에게 XMPP 메신저 대화를 보낼 수 있는지를 확인합니다.

테스트 사용자가 정의되지 않은 경우 어떤 사용자로 로그온할지를 알 수 없기 때문에 명령이 실패합니다. 풀에 대한 테스트 사용자를 정의하지 않은 경우에는 UserSipAddress 매개 변수와 함께 로그온 시도 시 명령이 사용해야 하는 사용자의 자격 증명을 포함해야 합니다.

    Test-CsXmppIM -TargetFqdn "atl-cs-001.litwareinc.com" -Receiver "adelany@contoso.com"

## 예제 2

예제 2에 표시된 명령은 특정 사용자(litwareinc\\pilar)가 로그온하여 사용자 adelaney@contoso.com에게 XMPP 메신저 대화를 보낼 수 있는지 테스트합니다. 이 작업을 수행하기 위해 이 예제의 첫 번째 명령은 Get-Credential cmdlet을 사용하여 사용자 Pilar Ackerman의 이름 및 암호를 포함하는 Windows PowerShell 명령줄 인터페이스 자격 증명 개체를 만듭니다. 로그온 이름 litwareinc\\pilar는 매개 변수로 포함되었으므로 관리자는 Windows PowerShell 자격 증명 요청 대화 상자에 Pilar Ackerman 계정의 암호만 입력하면 됩니다. 이렇게 만들어진 자격 증명 개체는 $cred1이라는 변수에 저장됩니다.

두 번째 명령은 이 사용자가 atl-cs-001.litwareinc.com 풀에 로그온하여 XMPP 메신저 대화를 보낼 수 있는지 확인합니다. 이 작업을 수행하기 위해 **Test-CsXmppIm** cmdlet을 4개의 매개 변수, 즉 TargetFqdn(등록자 풀의 FQDN), Receiver(메시지를 보낼 주소로 지정된 사용자의 SIP 주소), UserCredential(Pilar Ackerman의 사용자 자격 증명이 포함된 Windows PowerShell 개체) 및 UserSipAddress(제공된 사용자 자격 증명에 해당하는 SIP 주소)와 함께 호출합니다.

    $credential = Get-Credential "litwareinc\kenmyer"
    
    Test-CsXmppIM -TargetFqdn "atl-cs-001.litwareinc.com" -Receiver "adelany@contoso.com" -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $credential

## 자세한 정보

XMPP(Extensible Messaging and Presence Protocol)는 인터넷에서 메시지를 보내는 데 사용되는 XML 기반 표준 통신 프로토콜입니다. XMPP(이전 이름은 Jabber)는 Google Talk, Facebook 채팅을 비롯한 여러 인터넷 메시징 및 통신 응용 프로그램에서 지원됩니다. **Test-CsXmppIM** cmdlet은 사용자가 XMPP 네트워크의 사용자와 메신저 대화를 교환할 수 있는지 확인합니다. 이 테스트가 성공하려면 XMPP 사용자에 대한 유효한 SIP 주소가 있어야 하며 해당 SIP 주소는 허용 XMPP 파트너로 구성된 네트워크에 있어야 합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsXmppIM"}

**Lync Server 제어판:** **Test-CsXmppIM** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>Receiver</em></p></td>
<td><p>필수</p></td>
<td><p>문자열</p></td>
<td><p>테스트 메시지의 주소로 지정된 사용자의 SIP 주소입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>TargetFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>문자열</p></td>
<td><p>테스트할 풀의 정규화된 도메인 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserCredential</em></p></td>
<td><p>필수</p></td>
<td><p>PS 자격 증명</p></td>
<td><p>테스트할 사용자 계정의 사용자 자격 증명 개체입니다. UserCredential에 전달되는 값은 <strong>Get-Credential</strong> cmdlet을 사용하여 가져온 개체 참조여야 합니다. 예를 들어 이 코드는 사용자 litwareinc\kenmyer에 대한 자격 증명 개체를 반환하고 해당 개체를 $x:$x = Get-Credential &quot;litwareinc\kenmyer&quot; 변수에 저장합니다.</p>
<p>이 명령을 실행할 때는 사용자 암호를 제공해야 합니다.</p>
<p>상태 모니터링 구성 설정을 사용하여 테스트를 수행하는 경우 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Authentication</em></p></td>
<td><p>선택</p></td>
<td><p>SIP 가상 트랜잭션 인증 메커니즘</p></td>
<td><p>테스트할 계정의 사용자 자격 증명 개체입니다. UserCredential에 전달되는 값은 <strong>Get-Credential</strong> cmdlet을 사용하여 가져온 개체 참조여야 합니다. 예를 들어, 이 코드는 사용자 litwareinc\kenmyer에 대한 자격 증명 개체를 반환하고 해당 개체를 변수</p>
<p>$x = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
<p>이 명령을 실행할 때는 사용자 암호를 제공해야 합니다. 풀의 상태 모니터링 구성 설정에 따라 테스트를 실행하는 경우에는 이 매개 변수가 필요하지 않습니다.</p></td>
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
<tr class="odd">
<td><p><em>UserSipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>테스트할 사용자 계정의 SIP 주소입니다. 예를 들면 다음과 같습니다.</p>
<p>-UserSipAddress &quot;sip:kenmyer@litwareinc.com&quot;</p>
<p>UserSipAddress 매개 변수는 UserCredential과 같은 사용자 계정을 참조해야 합니다. 풀의 상태 모니터링 구성 설정에 따라 테스트를 실행하는 경우에는 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Test-CsXmppIM** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Test-CsXmppIM** cmdlet은 Microsoft.Rtc.SyntheticTransactions.TaskOutput 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Set-CsXmppGatewayConfiguration](set-csxmppgatewayconfiguration.md)

