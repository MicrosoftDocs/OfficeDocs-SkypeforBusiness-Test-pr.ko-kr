---
title: New-CsCommonAreaPhone
TOCTitle: New-CsCommonAreaPhone
ms:assetid: 6082d24d-de92-4a3c-8639-5d28341cbc84
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398430(v=OCS.15)
ms:contentKeyID: 49303797
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsCommonAreaPhone

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server를 사용하여 관리할 수 있는 새 공통 영역 전화를 만듭니다. 공통 영역 전화는 건물 로비, 직원 휴게실 또는 다수의 사람들이 사용할 가능성이 높은 기타 영역에 있는 전화로서 다수의 사용자들을 위한 것입니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsCommonAreaPhone -DN <ADObjectId> <COMMON PARAMETERS>

    New-CsCommonAreaPhone -OU <OUIdParameter> <COMMON PARAMETERS>

    COMMON PARAMETERS: -LineUri <String> -RegistrarPool <Fqdn> [-Confirm [<SwitchParameter>]] [-Description <String>] [-DisplayName <String>] [-DisplayNumber <String>] [-PassThru <SwitchParameter>] [-SipAddress <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 전화 번호 1-425-555-6710에 대한 새 공통 영역 전화를 만듭니다. LineUri는 E.164 형식으로 지정해야 합니다. 전화 번호 지정 외에도 이 명령은 등록자 풀(RegistrarPool), Active Directory 표시 이름(DisplayName), 해당 연락처 개체를 만들어야 하는 OU의 고유 이름(-OU)을 지정합니다.

    New-CsCommonAreaPhone -LineUri tel:+14255556710 -RegistrarPool redmond-cs-001.litwareinc.com -DisplayName "Building 14 Lobby" -OU "ou=Telecommunications,dc=litwareinc,dc=com"

## 예제 2

예제 2에 표시된 명령은 예제 1에 표시된 명령의 변형이지만, 예제 2에서는 새 공통 영역 전화가 기존 Active Directory 개체 연락처와 연결됩니다. 이 작업을 수행하기 위해 OU 매개 변수 대신 DN 매개 변수가 사용되며, 기존 연락처 개체의 고유 이름(cn=Building 14 Lobby,ou=Telecommunications,dc=litwareinc,dc=com)이 매개 변수 값으로 사용됩니다. 이 명령에서는 DisplayName도 생략되었으므로 새 공통 영역 전화는 기존 연락처 개체에 이미 할당된 표시 이름을 사용합니다.

    New-CsCommonAreaPhone -LineUri tel:+14255556710 -RegistrarPool redmond-cs-001.litwareinc.com -DN "cn=Building 14 Lobby,ou=Telecommunications,dc=litwareinc,dc=com"

## 자세한 정보

공통 영역 전화는 개별 사용자와 연결되지 않은 IP 전화입니다. 공통 영역 전화는 특정 사무실에 있는 것이 아니라 일반적으로 건물의 로비, 카페, 직원 라운지, 회의실 등 많은 사람이 모일 수 있는 장소에 있습니다. 따라서 관리자의 관리가 필요합니다. Lync Server를 통해 사용하는 전화는 일반적으로 개별 사용자에게 할당된 음성 정책 및 다이얼 플랜으로 유지 관리되는데, 공통 영역 전화에는 개별 사용자가 할당되지 않기 때문입니다.

이러한 문제를 해결하는 한 가지 방법은 모든 공통 영역 전화에 대해 Active Directory 연락처 개체를 만드는 방법이 있습니다. 연락처 개체는 **New-CsCommonAreaPhone** cmdlet을 사용하여 만들 수 있습니다. 이러한 연락처 개체에는 사용자 계정과 마찬가지로 정책 및 음성 계획을 할당할 수 있습니다. 따라서 공통 영역 전화가 개별 사용자와 연결되어 있지 않더라도 해당 전화에 대한 제어를 유지 관리할 수 있습니다. 예를 들어 사람들이 공통 영역 전화에서 통화를 전송하거나 대기할 수 없도록 하려면 통화 전송 및 통화 대기를 금지하는 음성 정책을 만들어 해당 정책을 공통 영역 전화에 할당하기만 하면 됩니다. 좀 더 정확하게 표현하자면 공통 영역 전화를 나타내는 연락처 개체에 할당하면 됩니다. 다음 명령은 음성 정책 CommonAreaPhoneVoicePolicy를 모든 공통 영역 전화에 할당합니다.

Get-CsCommonAreaPhone | Grant-CsVoicePolicy –PolicyName "CommonAreaPhoneVoicePolicy"

앞에서 설명했듯이, **New-CsCommonAreaPhone** cmdlet을 사용하여 새 공통 영역 전화를 만들 수 있습니다. **New-CsCommonAreaPhone** cmdlet은 공통 영역 전화에 사용할 새 연락처 개체를 만들거나, 기존 연락처 개체를 새 공통 영역 전화에 연결할 수 있습니다. 자세한 내용은 이 항목의 OU 및 DN 매개 변수 설명을 참조하세요.

이 cmdlet를 실행할 수 있는 사용자: 기본적으로 도메인 관리자 그룹의 구성원은 로컬로 **New-CsCommonAreaPhone** cmdlet을 실행할 수 있습니다. 특정 사이트 또는 특정 Active Directory OU(조직 구성 단위)에 대해 이 cmdlet을 실행할 권한은 **Grant-CsOUPermission** cmdlet을 사용하여 할당할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsCommonAreaPhone"}

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
<td><p><em>DN</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.ADObjectId</p></td>
<td><p>기존 Active Directory 연락처 개체를 새 공통 영역 전화와 연결할 수 있습니다. 공통 영역 전화와 연결할 연락처 개체가 있는 경우 DN 매개 변수 뒤에 해당 연락처의 고유 이름을 사용합니다(예: -DN &quot;cn=Building 14 Lobby,dc=litwareinc,dc=com&quot;). 지정한 연락처가 존재하지 않는 경우 명령이 실패합니다. 지정된 연락처가 이미 Lync Server에 대해 활성화된 경우에도 명령이 실패합니다. 이 경우 먼저 <strong>Disable-CsUser</strong> cmdlet을 사용하여 연락처를 활성화한 다음 <strong>New-CsCommonAreaPhone</strong> cmdlet을 실행해야 합니다.</p>
<p>DN 매개 변수는 특히 회의실 및 기타 엔터티에 대한 연락처 개체를 이미 만든 조직에서 유용합니다. 이러한 연락처는 주로 예약 목적으로 사용됩니다. DN 매개 변수를 사용하면 이러한 기존 연락처 개체 중 하나를 사용하여 새 공통 영역 전화를 만들 수 있습니다.</p>
<p>같은 명령에서 OU와 DN 매개 변수를 함께 사용할 수는 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>LineUri</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>공통 영역 전화의 전화 번호입니다. URI(Uniform Resource Identifier) 행은 E.164 형식으로 지정하고 &quot;TEL:&quot; 접두사가 앞에 와야 합니다(예: TEL:+14255551297). 모든 내선 번호는 회선 URI의 끝에 추가해야 합니다(예: TEL:+14255551297; ext=51297).</p></td>
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
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>공통 영역 전화의 Active Directory 설명 특성을 설정할 수 있습니다. 이렇게 하면 전화에 대한 추가 정보를 제공할 수도 있습니다. 예를 들어 전화에 문제가 발생할 경우 연락할 사람에 대한 세부 정보를 제공할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DisplayName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>공통 영역 전화의 Active Directory 표시 이름을 설정할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DisplayNumber</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>Lync에 표시되는 전화 번호입니다. DisplayNumber 속성의 형식은 원하는 대로 지정할 수 있습니다(예: 1-800-555-1234, 1-(800)-555-1234, 1.800.555.1234 등). 표시 이름을 선택한 경우 이 번호는 정규화할 수 있는 경우에만 공통 영역 전화 화면에 표시됩니다. 정규화는 번호 문자열을 표준 전화 번호 형식으로 변환하는 프로세스입니다. 표시 번호를 구성할 때 사용되는 전화 번호 형식에 대한 정규화 규칙이 없으면 공통 영역 전화의 화면에 DisplayNumber 속성 값 대신 LineUri 속성 값이 표시됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>공통 영역 전화를 나타내는 개체를 반환합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>공통 영역 전화를 SIP 장치(예: Lync)와 통신할 수 있도록 하는 고유 식별자입니다. SIP 주소는 &quot;sip:&quot; 접두사로 시작해야 하며 올바른 SIP 도메인을 포함해야 합니다(예: sip:bldg14lobby@litwareinc.com).</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsCommonAreaPhone** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsCommonAreaPhone** cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.OCSADCommonAreaPhoneContact 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsCommonAreaPhone](get-cscommonareaphone.md)  
[Move-CsCommonAreaPhone](move-cscommonareaphone.md)  
[Remove-CsCommonAreaPhone](remove-cscommonareaphone.md)  
[Set-CsCommonAreaPhone](set-cscommonareaphone.md)

