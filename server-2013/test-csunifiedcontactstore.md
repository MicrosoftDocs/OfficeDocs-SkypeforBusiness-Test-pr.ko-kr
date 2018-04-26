---
title: Test-CsUnifiedContactStore
TOCTitle: Test-CsUnifiedContactStore
ms:assetid: 0aeca874-87da-4bc8-b2f2-c9c7e0d86883
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204662(v=OCS.15)
ms:contentKeyID: 49302755
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsUnifiedContactStore

 

_**마지막으로 수정된 항목:** 2015-03-09_

통합 연락처 저장소를 통해 사용자 연락처에 액세스할 수 있는지 여부를 확인합니다. 사용자는 통합 연락처 저장소를 통해 Lync 2013, Outlook 및/또는 Outlook Web Access를 사용하여 액세스할 수 있는 단일 연락처 집합을 유지 관리할 수 있습니다. 이 cmdlet은 Lync Server 2013에 도입되었습니다.

## 구문

    Test-CsUnifiedContactStore -UserCredential <PSCredential> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] <COMMON PARAMETERS>

    Test-CsUnifiedContactStore -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-UserSipAddress <String>] <COMMON PARAMETERS>

    Test-CsUnifiedContactStore [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>]

## 예제

## 예제 1

예제 2에 표시된 명령은 사용자 litwareinc\\kenmyer의 연락처를 통합 연락처 저장소에서 찾을 수 있는지를 확인합니다. 이를 위해 예제의 첫 번째 명령은 **Get-Credential** cmdlet을 사용하여 사용자 litwareinc\\kenmyer에 대해 Windows PowerShell 명령줄 인터페이스 자격 증명 개체를 만듭니다. 유효한 자격 증명 개체를 만들고 **Test-CsUnifiedContactStore** cmdlet이 확인을 수행할 수 있도록 하려면 이 계정의 암호를 입력해야 합니다.

예제의 두 번째 명령은 제공된 자격 증명 개체($x) 및 사용자 litwareinc\\kenmyer의 SIP 주소를 사용하여 이 사용자의 연락처를 통합 연락처 저장소에서 찾을 수 있는지를 확인합니다.

    $credential = Get-Credential "litwareinc\kenmyer"
    
    Test-CsUnifiedContactStore -TargetFqdn "atl-cs-001.litwareinc.com" -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $credential

## 자세한 정보

Lync Server 2013에서 도입된 통합 연락처 저장소를 통해 관리자는 Lync Server가 아닌 Microsoft Exchange Server 2013에서 사용자 연락처를 저장할 수 있습니다. 그러면 사용자가 Lync 2013에서는 물론 Outlook과 Outlook Web Access에서도 같은 연락처 집합에 액세스할 수 있습니다. 계속 Lync Server에서 연락처를 저장할 수도 있는데, 이 경우 사용자는 서로 다른 두 연락처 집합(Outlook 및 Outlook Web Access에서 사용할 연락처 집합과 Lync 2013에서 사용할 연락처 집합)을 유지 관리해야 합니다.

**Test-CsUnifiedContactStore** cmdlet을 실행하면 사용자의 연락처가 통합 연락처 저장소로 이동되었는지를 확인할 수 있습니다. **Test-CsUnifiedContactStore** cmdlet은 지정된 사용자 계정을 가져와서 통합 연락처 저장소에 연결한 다음 해당 사용자의 연락처 검색을 시도합니다. 연락처를 검색할 수 없으면 명령이 실패하고 "사용자의 대화 상대를 받지 못했습니다. 사용자의 대화 상대가 있는지 확인하세요."라는 메시지가 표시됩니다.

사용자가 통합 연락처 저장소로 마이그레이션되었지만 대화 상대 목록에 연락처가 없으면 **Test-CsUnifiedContactStore** cmdlet은 실패합니다. 지정한 사용자에게 연락처가 한 명 이상 있어야 **Test-CsUnifiedContactStore** cmdlet이 정상적으로 완료됩니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsUnifiedContactStore"}

Lync Server 제어판: **Test-csUnifiedContactStore** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>테스트에서 사용할 사용자 계정의 사용자 자격 증명 개체입니다. UserCredential에 전달되는 값은 <strong>et-Credential</strong> cmdlet을 사용하여 가져온 개체 참조여야 합니다. 예를 들어 다음 코드는 사용자 litwareinc\kenmyer의 자격 증명 개체를 반환하고 이 개체를 $x라는 변수에 저장합니다.</p>
<p>$x = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
<p>이 명령을 실행할 때는 사용자 암호를 제공해야 합니다.</p>
<p><strong>CsHealthMonitoringConfiguration</strong> cmdlet을 통해 구성된 테스트 사용자를 사용하여 테스트를 실행하는 경우에는 이 매개 변수가 필요 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Authentication</em></p></td>
<td><p>선택</p></td>
<td><p>SIP 가상 트랜잭션 + 인증 메커니즘</p></td>
<td><p>테스트 실행 시 사용되는 인증 유형입니다. 사용 가능한 값은 다음과 같습니다.</p>
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
<td><p>테스트에서 사용할 사용자의 SIP 주소입니다. 예를 들면 다음과 같습니다.</p>
<p>-UserSipAddress &quot;sip:kenmyer@litwareinc.com&quot;</p>
<p><strong>CsHealthMonitoringConfiguration</strong> cmdlet을 통해 구성된 테스트 사용자를 사용하여 테스트를 실행하는 경우에는 이 매개 변수가 필요 없습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Test-CsUnifiedContactStore** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Test-CsUnifiedContactStore** cmdlet은 Microsoft.Rtc.SyntheticTransactions.WebTaskOutput 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsUserServicesPolicy](new-csuserservicespolicy.md)  
[Set-CsUserServicesPolicy](set-csuserservicespolicy.md)

