---
title: Set-CsMeetingRoom
TOCTitle: Set-CsMeetingRoom
ms:assetid: 3dd02280-6407-4e17-929c-7070f8d1c3cf
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204831(v=OCS.15)
ms:contentKeyID: 49303402
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsMeetingRoom

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존Lync Server 2013 회의실의 속성 값을 수정합니다. 회의실은 소규모 회의 공간의 비디오 회의 및 공동 작업 시나리오를 진행할 수 있도록 설계된 회의 장치입니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Set-CsMeetingRoom -Identity <UserIdParameter> [-AcpInfo <MultiValuedProperty>] [-AudioVideoDisabled <$true | $false>] [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-Enabled <$true | $false>] [-EnterpriseVoiceEnabled <$true | $false>] [-ExchangeArchivingPolicy <Uninitialized | UseLyncArchivingPolicy | NoArchiving | ArchivingToExchange>] [-HostedVoiceMail <$true | $false>] [-LineServerURI <String>] [-LineURI <String>] [-PassThru <SwitchParameter>] [-PrivateLine <String>] [-RemoteCallControlTelephonyEnabled <$true | $false>] [-SipAddress <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 회의실 RedmondMeetingRoom에 할당된 LineUri를 업데이트합니다.

    Set-CsMeetingRoom -Identity "RedmondMeetingRoom" -LineUri "tel:+12065551219"

## 예제 2

예제 2에서는 회의실 RedmondMeetingRoom을 일시적으로 사용하지 않도록 설정합니다. 이 작업은 Enabled 속성을 False($False)로 설정하여 수행합니다.

    Set-CsMeetingRoom -Identity "RedmondMeetingRoom" -Enabled $False

회의실을 다시 사용하도록 설정하려면 Enabled 속성을 True($True)로 설정하면 됩니다.

    Set-CsMeetingRoom -Identity "RedmondMeetingRoom" -Enabled $True

## 예제 3

예제 3에서는 조직의 모든 회의실을 일시적으로 사용하지 않도록 설정합니다. 이를 위해 먼저 매개 변수 없이 **Get-CsMeetingRoom** cmdlet을 호출합니다. 그러면 사용 가능한 모든 회의실의 컬렉션이 반환됩니다. 이 컬렉션은 컬렉션의 각 회의실을 일시적으로 사용하지 않도록 설정하는 **Set-CsMeetingRoom** cmdlet에 파이프됩니다.

    Get-CsMeetingRoom | Set-CsMeetingRoom -Enabled $False

## 예제 4

예제 4에서는 조직의 모든 회의실이 Microsoft Exchange Server 보관이 아닌 Lync Server 2013 보관을 사용하도록 구성됩니다. 이 작업을 수행하기 위해 먼저 **Get-CsMeetingRoom** cmdlet을 사용하여 사용 가능한 모든 회의실의 컬렉션을 반환합니다. 해당 컬렉션은 ExchangeArchivingPolicy cmdlet을 사용하여 컬렉션의 각 회의실이 Lync Server 보관을 사용하도록 구성하는 **Set-CsMeetingRoom** cmdlet에 파이프됩니다.

    Get-CsMeetingRoom | Set-CsMeetingRoom -ExchangeArchivingPolicy "UseLyncArchivingPolicy"

## 자세한 정보

Lync Server에서 회의실은 회의 공간에 설치되며 다음과 같은 고급 모임 기능을 제공하는 자체 포함 컴퓨터 장비입니다.

  - 원터치 방식 모임 참가 환경

  - 다중 뷰 비디오 갤러리

  - 회의실 화면 전면의 터치 가능 화이트보드

  - 예약된 모임 액세스 제공을 위한 일정 통합

  - 콘텐츠 공유 및 전환

이와 같은 새로운 끝점 장치를 관리하려면 먼저 장치에 대해 Microsoft Exchange Server 2013 리소스 사서함 계정을 만들고 사용하도록 설정한 다음 Lync Server 2013에 대해 해당 리소스 계정을 사용하도록 설정해야 합니다. Lync Server의 경우에는 회의실을 만들거나 제거하는 데 사용할 수 있는 cmdlet이 없습니다. 대신 [Enable-CsMeetingRoom](enable-csmeetingroom.md) cmdlet을 사용하여 회의실을 사용하도록 설정하고 [Disable-CsMeetingRoom](disable-csmeetingroom.md) cmdlet을 사용하여 회의실을 사용하지 않도록 설정합니다. 리소스 계정이 있어야 회의실을 사용하도록 설정할 수 있으며, 회의실을 사용하지 않도록 설정하면 해당 회의실이 회의실 컬렉션에서만 제거되며 리소스 사서함 계정이 삭제되지는 않습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsMeetingRoom"}

Lync Server 제어판: **Set-CsMeetingRoom** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>사용자 ID 매개 변수</p></td>
<td><p>수정할 회의실의 ID를 나타냅니다. 회의실 ID는 보통 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 회의실의 SIP 주소, 2) 회의실의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 회의실의 도메인 이름 및 로그온 이름(예: litwareinc\room14) 및 4) 회의실의 Active Directory 표시 이름(예: Room 14)입니다. 또한 회의실의 Active Directory 고유 이름을 사용하여 회의실 계정을 참조할 수도 있습니다.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>AcpInfo</em></p></td>
<td><p>선택</p></td>
<td><p>다중값 속성</p></td>
<td><p>하나 이상의 타사 오디오 회의 공급자를 회의실에 할당할 수 있습니다. 그러나 오디오 회의 공급자를 할당할 때는 <strong>Set-UserAcp</strong> cmdlet을 사용하는 것이 좋습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AudioVideoDisabled</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>회의실에서 Lync 2013을 사용하여 A/V(음성/화상) 통화를 할 수 있는지 여부를 나타냅니다. True로 설정하면 회의실은 대부분 메신저 대화를 주고받는 것으로 제한됩니다.</p>
<p>회의실이 원격 통화 제어, Enterprise Voice 및/또는 IP-PBX(Internet Protocol Private Branch Exchange) 소프트 전화 경로 지정을 사용하도록 설정된 경우에는 A/V 통신을 사용하지 않도록 설정할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>FQDN</p></td>
<td><p>회의실 정보를 검색하기 위해 지정된 도메인 컨트롤러에 연결하는 데 사용됩니다. 특정 도메인 컨트롤러에 연결하려면 DomainController 매개 변수 뒤에 컴퓨터 이름(예: atl-dc-001) 또는 FQDN(정규화된 도메인 이름)(예: atl-dc-001.litwareinc.com)을 포함합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Enabled</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>회의실이 Lync Server 2013에 대해 사용하도록 설정되었는지 여부를 나타냅니다. 이 값을 False로 설정하면 회의실이 Lync Server에 더 이상 로그온할 수 없으며 이 값을 True로 설정하면 회의실의 로그온 권한이 다시 사용하도록 설정됩니다.</p>
<p>Enabled 매개 변수로 계정을 사용하지 않도록 설정한 경우 해당 계정과 연관된 정보(할당된 정책 및 회의실이 Enterprise Voice 및/또는 원격 통화 제어를 사용하도록 설정되어 있는지 여부)는 그대로 유지됩니다. 따라서 나중에 Enabled 매개 변수로 계정을 다시 사용하도록 설정하면 연관된 계정 정보가 복원됩니다. 이것은 <strong>Disable-CsMeetingRoom</strong> cmdlet을 통해 회의실 계정을 사용하지 않도록 설정하는 것과는 다릅니다. Disable-CsMeetingRoom을 실행할 경우 해당 계정과 연관된 Lync Server 데이터가 모두 삭제됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnterpriseVoiceEnabled</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>회의실이 Microsoft VoIP(Voice over Internet Protocol)인 Enterprise Voice를 사용하도록 설정되었는지 여부를 나타냅니다. Enterprise Voice를 사용하면 회의실에서 표준 전화 네트워크 대신 인터넷을 사용하여 전화를 걸 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ExchangeArchivingPolicy</em></p></td>
<td><p>선택</p></td>
<td><p>Exchange 보관 정책 옵션 열거</p></td>
<td><p>회의실의 메신저 대화 및 회의 세션을 보관할 방법 및 위치를 나타냅니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>* Uninitialized</p>
<p>* UseLyncArchivingPolicy</p>
<p>* NoArchiving</p>
<p>* ArchivingToExchange</p></td>
</tr>
<tr class="odd">
<td><p><em>HostedVoiceMail</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>True로 설정하면 회의의 음성 메일 통화가 Microsoft Exchange Server 2013의 호스트된 버전으로 경로 지정됩니다. 또한 이 옵션을 True로 설정한 경우 회의실에서 다른 사용자의 음성 메일로 직접 전화를 걸 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>LineServerURI</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>회의실에 할당된 원격 통화 제어 전화 게이트웨이의 URI입니다. LineServerUri가 게이트웨이 URI이며 앞에 &quot;sip:&quot;이 옵니다. 예를 들면 다음과 같습니다.</p>
<p>-LineServerUri &quot;sip:rccgateway@litwareinc.com&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>LineURI</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>회의실에 할당된 전화 번호입니다. URI(Uniform Resource Identifier) 행은 E.164 형식으로 지정하고 &quot;TEL:&quot; 접두사를 사용해야 합니다. 예를 들면 다음과 같습니다.</p>
<p>-LineUri &quot;TEL:+14255551297&quot;</p>
<p>모든 내선 번호는 다음과 같이 줄 URI의 끝에 추가해야 합니다.</p>
<p>-LineUri &quot;TEL:+14255551297;ext=51297”</p></td>
</tr>
<tr class="even">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>수정되는 회의실을 나타내는 파이프라인을 통해 회의실 개체를 전달할 수 있도록 합니다. 기본적으로 <strong>Set-CsMeetingRoom</strong> cmdlet은 파이프라인을 통해 개체를 전달하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PrivateLine</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>회의실의 전용 전화 회선에 대한 전화 번호입니다. 전용 회선은 AD DS(Active Directory 도메인 서비스)에 게시되지 않으므로 다른 사람들이 쉽게 사용할 수 없는 전화 번호입니다. 또한 이 전용 회선은 대부분의 인바운드 통화 경로 지정 규칙을 무시합니다. 예를 들어 전용 회선으로 들어오는 통화는 회의실의 대리인에게 전달되지 않습니다. 전용 회선은 흔히 다른 팀 구성원이 받지 않아야 하는 개인적인 전화 통화나 업무상의 통화에 사용됩니다.</p>
<p>전용 회선 값은 E.164 형식으로 지정하고 &quot;TEL:&quot; 접두사로 시작해야 합니다. 예를 들면 다음과 같습니다.</p>
<p>-PrivateLine &quot;TEL:+14255551297&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>RemoteCallControlTelephonyEnabled</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>회의실이 원격 통화 제어 전화 통신에 대해 사용하도록 설정되었는지 여부를 나타냅니다. 원격 통화 제어에 대해 사용하도록 설정된 경우 회의실은 Lync Server 2013를 사용하여 유선 전화에 걸려온 전화를 받을 수 있습니다. 또한 Lync를 사용하여 전화를 걸 수도 있습니다. 이러한 통화는 모두 PSTN(공중 전화망)이라고도 하는 표준 전화 네트워크를 사용합니다. 인터넷을 통해 전화를 걸거나 받으려면 Enterprise Voice에 대해 회의실을 사용하도록 설정해야 합니다. 자세한 내용은 EnterpriseVoiceEnabled 매개 변수를 참고하세요.</p>
<p>또한 원격 통화 제어에 대해 사용하도록 설정하려는 회의실에는 LineUri 및 LineServerUri가 둘 다 있어야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>회의실이 Lync 2013 등의 SIP 장치를 사용하여 통신할 수 있도록 허용하는 고유 식별자(전자 메일 주소와 유사함)입니다. SIP 주소에는 다음과 같이 sip: 접두사 및 유효한 SIP 도메인을 사용해야 합니다.</p>
<p>-SipAddress &quot;sip:room14@litwareinc.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

**Set-CsMeetingRoom** cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.OCSADMeetingRoom 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Set-CsMeetingRoom** cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.OCSADMeetingRoom 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Disable-CsMeetingRoom](disable-csmeetingroom.md)  
[Enable-CsMeetingRoom](enable-csmeetingroom.md)  
[Get-CsMeetingRoom](get-csmeetingroom.md)  
[Move-CsMeetingRoom](move-csmeetingroom.md)

