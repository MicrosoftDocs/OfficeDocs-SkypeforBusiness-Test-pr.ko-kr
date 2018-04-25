---
title: Test-CsPersistentChatMessage
TOCTitle: Test-CsPersistentChatMessage
ms:assetid: 08c6db0b-23e2-4fbe-8276-181275a40daf
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204656(v=OCS.15)
ms:contentKeyID: 49302734
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsPersistentChatMessage

 

_**마지막으로 수정된 항목:** 2015-03-09_

한 쌍의 사용자가 영구 채팅 서비스(이전의 그룹 채팅 서비스)를 사용하여 메시지를 교환할 수 있는지 여부를 확인합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Test-CsPersistentChatMessage -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-ReceiverSipAddress <String>] [-RegistrarPort <Int32>] [-SenderSipAddress <String>] <COMMON PARAMETERS>

    Test-CsPersistentChatMessage -ReceiverCredential <PSCredential> -ReceiverSipAddress <String> -SenderCredential <PSCredential> -SenderSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] <COMMON PARAMETERS>

    Test-CsPersistentChatMessage [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-ChatRoomUri <String>] [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>] [-Setup <$true | $false>] [-TestUser1SipAddress <String>] [-TestUser2SipAddress <String>]

## 예제

## 예제 1

예제 2에 표시된 명령은 한 쌍의 사용자(litwareinc\\pilar 및 litwareinc\\kenmyer)가 Lync Server 2013에 로그온한 다음 영구 채팅 서비스를 사용하여 메시지를 교환할 수 있는지 테스트합니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 **Get-Credential** cmdlet을 사용하여 사용자 Pilar Ackerman의 이름 및 암호를 포함하는 Windows PowerShell 자격 증명 개체를 만듭니다. 로그온 이름 litwareinc\\pilar가 매개 변수로 포함되었으므로 관리자는 Windows PowerShell 자격 증명 요청 대화 상자에 Pilar Ackerman 계정의 암호만 입력하면 됩니다. 이렇게 만들어진 자격 증명 개체는 $cred1이라는 변수에 저장됩니다. 두 번째 명령도 같은 작업을 수행하지만 이번에는 Ken Myer 계정의 자격 증명 개체를 반환합니다.

자격 증명 개체가 반환되면 세 번째 명령은 이 두 사용자가 Lync Server 2013에 로그온하여 영구 채팅을 사용해 메시지를 교환할 수 있는지를 확인합니다. 이 작업을 수행하기 위해 **Test-CsPersistentChatMessage** cmdlet을 호출하며, 이때 사용되는 매개 변수는 TargetFqdn(고급 등록자 풀의 FQDN), SenderSipAddress(첫 번째 테스트 사용자의 SIP 주소), SenderCredential(첫 번째 테스트 사용자의 자격 증명을 포함하는 Windows PowerShell 개체), ReceiverSipAddress(두 번째 테스트 사용자의 SIP 주소) 및 ReceiverCredential(두 번째 테스트 사용자의 자격 증명을 포함하는 Windows PowerShell 개체)입니다.

    $cred1 = Get-Credential "litwareinc\pilar"
    $cred2 = Get-Credential "litwareinc\kenmyer"
    
    Test-CsPersistentChatMessage -TargetFqdn atl-persistentchat-001.litwareinc.com -SenderSipAddress "sip:pilar@litwareinc.com" -SenderCredential $cred1 -ReceiverSipAddress "sip:kenmyer@litwareinc.com" -ReceiverCredential $cred2

## 자세한 정보

**Test-CsPersistentChatMessage** cmdlet은 한 쌍의 테스트 사용자가 영구 채팅 서비스를 사용하여 메시지를 교환할 수 있는지 확인합니다. 이 작업을 수행하기 위해 cmdlet은 두 사용자를 Lync Server 2013에 로그온시키고 영구 채팅방에 사용자를 연결한 다음, 한 쌍의 메시지를 교환하고 채팅방을 종료한 후에 두 사용자를 로그오프시킵니다. 채팅방을 만들지 않았거나 두 테스트 사용자가 영구 채팅 서비스에 액세스할 수 있도록 하는 영구적 채팅 정책이 두 테스트 사용자 계정에 할당되지 않은 경우에는 이 cmdlet 호출이 실패합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsPersistentChatMessage"}

