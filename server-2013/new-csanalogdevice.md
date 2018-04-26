---
title: New-CsAnalogDevice
TOCTitle: New-CsAnalogDevice
ms:assetid: c02755d6-b651-4385-91a0-5b594dc67751
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412937(v=OCS.15)
ms:contentKeyID: 49304917
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsAnalogDevice

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server를 사용하여 관리할 수 있는 새 아날로그 장치를 만듭니다. 아날로그 장치는 PSTN(공중 전화망)에 연결된 전화 또는 장치입니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsAnalogDevice -DN <ADObjectId> <COMMON PARAMETERS>

    New-CsAnalogDevice -OU <OUIdParameter> <COMMON PARAMETERS>

    COMMON PARAMETERS: -AnalogFax <$true | $false> -Gateway <Fqdn> -LineUri <String> -RegistrarPool <Fqdn> [-Confirm [<SwitchParameter>]] [-DisplayName <String>] [-DisplayNumber <String>] [-PassThru <SwitchParameter>] [-SipAddress <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 전화 번호(LineUri)가 1-425-555-6001인 새 아날로그 장치를 만듭니다. 이 전화 번호는 E.164 형식을 사용하여 지정해야 합니다. LineUri 매개 변수 외에 이 명령에서 사용된 다른 매개 변수로는 장치의 Active Directory 표시 이름을 설정하는 DisplayName, 등록자 풀을 지정하는 RegistrarPool, 이 장치가 팩스가 아니라 전화임을 나타내도록 $False로 설정되는 -AnalogFax, 게이트웨이의 IP 주소로 설정되는 Gateway 및 장치의 연락처 개체를 만들 Active Directory OU의 고유 이름인 -OU가 있습니다.

    New-CsAnalogDevice -LineUri tel:+14255556001 -DisplayName "Building 14 Receptionist" -RegistrarPool redmond-Cs-001.litwareinc.com -AnalogFax $False -Gateway 192.168.0.240 -OU "ou=Telecommunications,dc=litwareinc,dc=com"

## 자세한 정보

아날로그 장치에는 PSTN(공중 전화망)에 연결된 전화, 팩스, 모뎀 및 TTY/TTD(텔레타이프/청각 장애자용 통신 장치) 장치가 포함됩니다. 아날로그 장치는 Enterprise Voice(Microsoft에서 제공하는 VoIP(Voice over Internet Protocol) 솔루션)를 활용하는 장치와 달리 디지털 패킷을 사용하여 정보를 전송하지 않습니다. 대신에 정보가 연속 신호를 사용하여 전송됩니다. 이 신호를 일반적으로 아날로그 신호라고 하며, 그래서 "아날로그 장치"라고 합니다.

Lync Server는 관리자가 아날로그 장치와 Active Directory 연락처 개체를 연결하여 아날로그 장치를 관리할 수 있도록 지원합니다. 장치가 연락처 개체에 연결되면 연락처에 정책 및 다이얼 플랜을 할당하여 아날로그 장치를 관리할 수 있습니다.

새 아날로그 장치를 만들려면 **New-CsAnalogDevice** cmdlet을 사용합니다. 이 cmdlet은 아날로그 장치에서 사용할 새 연락처 개체를 만들거나 기존의 연락처 개체를 새 장치와 연결할 수 있습니다. 자세한 내용은 이 항목의 OU 및 DN 매개 변수 설명을 참조하십시오.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsAnalogDevice** cmdlet을 로컬로 실행할 수 있습니다. 특정 사이트 또는 특정 Active Directory OU(조직 구성 단위)에 대해 이 cmdlet을 실행할 권한은 **Grant-CsOUPermission** cmdlet을 사용하여 할당할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsAnalogDevice"}

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
<td><p><em>AnalogFax</em></p></td>
<td><p>필수</p></td>
<td><p>System.Boolean</p></td>
<td><p>아날로그 장치가 팩스인 경우 True($True)로 설정합니다. 장치가 팩스가 아닌 경우 False($False)로 설정합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DN</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.ADObjectId</p></td>
<td><p>기존의 Active Directory 연락처 개체와 아날로그 장치를 연결하는 데 사용됩니다. 아날로그 장치와 연결할 연락처 개체가 있는 경우 DN 매개 변수를 사용하고 이 매개 변수 뒤에 해당 연락처의 고유 이름을 지정합니다(예: -DN &quot;cn=Building 14 Lobby,dc=litwareinc,dc=com&quot;). 지정한 연락처가 존재하지 않는 경우 명령이 실패합니다.</p>
<p>같은 명령에서 OU와 DN 매개 변수를 함께 사용할 수는 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Gateway</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>아날로그 장치에 사용될 PSTN 게이트웨이의 IP 주소입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>LineUri</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>아날로그 장치의 전화 번호입니다. URI(Uniform Resource Identifier) 행은 E.164 형식으로 지정하고 &quot;TEL:&quot; 접두사로 시작해야 합니다(예: TEL:+14255551297). 모든 내선 번호는 회선 URI의 끝에 추가해야 합니다(예: &quot;TEL:+14255551297;ext=51297&quot;).</p></td>
</tr>
<tr class="odd">
<td><p><em>OU</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.AD.OUIdParameter</p></td>
<td><p>연락처 개체를 저장할 Active Directory OU(조직 구성 단위)의 고유 이름입니다(예: -OU &quot;ou=Redmond,dc=litwareinc,dc=com&quot;).</p>
<p>OU 매개 변수를 포함하면 지정된 OU에 새 연락처가 만들어지고 이 연락처에 자동으로 GUID(Globally Unique identifier)가 공용 이름으로 할당됩니다. 따라서 연락처 개체는 {ce84964a-c4da-4622-ad34-c54ff3ed361f}와 유사한 이름을 갖게 됩니다.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>RegistrarPool</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>연락처 개체를 저장할 등록자 풀의 FQDN(정규화된 도메인 이름)입니다(예: -RegistrarPool &quot;atl-cs-001.litwareinc.com&quot;).</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DisplayName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>아날로그 장치의 Active Directory 표시 이름을 구성합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DisplayNumber</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>Lync에 표시되는 전화 번호입니다. DisplayNumber 속성의 형식은 원하는 대로 지정할 수 있습니다(예: 1-800-555-1234, 1-(800)-555-1234, 1.800.555.1234 등).</p></td>
</tr>
<tr class="even">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>공통 영역 전화를 나타내는 개체를 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>아날로그 장치가 Lync와 같은 SIP 장치와 통신할 수 있도록 허용하는 고유 식별자(전자 메일 주소와 유사함)입니다. SIP 주소에는 &quot;sip:&quot; 접두사를 붙여야 합니다(예: sip:bldg14lobby@litwareinc.com).</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsAnalogDevice** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsAnalogDevice** cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.OCSADAnalogDeviceContact 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsAnalogDevice](get-csanalogdevice.md)  
[Move-CsAnalogDevice](move-csanalogdevice.md)  
[Remove-CsAnalogDevice](remove-csanalogdevice.md)  
[Set-CsAnalogDevice](set-csanalogdevice.md)

