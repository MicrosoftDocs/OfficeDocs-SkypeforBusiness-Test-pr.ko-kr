---
title: Test-CsAVEdgeConnectivity
TOCTitle: Test-CsAVEdgeConnectivity
ms:assetid: 9f3b2c70-9239-4085-a108-43e0b7a308b5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205138(v=OCS.15)
ms:contentKeyID: 49304553
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsAVEdgeConnectivity

 

_**마지막으로 수정된 항목:** 2015-03-09_

A/V 에지 서버를 통한 연결을 확인합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Test-CsAVEdgeConnectivity -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-UserSipAddress <String>] <COMMON PARAMETERS>

    Test-CsAVEdgeConnectivity -UserCredential <PSCredential> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] <COMMON PARAMETERS>

    Test-CsAVEdgeConnectivity [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>]

## 예제

## 예제 1

예제 1에 표시된 명령은 미리 구성된 테스트 사용자가 atl-cs-001.litwareinc.com 풀에 대해 구성된 A/V 에지 서버에 연결할 수 있는지 확인합니다. atl-cs-001.litwareinc.com에 대해 상태 모니터링 테스트 사용자를 한 명 이상 정의하지 않은 경우에는 이 명령이 실패합니다.

    Test-CsAVEdgeConnectivity -TargetFqdn "atl-cs-001.litwareinc.com"

## 예제 2

예제 2에서 **Test-CsAVEdgeConnectivity** cmdlet은 SIP 주소가 sip:kenmyer@litwareinc.com인 사용자가 AV 에지 서버에 연결할 수 있는지 확인합니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 Get-Credential cmdlet을 사용하여 사용자 litwareinc\\kenmyer에 대한 Windows PowerShell 자격 증명 개체를 검색합니다. 이 개체를 가져올 때 해당 계정의 암호를 제공해야 합니다. 자격 증명 개체를 가져오고 나면 두 번째 명령이 **Test-CsAVEdgeConnectivity** cmdlet을 사용하여 사용자가 AV 에지 서버에 연결할 수 있는지 확인합니다.

    $cred = Get-Credential "litwareinc\kenmyer"
    
    Test-CsAVEdgeConnectivity -TargetFqdn "atl-cs-001.litwareinc.com" -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $cred

## 자세한 정보

**Test-CsAVEdgeConnectivity** cmdlet은 사용자가 등록자 풀에 할당된 AV 에지 서버에 연결할 수 있는지 확인합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsAVEdgeConnectivity"}

**Lync Server 제어판:** **Test-CsAVEdgeConnectivity** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>System.String</p></td>
<td><p>테스트할 풀의 FQDN(정규화된 도메인 이름)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>UserCredential</em></p></td>
<td><p>필수</p></td>
<td><p>System.Management.Automation.PSCredential</p></td>
<td><p>테스트할 계정의 사용자 자격 증명 개체입니다. UserCredential에 전달되는 값은 <strong>Get-Credential</strong> cmdlet을 사용하여 가져온 개체 참조여야 합니다. 예를 들어 다음 코드는 사용자 litwareinc\kenmyer에 대한 자격 증명 개체를 반환하고 해당 개체를 $x 변수에 저장합니다.</p>
<p>저장합니다. $x = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
<p>이 명령을 실행할 때는 사용자 암호를 제공해야 합니다. 풀의 상태 모니터링 구성 설정에 따라 테스트를 실행하는 경우에는 이 매개 변수가 필요하지 않습니다.</p></td>
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
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
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
<tr class="even">
<td><p><em>OutVerboseVariable</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 매개 변수가 있으면 cmdlet을 실행하여 얻은 자세한 출력이 지정된 변수에 저장됩니다. 예를 들어 출력을 $TestOutput이라는 변수에 저장하려면 다음과 같은 구문을 사용합니다.</p>
<p>-OutVerboseVariable TestOutput</p>
<p>변수 이름을 지정할 때 $ 문자를 추가해서는 안 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>RegistrarPort</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>등록자 서비스에서 사용하는 SIP 포트입니다. 등록자에서 기본 포트 5061을 사용하는 경우에는 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>UserSipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>테스트할 사용자 계정의 SIP 주소입니다(예: -UserSipAddress &quot;sip:kenmyer@litwareinc.com&quot;). UserSipAddress 매개 변수는 UserCredential과 동일한 사용자 계정을 참조해야 합니다. 풀의 상태 모니터링 구성 설정에 따라 테스트를 실행하는 경우에는 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Test-CsAVEdgeConnectivity** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Test-CsAVEdgeConnectivity** cmdlet은 Microsoft.Rtc.SyntheticTransactions.TaskOutput 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsAVEdgeConfiguration](get-csavedgeconfiguration.md)

