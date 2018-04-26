---
title: Test-CsLocationPolicy
TOCTitle: Test-CsLocationPolicy
ms:assetid: 49f7d148-d46d-4bcc-af9d-6a3a0fdde8ee
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425962(v=OCS.15)
ms:contentKeyID: 49303551
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsLocationPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

테스트를 실행하여 매개 변수 값에 지정된 조건을 기준으로 사용할 위치 정책을 결정합니다. 위치 정책에 포함된 설정은 E9-1-1(Enhanced 9-1-1)의 적용 여부와 방법을 결정합니다. E9-1-1을 사용하면 911 긴급 통화를 받는 사람이 발신자의 지리적 위치를 확인할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Test-CsLocationPolicy -UserCredential <PSCredential> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] <COMMON PARAMETERS>

    Test-CsLocationPolicy -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-UserSipAddress <String>] <COMMON PARAMETERS>

    Test-CsLocationPolicy [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>] [-Subnet <String>]

## 예제

## 예제 1

이 예제에서는 현재 사용자나 현재 구성된 사용자의 위치 정책을 확인합니다. TargetFqdn은 필수입니다.

    Test-CsLocationPolicy -TargetFqdn atl-cs-001.litwareinc.com 

## 예제 2

예제 2의 첫째 줄에서는 Windows PowerShell **Get-Credential** cmdlet을 호출합니다. 이 cmdlet은 사용자 자격 증명을 검색하고 보안 개체로 반환합니다. 이 cmdlet에 제공되는 매개 변수는 사용자 ID뿐입니다. 이 cmdlet을 실행하면 제공된 사용자 ID가 미리 채워지고 사용자 암호를 입력할 수 있는 텍스트 상자가 포함된 대화 상자가 열립니다. 이러한 사용자 자격 증명은 $cred 변수에 저장됩니다.

둘째 줄에서는 **Test-CsLocationPolicy** cmdlet을 호출합니다. 예제 1과 마찬가지로 대상 FQDN을 제공합니다. 그러나 이 예제에서는 미리 구성된 사용자를 사용하는 대신 SIP 주소가 kenmyer@litwareinc.com인 사용자에 대해 테스트를 실행합니다. sip: 접두사가 있는 해당 값을 UserSipAddress 매개 변수에 전달하고 $cred 변수에 저장된 사용자 자격 증명을 UserCredential 매개 변수에 전달합니다.

    $cred = Get-Credential "litwareinc\kenmyer"
    Test-CsLocationPolicy -TargetFqdn atl-cs-001.litwareinc.com -UserCredential $cred -UserSipAddress "sip:kenmyer@litwareinc.com"

## 예제 3

이 예제는 예제 2와 유사하지만 사용자 자격 증명을 지정하지 않습니다. 사용자 자격 증명을 지정하지 않고 **Test-CsLocationPolicy** cmdlet을 호출하면 사용자의 위치 정책을 인증하고 검색하는 데 이 cmdlet을 실행 중인 컴퓨터의 서버 인증서가 사용됩니다. 컴퓨터에 서버 인증서가 없는 경우에는 예제 2에 표시된 대로 자격 증명을 지정해야 합니다. 컴퓨터에 서버 인증서가 있는지 여부를 확인하려면 **Get-CsCertificate** cmdlet을 호출합니다.

    Test-CsLocationPolicy -TargetFqdn atl-cs-001.litwareinc.com -UserSipAddress "sip:kenmyer@litwareinc.com"

## 예제 4

이 예제에서는 서브넷 ID가 172.15.11.0인 서브넷의 위치 정책을 확인합니다. 서브넷에 위치 정책이 연결되어 있지 않으면 현재 구성된 사용자에 대한 위치 정책이 검색됩니다.

참고: 서브넷에 대한 위치 정책을 설정하려면 **Set-CsNetworkSite** cmdlet의 LocationPolicy 매개 변수를 위치 정책 ID로 설정한 다음 **Set-CsNetworkSubnet**의 NetworkSiteId 매개 변수를 해당 사이트의 ID로 설정합니다. 예를 들면 다음과 같습니다.

Set-CsNetworkSite Portland –LocationPolicy Reno

Set-CsNetworkSubnet 175.15.11.0 –NetworkSiteID Portland

    Test-CsLocationPolicy -TargetFqdn atl-cs-001.litwareinc.com -Subnet 172.15.11.0

## 자세한 정보

