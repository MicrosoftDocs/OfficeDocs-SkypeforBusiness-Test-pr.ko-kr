---
title: Test-CsAddressBookWebQuery
TOCTitle: Test-CsAddressBookWebQuery
ms:assetid: 9753dcba-83b3-437b-98f0-2806305a5bbb
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398773(v=OCS.15)
ms:contentKeyID: 49304457
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsAddressBookWebQuery

 

_**마지막으로 수정된 항목:** 2015-03-09_

주소록 웹 쿼리 서비스를 사용하여 주소록의 정보를 검색하고 반환할 수 있는지 테스트합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Test-CsAddressBookWebQuery -UserCredential <PSCredential> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-External <SwitchParameter>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] <COMMON PARAMETERS>

    Test-CsAddressBookWebQuery -TargetUri <String> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-WebCredential <PSCredential>] <COMMON PARAMETERS>

    Test-CsAddressBookWebQuery -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-External <SwitchParameter>] [-RegistrarPort <Int32>] [-UserSipAddress <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>] [-TargetSipAddress <String>]

## 예제

## 예제 1

예제 1에서는 SIP 주소가 sip:kenmyer@litwareinc.com인 연락처를 검색하여 atl-cs-001.litwareinc.com 풀에 대한 주소록 웹 쿼리 서비스를 테스트합니다. 이 명령은 atl-cs-001.litwareinc.com 풀에 대해 테스트 사용자가 정의된 경우에만 작동합니다. 등록자가 정의된 경우 명령은 풀에 대해 정의된 첫 번째 테스트 사용자의 자격 증명으로 실행됩니다.

테스트 사용자가 정의되지 않은 경우 명령이 실패합니다. 풀에 대한 테스트 사용자를 정의하지 않은 경우 UserSipAddress 매개 변수와 명령을 실행할 사용자의 자격 증명을 포함해야 합니다.

    Test-CsAddressBookWebQuery -TargetFqdn atl-cs-001.litwareinc.com  -TargetSipAddress "sip:kenmyer@litwareinc.com"

## 예제 2

예제 2에 표시된 명령도 주소록 웹 쿼리 서비스의 가용성을 테스트합니다. 단, 이 경우에는 사용자 Ken Myer(litwareinc\\kenmyer)에 대한 자격 증명으로 명령이 실행됩니다. 이 작업을 수행하기 위해 첫 번째 명령은 **Get-Credential** cmdlet을 사용하여 사용자 Ken Myer의 이름 및 암호를 포함하는 Windows PowerShell 자격 증명 개체를 만듭니다. 로그온 이름 litwareinc\\kenmyer는 매개 변수로 포함되었으므로 관리자는 Windows PowerShell 자격 증명 요청 대화 상자에 Ken Myer 계정의 암호만 입력하면 됩니다. 그러면 해당 자격 증명 개체는 변수 $cred1에 저장됩니다.

두 번째 명령에서는 **Test-CsAddressBookWebQuery** cmdlet을 사용하여 atl-cs-001.litwareinc.com 풀에 대한 주소록 웹 쿼리 서비스를 테스트합니다. Ken Myer의 사용자 자격 증명으로 이 명령을 실행하기 위해 UserCredential 매개 변수가 포함되었습니다(매개 변수 값 $cred1). 또한 명령에서는 TargetSipAddress를 사용하여 주소록에서 SIP 주소가 sip:kenmyer@litwareinc.com인 연락처를 검색하도록 지정합니다.

    $cred1 = Get-Credential "litwareinc\kenmyer"
    
    Test-CsAddressBookWebQuery -TargetFqdn atl-cs-001.litwareinc.com -UserCredential $cred1 -UserSipAddress "sip:kenmyer@litwareinc.com" -TargetSipAddress "sip:kenmyer@litwareinc.com"

## 예제 3

예제 3에서는 atl-cs-001.litwareinc.com에 대해 주소록 웹 쿼리 서비스를 테스트하는 방법을 보여 줍니다. 이 작업을 수행하기 위해 **Test-CsAddressBookWebQuery** cmdlet을 세 가지 매개 변수와 함께 호출합니다. 주소록 웹 쿼리 서비스의 URI를 지정하는 TargetUri, 테스트에 사용할 사용자 계정의 Windows PowerShell SIP 주소가 포함된 UserSipAddress 및 검색할 사용자 계정의 SIP 주소가 포함된 TargetSipAddress가 사용됩니다.

    Test-CsAddressBookWebQuery -TargetUri https://atl-cs-001.litwareinc.com/groupexpansion -UserSipAddress "sip:packerman@litwareinc.com" -TargetSipAddress "sip:kenmyer@litwareinc.com"

## 자세한 정보

**Test-CsAddressBookWebQuery** cmdlet은 "가상 트랜잭션"의 한 예입니다. 가상 트랜잭션은 Lync Server에서 사용자가 시스템 로그온, 메신저 대화 교환 또는 PSTN(공중 전화망)의 전화로 전화 걸기와 같은 일반적인 작업을 성공적으로 수행할 수 있는지 확인하는 데 사용됩니다. 이러한 테스트는 관리자가 "수동으로" 수행하거나 Microsoft System Center Operations Manager(이전 Microsoft Operations Manager)와 같은 응용 프로그램에 의해 자동으로 실행될 수 있습니다.

