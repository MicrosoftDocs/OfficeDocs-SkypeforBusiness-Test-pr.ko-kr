---
title: Remove-CsCommonAreaPhone
TOCTitle: Remove-CsCommonAreaPhone
ms:assetid: f2c93bec-4b99-4b69-abe0-d2d9e33dcadd
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413016(v=OCS.15)
ms:contentKeyID: 49305508
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsCommonAreaPhone

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server를 사용하여 관리되는 전화 컬렉션에서 기존의 공통 영역 전화를 제거합니다. 공통 영역 전화는 건물 로비, 직원 휴게실 또는 다수의 사람들이 사용할 가능성이 높은 기타 영역에 있는 전화로서 다수의 사용자를 위한 것입니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsCommonAreaPhone -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 표시 이름이 "Building 14 Lobby"인 공통 영역 전화를 삭제합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsCommonAreaPhone** cmdlet을 Filter 매개 변수 및 필터 값 "{DisplayName -eq "Building 14 Lobby"}"와 함께 호출합니다. 그런 다음 반환된 개체가 **Remove-CsCommonAreaPhone** cmdlet에 파이프되고 이 cmdlet에 의해 삭제됩니다.

    Get-CsCommonAreaPhone -Filter {DisplayName -eq "Building 14 Lobby"} | Remove-CsCommonAreaPhone

## 예제 2

예제 2에서 명령은 다이얼 플랜이 할당되지 않은 모든 공통 영역 전화를 삭제합니다. 이 작업을 수행하기 위해 먼저 **Get-CsCommonAreaPhone** cmdlet 및 Filter 매개 변수를 사용하여 지정된 항목을 반환합니다. 필터 값 {DialPlan -eq $Null}은 다이얼 플랜이 할당되지 않은 공통 영역 전화에 대한 데이터만 반환하도록 제한합니다. 필터링된 컬렉션은 컬렉션의 각 전화를 삭제하는 **Remove-CsCommonAreaPhone** cmdlet에 파이프됩니다.

    Get-CsCommonAreaPhone -Filter {DialPlan -eq $Null} | Remove-CsCommonAreaPhone

## 예제 3

예제 3에서는 Active Directory의 Redmond OU에 연락처 개체가 있는 모든 공통 영역 전화를 삭제합니다. 이 작업을 수행하기 위해**Get-CsCommonAreaPhone** cmdlet을 먼저 호출하여 Redmond OU에 연락처 개체가 있는 모든 공통 영역 전화를 반환합니다. OU 매개 변수 및 매개 변수 값 "ou=Redmond,dc=litwareinc,dc=com”은 지정된 조직 구성 단위에 대한 데이터만 반환하도록 제한합니다. 반환된 컬렉션은 컬렉션의 각 전화를 삭제하는 **Remove-CsCommonAreaPhone** cmdlet에 파이프됩니다.

    Get-CsCommonAreaPhone -OU "ou=Redmond,dc=litwareinc,dc=com" | Remove-CsCommonAreaPhone

## 자세한 정보

공통 영역 전화는 개별 사용자와 연결되지 않은 IP 전화입니다. 공통 영역 전화는 특정 사무실에 있는 것이 아니라 일반적으로 건물의 로비, 카페, 직원 라운지, 회의실 등 많은 사람이 모일 수 있는 장소에 있습니다. 따라서 관리자의 관리가 필요합니다. Lync Server를 통해 사용하는 전화는 일반적으로 개별 사용자에게 할당된 음성 정책 및 다이얼 플랜으로 유지 관리되는데, 공통 영역 전화에는 개별 사용자가 할당되지 않기 때문입니다.

이러한 문제를 해결하는 한 가지 방법은 모든 공통 영역 전화에 대해 Active Directory 연락처 개체를 만드는 방법이 있습니다. 연락처 개체는 **New-CsCommonAreaPhone** cmdlet을 사용하여 만들 수 있습니다. 이러한 연락처 개체에는 사용자 계정과 마찬가지로 정책 및 음성 계획을 할당할 수 있습니다. 따라서 공통 영역 전화가 개별 사용자와 연결되어 있지 않더라도 해당 전화에 대한 제어를 유지 관리할 수 있습니다. 예를 들어 사람들이 공통 영역 전화에서 통화를 전송하거나 대기할 수 없도록 하려면 통화 전송 및 통화 대기를 금지하는 음성 정책을 만들어 해당 정책을 공통 영역 전화에 할당하기만 하면 됩니다. 좀 더 정확하게 표현하자면 공통 영역 전화를 나타내는 연락처 개체에 할당하면 됩니다. 예를 들어 다음 명령은 음성 정책 CommonAreaPhoneVoicePolicy를 모든 공통 영역 전화에 할당합니다.

Get-CsCommonAreaPhone | Grant-CsVoicePolicy –PolicyName "CommonAreaPhoneVoicePolicy"

때때로 공통 영역 전화와 연결된 연락처 개체를 삭제해야 하는 경우가 있습니다. 예를 들어 직원 휴게실에서 전화를 제거하는 경우 해당 전화와 연결된 연락처 개체가 없어도 됩니다. **Remove-CsCommonAreaPhone** cmdlet을 사용하면 공통 영역 전화를 삭제할 수 있습니다. 이 cmdlet을 실행하면 **Get-CsCommonAreaPhone** cmdlet에 의해 반환된 공통 영역 전화 목록에서 전화가 삭제됩니다. 또한 해당 전화와 연결된 연락처 개체가 Active Directory 도메인 서비스에서 삭제됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 그룹의 구성원은 **Remove-CsCommonAreaPhone** cmdlet을 로컬로 실행할 수 있습니다. 특정 사이트 또는 특정 Active Directory OU(조직 구성 단위)에 대해 이 cmdlet을 실행할 권한은 **Grant-CsOUPermission** cmdlet을 사용하여 할당할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsCommonAreaPhone"}

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
<td><p>공통 영역 전화의 고유 식별자입니다. 공통 영역 전화는 연결된 연락처 개체의 Active Directory 고유 이름을 사용하여 식별됩니다. 기본적으로 공통 영역 전화는 GUID(Globally Unique Identifier)를 공용 이름으로 사용합니다. 따라서 일반적으로 CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com과 유사한 ID가 지정됩니다. <strong>Get-CsCommonAreaPhone</strong> cmdlet을 사용하여 공통 영역 전화를 검색한 다음 반환된 개체를 <strong>Remove-CsCommonAreaPhone</strong> cmdlet에 파이프하면 더 쉽기 때문입니다.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
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

Microsoft.Rtc.Management.ADConnect.Schema.OCSADCommonAreaPhoneContact 개체입니다. **Remove-CsCommonAreaPhone** cmdlet은 공통 영역 전화 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Remove-CsCommonAreaPhone** cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.OCSADCommonAreaPhoneContact 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsCommonAreaPhone](get-cscommonareaphone.md)  
[Move-CsCommonAreaPhone](move-cscommonareaphone.md)  
[New-CsCommonAreaPhone](new-cscommonareaphone.md)  
[Set-CsCommonAreaPhone](set-cscommonareaphone.md)