위치 정책은 E9-1-1 기능 및 클라이언트 위치와 관련된 설정을 적용하는 데 사용됩니다. 사용자가 E9-1-1을 사용하도록 설정되어 있는지 여부를 확인하고, 설정된 경우 응급 통화에 대한 행동을 결정합니다. 예를 들어 위치 정책을 사용하여 응급 통화 번호(한국의 경우 119)를 정의하고, 회사 보안 부서에 자동으로 알림을 제공할지 여부, 통화를 경로 지정할 방법 등을 지정할 수 있습니다. 이 cmdlet은 특정 풀, 서브넷, 스위치 또는 무선 액세스 지점의 특정 클라이언트에서 전화가 걸려올 때 사용할 위치 정책에 대한 정보를 반환합니다.

이 cmdlet을 호출할 때 사용자를 지정하지 않으면 현재 구성된 사용자가 테스트됩니다. 현재 구성된 사용자를 찾으려면 **Get-CsHealthMonitoringConfiguration** cmdlet을 호출합니다. 구성된 사용자를 설정하려면 **Set-CsHealthMonitoringConfiguration** cmdlet을 호출합니다.

사용자나 서브넷에 대한 위치 정책을 찾은 경우 테스트가 성공합니다. 기본적으로 반환되는 정보에는 위치 정책의 이름(사용자별 정책이 할당된 경우) 및 사용자나 서브넷이 E9-1-1을 활성화했는지 여부가 포함됩니다. 테스트에 대한 추가 정보를 검색하려면 Windows PowerShell 일반 매개 변수인 Verbose를 포함합니다.

사용자나 네트워크 서브넷에 대해 위치 정책을 테스트할 수 있습니다. Subnet 매개 변수의 값을 지정하여 서브넷에 대해 테스트를 실행하는 경우 이 cmdlet은 해당 서브넷에 대한 위치 정책을 확인하려고 합니다. 서브넷에 위치 정책이 할당되어 있지 않으면 구성된 사용자에 대한 위치 정책이 검색됩니다. 서브넷 정책이 성공적으로 검색되면 subnet-tagid로 시작하는 LocationPolicyTagID 값이 출력에 포함됩니다. 서브넷에 대한 위치 정책을 찾을 수 없는 경우 LocationPolicyTagID가 user-tagid로 시작합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Test-CsLocationPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsLocationPolicy"}

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
<td><p>지정한 사용자나 서브넷이 이동할 대상 풀의 FQDN(정규화된 도메인 이름)입니다. 사용자를 지정하지 않으면 미리 구성된 사용자나 현재 사용자가 가정됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>UserCredential</em></p></td>
<td><p>필수</p></td>
<td><p>PS 자격 증명</p></td>
<td><p>위치 정책을 테스트할 사용자 계정의 사용자 ID와 암호가 포함된 개체입니다. <strong>Get-Credential</strong> cmdlet을 호출하고 적절한 정보를 채운 다음 출력을 변수에 저장하여 자격 증명 개체를 검색할 수 있습니다.</p></td>
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
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
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
<td><p>문자열</p></td>
<td><p>이 매개 변수가 있으면 cmdlet을 실행하여 얻은 자세한 출력이 지정된 변수에 저장됩니다. 예를 들어 출력을 $TestOutput이라는 변수에 저장하려면 다음과 같은 구문을 사용합니다.</p>
<p>-OutVerboseVariable TestOutput</p>
<p>변수 이름을 지정할 때 $ 문자를 추가해서는 안 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>RegistrarPort</em></p></td>
<td><p>선택</p></td>
<td><p>Int32</p></td>
<td><p>등록자 서비스의 포트 번호입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Subnet</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>위치 정책을 테스트할 네트워크 서브넷의 ID(IP 주소)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserSipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>위치 정책을 테스트할 사용자의 SIP 주소입니다. 이 주소는 sip:&lt;사용자 ID&gt; 형식을 사용해야 합니다(예: sip:kenmyer@litwareinc.com).</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

**Test-CsLocationPolicy** cmdlet은 Microsoft.Rtc.SyntheticTransactions.TaskOutput 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsLocationPolicy](new-cslocationpolicy.md)  
[Remove-CsLocationPolicy](remove-cslocationpolicy.md)  
[Set-CsLocationPolicy](set-cslocationpolicy.md)  
[Get-CsLocationPolicy](get-cslocationpolicy.md)  
[Grant-CsLocationPolicy](grant-cslocationpolicy.md)  
[Get-CsHealthMonitoringConfiguration](get-cshealthmonitoringconfiguration.md)  
[Set-CsHealthMonitoringConfiguration](set-cshealthmonitoringconfiguration.md)  
[Set-CsNetworkSite](set-csnetworksite.md)