가상 트랜잭션은 일반적으로 두 가지 방법으로 수행됩니다. 많은 관리자가 **CsHealthMonitoringConfiguration** cmdlet을 사용하여 각 등록자 풀의 테스트 사용자를 설정합니다. 이러한 테스트 사용자는 가상 트랜잭션에 사용하도록 미리 구성된 사용자 쌍입니다. 일반적으로 이러한 계정은 테스트 계정이며 실제 사용자가 소유한 계정은 아닙니다. 풀에 테스트 사용자가 구성되면 관리자는 테스트에 참여한 사용자 계정의 ID 및 자격 증명을 지정하지 않고도 해당 풀에 대해 가상 트랜잭션을 실행할 수 있습니다.

또는 실제 사용자 계정을 사용하여 가상 트랜잭션을 실행할 수 있습니다. 예를 들어 두 사용자가 메신저 대화를 교환할 수 없는 경우 관리자는 이 두 사용자 계정(테스트 계정 쌍이 아님)을 사용하여 가상 트랜잭션을 실행한 다음 문제를 진단 및 해결할 수 있습니다. 실제 사용자 계정을 사용하여 가상 트랜잭션을 수행하도록 결정한 경우 각 사용자에 대한 로그온 이름 및 암호를 제공해야 합니다.

관리자는 **Test-CsAddressBookWebQuery** cmdlet을 통해 사용자가 주소록 웹 쿼리 서비스를 사용하여 특정 연락처를 검색할 수 있는지 확인할 수 있습니다. **Test-CsAddressBookWebQuery** cmdlet은 실행 시 먼저 인증을 위해 웹 티켓 서비스에 연결됩니다. 인증이 성공할 경우 cmdlet은 주소록 웹 쿼리 서비스에 연결하고 특정 연락처를 검색합니다. 연락처가 발견되면 이 정보를 로컬 컴퓨터로 반환합니다. 이러한 단계가 모두 완료되어야 테스트가 성공한 것으로 표시됩니다.

이 cmdlet을 실행할 수 있는 사용자: 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsAddressBookWebQuery"}

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
<td><p>주소록 웹 쿼리 서비스를 테스트할 등록자 풀의 정규화된 도메인 이름입니다 예를 들면 다음과 같습니다. -TargetFqdn &quot;atl-cs-001.litwareinc.com&quot;.</p>
<p>같은 명령에서 TargetUri 매개 변수와 TargetFqdn 매개 변수를 함께 사용할 수는 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>TargetUri</em></p></td>
<td><p>필수</p></td>
<td><p>문자열</p></td>
<td><p>주소록 웹 쿼리 서비스의 URI(Uniform Resource Identifier)입니다. 예를 들면 다음과 같습니다. -TargetUri &quot;https://atl-cs-001.litwareinc.com/groupexpansion&quot;.</p>
<p>같은 명령에서 TargetUri 매개 변수와 TargetFqdn 매개 변수를 함께 사용할 수는 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserCredential</em></p></td>
<td><p>필수</p></td>
<td><p>PS 자격 증명</p></td>
<td><p>테스트에 사용할 사용자 계정에 대한 사용자 자격 증명 개체입니다. UserCredential에 전달되는 값은 <strong>Get-Credential</strong> cmdlet을 사용하여 가져온 개체 참조여야 합니다. 예를 들어 다음 코드는 사용자 litwareinc\kenmyer에 대한 자격 증명 개체를 반환하고 이 개체를 변수 $x에</p>
<p>저장합니다. $x = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
<p>이 명령을 실행할 때 사용자 암호를 입력해야 합니다.</p></td>
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
<td><p><em>External</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>외부 사용자가 주소록 웹 쿼리 서비스를 사용할 수 있는지 확인하는 데 사용됩니다.</p></td>
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
<p>참고: 변수 이름을 지정할 때 $ 문자를 추가해서는 안 됩니다. 로거 변수에 저장된 정보를 HTML 파일에 저장하려면 다음 명령을 사용합니다.</p>
<p>$TestOutput.ToHTML() &gt; C:\Logs\TestOutput.html</p>
<p>로거 변수에 저장된 정보를 XML 파일에 저장하려면 다음 명령을 사용합니다.</p>
<p></p>
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
<td><p><em>TargetSipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>주소록 웹 쿼리 서비스에서 반환해야 할 연락처의 SIP 주소입니다. 예를 들면 다음과 같습니다. -TargetSipAddress &quot;sip:kenmyer@litwareinc.com&quot;.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserSipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>테스트에 사용할 사용자의 SIP 주소입니다. 이 매개 변수를 지정하지 않으면 <strong>Test-CsAddressBookWebQuery</strong> cmdlet이 테스트할 풀에 대해 상태 모니터링 구성 설정을 사용하여 검사를 수행합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WebCredential</em></p></td>
<td><p>선택</p></td>
<td><p>PS 자격 증명</p></td>
<td><p>위치 정보 서비스에 액세스하기 위한 사용자 자격 증명이 포함된 개체입니다. 이 개체는 <strong>Get-Credential</strong> cmdlet을 호출하고 적절한 자격 증명을 제공하면 검색할 수 있습니다.</p>
<p>TargetUri 및 UserSipAddress 매개 변수를 지정한 경우 명령을 실행하는 컴퓨터에 서버 인증서가 없으면 이 매개 변수가 필요합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Test-CsAddressBookWebQuery** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Test-CsAddressBookWebQuery** cmdlet은 Microsoft.Rtc.SyntheticTransactions.TaskOutput 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Test-CsAddressBookService](test-csaddressbookservice.md)  
[Update-CsAddressBook](update-csaddressbook.md)