Lync Server 제어판: **Test-CsPersistentChatMessage** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>ReceiverCredential</em></p></td>
<td><p>필수</p></td>
<td><p>PS 자격 증명</p></td>
<td><p>테스트할 두 사용자 계정 중 첫 번째 사용자 계정의 사용자 자격 증명 개체입니다. ReceiverCredential에 전달되는 값은 Get-Credential cmdlet을 사용하여 가져온 개체 참조여야 합니다. 예를 들어 다음 코드는 사용자 litwareinc\pilar의 자격 증명 개체를 반환하고 이 개체를 $y라는 변수에 저장합니다.</p>
<p>$y = Get-Credential &quot;litwareinc\pilar&quot;</p>
<p>이 명령을 실행할 때는 사용자 암호를 제공해야 합니다.</p>
<p>풀의 상태 모니터링 구성 설정에 따라 테스트를 실행하는 경우에는 받는 사람 자격 증명이 필요하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SenderCredential</em></p></td>
<td><p>필수</p></td>
<td><p>PS 자격 증명</p></td>
<td><p>테스트할 두 사용자 계정 중 두 번째 사용자 계정의 사용자 자격 증명 개체입니다. SenderCredential에 전달되는 값은 <strong>Get-Credential</strong> cmdlet을 사용하여 가져온 개체 참조여야 합니다. 예를 들어 다음 코드는 사용자 litwareinc\kenmyer의 자격 증명 개체를 반환하고 이 개체를 $x라는 변수에 저장합니다.</p>
<p>$x = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
<p>이 명령을 실행할 때는 사용자 암호를 제공해야 합니다.</p>
<p>풀의 상태 모니터링 구성 설정에 따라 테스트를 실행하는 경우에는 보낸 사람 자격 증명이 필요하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>TargetFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>문자열</p></td>
<td><p>테스트할 고급 등록자 풀의 FQDN(정규화된 도메인 이름)입니다.</p></td>
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
<td><p><em>ChatRoomUri</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>영구 채팅 서버의 정규화된 도메인 이름과 채팅방의 이름으로 구성된 채팅방 위치입니다. 예를 들면 다음과 같습니다.</p>
<p>-ChatRoomIdentity &quot;atl-persistentchat-001.litwareinc.com\ITChatRoom&quot;</p></td>
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
<p>$TestOutput. ToHTML() &gt; C:\Logs\TestOutput.html</p>
<p>로거 변수에 저장된 정보를 XML 파일에 저장하려면 다음 명령을 사용합니다.</p>
<p>$TestOutput. ToXML() &gt; C:\Logs\TestOutput.xml</p></td>
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
<td><p><em>ReceiverSipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>테스트할 두 사용자 계정 중 첫 번째 사용자 계정의 SIP 주소입니다. 예를 들면 다음과 같습니다.</p>
<p>-ReceiverSipAddress &quot;sip:pilar@litwareinc.com&quot;</p>
<p>ReceiverSIPAddress 매개 변수는 ReceiverCredential과 동일한 사용자 계정을 참조해야 합니다.</p>
<p>풀의 상태 모니터링 구성 설정에 따라 테스트를 실행하는 경우에는 SIP 주소가 필요하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>RegistrarPort</em></p></td>
<td><p>선택</p></td>
<td><p>Int32</p></td>
<td><p>등록자 서비스에서 사용하는 SIP 포트입니다. 등록자에서 기본 포트 5061을 사용하는 경우에는 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SenderSipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>테스트할 두 사용자 계정 중 두 번째 사용자 계정의 SIP 주소입니다. 예를 들면 다음과 같습니다.</p>
<p>-SenderSipAddress &quot;sip:kenmyer@litwareinc.com&quot;</p>
<p>SenderSipAddress 매개 변수는 SenderCredential과 동일한 사용자 계정을 참조해야 합니다.</p>
<p>풀의 상태 모니터링 구성 설정에 따라 테스트를 실행하는 경우에는 SIP 주소가 필요하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Setup</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>Lync Server 토폴로지에 액세스할 수 없는 감시자 노드 컴퓨터에 대해 cmdlet을 실행할 수 있습니다. 이 작업을 허용하려면 먼저 토폴로지에 액세스할 수 없는 컴퓨터에서 Setup 매개 변수를 포함하여 <strong>Test-CsPersistentChatMessage</strong>를 실행합니다. 그리고 나면 감시자 노드 컴퓨터에 대해 cmdlet을 실행할 수 있습니다.</p>
<p>Setup 매개 변수를 사용하는 경우에는 TestUser1SipAddress 및 TestUser2SipAddress 매개 변수도 사용해야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>TestUser1SipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>Setup 매개 변수와 함께 사용되는 첫 번째 테스트 사용자의 SIP 주소입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>TestUser2SipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>Setup 매개 변수와 함께 사용되는 두 번째 테스트 사용자의 SIP 주소입니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Test-CsPersistentChatMessage** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Test-CsPersistentChatMessage** cmdlet은 Microsoft.Rtc.SyntheticTransactions.TaskOutput 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Grant-CsPersistentChatPolicy](grant-cspersistentchatpolicy.md)  
[New-CsPersistentChatPolicy](new-cspersistentchatpolicy.md)  
[Set-CsPersistentChatPolicy](set-cspersistentchatpolicy.md)

