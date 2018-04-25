---
title: Test-CsPhoneBootstrap
TOCTitle: Test-CsPhoneBootstrap
ms:assetid: b132446b-f264-405e-8e3a-971ab1c37694
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412852(v=OCS.15)
ms:contentKeyID: 49304749
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsPhoneBootstrap

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자가 Lync Phone Edition 호환 장치를 사용하여 Lync Server에 로그온할 수 있는지 확인합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Test-CsPhoneBootstrap -PhoneOrExt <String> -PIN <String> [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] [-TargetUri <String>] [-UserSipAddress <String>]

## 예제

## 예제 1

예제 1에 표시된 명령은 지정된 전화 번호 및 PIN을 가진 사용자가 Lync Phone Edition 호환 장치를 사용하여 Lync Server에 연결할 수 있는지 확인합니다. 테스트를 실행하려면 사용자의 전화 번호(+14255551219) 및 PIN(0712)을 제공해야 합니다.

    Test-CsPhoneBootstrap -PhoneOrExt "+14255551219" -Pin "0712"

## 예제 2

예제 2에서는 지정된 전화 번호 및 PIN을 가진 사용자가 Lync Phone Edition 호환 장치를 사용하여 Lync Server에 연결할 수 있는지 확인합니다. 이 예제에서는 UserSipAddress 매개 변수가 추가 검사로 포함됩니다. SIP 주소를 가진 사용자가 지정된 전화 번호 및 PIN을 가진 사용자와 다른 경우 테스트가 실패하게 됩니다.

    Test-CsPhoneBootstrap -PhoneOrExt "+14255551219" -Pin "0712" -UserSipAddress "sip:kenmyer@litwareinc.com"

## 자세한 정보

Lync Server에 연결하려면 Lync Phone Edition 호환 장치는 DHCP(Dynamic Host Configuration Protocol)를 사용하여 Lync Server 등록자의 주소를 검색해야 합니다. 이러한 장치는 또한 유효한 전화 번호 및 관련 개인식별번호(PIN)를 제공해야 시스템의 인증을 받을 수 있습니다. 이 프로세스를 부트스트랩이라고 합니다. **Test-CsPhoneBootstrap** cmdlet을 사용하여 관리자는 특정 사용자가 자신에게 할당된 전화 번호 및 PIN을 사용하여 Lync Phone Edition 호환 장치에서 시스템에 로그온할 수 있는지 확인할 수 있습니다. 테스트를 실행하는 데 실제로 장치가 필요하지는 않습니다.

**Test-CsPhoneBootstrap** cmdlet에서 확인하기 위해서는 테스트할 사용자 계정을 호스트하는 등록자 풀을 DHCP를 사용하여 검색할 수 있어야 합니다. 이 방법으로 등록자를 검색할 수 있는지 확인하려면 [Get-CsRegistrarConfiguration](get-csregistrarconfiguration.md) cmdlet을 사용하여 EnableDHCPServer 속성 값을 확인하십시오. 이 속성이 False로 설정되어 있으면 [Set-CsRegistrarConfiguration](set-csregistrarconfiguration.md) cmdlet을 사용하여 속성 값을 True로 설정하고 DHCP를 사용하여 등록자를 검색할 수 있도록 해야 합니다. 또한 Enterprise DHCP Server를 사용하고 Lync Server 관련 옵션을 구성하여 이 작업을 수행할 수도 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsPhoneBootstrap"}

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
<td><p><em>PhoneOrExt</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>테스트할 사용자 계정의 전화 번호 또는 내선 번호입니다(예: -PhoneOrExt &quot;+14255551219&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>PIN</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>테스트할 사용자 계정의 PIN입니다.</p></td>
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
<td><p><em>TargetFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>테스트할 사용자 계정을 호스트하는 등록자 풀의 FQDN(정규화된 도메인 이름)입니다. 지정하지 않을 경우 등록자 풀을 찾는 데 DHCP 검색이 사용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>TargetUri</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>인증서 프로비전 서비스의 URL입니다. 이 매개 변수를 포함하지 않을 경우 대상 URI를 찾는 데 DHCP 검색이 사용됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserSipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>텍스트에 사용되는 사용자 계정의 SIP 주소입니다(예: -UserSipAddress &quot;sip:kenmyer@litwareinc.com&quot;). UserSipAddress 매개 변수는 제공된 전화 번호 및 PIN을 참조해야 합니다. 포함된 전화 번호 및 PIN이 UserSipAddress 매개 변수에 의해 지정된 사용자에게 속하지 않는 경우 테스트가 실패하게 됩니다. SIP 주소는 &quot;sip:&quot; 접두사로 시작해야 합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Test-CsPhoneBootstrap** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Test-CsPhoneBootstrap** cmdlet은 Microsoft.Rtc.SyntheticTransactions.TaskOutput 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Test-CsRegistration](test-csregistration.md)

