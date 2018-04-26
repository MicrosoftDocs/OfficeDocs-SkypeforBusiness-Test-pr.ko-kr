---
title: Debug-CsAddressBookReplication
TOCTitle: Debug-CsAddressBookReplication
ms:assetid: c138f274-7a1f-4074-b6a2-548274af5199
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205232(v=OCS.15)
ms:contentKeyID: 49304926
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Debug-CsAddressBookReplication

 

_**마지막으로 수정된 항목:** 2015-03-09_

Active Directory 및 Lync Server 2013 주소록 서비스 간의 복제를 확인합니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Debug-CsAddressBookReplication [-DomainController <String>] [-User <String>] [-VerifyReplication <SwitchParameter>] [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>] [-PoolFqdn <Fqdn>] [-VerifyNormalization <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 현재 풀에 대해 주소록 복제를 확인합니다. 지정된 풀에 대한 복제를 확인하려면 PoolFqdn 매개 변수와 확인할 풀의 정규화된 도메인 이름을 차례로 포함합니다.

    Debug-CsAddressBookReplication

## 예제 2

예제 2에서는 현재 풀에 대해 주소록 복제를 확인할 때 User 매개 변수를 포함합니다. User 매개 변수를 포함하면 지정된 사용자에 대한 관련 정보가 추가로 반환됩니다.

    Debug-CsAddressBookReplication -User "sip:kenmyer@litwareinc.com"

## 예제 3

예제 3에서는 VerifyReplication 매개 변수를 사용하여 지정된 사용자 계정을 변경한 후에 해당 변경 내용을 주소록으로 복제할 수 있는지 확인합니다.

    Debug-CsAddressBookReplication -User "sip:kenmyer@litwareinc.com" -VerifyReplication 

## 예제 4

예제 4에 표시된 명령은 VerifyNormalization 매개 변수를 사용하여 주소록 정규화 규칙을 적용할 수 없는 사용자 계정에 대한 정보를 반환합니다.

    Debug-CsAddressBookReplication -VerifyNormalization

## 자세한 정보

주소록 서버는 AD DS(Active Directory 도메인 서비스)와 Microsoft Lync Server 사이의 중재자입니다. 주소록 서버를 사용하면 Lync Server에 저장된 사용자 정보와 AD DS에 저장된 사용자 정보가 동기화됩니다. 이 작업은 주소록 파일을 사용자 데이터베이스에 저장된 정보와 주기적으로 동기화하는 방식으로 수행됩니다.

관리자는 **Debug-CsAddressBookReplication** cmdlet을 사용하여 Active Directory와 Lync Server 간에 데이터가 복제되고 있는지 확인할 수 있습니다. Active Directory와 주소록 서버 간에 복제를 완전하게 테스트하려면 시간이 많이 걸리고 리소스가 많이 사용될 수 있습니다. 따라서 **Debug-CsAddressBookReplication**은 문제 해결 시나리오에서만 사용하는 것이 좋습니다. 주소록 서버의 작동을 주기적으로 확인하려는 경우에는 **Test-CsAddressBookService** cmdlet 및/또는 **Test-CsAddressBookWebQuery** cmdlet을 대신 사용해야 합니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Debug-CsAddressBookReplication"}

**Lync Server 제어판:** D**ebug-CsAddressBookReplication** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>주소록 복제를 확인할 때 연결할 도메인 컨트롤러를 지정할 수 있습니다. 이 매개 변수를 포함하지 않으면 cmdlet이 사용 가능한 첫 번째 도메인 컨트롤러를 사용합니다.</p></td>
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
<p>참고: 변수 이름을 지정할 때 $ 문자를 추가해서는 안 됩니다.</p>
<p>로거 변수에 저장된 정보를 HTML 파일에 저장하려면 다음 명령을 사용합니다.</p>
<p>$TestOutput.ToHTML() &gt; C:\Logs\TestOutput.html</p>
<p>로거 변수에 저장된 정보를 XML 파일에 저장하려면 다음 명령을 사용합니다.</p>
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
<td><p><em>PoolFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>확인할 풀의 정규화된 도메인 이름입니다. 이 매개 변수를 포함하지 않으면 <strong>Debug-CsAddressBookReplication</strong> cmdlet이 현재 풀을 확인합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>User</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 매개 변수를 포함하면 지정된 사용자 계정에 대한 상세 복제 정보를 반환합니다. 사용자의 SIP 주소, 전자 메일 주소 또는 SamAccountName를 사용하여 확인할 사용자 계정을 지정할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>VerifyNormalization</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 지정하면 주소록 정규화가 실패한 사용자 계정에 대한 상세 정보를 반환합니다. 정규화 규칙은 전화 번호를 Lync Server 2013에서 사용하는 E.164 형식으로 변환하는 데 사용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>VerifyReplication</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 지정하면 <strong>Debug-CsAddressBookReplication</strong> cmdlet이 Active Directory에서 지정된 사용자 계정을 수정한 다음 변경 내용이 주소록으로 복제되었는지 확인합니다. 사용자 계정은 테스트용으로만 수정되며 해당 계정의 속성 값이 실제로 변경되지는 않습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Debug-CsAddressBookReplication** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Debug-CsAddressBookReplication** cmdlet은 Microsoft.Rtc.SyntheticTransactions.Activities.Database.AddressBookReplicationTaskOutput 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Test-CsAddressBookService](test-csaddressbookservice.md)  
[Test-CsAddressBookWebQuery](test-csaddressbookwebquery.md)

