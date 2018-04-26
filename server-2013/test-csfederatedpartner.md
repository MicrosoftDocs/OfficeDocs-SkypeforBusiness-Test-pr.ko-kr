---
title: Test-CsFederatedPartner
TOCTitle: Test-CsFederatedPartner
ms:assetid: 1f56bf80-37b4-4520-b8a5-da0740a894a2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398281(v=OCS.15)
ms:contentKeyID: 49303016
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsFederatedPartner

 

_**마지막으로 수정된 항목:** 2015-03-09_

페더레이션 도메인에 연결할 수 있는지 확인합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Test-CsFederatedPartner -Domain <String> -TargetFqdn <String> [-Certificate <X509Certificate2>] [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>] [-ProxyFqdn <String>]

## 예제

## 예제 1

예제 1에 표시된 명령은 로컬 액세스 프록시 서버(accessproxy.litwareinc.com)와 페더레이션 도메인 Fabrikam.com 간의 연결을 확인합니다.

    Test-CsFederatedPartner -TargetFqdn accessproxy.litwareinc.com -Domain fabrikam.com

## 예제 2

예제 2에서는 도메인과 Lync Server 푸시 알림 서비스 간의 연결을 테스트하는 방법을 보여 줍니다. 이 테스트에 성공하려면 이 서비스를 호스팅 공급자로 구성하고 push.lync.com을 허용 도메인 목록에 추가해 두어야 합니다. 자세한 내용은 [Lync Server 2013의 푸시 알림 구성](lync-server-2013-configuring-for-push-notifications.md)을 참고하세요.

    Test-CsFederatedPartner -TargetFqdn accessproxy.litwareinco.com -Domain push.lync.com -ProxyFqdn sipfed.online.lync.com

## 예제 3

예제 3에서는 허용 도메인 목록의 모든 도메인에 대한 연결이 확인됩니다. 이를 위해 명령은 먼저 Get-CsAllowedDomain cmdlet을 사용하여 모든 허용 도메인의 컬렉션을 검색합니다. 이 컬렉션은 ForEach-Object cmdlet에 파이프됩니다. 그러면 ForEach-Object가 컬렉션의 각 도메인에 대해 Test-CsFederatedPartner cmdlet을 실행합니다.

    Get-CsAllowedDomain | ForEach-Object {Test-CsFederatedPartner -TargetFqdn accessproxy.litwareinc.com -Domain $_.Identity}

## 자세한 정보

**Test-CsFederatedPartner**는 페더레이션 파트너의 도메인에 연결할 수 있는지 확인합니다. 도메인 연결을 확인하려면 해당 도메인이 허용되는 (페더레이션) 도메인 컬렉션에 표시되어야 합니다. **New-CsAllowedDomain** cmdlet을 사용하여 허용 목록에 도메인을 추가할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsFederatedPartner"}

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
<td><p><em>Domain</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>페더레이션 파트너의 FQDN(정규화된 도메인 이름)입니다. 예: -Domain &quot;fabrikam.com&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>TargetFqdn</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>조직에서 페더레이션 SIP 트래픽에 사용하는 액세스 프록시 서버의 FQDN입니다. TargetFqdn은 페더레이션 SIP 트래픽이 전달되는 프록시 서버의 내부 에지를 가리켜야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Certificate</em></p></td>
<td><p>선택</p></td>
<td><p>System.Security.Cryptography.X509Certificates.X509Certificate2</p></td>
<td><p>페더레이션 도메인에 연결할 때 인증을 위해 X509 인증서를 제공할 수 있습니다.</p></td>
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
<td><p><em>ProxyFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>페더레이션 조직에서 사용하는 액세스 프록시 서버의 FQDN입니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Test-CsFederatedPartner**는 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Test-CsFederatedPartner**는 Microsoft.Rtc.SyntheticTransactions.TaskOutput 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsAllowedDomain](get-csalloweddomain.md)

