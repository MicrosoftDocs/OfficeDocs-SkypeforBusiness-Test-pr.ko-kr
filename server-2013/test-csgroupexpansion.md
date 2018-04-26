---
title: Test-CsGroupExpansion
TOCTitle: Test-CsGroupExpansion
ms:assetid: e41db33d-d028-4171-9418-ec04885be2fc
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399009(v=OCS.15)
ms:contentKeyID: 49305322
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsGroupExpansion

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자가 그룹 확장을 사용할 수 있는지 테스트합니다. Lync Server에서는 사용자가 Active Directory 메일 그룹을 대화 상대로 구성할 수 있습니다. 그룹을 "확장"하면 각 구성원의 이름 및 현재 상태 정보가 표시됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Test-CsGroupExpansion -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-External <SwitchParameter>] [-RegistrarPort <Int32>] [-UserSipAddress <String>] <COMMON PARAMETERS>

    Test-CsGroupExpansion -UserCredential <PSCredential> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-External <SwitchParameter>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] <COMMON PARAMETERS>

    Test-CsGroupExpansion -TargetUri <String> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-WebCredential <PSCredential>] <COMMON PARAMETERS>

    COMMON PARAMETERS: -GroupEmailAddress <String> [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>]

## 예제

## 예제 1

예제 1에 표시된 명령은 등록자 풀 atl-cs-001.litwareinc.com에 연결하여 그룹 확장을 확인합니다. 테스트를 실행하기 위해 명령은 FinanceGroup@litwareinc.com 그룹을 사용합니다.

    Test-CsGroupExpansion -TargetFqdn atl-cs-001.litwareinc.com -GroupEmailAddress FinanceGroup@litwareinc.com 

## 자세한 정보

사용자는 때때로 Active Directory 메일 그룹의 모든 구성원과 정기적으로 통신해야 합니다. 예를 들어 이 그룹은 팀의 모든 구성원 또는 특정 프로젝트에 할당된 모든 사용자로 구성될 수 있습니다. 이러한 점을 인식하여 Lync Server에서는 메일 그룹을 대화 상대로 구성할 수 있는 기능을 제공합니다. 메일 그룹을 대화 상대로 구성하면 그룹의 각 개별 구성원 대신 그룹으로 메시지를 보내 모든 그룹 구성원에게 동일한 메신저 대화를 전송할 수 있습니다.

그룹의 특정 개인과 통신하거나 특정 개인의 현재 상태를 확인해야 하는 경우도 있을 수 있습니다. 그룹 확장을 사용하면 모든 그룹 구성원과 이들의 현재 상태를 빠르고 쉽게 확인할 수 있습니다. 또한 그룹의 모든 구성원이 아니라 하나 이상의 그룹 구성원을 선택한 다음 이들에게만 메신저 대화를 보낼 수도 있습니다.

그룹 확장은 **Set-CsWebServiceConfiguration** cmdlet을 사용하여 설정 및 해제합니다. 그룹 확장을 사용하는 경우 **Test-CsGroupExpansion** cmdlet을 실행하여 기능 작동 여부를 확인할 수 있습니다. 이 cmdlet을 사용할 때는 그룹의 전자 메일 주소를 사용하여 Active Directory 메일 그룹을 지정합니다. 그러면 **Test-CsGroupExpansion** cmdlet에서 그룹 확장을 사용하여 그룹 구성원을 검색하고 검색된 목록을 사용자가 제공한 그룹 구성원 전자 메일 주소와 비교합니다. 두 목록이 일치하면 그룹 확장이 제대로 작동하는 것입니다.

서비스 자체를 테스트하거나, 연결된 웹 서비스를 테스트하는 두 가지 방법으로 그룹 확장을 테스트할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsGroupExpansion"}

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
<td><p><em>GroupEmailAddress</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>대상 메일 그룹의 전자 메일 주소입니다(예: -GroupEmailAddress &quot;FinanceGroup@litwareinc.com&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>TargetFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>그룹 확장을 테스트할 등록자 풀의 FQDN(정규화된 도메인 이름)입니다(예: -TargetFqdn &quot;atl-cs-001.litwareinc.com&quot;).</p>
<p>같은 명령에서 TargetUri 매개 변수와 TargetFqdn 매개 변수를 함께 사용할 수는 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>TargetUri</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>그룹 확장 웹 서비스의 URI(Uniform Resource Identifier)입니다(예: -TargetUri &quot;https://atl-cs-001.litwareinc.com/groupexpansion&quot;).</p>
<p>같은 명령에서 TargetUri 매개 변수와 TargetFqdn 매개 변수를 함께 사용할 수는 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>UserCredential</em></p></td>
<td><p>필수</p></td>
<td><p>System.Management.Automation.PSCredential</p></td>
<td><p>테스트에서 사용할 사용자 계정의 사용자 자격 증명 개체입니다. UserCredential에 전달되는 값은 <strong>Get-Credential</strong> cmdlet을 사용하여 가져온 개체 참조여야 합니다. 예를 들어 다음 코드는 사용자 litwareinc\kenmyer의 자격 증명 개체를 반환하고 이 개체를 $x라는 변수에 저장합니다.</p>
<p>$x = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
<p>이 명령을 실행할 때는 사용자 암호를 제공해야 합니다.</p>
<p>로그온한 사용자의 자격 증명으로 TargetFqdn 매개 변수를 사용하여 테스트를 실행하는 경우에는 사용자 자격 증명이 필요하지 않습니다. 사용자 자격 증명은 TargetUri 매개 변수를 사용하는 경우에 필요합니다.</p></td>
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
<td><p><em>External</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>외부 사용자가 그룹 확장을 사용할 수 있는지 확인하는 데 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
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
<tr class="odd">
<td><p><em>OutVerboseVariable</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 매개 변수가 있으면 cmdlet을 실행하여 얻은 자세한 출력이 지정된 변수에 저장됩니다. 예를 들어 출력을 $TestOutput이라는 변수에 저장하려면 다음과 같은 구문을 사용합니다.</p>
<p>-OutVerboseVariable TestOutput</p>
<p>변수 이름을 지정할 때 $ 문자를 추가해서는 안 됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>RegistrarPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>등록자 서비스에서 사용하는 SIP 포트입니다. 등록자에서 기본 포트 5061을 사용하는 경우에는 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserSipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>테스트에서 사용할 사용자의 SIP 주소입니다. 이 매개 변수를 지정하지 않으면 <strong>Test-CsGroupExpansion</strong> cmdlet에서 로그온한 사용자의 계정을 사용하여 검사를 수행합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WebCredential</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSCredential</p></td>
<td><p>위치 정보 서비스에 액세스하기 위한 사용자 자격 증명이 포함된 개체입니다. 이 개체는 <strong>Get-Credential</strong> cmdlet을 호출하고 적절한 자격 증명을 제공하면 검색할 수 있습니다.</p>
<p>TargetUri 및 UserSipAddress 매개 변수를 지정한 경우 명령을 실행하는 컴퓨터에 서버 인증서가 없으면 이 매개 변수가 필요합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Test-CsGroupExpansion** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Test-CsGroupExpansion** cmdlet은 Microsoft.Rtc.SyntheticTransactions.TaskOutput 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Test-CsAddressBookService](test-csaddressbookservice.md)  
[Test-CsAddressBookWebQuery](test-csaddressbookwebquery.md)

