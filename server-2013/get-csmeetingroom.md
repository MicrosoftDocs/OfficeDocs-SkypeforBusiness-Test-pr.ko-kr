---
title: Get-CsMeetingRoom
TOCTitle: Get-CsMeetingRoom
ms:assetid: ce361cb8-042c-4708-8f9c-7e67a34a570d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205277(v=OCS.15)
ms:contentKeyID: 49305067
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsMeetingRoom

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 모든 Lync Server 2013 회의실에 대한 정보를 반환합니다. 회의실은 소규모 회의 공간의 비디오 회의 및 공동 작업 시나리오를 진행할 수 있도록 설계된 회의 장치입니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Get-CsMeetingRoom [-Identity <UserIdParameter>] [-Credential <PSCredential>] [-DomainController <Fqdn>] [-Filter <String>] [-LdapFilter <String>] [-OU <OUIdParameter>] [-ResultSize <Unlimited>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 사용하도록 구성된 모든 회의실에 대한 정보를 반환합니다.

    Get-CsMeetingRoom

## 예제 2

예제 2에서는 단일 회의실, 즉 SIP 주소가 sip:RedmondMeetingRoom@litwareinc.com인 시스템에 대한 정보를 반환합니다.

    Get-CsMeetingRoom -Identity "sip:RedmondMeetingRoom@litwareinc.com"

## 예제 3

예제 3에 표시된 명령은 사용자별 음성 정책 RedmondVoicePolicy가 할당된 모든 회의실에 대한 정보를 반환합니다. 이를 위해 명령에 Filter 매개 변수 및 필터 값 {VoicePolicy -eq "RedmondVoicePolicy}를 포함합니다. 이 필터 값은 반환되는 데이터를 VoicePolicy 속성이 RedmondVoicePolicy인(-eq) 회의실로 제한합니다.

    Get-CsMeetingRoom -Filter {VoicePolicy -eq "RedmondVoicePolicy"}

## 자세한 정보

Lync Server에서 회의실은 회의 공간에 설치되며 다음과 같은 고급 모임 기능을 제공하는 자체 포함 컴퓨터 장비입니다.

  - 원터치 방식 모임 참가 환경

  - 다중 뷰 비디오 갤러리

  - 회의실 화면 전면의 터치 가능 화이트보드

  - 예약된 모임 액세스 제공을 위한 일정 통합

  - 콘텐츠 공유 및 전환

이와 같은 새로운 끝점 장치를 관리하려면 먼저 장치에 대해 Microsoft Exchange Server 2013 리소스 사서함 계정을 만들고 사용하도록 설정한 다음 Lync Server 2013에 대해 해당 리소스 계정을 사용하도록 설정해야 합니다. Lync Server의 경우에는 회의실을 만들거나 제거하는 데 사용할 수 있는 cmdlet이 없습니다. 대신 [Enable-CsMeetingRoom](enable-csmeetingroom.md) cmdlet을 사용하여 회의실을 사용하도록 설정하고 [Disable-CsMeetingRoom](disable-csmeetingroom.md) cmdlet을 사용하여 회의실을 사용하지 않도록 설정합니다. 리소스 계정이 있어야 회의실을 사용하도록 설정할 수 있으며, 회의실을 사용하지 않도록 설정하면 해당 회의실이 회의실 컬렉션에서만 제거되며 리소스 사서함 계정이 삭제되지는 않습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsMeetingRoom"}

**Lync Server 제어판:** **Get-CsMeetingRoom** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p>대체 자격 증명으로 <strong>Get-CsMeetingRoom</strong> cmdlet을 실행하는 데 사용됩니다. Windows에 로그온하는 데 사용한 계정에 연락처 개체를 사용하는 데 필요한 권한이 없는 경우 이 기능이 필요할 수 있습니다.</p>
<p>Credential 매개 변수를 사용하려면 먼저 <strong>Get-Credential</strong> cmdlet을 사용하여 PSCredential 개체를 만들어야 합니다. 자세한 내용은 <strong>Get-Credential</strong> cmdlet 도움말 항목을 참조하십시오.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>회의실 정보를 검색하기 위해 지정된 도메인 컨트롤러에 연결하는 데 사용됩니다. 특정 도메인 컨트롤러에 연결하려면 DomainController 매개 변수 뒤에 컴퓨터 이름(예: atl-dc-001) 또는 FQDN(정규화된 도메인 이름)(예: atl-dc-001.litwareinc.com)을 포함합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>Lync Server 관련 특성을 필터링하여 반환된 데이터를 제한할 수 있습니다. 예를 들어, 특정 음성 정책이 할당된 회의실 또는 특정 음성 정책이 할당되지 않은 회의실에 대한 데이터만 반환하도록 제한할 수 있습니다.</p>
<p>Filter 매개 변수는 Where-Object cmdlet에 사용되는 구문과 거의 동일한 Windows PowerShell 필터링 구문을 사용합니다. 예를 들어 RedmondVoicePolicy 음성 정책이 할당된 회의실만 반환하는 필터는 다음과 같습니다.</p>
<p>{VoicePolicy -eq &quot;RedmondVoicePolicy&quot;}</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>검색할 회의실의 ID를 나타냅니다. 회의실 ID는 보통 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 회의실의 SIP 주소, 2) 회의실의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 회의실의 도메인 이름 및 로그온 이름(예: litwareinc\room14) 및 4) 회의실의 Active Directory 표시 이름(예: Room 14)입니다.</p>
<p>또한 회의실의 Active Directory 고유 이름을 사용하여 회의실 계정을 참조할 수도 있습니다.</p>
<p>표시 이름을 회의실 ID로 사용할 경우 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어 &quot;*Redmond*&quot;라는 ID는 표시 이름이 &quot;Redmond&quot; 문자열 값을 포함하는 모든 회의실을 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LdapFilter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>일반 Active Directory 특성(즉, Lync Server와 관련되지 않은 특성)을 필터링하여 반환되는 데이터를 제한할 수 있습니다. 예를 들어 반환되는 데이터를 특정 부서에 속하는 회의실로 제한할 수 있습니다. LdapFilter 매개 변수는 필터를 만들 때 LDAP 쿼리 언어를 사용합니다. 예를 들어 Redmond 시의 회의실만 반환하는 필터는 다음과 같습니다.</p>
<p>-LdapFilter &quot;l=Redmond&quot;</p>
<p>해당 구문에서 &quot;l&quot;(소문자 L)은 Active Directory 특성(locality)을 나타내고 &quot;=&quot;는 비교 연산자(같음)를 나타내며 &quot;Redmond&quot;는 필터 값을 나타냅니다.</p></td>
</tr>
<tr class="even">
<td><p><em>OU</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.AD.OUIdParameter</p></td>
<td><p>특정 OU(조직 구성 단위) 또는 컨테이너의 회의실에 대한 정보를 반환하는 데 사용됩니다. OU 매개 변수는 지정한 OU 및 모든 하위 OU의 데이터를 반환합니다. 예를 들어 Finance OU에 두 개의 하위 OU인 AccountsPayable 및 AccountsReceivable이 있는 경우 이러한 세 개의 각 OU에서 회의실이 반환됩니다.</p>
<p>OU를 지정할 때는 다음과 같이 해당 컨테이너에 대한 DN(고유 이름)을 사용합니다.</p>
<p>-OU &quot;OU=MeetingRooms,dc=litwareinc,dc=com&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>ResultSize</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.Unlimited</p></td>
<td><p>cmdlet에서 반환되는 레코드 수를 제한할 수 있습니다. 예를 들어 포리스트에 있는 회의실 수에 상관없이 7개의 회의실을 반환하려면 ResultSize 매개 변수를 포함하고 매개 변수 값을 7로 설정합니다. 반환될 7개의 회의실을 지정하는 방법은 없습니다.</p>
<p>결과 크기는 0에서 2147483647(포함) 사이의 임의 정수로 설정할 수 있습니다. 0으로 설정할 경우 명령이 실행되지만 데이터가 반환되지 않습니다. ResultSize를 7로 설정했지만 포리스트에 회의실이 3개만 있는 경우 3개의 회의실이 반환된 다음 오류 없이 완료됩니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

문자열. **Get-CsMeetingRoom** cmdlet은 Lync Server 2013 회의실로 사용하도록 설정된 사용자 계정의 ID를 나타내는 파이프라인된 문자열 값을 허용합니다.

## 반환 형식

**Get-CsMeetingRoom** cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.OCSADMeetingRoom 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Disable-CsMeetingRoom](disable-csmeetingroom.md)  
[Enable-CsMeetingRoom](enable-csmeetingroom.md)  
[Move-CsMeetingRoom](move-csmeetingroom.md)  
[Set-CsMeetingRoom](set-csmeetingroom.md)

