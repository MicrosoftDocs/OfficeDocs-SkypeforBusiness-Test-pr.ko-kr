---
title: Test-CsRegistration
TOCTitle: Test-CsRegistration
ms:assetid: 9e38cb36-c97a-43f2-97fe-64759f663be2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412737(v=OCS.15)
ms:contentKeyID: 49304542
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsRegistration

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자가 Lync Server에 로그온할 수 있는지 테스트합니다. **Test-CsRegistration** cmdlet은 "가상 트랜잭션", 즉 상태 및 성능 모니터링에 사용되는 일반 Lync Server 작업의 시뮬레이션입니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Test-CsRegistration -UserCredential <PSCredential> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] <COMMON PARAMETERS>

    Test-CsRegistration -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-UserSipAddress <String>] <COMMON PARAMETERS>

    Test-CsRegistration [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>]

## 예제

## 예제 1

예제 1에서는 atl-cs-001.litwareinc.com 풀에 대한 등록자 서비스를 테스트합니다. 이 명령은 atl-cs-001.litwareinc.com 풀에 대해 테스트 사용자가 정의된 경우에만 작동합니다. 사용자가 정의된 경우 테스트 사용자가 Lync Server에 로그온할 수 있는지 여부를 확인합니다.

테스트 사용자가 정의되지 않은 경우 어떤 사용자로 로그온할지를 알 수 없기 때문에 명령이 실패합니다. 풀에 대한 테스트 사용자를 정의하지 않은 경우에는 UserSipAddress 매개 변수와 함께 로그온 시도 시 명령이 사용해야 하는 사용자의 자격 증명을 포함해야 합니다.

    Test-CsRegistration -TargetFqdn atl-cs-001.litwareinc.com 

## 예제 2

예제 2에 표시된 명령은 특정 사용자(litwareinc\\pilar)가 Lync Server에 로그온할 수 있는지 테스트합니다. 이 작업을 수행하기 위해 이 예제의 첫 번째 명령은 **Get-Credential** cmdlet을 사용하여 사용자 Pilar Ackerman의 이름 및 암호를 포함하는 Windows PowerShell 자격 증명 개체를 만듭니다. 로그온 이름 litwareinc\\pilar는 매개 변수로 포함되었으므로 관리자는 Windows PowerShell 자격 증명 요청 대화 상자에 Pilar Ackerman 계정의 암호만 입력하면 됩니다. 이렇게 만들어진 자격 증명 개체는 $cred1이라는 변수에 저장됩니다.

두 번째 명령은 이 사용자가 풀 atl-cs-001.litwareinc.com에 로그온할 수 있는지 확인합니다. 이 작업을 수행하기 위해 **Test-CsRegistration** cmdlet을 TargetFqdn(등록자 풀의 FQDN), UserCredential(Pilar Ackerman의 사용자 자격 증명이 포함된 Windows PowerShell 개체) 및 UserSipAddress(제공된 사용자 자격 증명에 해당하는 SIP 주소)의 매개 변수와 함께 호출합니다.

    $cred1 = Get-Credential "litwareinc\pilar"
    
    Test-CsRegistration -TargetFqdn atl-cs-001.litwareinc.com -UserCredential $cred1 -UserSipAddress "sip:pilar@litwareinc.com"

## 자세한 정보

**Test-CsRegistration** cmdlet은 Lync Server "가상 트랜잭션"의 한 예입니다. 가상 트랜잭션은 Lync Server에서 사용자가 시스템 로그온, 메신저 대화 교환 또는 PSTN(공중 전화망)의 전화로 전화 걸기와 같은 일반적인 작업을 성공적으로 수행할 수 있는지 확인하는 데 사용됩니다. 이러한 테스트는 관리자가 "수동으로" 수행하거나 Microsoft System Center Operations Manager(이전 Microsoft Operations Manager)와 같은 응용 프로그램에 의해 자동으로 실행될 수 있습니다.

가상 트랜잭션은 일반적으로 두 가지 방법으로 수행됩니다. 많은 관리자가 CsHealthMonitoringConfiguration cmdlet을 사용하여 각 등록자 풀의 테스트 사용자를 설정합니다. 이러한 테스트 사용자는 가상 트랜잭션에 사용하도록 미리 구성된 사용자 쌍입니다. 일반적으로 이러한 계정은 테스트 계정이며 실제 사용자가 소유한 계정은 아닙니다. 풀에 테스트 사용자가 구성되면 관리자는 테스트에 참여한 사용자 계정의 ID 및 자격 증명을 지정하지 않고도 해당 풀에 대해 가상 트랜잭션을 실행할 수 있습니다.

