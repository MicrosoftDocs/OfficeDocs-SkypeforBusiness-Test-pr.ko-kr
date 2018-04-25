---
title: Test-CsLisConfiguration
TOCTitle: Test-CsLisConfiguration
ms:assetid: 6983d42e-6b93-4365-b0f1-81031d6e251b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398497(v=OCS.15)
ms:contentKeyID: 49303923
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsLisConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

LIS(위치 정보 서버) 구성을 테스트합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Test-CsLisConfiguration -UserCredential <PSCredential> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-External <SwitchParameter>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] <COMMON PARAMETERS>

    Test-CsLisConfiguration -TargetUri <String> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-WebCredential <PSCredential>] <COMMON PARAMETERS>

    Test-CsLisConfiguration -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-External <SwitchParameter>] [-RegistrarPort <Int32>] [-UserSipAddress <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-BssId <String>] [-ChassisId <String>] [-Force <SwitchParameter>] [-Mac <String>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>] [-PortId <String>] [-PortIdSubType <InterfaceAlias | InterfaceName | LocallyAssigned>] [-Subnet <String>]

## 예제

## 예제 1

이 예제에서는 FQDN atl-cs-001.litwareinc.com의 LIS 구성을 테스트합니다. 현재 사용자 자격 증명을 사용하여 해당 FQDN의 LIS 웹 서비스로 연결이 가능할 경우 테스트는 성공합니다. 서브넷 IP 주소 192.168.0.0에 매핑되는 위치를 찾을 수 있는 경우 해당 위치 주소가 반환됩니다.

이 명령이 성공하려면 가상 트랜잭션 사용자를 포함한 상태 모니터링 구성이 있어야 합니다. 상태 모니터링 구성이 존재하는지 확인하려면 **Get-CsHealthMonitoringConfiguration** cmdlet을 실행합니다. 새 상태 모니터링 구성을 만들려면 **New-CsHealthMonitoringConfiguration** cmdlet을 실행합니다.

    Test-CsLisConfiguration -TargetFqdn atl-cs-001.litwareinc.com -Subnet 192.168.0.0

## 예제 2

이 예제는 예제 1과 동일하지만 UserSipAddress 매개 변수가 추가되었습니다. 설정된 가상 트랜잭션 사용자가 없지만 명령을 실행 중인 컴퓨터에 서버 인증서가 있으면 이 명령을 사용합니다.

    Test-CsLisConfiguration -TargetFqdn atl-cs-001.litwareinc.com -Subnet 192.168.0.0 -UserSipAddress sip:kmyer@litwareinc.com

## 예제 3

이 예제의 첫째 줄에서는 사용자 ID와 암호를 입력하라는 메시지를 표시하는 Windows PowerShell cmdlet인 **Get-Credential** cmdlet을 호출합니다. 이 정보는 암호화된 방식으로 변수 $cred에 저장됩니다.

둘째 줄은 예제 2의 명령과 동일하지만 UserSipAddress 매개 변수가 추가되었습니다. 설정된 가상 트랜잭션 사용자가 없고 명령을 실행 중인 컴퓨터에 서버 인증서가 없으면 이 명령을 사용합니다.

    $cred = Get-Credential
    Test-CsLisConfiguration -TargetFqdn atl-cs-001.litwareinc.com -Subnet 192.168.0.0 -UserSipAddress sip:kmyer@litwareinc.com -UserCredential $cred

## 예제 4

이 예제의 첫째 줄에서는 사용자 ID와 암호를 입력하라는 메시지를 표시하는 **Get-Credential** cmdlet을 호출합니다. 이 정보는 암호화된 방식으로 변수 $cred에 저장됩니다.

