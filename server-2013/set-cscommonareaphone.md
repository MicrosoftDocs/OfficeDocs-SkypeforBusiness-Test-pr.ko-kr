---
title: Set-CsCommonAreaPhone
TOCTitle: Set-CsCommonAreaPhone
ms:assetid: 765ab74c-33ca-4b17-ba15-edb2fe559ebb
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398579(v=OCS.15)
ms:contentKeyID: 49304070
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsCommonAreaPhone

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server에서 관리하는 공용 지역 전화의 속성 값을 수정합니다. 공통 영역 전화는 건물 로비, 직원 휴게실 또는 다수의 사람들이 사용할 가능성이 높은 기타 영역에 있는 전화로서 다수의 사용자를 위한 것입니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsCommonAreaPhone -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-Description <String>] [-DisplayName <String>] [-DisplayNumber <String>] [-DomainController <Fqdn>] [-Enabled <$true | $false>] [-EnterpriseVoiceEnabled <$true | $false>] [-ExchangeArchivingPolicy <Uninitialized | UseLyncArchivingPolicy | NoArchiving | ArchivingToExchange>] [-LineURI <String>] [-PassThru <SwitchParameter>] [-SipAddress <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 공통 영역 전화의 Active Directory 표시 이름을 1-425-555-6710이라는 전화 번호로 수정합니다. 이 작업을 수행하기 위해 먼저 Filter 매개 변수와 함께 **Get-CsCommonAreaPhone** cmdlet을 호출합니다. 필터 값 {LineUri -eq "tel:+14255556710"}은 반환되는 데이터를 LineUri 속성이 tel:+14255556710과 같은 공통 영역 전화로 제한합니다. 반환된 개체는 **Set-CsCommonAreaPhone** cmdlet에 파이프되어 DisplayName 속성 값이 "Employee Lounge"로 설정됩니다.

    Get-CsCommonAreaPhone -Filter {LineUri -eq "tel:+14255556710"} | Set-CsCommonAreaPhone -DisplayName "Employee Lounge"

## 예제 2

예제 2에 표시된 명령을 사용하면 현재 조직에서 사용하도록 구성된 모든 공통 영역 전화를 사용할 수 있습니다. 이 작업을 수행하기 위해 명령은 매개 변수 없이 **Get-CsCommonAreaPhone** cmdlet을 호출하여 모든 공통 영역 전화의 컬렉션을 반환합니다. 이 컬렉션은 컬렉션의 각 항목에 대해 Enabled 속성을 True로 설정하는 **Set-CsCommonAreaPhone** cmdlet에 파이프됩니다.

    Get-CsCommonAreaPhone | Set-CsCommonAreaPhone -Enabled $True

## 예제 3

예제 3에서는 Description 속성에 값이 할당되지 않은 모든 공통 영역 전화에 일반 설명을 추가합니다. 이 작업을 수행하기 위해 Filter 매개 변수와 함께 **Get-CsCommonAreaPhone** cmdlet을 호출합니다. 필터 값 {Description -eq $Null}은 Description 속성이 null 값과 같은 공통 영역 전화만 반환되도록 합니다. 이 필터링된 컬렉션은 컬렉션의 각 항목에 일반 설명 "Common area phone"을 할당하는 **Set-CsCommonAreaPhone** cmdlet에 파이프됩니다.

    Get-CsCommonAreaPhone -Filter {Description -eq $Null} | Set-CsCommonAreaPhone -Description "Common area phone"

## 자세한 정보

공통 영역 전화는 개별 사용자와 연결되지 않은 IP 전화입니다. 공통 영역 전화는 특정 사무실에 있는 것이 아니라 일반적으로 건물의 로비, 카페, 직원 라운지, 회의실 등 많은 사람이 모일 수 있는 장소에 있습니다. 따라서 관리자의 관리가 필요합니다. Lync Server를 통해 사용하는 전화는 일반적으로 개별 사용자에게 할당된 음성 정책 및 다이얼 플랜으로 유지 관리되는데, 공통 영역 전화에는 개별 사용자가 할당되지 않기 때문입니다.

이러한 문제를 해결하는 한 가지 방법은 모든 공통 영역 전화에 대해 Active Directory 연락처 개체를 만드는 것입니다. 연락처 개체는 **New-CsCommonAreaPhone** cmdlet을 사용하여 만들 수 있습니다. 이러한 연락처 개체에는 사용자 계정과 마찬가지로 정책 및 음성 계획을 할당할 수 있습니다. 따라서 공통 영역 전화가 개별 사용자와 연결되어 있지 않더라도 해당 전화에 대한 제어를 유지 관리할 수 있습니다. 예를 들어 사람들이 공통 영역 전화에서 통화를 전송하거나 대기할 수 없도록 하려면 통화 전송 및 통화 대기를 금지하는 음성 정책을 만들어 해당 정책을 공통 영역 전화에 할당하기만 하면 됩니다. 좀 더 정확하게 표현하자면 공통 영역 전화를 나타내는 연락처 개체에 할당하면 됩니다. 다음 명령은 음성 정책 CommonAreaPhoneVoicePolicy를 모든 공통 영역 전화에 할당합니다.

Get-CsCommonAreaPhone | Grant-CsVoicePolicy –PolicyName "CommonAreaPhoneVoicePolicy"

**Set-CsCommonAreaPhone** cmdlet은 공통 영역 전화에 연결된 연락처 개체의 속성을 수정하는 방법을 제공합니다. 특히, 전화에 연결된 URI(Uniform Resource Identifier) 행 또는 연락처의 Active Directory 표시 이름을 변경할 수 있습니다. 또한 CsEnabled 매개 변수를 사용하여 Lync Server에서 계정을 사용하거나 사용하지 않도록 설정할 수 있습니다.

또한 CsClientPolicy cmdlet을 사용하여 공통 영역 전화에 대해 "hotdesking"을 구성할 수 있습니다. 전화가 hotdesked되면 사용자는 해당 Lync Server 자격 증명을 사용하여 전화에 로그온할 수 있습니다. 무엇보다도 이렇게 하면 사용자가 자신의 대화 상대에 손쉽게 액세스할 수 있습니다. 자세한 내용은 [Set-CsClientPolicy](set-csclientpolicy.md) cmdlet의 도움말 항목을 참조하십시오.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 그룹의 구성원은 **Set-CsCommonAreaPhone** cmdlet을 로컬로 실행할 수 있습니다. 특정 사이트 또는 특정 Active Directory OU(조직 구성 단위)에 대해 이 cmdlet을 실행할 권한은 **Grant-CsOUPermission** cmdlet을 사용하여 할당할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsCommonAreaPhone"}

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
<td><p>공통 영역 전화의 고유 식별자입니다. 공통 영역 전화는 연결된 연락처 개체의 Active Directory 고유 이름을 사용하여 식별됩니다. 기본적으로 공통 영역 전화는 GUID(Globally Unique Identifier)를 공용 이름으로 사용합니다. 따라서 일반적으로 CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com과 유사한 ID가 지정됩니다. <strong>Get-CsCommonAreaPhone</strong> cmdlet을 사용하여 공통 영역 전화를 검색한 다음 반환된 개체를 <strong>Set-CsCommonAreaPhone</strong> cmdlet에 파이프하면 더 쉽기 때문입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>공통 영역 전화의 Active Directory 설명 특성을 수정할 수 있습니다. 이 방법을 사용하면 전화에 대한 추가 정보를 제공할 수 있습니다. 예를 들어 전화에 문제가 있는 경우에 연락할 사람에 대한 정보를 제공할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DisplayName</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>공통 영역 전화의 Active Directory 표시 이름을 수정할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DisplayNumber</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>Lync에 표시되는 전화 번호입니다. DisplayNumber 속성의 형식은 원하는 대로 지정할 수 있습니다(예: 1-800-555-1234, 1-(800)-555-1234, 1.800.555.1234 등). 표시 이름을 선택한 경우 이 번호는 정규화할 수 있는 경우에만 공통 영역 전화 화면에 표시됩니다. 정규화는 번호 문자열을 표준 전화 번호 형식으로 변환하는 프로세스입니다. 표시 번호를 구성할 때 사용되는 전화 번호 형식에 대한 정규화 규칙이 없으면 공통 영역 전화의 화면에 DisplayNumber 속성 값 대신 LineUri 속성 값이 표시됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>FQDN</p></td>
<td><p>대화 상대 정보를 수정하기 위해 지정된 도메인 컨트롤러에 연결할 수 있게 합니다. 특정 도메인 컨트롤러에 연결하려면 DomainController 매개 변수 뒤에 컴퓨터 이름(예: atl-mcs-001) 또는 정규화된 도메인 이름(예: atl-mcs-001.litwareinc.com)을 포함합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Enabled</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>공통 영역 전화의 연락처 개체가 Lync Server를 사용하도록 설정되었는지 여부를 나타냅니다.</p>
<p>Enabled 매개 변수를 사용하여 연락처를 비활성화할 경우 해당 계정과 연관된 정보(할당된 정책 및 연락처가 Enterprise Voice, 원격 통화 제어 및/또는 음성 메일 통합에 대해 활성화되었는지 여부)는 유지됩니다. 따라서 나중에 Enabled 매개 변수를 사용하여 계정을 다시 활성화하면 연관된 계정 정보가 복원됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnterpriseVoiceEnabled</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>공통 영역 전화의 연락처 개체가 Microsoft에서 제공하는 VoIP(Voice over Internet Protocol) 솔루션인 Enterprise Voice를 사용하도록 설정되었는지 여부를 나타냅니다. Enterprise Voice를 사용하면 표준 전화 네트워크가 아니라 인터넷을 사용하여 전화를 걸 수 있습니다.</p></td>
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
<td><p><em>LineURI</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>공통 영역 전화의 전화 번호입니다. URI(Uniform Resource Identifier) 행은 E.164 형식으로 지정하고 &quot;TEL:&quot; 접두사가 앞에 와야 합니다(예: TEL:+14255551297). 모든 내선 번호는 회선 URI 끝에 추가해야 합니다(예: TEL:+14255551297; ext=51297).</p></td>
</tr>
<tr class="odd">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>공통 영역 전화를 나타내는 개체를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>공통 영역 전화를 SIP 장치(예: Lync)와 통신할 수 있도록 하는 고유 식별자입니다. SIP 주소에는 &quot;sip:&quot; 접두사를 붙이고 올바른 SIP 도메인을 포함해야 합니다(예: sip:bldg14lobby@litwareinc.com).</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.ADConnect.Schema.OCSADCommonAreaPhoneContact 개체입니다.

## 반환 형식

기본적으로 **Set-CsCommonAreaPhone** cmdlet은 개체나 값을 반환하지 않습니다. 그러나 PassThru 매개 변수를 포함한 경우 이 cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.OCSADCommonAreaPhoneContact 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsCommonAreaPhone](get-cscommonareaphone.md)  
[Move-CsCommonAreaPhone](move-cscommonareaphone.md)  
[New-CsCommonAreaPhone](new-cscommonareaphone.md)  
[Remove-CsCommonAreaPhone](remove-cscommonareaphone.md)

