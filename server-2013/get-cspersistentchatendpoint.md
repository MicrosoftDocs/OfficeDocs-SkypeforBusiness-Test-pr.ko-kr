---
title: Get-CsPersistentChatEndpoint
TOCTitle: Get-CsPersistentChatEndpoint
ms:assetid: 2c37edd6-6892-4b2d-8586-6f59ab668d4b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204764(v=OCS.15)
ms:contentKeyID: 49303153
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsPersistentChatEndpoint

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 영구 채팅 끝점에 대한 정보를 반환합니다. 영구 채팅 끝점은 Lync Server 2013 영구 채팅 풀의 URL을 제공하는 Active Directory 대화 상대 개체입니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsPersistentChatEndpoint [-Identity <UserIdParameter>] [-Credential <PSCredential>] [-DomainController <Fqdn>] [-Filter <String>] [-LdapFilter <String>] [-OU <OUIdParameter>] [-PersistentChatPoolFqdn <Fqdn>] [-ResultSize <Unlimited>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 사용하도록 구성된 모든 영구 채팅 끝점에 대한 정보를 반환합니다.

    Get-CsPersistentChatEndpoint

## 예제 2

예제 2에서는 Filter 매개 변수를 사용하여 ID가 "sip:pce@litwareinc.com"인 영구 채팅 끝점에 대한 정보를 반환합니다. 여기서는 SIP 주소가 ID로 사용됩니다.

    Get-CsPersistentChatEndpoint -Identity "sip:pce@litwareinc.com"

## 예제 3

예제 3에서는 영구 채팅 풀 atl-pcpool-001.litwareinc.com에서 사용하도록 구성된 모든 영구 채팅 끝점에 대한 정보를 반환합니다. 이 작업은 PoolFqdn 매개 변수 뒤에 영구 채팅 풀의 정규화된 도메인 이름을 붙여서 포함하는 방법으로 수행합니다.

    Get-CsPersistentChatEndpoint -PersistentChatPoolFqdn atl-pcpool-001.litwareinc.com

## 자세한 정보

Microsoft Lync Server 2010에서 사용되었던 그룹 채팅 서비스 대신 제공되는 영구 채팅 서비스를 사용하는 조직에서는 인터넷 토론 포럼과 비슷한 메시징 및 공동 작업 기능을 사용할 수 있습니다. 사용자는 실시간으로 메시지를 교환하는 동시에 언제든지 대화를 다시 방문하여 다시 시작할 수 있습니다. 특정 주제에 대해 대화를 할 수 있으며, 해당 대화를 모든 사용자가 확인할 수 있도록 하거나 선택한 사용자 집합만 확인하도록 할 수 있습니다. 마찬가지로 개별 채팅방도 누구나 메시지를 게시할 수 있도록 구성하거나 지정된 발표자만 메시지를 게시하도록 구성할 수 있습니다.

영구 채팅 서비스를 설치하면 각 영구 채팅 풀에 대해 끝점이 자동으로 만들어집니다. 이 끝점은 풀 URI를 유지 관리하는 Active Directory 대화 상대 개체입니다. 모든 사용자가 Lync 2013을 실행하는 경우에는 이 끝점만 있으면 됩니다.

그러나 Microsoft Lync 2010 등의 레거시 클라이언트를 실행하는 사용자가 있는 경우 해당 사용자는 레거시 클라이언트가 풀을 가리키도록 지정할 때 기본 영구 채팅 URI를 사용하기가 어려울 수 있습니다. 이러한 경우 관리자는 [New-CsPersistentChatEndpoint](new-cspersistentchatendpoint.md) cmdlet을 사용하여 풀에 대해 추가 대화 상대 개체, 즉 확인 및 사용이 보다 간편한 URI를 제공하는 대화 상대 개체를 만들 수 있습니다. **Get-CsPersistentChatEndpoint** cmdlet을 사용하면 조직에서 사용하도록 구성된 모든 영구 채팅 끝점에 대한 정보를 반환할 수 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsPersistentChatEndpoint"}

**Lync Server 제어판:** **Get-CsPersistentChatEndpoint** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>Credential</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSCredential</p></td>
<td><p>대체 자격 증명으로 <strong>Get-CsPersistentChatEndpoint</strong> cmdlet을 실행할 수 있게 합니다. Windows에 로그온하는 데 사용한 계정에 사용자 개체를 사용하는 데 필요한 권한이 없는 경우 이 기능이 필요할 수 있습니다.</p>
<p>Credential 매개 변수를 사용하려면 먼저 <strong>Get-Credential</strong> cmdlet을 사용하여 PSCredential 개체를 만들어야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>사용자 정보를 검색하기 위해 지정한 도메인 컨트롤러에 연결할 수 있습니다. 특정 도메인 컨트롤러에 연결하려면 DomainController 매개 변수 뒤에 FQDN(정규화된 도메인 이름)을 포함합니다. 예를 들면 다음과 같습니다.</p>
<p>-DomainController &quot;atl-dc-001.litwareinc.com&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>Lync Server 관련 특성을 필터링하여 반환된 데이터를 제한할 수 있습니다. 예를 들어, 특정 음성 정책이 할당된 영구 채팅 끝점 또는 특정 음성 정책이 할당되지 않은 끝점에 대한 데이터만 반환하도록 제한할 수 있습니다.</p>
<p>Filter 매개 변수는 <strong>Where-Object</strong> cmdlet에 사용되는 것과 동일한 Windows PowerShell 필터링 구문을 사용합니다. 예를 들어 사용자별 회의 정책이 할당된 끝점만 반환하는 필터는 다음과 같이 표시됩니다. 여기서 ConferencingPolicy는 Active Directory 특성을 나타내고, -ne는 비교 연산자(같지 않음)를 나타내고, $Null(기본 제공 Windows PowerShell 변수)은 필터 값을 나타냅니다.</p>
<p>-Filter {ConferencingPolicy -ne $Null}</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>반환할 영구 채팅 끝점의 고유 식별자입니다. 끝점 ID는 보통 다음과 같이 끝점의 SIP 주소나 표시 이름을 사용하여 지정됩니다.</p>
<p>-Identity &quot;sip:pcEndpoint1@litwareinc.com&quot;</p>
<p>그러나 다음과 같이 끝점의 전체 ID를 사용할 수도 있습니다.</p>
<p>-Identity &quot;CN={33e5014b-dcba-46b5-9bf7-48f4d5fca69d}, CN=Application Contacts,CN=RTC Service,CN=Services,CN=Configuration,DC=litwareinc,DC=com&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>LdapFilter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>일반 Active Directory 특성(즉, Lync Server와 관련되지 않은 특성)을 필터링하여 반환되는 데이터를 제한할 수 있습니다. 영구 채팅 끝점에는 Lync Server 특성이 아닌 항목이 거의 없으므로 이 매개 변수는 최소한의 값으로 설정하면 됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>OU</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.AD.OUIdParameter</p></td>
<td><p>특정 OU(조직 구성 단위) 또는 컨테이너의 사용자 계정에 대한 정보를 반환할 수 있습니다. 새 영구 채팅 끝점은 모두 같은 Active Directory 컨테이너(ApplicationContacts/RTC Service/Services/Configuration)에서 만들어지므로 이 매개 변수는 최소한의 값으로 설정하면 됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PersistentChatPoolFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>영구 채팅 끝점과 연결된 영구 채팅 풀의 정규화된 도메인 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ResultSize</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.Unlimited</p></td>
<td><p>cmdlet에서 반환되는 레코드 수를 제한하는 데 사용됩니다. 예를 들어 포리스트에 있는 사용자 수에 상관없이 7명의 연락처를 반환하려면 ResultSize 매개 변수를 포함하고 매개 변수 값을 7로 설정합니다. 반환될 7명의 사용자를 지정하는 방법은 없습니다.</p>
<p>결과 크기는 0에서 2147483647(포함) 사이의 임의 정수로 설정할 수 있습니다. 0으로 설정할 경우 명령이 실행되지만 데이터가 반환되지 않습니다. ResultSize를 7로 설정했지만 포리스트에 연락처가 3개만 있는 경우 3개의 연락처가 반환된 다음 오류 없이 완료됩니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

문자열 값입니다. **Get-CsPersistentChatEndpoint** cmdlet은 영구 채팅 끝점의 SIP 주소 또는 ID를 나타내는 문자열 값을 허용합니다.

## 반환 형식

**Get-CsPersistentChatEndpoint** cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.OCSPersistentChatContact 클래스의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsPersistentChatEndpoint](new-cspersistentchatendpoint.md)  
[Remove-CsPersistentChatEndpoint](remove-cspersistentchatendpoint.md)