둘째 줄에서는 원격 사용자의 SIP 주소를 기반으로 웹 서비스 URI(https://atl-cs-001.litwareinc.com/locationinformation/lisservice.svc)를 호출하고, WebCredential 매개 변수에 전달하여 첫째 줄에서 얻은 자격 증명을 사용하여 LIS 구성을 테스트합니다. 지정된 사용자 자격 증명을 사용하여 해당 URI의 LIS 웹 서비스로 연결이 가능할 경우 테스트는 성공합니다. 위치를 찾을 수 있는 경우 이 위치는 위치 주소가 반환되는 서브넷 IP 주소 192.168.0.0, MAC 주소 0A-23-00-00-00-AA 또는 포트 ID 4500 및 ChassisId 0A-23-00-00-00-AA에 매핑됩니다.

명령을 실행 중인 컴퓨터에 서버 인증서가 없으면 이 명령을 사용합니다.

    $cred = Get-Credential
    Test-CsLisConfiguration -TargetUri https://atl-cs-001.litwareinc.com/locationinformation/lisservice.svc -UserSipAddress sip:kmyer@litwareinc.com -WebCredential $cred -Subnet 192.168.0.0 -Mac 0A-23-00-00-00-AA -PortId 4500 -ChassisId 0A-23-00-00-00-AA

## 예제 5

이 예제는 예제 4와 동일하지만 WebCredential 매개 변수를 사용하지 않아 **Get-Credential** cmdlet을 호출하지 않는다는 점이 다릅니다. 명령을 실행 중인 컴퓨터에 서버 인증서가 있으면 이 명령을 사용합니다.

    Test-CsLisConfiguration -TargetUri https://atl-cs-001.litwareinc.com/locationinformation/lisservice.svc -UserSipAddress sip:kmyer@litwareinc.com -Subnet 192.168.0.0 -Mac 0A-23-00-00-00-AA -PortId 4500 -ChassisId 0A-23-00-00-00-AA

## 자세한 정보

이 cmdlet은 제공된 매개 변수의 정보를 기반으로 LIS(위치 정보 서버) 웹 서비스에 연결할 수 있는지 여부를 확인합니다. 웹 서비스에 연결할 수 있고 제공된 매개 변수에 해당하는 위치가 발견되는 경우 테스트는 통과된 것으로 간주되고 위치가 표시됩니다. 위치를 찾을 수 없는 경우에도 웹 서비스에 연결할 수 있으면 테스트는 통과되지만 위치 정보는 반환되지 않습니다. 또한 선택 매개 변수를 제공하지 않고 이 cmdlet을 호출할 경우 웹 서비스에 연결이 가능하면 테스트는 통과되지만 위치 정보는 역시 반환되지 않습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Test-CsLisConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsConfiguration"}

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
<td><p>테스트를 실행할 서버의 FQDN(정규화된 도메인 이름)(server.litwareinc.com 형식)입니다.</p>
<p>TargetFqdn을 지정할 수 없는 경우 TargetUri 매개 변수를 지정하지 않으면 이 매개 변수가 필요합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>TargetUri</em></p></td>
<td><p>필수</p></td>
<td><p>문자열</p></td>
<td><p>위치 정보 서비스의 URI(Uniform Resource Identifier)입니다. 위치 정보 서비스의 URI를 검색하려면 Get-CsService –WebServer | Select-Object LIServiceInternalUri 명령을 실행하면 됩니다.</p>
<p>이 매개 변수에 대한 값을 지정하는 경우 UserSipAddress 매개 변수도 필요합니다. 명령을 실행하려는 컴퓨터에 서버 인증서가 없는 경우 WebCredential 매개 변수의 값도 지정해야 합니다.</p>
<p>TargetFqdn 매개 변수를 지정하지 않을 경우 이 매개 변수가 필요합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserCredential</em></p></td>
<td><p>필수</p></td>
<td><p>PS 자격 증명</p></td>
<td><p>위치 정보 서비스에 액세스하기 위한 사용자 자격 증명이 포함된 개체입니다. 이 개체는 <strong>Get-Credential</strong> cmdlet을 호출하고 적절한 자격 증명을 제공하면 검색할 수 있습니다.</p>
<p>TargetFqdn 및 UserSipAddress 매개 변수를 지정한 경우 cmdlet을 실행 중인 컴퓨터에 서버 인증서가 없으면 이 매개 변수가 필요합니다.</p></td>
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
<td><p><em>BssId</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>무선 액세스 지점의 BSSID(기본 서비스 집합 식별자)입니다. 이 값은 nn-nn-nn-nn-nn-nn 형식이어야 합니다(예: 12-34-56-78-90-ab).</p></td>
</tr>
<tr class="even">
<td><p><em>ChassisId</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>네트워크 스위치의 MAC(미디어 액세스 제어) 주소입니다. 이 값은 nn-nn-nn-nn-nn-nn 형식(예: 12-34-56-78-90-ab) 또는 IP 주소입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>External</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>이 매개 변수는 위치 정보 서버에 대해 지원되지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Mac</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>포트 스위치의 MAC 주소입니다. 이 값은 nn-nn-nn-nn-nn-nn 형식이어야 합니다(예: 12-34-56-78-90-ab).</p></td>
</tr>
<tr class="even">
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
<tr class="odd">
<td><p><em>OutVerboseVariable</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>이 매개 변수가 있으면 cmdlet을 실행하여 얻은 자세한 출력이 지정된 변수에 저장됩니다. 예를 들어 출력을 $TestOutput이라는 변수에 저장하려면 다음과 같은 구문을 사용합니다.</p>
<p>-OutVerboseVariable TestOutput</p>
<p>변수 이름을 지정할 때 $ 문자를 추가해서는 안 됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PortId</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>테스트할 위치와 연결된 포트의 ID입니다. 여기에는 MAC 주소 또는 IP 주소도 포함될 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PortIdSubType</em></p></td>
<td><p>선택</p></td>
<td><p>포트 ID 하위 유형</p></td>
<td><p>포트의 하위 유형입니다. 이 값은 숫자 값 또는 문자열로 입력할 수 있지만 유효한 하위 유형이어야 합니다. 사용할 수 있는 하위 유형은 다음과 같습니다.</p>
<p>1: InterfaceAlias</p>
<p>5: InterfaceName</p>
<p>7: LocallyAssigned</p></td>
</tr>
<tr class="even">
<td><p><em>RegistrarPort</em></p></td>
<td><p>선택</p></td>
<td><p>Int32</p></td>
<td><p>등록자 서비스의 포트 번호입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Subnet</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>서브넷의 IP 주소입니다. 이 값은 IPv4 주소(192.0.2.0과 같이 마침표로 숫자 구분)로 입력되어야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>UserSipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>원격 사용자의 SIP 주소입니다.</p>
<p>이 매개 변수의 값을 지정하는 경우 TargetFqdn 또는 TargetUri 매개 변수도 필수입니다.</p>
<p>가상 트랜잭션 사용자를 설정하지 않은 경우 TargetFqdn 매개 변수만 지정하면 이 매개 변수가 필요합니다. 가상 트랜잭션 사용자가 설정되었는지 확인하려면 <strong>Get-CsHealthMonitoringConfiguration</strong> cmdlet을 실행합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WebCredential</em></p></td>
<td><p>선택</p></td>
<td><p>PS 자격 증명</p></td>
<td><p>위치 정보 서비스에 액세스하기 위한 사용자 자격 증명이 포함된 개체입니다. 이 개체는 <strong>Get-Credential</strong> cmdlet을 호출하고 적절한 자격 증명을 제공하면 검색할 수 있습니다.</p>
<p>TargetUri 및 UserSipAddress 매개 변수를 지정한 경우 명령을 실행하는 컴퓨터에 서버 인증서가 없으면 이 매개 변수가 필요합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

**Test-CsLisConfiguration** cmdlet은 Microsoft.Rtc.SyntheticTransactions.TaskOutput 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Debug-CsLisConfiguration](debug-cslisconfiguration.md)  
[Publish-CsLisConfiguration](publish-cslisconfiguration.md)  
[Unpublish-CsLisConfiguration](unpublish-cslisconfiguration.md)  
[Import-CsLisConfiguration](import-cslisconfiguration.md)  
[Export-CsLisConfiguration](export-cslisconfiguration.md)

