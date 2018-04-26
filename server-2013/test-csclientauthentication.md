---
title: Test-CsClientAuthentication
TOCTitle: Test-CsClientAuthentication
ms:assetid: 6a25b2c6-0cb2-473c-af92-0be5cead8a19
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ619181(v=OCS.15)
ms:contentKeyID: 49303928
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsClientAuthentication

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자가 인증서 프로비전 서비스에서 다운로드한 인증서를 사용하여 Lync Server에 로그온할 수 있는지 확인합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다. 이는 Lync Server 2010에서 사용하던 **Test-CSClientAuth** cmdlet을 대체합니다.

## 구문

    Test-CsClientAuthentication -UserCredential <PSCredential> -UserSipAddress <String> [-Force <SwitchParameter>] [-LiveIdAuthentication <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] [-TargetUri <String>]

## 예제

## 예제 1

예제 1의 명령은 사용자 litwareinc\\kenmyer가 클라이언트 인증서를 사용하여 등록자 풀 atl-cs-001.litwareinc.com에 로그온할 수 있는지 테스트합니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 **Get-Credential** cmdlet을 사용하여 해당 사용자의 자격 증명 개체를 만듭니다. 만들어진 자격 증명 개체(사용자 암호를 입력해야 함)는 $cred1 변수에 저장됩니다.

그런 다음 두 번째 명령이 **Test-CsClientAuthentication** cmdlet을 호출하여 등록자 풀의 FQDN(TargetFqdn), 사용자의 SIP 주소(UserSipAddress) 및 첫 번째 명령으로 생성된 자격 증명 개체(UserCredential)를 지정합니다.

    $cred1 = Get-Credential "litwareinc\kenmyer"
    
    Test-CsClientAuthentication -TargetFqdn atl-cs-001.litwareinc.com -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $cred1

## 자세한 정보

클라이언트 인증서는 Lync Server에서 사용자를 인증하는 대체 방법을 제공합니다. 사용자가 클라이언트 인증서를 사용하여 시스템에 로그온할 수 있는지 여부를 확인하려면 **Test-CsClientAuthentication** cmdlet을 실행하면 됩니다. 이 **Test-CsClientAuthentication** cmdlet을 실행할 경우 테스트되는 사용자 계정의 등록자 풀 및 SIP 주소를 지정해야 합니다. 또한 사용자의 로그온 이름 및 암호를 제공할 수 있어야 합니다. **Test-CsClientAuthentication** cmdlet을 호출하면 이 cmdlet은 인증서 프로비전 서비스에 연결하여 지정된 사용자의 클라이언트 인증서 복사본을 다운로드합니다. 그런 다음 **Test-CsClientAuthentication** cmdlet은 클라이언트 인증서를 찾아서 다운로드할 수 있는 경우 해당 인증서를 사용하여 로그온을 시도합니다. 로그온에 성공하면 **Test-CsClientAuthentication** cmdlet은 로그오프되고 테스트 성공을 보고합니다.

인증서를 찾거나 다운로드할 수 없거나 해당 인증서를 사용하여 로그온할 수 없는 경우 **Test-CsClientAuthentication** cmdlet은 테스트 실패를 보고합니다.

이 cmdlet을 실행할 수 있는 사용자: 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsClientAuthentication"}

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
<td><p><em>UserCredential</em></p></td>
<td><p>필수</p></td>
<td><p>System.Management.Automation.PSCredential</p></td>
<td><p>테스트에서 사용할 사용자 계정의 사용자 자격 증명 개체입니다. UserCredential에 전달되는 값은 <strong>Get-Credential</strong> cmdlet을 사용하여 가져온 개체 참조여야 합니다. 예를 들어 다음 코드는 사용자 litwareinc\kenmyer의 자격 증명 개체를 반환하고 이 개체를 $x라는 변수에 저장합니다.</p>
<p>$x = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
<p>이 명령을 실행할 때는 사용자 암호를 제공해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>UserSipAddress</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>테스트에서 사용할 사용자의 SIP 주소입니다(예: -UserSipAddress sip:kenmyer@litwareinc.com).</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>LiveIdAuthentication</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>테스트 사용자가 OrgId(Business LiveId) 자격 증명을 사용하여 로그온할 수 있는지 테스트합니다.</p></td>
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
<td><p>등록자 서비스에서 사용하는 SIP 포트입니다. 이 매개 변수는 등록자가 기본 포트 5061을 사용하는 경우에는 필요하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>TargetFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>클라이언트 인증을 테스트할 등록자 풀의 FQDN(정규화된 도메인 이름)입니다(예: -TargetFqdn &quot;atl-cs-001.litwareinc.com&quot;).</p></td>
</tr>
<tr class="odd">
<td><p><em>TargetUri</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>인증서 프로비전 서비스의 URL입니다. 이 매개 변수를 포함하지 않으면 <strong>Test-CsClientAuthentication</strong> cmdlet은 등록자 풀에 구성된 인증서 프로비전 서비스를 사용합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음

## 반환 형식

**Test-CsClientAuthentication** cmdlet은 Microsoft.Rtc.SyntheticTransactions.TaskOutput 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsWebServiceConfiguration](get-cswebserviceconfiguration.md)  
[Test-CsRegistration](test-csregistration.md)

