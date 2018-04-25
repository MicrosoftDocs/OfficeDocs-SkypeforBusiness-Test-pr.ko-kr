---
title: Enable-CsMeetingRoom
TOCTitle: Enable-CsMeetingRoom
ms:assetid: 88af3267-80c5-46c0-aaef-135843b42a04
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205062(v=OCS.15)
ms:contentKeyID: 49304291
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Enable-CsMeetingRoom

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 2013 회의실을 사용하도록 설정합니다. 회의실은 소규모 회의 공간의 비디오 회의 및 공동 작업 시나리오를 진행할 수 있도록 설계된 회의 장치입니다. 회의실을 사용하도록 설정하려면 먼저 해당 시스템을 나타내는 Active Directory 사용자 계정을 만들어야 합니다. 회의실 개체는 사용자 계정을 기반으로 하지만 **Get-CsUser** cmdlet을 실행할 때는 표시되지 않습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Enable-CsMeetingRoom -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-HostingProviderProxyFqdn <Fqdn>] [-OriginatorSid <SecurityIdentifier>] [-PassThru <SwitchParameter>] [-ProxyPool <Fqdn>] [-RegistrarPool <Fqdn>] [-SipAddress <String>] [-SipAddressType <FirstLastName | EmailAddress | UserPrincipalName | SAMAccountName | None>] [-SipDomain <Fqdn>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID(여기서는 Active Directory 표시 이름)가 Redmond Meeting room인 회의실을 사용하도록 설정합니다. 새 회의실의 홈은 등록자 풀 arl-cs-001.litwareinc.com이며 SIP 주소 sip:RedmondMeetingRoom@litwareinc.com이 지정됩니다.

    Enable-CsMeetingRoom -Identity "Redmond Meeting room" -RegistrarPool "atl-cs-001.litwareinc.com" -SipAddress "sip:RedmondMeetingRoom@litwareinc.com"

## 예제 2

예제 2에서는 MeetingsRoom OU에 있는 모든 회의실을 사용하도록 설정합니다. 즉, 이 명령은 MeetingsRoom OU의 모든 사용자 계정을 사용하도록 설정합니다. 이 작업을 수행하기 위해 명령은 먼저 OU 매개 변수를 포함하여 **Get-CsAdUser** cmdlet을 호출합니다. 매개 변수 값 "OU=MeetingRooms,dc=litwareinc,dc=com"은 반환되는 데이터를 MeetingRooms OU에 있는 사용자 계정으로 제한합니다. 이러한 계정은 **Enable-CsMeetingRoom** cmdlet에 파이프되며, 해당 cmdlet은 컬렉션의 각 계정을 가져와 회의실로 사용하도록 설정합니다. 각각의 새 회의실에 대한 홈은 등록자 풀 atl-cs-001.litwareinc.com으로 지정되며 계정의 SamAccountName 매개 변수(예: room14) 및 SIP 도메인 litwareinc.com으로 구성된 SIP 주소가 지정됩니다.

    Get-CsAdUser -OU "OU=MeetingRooms,dc=litwareinc,dc=com" | Enable-CsMeetingRoom -RegistrarPool "atl-cs-001.litwareinc.com" -SipAddressType "SamAccountName" -SipDomain "litwareinc.com"

## 자세한 정보

Lync Server에서 회의실은 회의 공간에 설치되며 다음과 같은 고급 모임 기능을 제공하는 자체 포함 컴퓨터 장비입니다.

  - 원터치 방식 모임 참가 환경

  - 다중 뷰 비디오 갤러리

  - 회의실 화면 전면의 터치 가능 화이트보드

  - 예약된 모임 액세스 제공을 위한 일정 통합

  - 콘텐츠 공유 및 전환

이와 같은 새로운 끝점 장치를 관리하려면 먼저 장치에 대해 Microsoft Exchange Server 2013 리소스 사서함 계정을 만들고 사용하도록 설정한 다음 Lync Server 2013에 대해 해당 리소스 계정을 사용하도록 설정해야 합니다. Lync Server의 경우에는 회의실을 만들거나 제거하는 데 사용할 수 있는 cmdlet이 없습니다. 대신 **Enable-CsMeetingRoom** cmdlet을 사용하여 회의실을 사용하도록 설정하고 [Disable-CsMeetingRoom](disable-csmeetingroom.md) cmdlet을 사용하여 회의실을 사용하지 않도록 설정합니다. 리소스 계정이 있어야 회의실을 사용하도록 설정할 수 있으며, 회의실을 사용하지 않도록 설정하면 해당 회의실이 회의실 컬렉션에서만 제거되며 리소스 사서함 계정이 삭제되지는 않습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Enable-CsMeetingRoom"}

**Lync Server 제어판:** **Enable-CsMeetingRoom** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>회의실로 구성할 사용자 계정의 ID를 나타냅니다. 사용자 ID는 보통 네 가지 형식 중 하나를 사용하여 지정되는데, 이러한 형식은 1) 사용자의 SIP 주소, 2) 사용자의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그온 이름(예: litwareinc\room14) 및 4) 사용자의 Active Directory 표시 이름(예: Room 14)입니다.</p>
<p>또한 사용자의 Active Directory 고유 이름을 사용하여 사용자 계정을 참조할 수도 있습니다.</p>
<p>표시 이름을 사용자 ID로 사용할 경우 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어 &quot;* Smith&quot;라는 ID는 표시 이름이 &quot; Smith&quot; 문자열 값으로 끝나는 모든 사용자를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>회의실을 사용하도록 설정하기 위해 지정된 도메인 컨트롤러에 연결할 수 있도록 합니다. 특정 도메인 컨트롤러에 연결하려면 DomainController 매개 변수 뒤에 컴퓨터 이름(예: atl-dc-001) 또는 FQDN(정규화된 도메인 이름)(예: atl-dc-001.litwareinc.com)을 포함합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>HostingProviderProxyFqdn</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>호스팅 공급자 프록시 서버의 정규화된 도메인 이름입니다. 이 매개 변수는 Microsoft Lync Online에서만 사용할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>OriginatorSid</em></p></td>
<td><p>선택</p></td>
<td><p>System.Security.Principal.SecurityIdentifier</p></td>
<td><p>msRTCSIP-OriginatorSID 특성의 값입니다. 이 Active Directory 특성은 Single Sign-On을 사용하도록 설정하는 데만 사용됩니다. 이 매개 변수는 Microsoft Lync Online에서만 사용할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Lync Server에 대해 사용하도록 설정되는 회의실을 나타내는 파이프라인을 통해 회의실 개체를 전달할 수 있도록 합니다. 기본적으로 <strong>Enable-CsMeetingRoom</strong> cmdlet은 파이프라인을 통해 개체를 전달하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ProxyPool</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>프록시 풀 이름입니다. 이 매개 변수는 Microsoft Lync Online에서만 사용할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>RegistrarPool</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>회의실의 Lync Server 계정이 속하는 등록자 풀을 나타냅니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>회의실에 특정 SIP 주소를 할당할 수 있습니다. SIP 주소를 지정할 때 주소 앞에 접두사 &quot;sip:&quot;이 와야 합니다. 이는 SipAddress 매개 변수에 제공된 값이 다음과 같이 표시됨을 의미합니다.</p>
<p>sip:room14@litwareinc.com</p>
<p>Lync Server에서 회의실에 대해 SIP 주소를 자동으로 생성하도록 하려면 SipAddressType 매개 변수를 사용할 때 SipAddress 매개 변수를 사용하지 않아야 합니다.</p>
<p>여러 회의실을 동시에 사용하도록 설정하려는 경우에는 SipAddress 매개 변수를 사용할 수 없습니다. 대신 SipAddressType 매개 변수를 사용하여 이러한 회의실의 SIP 주소를 자동 생성해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SipAddressType</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.AD.Cmdlets.AddressType</p></td>
<td><p>새 회의실에 대한 SIP 주소를 자동으로 생성하도록 Lync Server에 명령합니다. Lync Server에서 SIP 주소를 자동으로 생성하도록 하려면 SipAddressType 매개 변수를 포함하고 다음 매개 변수 값 중 하나를 사용해야 합니다.</p>
<p>* FirstLastName. SIP 주소는 사용자의 이름, 마침표, 성, SIP 도메인을 순서대로 포함합니다. 예를 들어, 사용자 Room 14의 SIP 주소는 Room.14@litwareinc.com과 같습니다. 이 주소 형식을 사용하는 경우 SipDomain 매개 변수도 포함해야 합니다.</p>
<p>* EmailAddress. Active Directory에 정의된 사용자의 전자 메일 주소가 SIP 주소로 사용됩니다. 즉, 사용자의 UPN이 SIP 주소로 사용됩니다.</p>
<p></p>
<p>* SamAccountName. SIP 주소는 사용자의 SamAccountName(로그온 이름)과 SIP 도메인을 순서대로 포함합니다. 예를 들어 SamAccountName이 room14인 사용자의 SIP 주소는 room14@litwareinc.com과 같습니다. 이 주소 형식을 사용하는 경우 SipDomain 매개 변수도 포함해야 합니다.</p>
<p>SIPAddress 매개 변수를 사용하여 사용자에게 SIP 주소를 명시적으로 할당할 경우 SipAddressType 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SipDomain</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>사용하도록 설정할 회의실의 SIP 도메인입니다. SIPAddressType 매개 변수를 사용하여 Lync Server에서 사용자의 SIP 주소를 자동으로 생성하도록 하고 SIP 주소가 SamAccountName 또는 사용자의 이름과 성을 기반으로 할 경우 이 매개 변수가 필요합니다. SIP 주소가 사용자의 전자 메일 주소 또는 UPN을 기반으로 할 경우 도메인 이름이 이미 해당 특성 값에 포함되어 있기 때문에 이 매개 변수가 필요하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>실제로 명령을 수행하지는 않고 명령을 실행했을 때 발생할 결과에 대해 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

문자열 또는 Microsoft.Rtc.Management.ADConnect.Schema.ADUser 개체입니다. **Enable-CsMeetingRoom** cmdlet은 Lync Server에 대해 사용하도록 설정된 사용자 계정의 ID를 나타내는 파이프라인된 문자열 값을 허용합니다. 또한 Active Directory 사용자 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Enable-CsMeetingRoom** cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.OCSADMeetingRoom 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Disable-CsMeetingRoom](disable-csmeetingroom.md)  
[Get-CsMeetingRoom](get-csmeetingroom.md)  
[Move-CsMeetingRoom](move-csmeetingroom.md)  
[Set-CsMeetingRoom](set-csmeetingroom.md)

