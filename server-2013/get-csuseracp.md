---
title: Get-CsUserAcp
TOCTitle: Get-CsUserAcp
ms:assetid: de65eafe-e306-4ada-8509-9688e81491f9
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398978(v=OCS.15)
ms:contentKeyID: 49305262
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsUserAcp

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자 또는 사용자 그룹에 할당된 오디오 회의 공급자에 대한 정보를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsUserAcp [-Identity <UserIdParameter>] [-Credential <PSCredential>] [-Filter <String>] [-LdapFilter <String>] [-ResultSize <Unlimited>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직의 모든 사용자에 대한 오디오 회의 공급자 정보를 반환합니다.

    Get-CsUserAcp

## 예제 2

예제 2에서는 ID가 Ken Myer인 단일 사용자에 대한 오디오 회의 공급자 정보를 반환합니다. 이 경우 ID는 사용자의 Active Directory 표시 이름을 사용하여 지정합니다.

    Get-CsUserAcp -Identity "Ken Myer"

## 예제 3

예제 3에서는 하나 이상의 오디오 회의 공급자가 할당된 모든 사용자에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 필터 값 {AcpInfo –ne $Null}과 함께 Filter 매개 변수를 포함합니다. 이 필터 값은 반환되는 데이터를 AcpInfo 속성 값이 null 값과 같지 않은 사용자로 제한합니다. 오디오 회의 공급자가 할당되지 않은 사용자에 대한 정보를 반환하려면 다음 필터 값을 사용합니다.

{AcpInfo –eq $Null}

    Get-CsUserAcp -Filter {AcpInfo -ne $Null}

## 예제 4

예제 4에서는 오디오 회의 공급자 Fabrikam ACP가 할당된 사용자에 대한 오디오 회의 공급자 정보를 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsUserAcp** cmdlet을 사용하여 조직의 모든 사용자에 대한 오디오 회의 공급자 정보를 반환합니다. 이 정보는 AcpInfo 속성에 문자열 값 "Fabrikam ACP"가 포함된(-match) 사용자를 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsUserAcp | Where-Object {$_.AcpInfo -match "Fabrikam ACP"}

## 예제 5

예제 5에서는 사용자 Ken Myer에게 할당된 오디오 회의 공급자에 대한 자세한 정보를 표시합니다. 이 작업을 수행하기 위해 먼저 **Get-CsUserAcp** cmdlet을 호출하여 Ken Myer에 대한 오디오 회의 공급자 정보를 반환합니다. 이 데이터는 ExpandProperty 매개 변수를 사용하여 AcpInfo 속성 값을 "확장"하는 **Select-Object** cmdlet에 파이프됩니다. 속성 값이 확장된다는 것은 해당 값에 저장된 모든 정보가 읽기 쉬운 형식으로 표시된다는 것을 의미합니다.

    Get-CsUserAcp -Identity "Ken Myer" | Select-Object -ExpandProperty AcpInfo

## 자세한 정보

오디오 회의 공급자는 조직에 회의 서비스를 제공하는 타회사입니다. 특히, 외부에 있거나 회사 네트워크 또는 인터넷에 연결되지 않은 사용자는 오디오 회의 공급자를 통해 회의 또는 모임의 오디오 부분에 참여할 수 있습니다. 오디오 회의 공급자는 실시간 번역, 기록 및 회의별 실시간 운영자 지원과 같은 최고의 서비스를 제공합니다.

Lync Server는 오디오 회의 공급자와의 완전한 통합을 허용하지 않습니다. **CsUserAcp** cmdlet을 통해 관리자는 전화 번호 및 암호를 설정하고, 사용자가 모임을 예약할 때마다 오디오 회의 공급자 통합에 사용할 수 있는 기타 정보를 구성할 수 있습니다. 그러나 이러한 cmdlet은 온-프레미스 버전의 Lync Server용으로 고안된 것이 아니고 원래 Lync Online에서 사용하도록 만들어진 것이므로 속성 값 할당 외에 추가 오디오 회의 공급자 통합이 제공되지 않습니다.

**Get-CsUserAcp** cmdlet을 사용하면 사용자 또는 사용자 그룹에 할당된 오디오 회의 공급자에 대한 정보를 반환할 수 있습니다. 단일 사용자에 대한 오디오 회의 공급자 정보를 반환하려면 Identity 매개 변수 뒤에 정보를 반환할 사용자의 ID를 포함하기만 하면 됩니다. 여러 사용자에 대한 정보를 반환하려는 경우에는 LdapFilter 또는 Filter 매개 변수를 사용할 수 있습니다. LdapFilter 매개 변수를 사용하면 사용자 계정 정보를 지정할 때 Department나 Title과 같은 일반 Active Directory 특성을 사용할 수 있습니다. 예를 들어 "Title=Accountant" 매개 변수 값은 반환되는 정보를 직함이 Accountant인 사용자로 제한합니다. Filter 매개 변수를 사용하면 Lync Server 관련 특성(예: VoicePolicy 또는 EnterpriseVoiceEnabled)을 사용하여 반환되는 데이터를 필터링할 수 있습니다. 예를 들어 필터 값 {EnterpriseVoiceEnabled –eq $True}는 **Get-CsUserAcp** cmdlet에서 반환하는 사용자 계정을 Enterprise Voice에 대해 활성화된 사용자로 제한합니다.

또는 매개 변수 없이 **Get-CsUserAcp** cmdlet을 호출하여 모든 사용자에 대한 오디오 회의 공급자 정보를 반환할 수 있습니다. **Get-CsUserAcp** cmdlet은 Lync Server에 대해 활성화되지 않은 사용자를 포함하여 모든 사용자에 대한 오디오 회의 공급자 정보를 반환합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalReadOnlyAdmins 그룹의 구성원은 **Get-CsUserAcp** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsUserAcp"}

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
<td><p><em>Credential</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSCredential</p></td>
<td><p>대체 자격 증명으로 <strong>Get-CsUserAcp</strong> cmdlet을 실행하는 데 사용됩니다. Windows에 로그온하는 데 사용한 계정에 연락처 개체를 사용하는 데 필요한 권한이 없는 경우 이 기능이 필요할 수 있습니다.</p>
<p>Credential 매개 변수를 사용하려면 먼저 <strong>Get-Credential</strong> cmdlet을 사용하여 PSCredential 개체를 만들어야 합니다. 자세한 내용은 <strong>Get-Credential</strong> cmdlet 도움말 항목을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>Lync Server 관련 특성을 필터링하여 반환된 데이터를 제한하는 데 사용됩니다. 예를 들어 특정 음성 정책이 할당된 사용자 또는 특정 음성 정책이 할당되지 않은 사용자에 대한 데이터만 반환하도록 제한할 수 있습니다.</p>
<p>Filter 매개 변수는 <strong>Where-Object</strong> cmdlet에 사용되는 구문과 동일한 Windows PowerShell 필터링 구문을 사용합니다. 예를 들어 Enterprise Voice를 사용하도록 설정된 사용자만 반환하는 필터는 다음과 유사한 형태입니다. 여기서 EnterpriseVoiceEnabled는 Active Directory 도메인 서비스 특성을 나타내고 -eq는 비교 연산자(같음)를 나타내며 $True(기본 제공 Windows PowerShell 변수)는 필터 값을 나타냅니다.</p>
<p>{EnterpriseVoiceEnabled -eq $True}</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>검색할 사용자 계정의 ID를 나타냅니다. 사용자 ID는 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 사용자의 SIP 주소, 2) 사용자의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그온 이름(예: litwareinc\kenmyer) 그리고 4) 사용자의 Active Directory 도메인 서비스 표시 이름(예: Ken Myer)입니다. 또한 사용자의 Active Directory 고유 이름을 사용하여 사용자 계정을 참조할 수도 있습니다.</p>
<p>표시 이름을 사용자 ID로 사용할 경우 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어 ID &quot;* Smith&quot;는 표시 이름이 문자열 값 &quot; Smith&quot;로 끝나는 모든 사용자를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>LdapFilter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>일반 Active Directory 특성(즉, Lync Server와 관련되지 않은 특성)을 필터링하여 반환되는 데이터를 제한할 수 있습니다. 예를 들어 특정 부서에서 일하는 사용자나 지정된 관리자 또는 직위를 가진 사용자에 대한 데이터만 반환하도록 제한할 수 있습니다.</p>
<p>필터를 만들 때 LdapFilter 매개 변수는 LDAP 쿼리 언어를 사용합니다. 예를 들어, Redmond 도시에 일하는 사용자만 반환하는 필터는 &quot;l&quot;(소문자 L)을 사용하여 &quot;l=Redmond&quot;와 같이 나타납니다. 여기서 &quot;l&quot;는 Active Directory 특성(구/군/시)을 나타내고 &quot;=&quot;는 비교 연산자(같음)를 나타내며 &quot;Redmond&quot;는 필터 값을 나타냅니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ResultSize</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.Unlimited</p></td>
<td><p>명령에서 반환되는 레코드 수를 제한하는 데 사용됩니다. 예를 들어, 포리스트에 있는 사용자 수에 상관없이 7명의 사용자만 반환하려면 ResultSize 매개 변수를 포함하고 매개 변수 값을 7로 설정합니다. 반환될 7명의 사용자를 지정하는 방법은 없습니다. ResultSize를 7로 설정했지만 포리스트에 사용자가 3명만 있는 경우 3명의 사용자가 반환된 다음, 오류 없이 완료됩니다.</p>
<p>결과 크기는 0-2147483647(포함) 사이의 임의 정수로 설정할 수 있습니다. 0으로 설정할 경우 명령이 실행되지만 데이터가 반환되지 않습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

문자열. **Get-CsUserAcp** cmdlet은 Lync Server를 사용하도록 설정된 사용자 계정의 ID를 나타내는 파이프라인된 문자열 값을 허용합니다.

## 반환 형식

**Get-CsUserAcp** cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.ADUserAcp 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Remove-CsUserAcp](remove-csuseracp.md)  
[Set-CsUserAcp](set-csuseracp.md)