또는 실제 사용자 계정을 사용하여 가상 트랜잭션을 실행할 수 있습니다. 예를 들어 두 사용자가 메신저 대화를 교환할 수 없는 경우 관리자는 이 두 사용자 계정(테스트 계정 쌍이 아님)을 사용하여 가상 트랜잭션을 실행하고 문제를 진단 및 해결할 수 있습니다. 실제 사용자 계정을 사용하여 가상 트랜잭션을 수행하도록 결정한 경우 각 사용자에 대한 로그온 이름 및 암호를 제공해야 합니다.

**Test-CsRegistration** cmdlet을 사용하면 조직의 사용자가 Lync Server에 로그온할 수 있는지 확인할 수 있습니다. 이 확인을 수행하려면 **Test-CsRegistration** cmdlet에 단일 테스트 계정이 필요합니다. 테스트를 수행할 풀에 대한 상태 모니터링 등록자를 설정한 경우 계정을 지정할 필요가 없습니다. 대신 **Test-CsRegistration** cmdlet은 풀에 할당된 첫 번째 테스트 계정을 자동으로 사용합니다. 자세한 내용은 [New-CsHealthMonitoringConfiguration](new-cshealthmonitoringconfiguration.md) cmdlet 도움말 항목을 참조하십시오. 또는 풀에 할당되지 않은 계정을 사용하여 테스트를 수행할 수 있습니다. 이렇게 하면 테스트 사용자를 구성하지 않은 경우에도 테스트를 실행할 수 있습니다. 또한 특정 사용자가 Lync Server에 로그온할 수 있는지 테스트할 수 있습니다. 이 방법을 사용하도록 선택할 경우 테스트되는 계정의 사용자 이름과 암호를 제공해야 합니다.

**Test-CsRegistration** cmdlet은 실행 시 테스트 사용자를 Lync Server에 로그온시킨 다음 성공할 경우 시스템에서 테스트 사용자의 연결을 끊습니다. 이 작업은 모두 사용자 상호 작용 없이 실제 사용자에게 영향을 미치지 않고 수행됩니다. 예를 들어 테스트 계정 sip:kenmyer@litwareinc.com이 실제 Lync Server 계정을 가진 실제 사용자에 해당한다고 가정해 보겠습니다. 이 경우 실제 Ken Myer를 방해하지 않고 테스트가 수행됩니다. Ken Myer 테스트 계정이 시스템에서 로그오프해도 사람 Ken Myer는 계속 로그온 상태로 남아 있게 됩니다.

Verbose 매개 변수를 추가하면 **Test-CsRegistration** cmdlet에서 테스트를 완료하기 위해 수행하는 모든 작업에 대한 자세한 설명을 볼 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsRegistration"}

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
<td><p><em>UserCredential</em></p></td>
<td><p>필수</p></td>
<td><p>PS 자격 증명</p></td>
<td><p>테스트할 계정의 사용자 자격 증명 개체입니다. UserCredential에 전달되는 값은 <strong>Get-Credential</strong> cmdlet을 사용하여 가져온 개체 참조여야 합니다. 예를 들어 이 코드는 사용자 litwareinc\kenmyer에 대한 자격 증명 개체를 반환하고 해당 개체를 변수</p>
<p>$x에 저장합니다. $x = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
<p>이 명령을 실행할 때는 사용자 암호를 제공해야 합니다. 풀의 상태 모니터링 구성 설정에 따라 테스트를 실행하는 경우에는 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Authentication</em></p></td>
<td><p>선택</p></td>
<td><p>SIP 가상 트랜잭션 인증 메커니즘</p></td>
<td><p>테스트에서 사용되는 인증 유형입니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>* TrustedServer</p>
<p>* Negotiate</p>
<p>* ClientCertificate</p>
<p>* LiveID</p></td>
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
<td><p><em>UserSipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>테스트할 사용자 계정의 SIP 주소입니다(예: -UserSipAddress &quot;sip:kenmyer@litwareinc.com&quot;). UserSipAddress 매개 변수는 UserCredential과 동일한 사용자 계정을 참조해야 합니다. 풀의 상태 모니터링 구성 설정에 따라 테스트를 실행하는 경우에는 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Test-CsRegistration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Test-CsRegistration** cmdlet은 Microsoft.Rtc.SyntheticTransactions.TaskOutput 개체의 인스턴스를 반환합니다.

