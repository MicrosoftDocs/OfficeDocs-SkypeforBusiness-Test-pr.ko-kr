---
title: Set-CsUser
TOCTitle: Set-CsUser
ms:assetid: 6c452df7-75c9-4d94-86bc-4990d718ffe9
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398510(v=OCS.15)
ms:contentKeyID: 49303944
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsUser

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 사용자 계정의 Lync Server 속성을 수정합니다. Lync Server에 사용하도록 활성화된 계정에 대해서만 속성을 수정할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsUser -Identity <UserIdParameter> [-AcpInfo <MultiValuedProperty>] [-AudioVideoDisabled <$true | $false>] [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-Enabled <$true | $false>] [-EnterpriseVoiceEnabled <$true | $false>] [-ExchangeArchivingPolicy <Uninitialized | UseLyncArchivingPolicy | NoArchiving | ArchivingToExchange>] [-HostedVoiceMail <$true | $false>] [-LineServerURI <String>] [-LineURI <String>] [-PassThru <SwitchParameter>] [-PrivateLine <String>] [-RemoteCallControlTelephonyEnabled <$true | $false>] [-SipAddress <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 ID가 Pilar Ackerman인 사용자 계정을 수정하기 위해 **Set-CsUser** cmdlet이 사용됩니다. 이 예제에서는 Microsoft의 VoIP 구현인 Enterprise Voice를 사용하도록 계정을 수정합니다. EnterpriseVoiceEnabled 매개 변수를 추가한 다음, 해당 매개 변수 값을 $True로 설정하여 이 작업을 수행합니다.

    Set-CsUser -Identity "Pilar Ackerman" -EnterpriseVoiceEnabled $True

## 예제 2

예제 2에서는 Finance 부서의 모든 사용자가 Enterprise Voice에 대해 활성화된 계정을 가집니다. 이 명령에서는 먼저 **Get-CsUser** cmdlet 및 LdapFilter 매개 변수를 사용하여 Finance 부서에서 일하는 모든 사용자의 컬렉션을 반환합니다. 그런 다음, 해당 정보는 사용자 컬렉션의 각 계정에 대해 Enterprise Voice를 활성화하는 **Set-CsUser** cmdlet에 파이프됩니다.

    Get-CsUser -LdapFilter "Department=Finance" | Set-CsUser -EnterpriseVoiceEnabled $True

## 자세한 정보

**Set-CsUser** cmdlet을 사용하면 Active Directory 도메인 서비스에 저장된 Lync Server 관련 사용자 계정 특성을 수정할 수 있습니다. 예를 들어 Lync Server에 대해 사용자를 비활성화 또는 다시 활성화하거나, A/V(오디오/비디오) 통신에 대해 사용자를 활성화 또는 비활성화하거나, 사용자의 전용 회선 및 회선 URI 번호를 수정할 수 있습니다. **Set-CsUser** cmdlet은 Lync Server에 대해 활성화된 사용자만 사용할 수 있습니다.

Lync Server와 관련된 특성만 **Set-CsUser** cmdlet을 사용하여 수정할 수 있습니다. 직위 또는 부서 등의 기타 사용자 계정 특성은 이 cmdlet을 사용하여 수정할 수 없습니다. 하지만 Lync Server 특성은 Set-CsUser cmdlet이나 Lync Server 제어판을 통해서만 수정되어야 한다는 점에 유의하세요. 이러한 특성을 수동으로 구성하려고 하면 안 됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 그룹의 구성원은 **Set-CsUser** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsUser\\b"}

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
<td><p>사용자 ID 매개 변수</p></td>
<td><p>수정할 사용자 계정의 ID를 나타냅니다. 사용자 ID는 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 사용자의 SIP 주소, 2) 사용자의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 사용자의 도메인 이름 및 로그온 이름(예: litwareinc\kenmyer) 및 4) 사용자의 Active Directory 표시 이름(예: Ken Myer)입니다. 또한 사용자의 Active Directory 고유 이름을 사용하여 사용자 ID를 참조할 수도 있습니다.</p>
<p>표시 이름을 사용자 ID로 사용할 경우 별표(*) 와일드카드 문자를 사용할 수 있습니다. 예를 들어 &quot;* Smith&quot;라는 ID는 표시 이름이 &quot; Smith&quot; 문자열 값으로 끝나는 모든 사용자를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AcpInfo</em></p></td>
<td><p>선택</p></td>
<td><p>다중값 속성</p></td>
<td><p>하나 이상의 타사 오디오 회의 공급자를 사용자에게 할당할 수 있습니다. 그러나 오디오 회의 공급자를 할당할 때는 <strong>Set-UserAcp</strong> cmdlet을 사용하는 것이 좋습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AudioVideoDisabled</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>사용자가 Lync를 사용하여 A/V(음성/화상) 통화를 할 수 있는지 여부를 나타냅니다. True로 설정하면 대부분 메신저 대화를 주고받는 것으로 제한됩니다.</p>
<p>사용자가 원격 통화 제어, Enterprise Voice 및/또는 IP-PBX(Internet Protocol Private Branch Exchange) 소프트 전화 경로 지정을 사용하도록 설정된 경우에는 A/V 통신을 비활성화할 수 없습니다.</p></td>
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
<td><p>사용자 계정을 수정할 때 연결할 도메인 컨트롤러를 지정할 수 있습니다. 이 매개 변수를 포함하지 않으면 cmdlet이 사용 가능한 첫 번째 도메인 컨트롤러를 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Enabled</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>사용자가 Lync Server에 대해 활성화되었는지 여부를 나타냅니다. 이 값을 False로 설정하면 사용자가 Lync Server에 더 이상 로그온할 수 없으며 이 값을 True로 설정하면 사용자의 로그온 권한이 다시 활성화됩니다.</p>
<p>Enabled 매개 변수를 사용하여 계정을 비활성화한 경우 해당 계정과 연관된 정보(할당된 정책 및 사용자가 Enterprise Voice 및/또는 원격 통화 제어를 사용하도록 설정되어 있는지 여부)는 그대로 유지됩니다. 따라서 나중에 Enabled 매개 변수를 사용하여 계정을 다시 활성화하면 연관된 계정 정보가 복원됩니다. 이것은 <strong>Disable-CsUser</strong> cmdlet을 사용하여 사용자 계정을 비활성화하는 것과 다릅니다. <strong>Disable-CsUser</strong> cmdlet을 실행할 경우 해당 계정과 연관된 Lync Server 데이터가 모두 삭제됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnterpriseVoiceEnabled</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>사용자가 Microsoft VoIP(Voice over Internet Protocol)인 Enterprise Voice를 사용하도록 설정되었는지 여부를 나타냅니다. Enterprise Voice를 사용하면 표준 전화 네트워크 대신 인터넷을 사용하여 전화를 걸 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ExchangeArchivingPolicy</em></p></td>
<td><p>선택</p></td>
<td><p>Exchange 보관 정책 옵션 열거</p></td>
<td><p>연락처의 메신저 대화 세션이 보관되는 위치를 나타냅니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>* Uninitialized</p>
<p>* UseLyncArchivingPolicy</p>
<p>* ArchivingToExchange</p>
<p>* NoArchiving</p></td>
</tr>
<tr class="odd">
<td><p><em>HostedVoiceMail</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>True로 설정하면 사용자의 음성 메일 통화가 Microsoft Exchange Server의 호스트된 버전으로 경로 지정됩니다. 또한 이 옵션을 True로 설정한 경우 Lync 사용자는 다른 사용자의 음성 메일로 직접 전화를 걸 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>LineServerURI</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>사용자에게 할당된 원격 통화 제어 전화 게이트웨이의 URI입니다. LineServerUri는 게이트웨이 URI이며 앞에 &quot;sip:&quot;이 옵니다(예: sip:rccgateway@litwareinc.com).</p></td>
</tr>
<tr class="odd">
<td><p><em>LineURI</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>사용자에게 할당된 전화 번호입니다. URI(Uniform Resource Identifier) 행은 E.164 형식으로 지정하고 &quot;TEL:&quot; 접두사로 시작해야 합니다(예: TEL:+14255551297). 모든 내선 번호는 회선 URI의 끝에 추가해야 합니다(예: TEL:+14255551297; ext=51297).</p>
<p>Lync Server에서는 TEL:+14255551297과 TEL:+14255551297;ext=51297을 각기 다른 두 번호로 처리한다는 점을 알고 있어야 합니다. Ken Myer에게 줄 URI TEL:+14255551297을 할당하고 이후에 Pilar Ackerman에게 줄 URI TEL:+14255551297;ext=51297을 할당하려고 하면 할당에 성공하며, Pilar에게 할당된 번호는 중복된 번호로 플래그가 지정되지 않습니다. 이는 해당 설정에 따라 이러한 두 번호가 실제로 다를 수 있기 때문입니다. 예를 들어 특정 조직에서 1-425-555-1297로 전화를 걸면 통화가 Exchange 자동 전화 교환으로 라우팅됩니다. 이와 반대로 내선 번호(51297)로만 전화를 걸거나 Lync를 사용하여 번호 1-425-555-1297과 내선 번호 51297로 전화를 걸면 통화가 해당 사용자에게 바로 라우팅됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>계정이 수정되는 사용자를 나타내는 사용자 개체를 파이프라인을 통해 전달할 수 있습니다. 기본적으로 <strong>Set-CsUser</strong> cmdlet은 파이프라인을 통해 개체를 전달하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PrivateLine</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>사용자의 전용 전화 회선에 대한 전화 번호입니다. 전용 회선은 Active Directory 도메인 서비스에 게시되지 않으므로 다른 사람들이 쉽게 사용할 수 없는 전화 번호입니다. 또한 이 전용 회선은 대부분의 인바운드 통화 경로 지정 규칙을 무시합니다. 예를 들어, 전용 회선으로 들어오는 통화는 대리인에게 전달되지 않습니다. 전용 회선은 흔히 다른 팀 구성원이 받지 않아야 하는 개인적인 전화 통화나 비즈니스 통화에 사용됩니다.</p>
<p>전용 회선 값은 E.164 형식으로 지정하고 &quot;TEL:&quot; 접두사로 시작해야 합니다(예: TEL:+14255551297).</p></td>
</tr>
<tr class="even">
<td><p><em>RemoteCallControlTelephonyEnabled</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>사용자가 원격 통화 제어 전화 통신에 대해 활성화되었는지 여부를 나타냅니다. 원격 통화 제어에 대해 활성화된 경우 사용자는 Lync Server를 사용하여 유선 전화에 걸려온 전화를 받을 수 있습니다. 또한 Lync를 사용하여 전화를 걸 수도 있습니다. 이러한 통화는 모두 PSTN(공중 전화망)이라고도 하는 표준 전화 네트워크를 사용합니다. 인터넷을 통해 전화를 걸거나 받으려면 Enterprise Voice에 대해 사용자를 활성화해야 합니다. 자세한 내용은 매개 변수 EnterpriseVoiceEnabled를 참조하십시오.</p>
<p>원격 통화 제어에 대해 활성화하려면 사용자는 LineUri 및 LineServerUri를 둘 다 갖고 있어야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>사용자가 Lync와 같은 SIP 장치를 사용하여 통신할 수 있도록 허용하는 고유 식별자(전자 메일 주소와 유사함)입니다. SIP 주소는 sip: 접두사 및 유효한 SIP 도메인을 사용해야 합니다(예: -SipAddress sip:kenmyer@litwareinc.com).</p></td>
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

문자열 또는 Microsoft.Rtc.Management.ADConnect.Schema.ADUser 개체입니다. **Set-CsUser** cmdlet은 Lync Server를 사용하도록 설정된 사용자 계정의 ID를 나타내는 파이프라인된 문자열 값을 허용합니다. 또한 Active Directory 사용자 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Set-CsUser** cmdlet은 개체를 반환하지 않습니다.

## 참고 항목

#### 기타 리소스

[Disable-CsUser](disable-csuser.md)  
[Enable-CsUser](enable-csuser.md)  
[Get-CsUser](get-csuser.md)  
[Move-CsUser](move-csuser.md)

