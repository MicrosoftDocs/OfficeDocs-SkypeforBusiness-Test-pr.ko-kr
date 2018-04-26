---
title: Set-CsAnalogDevice
TOCTitle: Set-CsAnalogDevice
ms:assetid: b05e729e-cdef-4c78-8ce7-b183c3208a93
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412843(v=OCS.15)
ms:contentKeyID: 49304737
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsAnalogDevice

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server를 사용하여 관리할 수 있는 아날로그 장치의 컬렉션에서 기존 장치를 수정합니다. 아날로그 장치는 PSTN(공중 전화망)에 연결된 전화 또는 장치입니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsAnalogDevice -Identity <UserIdParameter> [-AnalogFax <$true | $false>] [-Confirm [<SwitchParameter>]] [-DisplayName <String>] [-DisplayNumber <String>] [-DomainController <Fqdn>] [-Enabled <$true | $false>] [-EnterpriseVoiceEnabled <$true | $false>] [-ExchangeArchivingPolicy <Uninitialized | UseLyncArchivingPolicy | NoArchiving | ArchivingToExchange>] [-Gateway <Fqdn>] [-LineURI <String>] [-PassThru <SwitchParameter>] [-SipAddress <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 ID가 CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com인 아날로그 장치의 LineUri 속성 값을 변경합니다.

    Set-CsAnalogDevice -Identity "CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com" -LineUri "TEL:+14255551298"

## 예제 2

예제 2에 표시된 명령은 현재 게이트웨이 192.168.0.240을 사용 중인 각 아날로그 장치의 게이트웨이를 변경합니다. 이 작업을 수행하기 위해 **Get-CsAnalogDevice** cmdlet을 Filter 매개 변수와 함께 호출합니다. 필터 값 {Gateway -eq "192.168.0.240"}은 게이트웨이가 192.168.0.240과 같은(-eq) 장치만 반환되도록 합니다. 이 필터링된 컬렉션은 컬렉션의 각 항목에서 Gateway 속성 값을 192.168.1.100으로 변경하는 **Set-CsAnalogDevice** cmdlet에 파이프됩니다.

    Get-CsAnalogDevice -Filter {Gateway -eq "192.168.0.240"} | Set-CsAnalogDevice -Gateway "192.168.1.100"

## 자세한 정보

아날로그 장치에는 PSTN(공중 전화망)에 연결된 전화, 팩스, 모뎀 및 TTY/TTD(텔레타이프/청각 장애자용 통신 장치) 장치가 포함됩니다. 아날로그 장치는 Enterprise Voice(Microsoft에서 제공하는 VoIP(Voice over Internet Protocol) 솔루션)를 활용하는 장치와 달리 디지털 패킷을 사용하여 정보를 전송하지 않습니다. 대신에 정보가 연속 신호를 사용하여 전송됩니다. 이 신호를 일반적으로 아날로그 신호라고 하며, 그래서 "아날로그 장치"라고 합니다.

Lync Server는 관리자가 아날로그 장치와 Active Directory 연락처 개체를 연결하여 아날로그 장치를 관리할 수 있도록 지원합니다. 장치가 연락처 개체에 연결되면 연락처에 정책 및 다이얼 플랜을 할당하여 아날로그 장치를 관리할 수 있습니다.

**Set-CsAnalogDevice** cmdlet을 사용하면 아날로그 장치와 연결된 연락처 개체의 속성을 수정할 수 있습니다. 예를 들어 장치와 연결된 연락처의 Active Directory 표시 이름 또는 줄 URI(Uniform Resource Identifier)를 변경할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsAnalogDevice** cmdlet을 로컬로 실행할 수 있습니다. 특정 사이트 또는 특정 Active Directory OU(조직 구성 단위)에 대해 이 cmdlet을 실행할 권한은 **Grant-CsOUPermission** cmdlet을 사용하여 할당할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsAnalogDevice"}

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
<td><p>수정할 아날로그 장치의 고유 식별자입니다. 아날로그 장치는 연결된 연락처 개체의 Active Directory DN(고유 이름)을 사용하여 식별됩니다. 기본적으로 아날로그 장치는 공용 이름으로 GUID(Globally Unique Identifier)를 사용합니다. 따라서 일반적으로 CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com과 유사한 ID가 지정됩니다. 그러므로 <strong>Get-CsAnalogDevice</strong> cmdlet을 사용하여 아날로그 장치 개체를 반환하고 반환된 개체를 <strong>Set-CsAnalogDevice</strong> cmdlet에 파이프하는 방식으로 아날로그 장치를 수정하는 것이 더 편리합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AnalogFax</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>아날로그 장치가 팩스인 경우 True($True)로 설정합니다. 장치가 팩스가 아닌 경우 False($False)로 설정합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DisplayName</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>아날로그 장치의 Active Directory 표시 이름을 구성합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DisplayNumber</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>Lync에 표시되는 전화 번호입니다. DisplayNumber 속성의 형식은 원하는 대로 지정할 수 있습니다(예: 1-800-555-1234, 1-(800)-555-1234, 1.800.555.1234 등).</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>FQDN</p></td>
<td><p>대화 상대 정보를 수정하기 위해 지정된 도메인 컨트롤러에 연결하는 데 사용됩니다. 특정 도메인 컨트롤러에 연결하려면 DomainController 매개 변수 뒤에 컴퓨터 이름(예: atl-mcs-001) 또는 FQDN(정규화된 도메인 이름)(예: atl-mcs-001.litwareinc.com)을 포함합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Enabled</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>True($True)로 설정하면 아날로그 장치를 Lync와 함께 사용할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnterpriseVoiceEnabled</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>아날로그 장치의 연락처 개체가 Microsoft에서 제공하는 VoIP 솔루션인 Enterprise Voice에 대해 활성화되었는지 여부를 나타냅니다. Enterprise Voice를 사용하면 표준 전화 네트워크가 아니라 인터넷을 사용하여 전화를 걸 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ExchangeArchivingPolicy</em></p></td>
<td><p>선택</p></td>
<td><p>Exchange 보관 정책 옵션 열거</p></td>
<td><p>연락처의 메신저 대화 세션이 보관되는 위치를 나타냅니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>* Uninitialized</p>
<p>* UseLyncArchivingPolicy</p>
<p>* ArchivingToExchange</p>
<p>* NoArchiving</p></td>
</tr>
<tr class="even">
<td><p><em>Gateway</em></p></td>
<td><p>선택</p></td>
<td><p>FQDN</p></td>
<td><p>아날로그 장치에 사용될 PSTN 게이트웨이의 IP 주소입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LineURI</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>아날로그 장치의 전화 번호입니다. 회선 URI는 E.164 형식을 사용하여 지정하고 &quot;TEL:&quot; 접두사로 시작해야 합니다(예: TEL:+14255551297). 모든 내선 번호는 회선 URI의 끝에 추가해야 합니다(예: TEL:+14255551297; ext=51297).</p></td>
</tr>
<tr class="even">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>공통 영역 전화를 나타내는 개체를 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>아날로그 장치가 Lync 2013과 같은 SIP 장치와 통신할 수 있도록 허용하는 고유 식별자입니다. SIP 주소에는 &quot;sip:&quot; 접두사를 붙여야 합니다(예: sip:bldg14lobby@litwareinc.com).</p></td>
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

Microsoft.Rtc.Management.ADConnect.Schema.OCSADAnalogDeviceContact 개체입니다. **Set-CsAnalogDevice** cmdlet은 아날로그 장치 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

기본적으로 **Set-CsAnalogDevice** cmdlet은 개체나 값을 반환하지 않습니다. 그러나 PassThru 매개 변수를 포함할 경우 Microsoft.Rtc.Management.ADConnect.Schema.OCSADAnalogDeviceContact 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsAnalogDevice](get-csanalogdevice.md)  
[Move-CsAnalogDevice](move-csanalogdevice.md)  
[New-CsAnalogDevice](new-csanalogdevice.md)  
[Remove-CsAnalogDevice](remove-csanalogdevice.md)

