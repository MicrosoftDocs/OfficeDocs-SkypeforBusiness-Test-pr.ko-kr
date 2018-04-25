---
title: Remove-CsAnalogDevice
TOCTitle: Remove-CsAnalogDevice
ms:assetid: 61250894-fde6-476d-aaa2-ec5692af02b3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398433(v=OCS.15)
ms:contentKeyID: 49303801
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsAnalogDevice

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server를 사용하여 관리할 수 있는 아날로그 장치의 컬렉션에서 기존 장치를 제거합니다. 아날로그 장치는 PSTN(공중 전화망)에 연결된 전화 또는 장치입니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsAnalogDevice -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 ID가 CN={e5e7daba-394e-46ec-95a1-1f2a9947aad2},CN=Users,DC=litwareinc,DC=com인 아날로그 장치를 삭제합니다.

    Remove-CsAnalogDevice -Identity "CN={e5e7daba-394e-46ec-95a1-1f2a9947aad2},CN=Users,DC=litwareinc,DC=com"

## 예제 2

예제 2에 표시된 명령은 표시 이름에 "Building 14 Receptionist"가 할당된 모든 아날로그 장치를 삭제합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsAnalogDevice** cmdlet과 Filter 매개 변수를 사용합니다. 필터 값 {DisplayName -eq "Building 14 Receptionist"}는 DisplayName 속성이 "Building 14 Receptionist"와 같은 항목만 반환하도록 제한합니다. 그런 다음 반환된 항목은 **Remove-CsAnalogDevice** cmdlet에 파이프되어 제거됩니다.

    Get-CsAnalogDevice -Filter {DisplayName -eq "Building 14 Receptionist"} | Remove-CsAnalogDevice

## 예제 3

예제 3에서는 음성 정책 RedmondVoicePolicy가 할당된 모든 아날로그 장치를 삭제합니다. 이 작업을 수행하기 위해 **Get-CsAnalogDevice** cmdlet 및 Filter 매개 변수를 사용하여 VoicePolicy 속성이 RedmondVoicePolicy와 같은 모든 아날로그 장치를 검색합니다. 필터링된 컬렉션은 해당 컬렉션의 각 항목을 삭제하는 **Remove-CsAnalogDevice** cmdlet에 파이프됩니다.

    Get-CsAnalogDevice -Filter {VoicePolicy -eq "RedmondVoicePolicy"} | Remove-CsAnalogDevice

## 예제 4

예제 4에 표시된 명령은 조직에서 현재 사용 중인 모든 아날로그 팩스를 제거합니다. 이 작업을 수행하기 위해 먼저 **Get-CsAnalogDevice** cmdlet을 Filter 매개 변수와 함께 호출합니다. 필터 값 {AnalogFax –eq $True}는 AnalogFax 속성이 True와 같은 장치만 선택합니다. 그런 다음 이 필터링된 컬렉션은 컬렉션의 각 항목을 제거하는 **Remove-CsAnalogDevice** cmdlet에 파이프됩니다.

    Get-CsAnalogDevice -Filter {AnalogFax -eq $True} | Remove-CsAnalogDevice

## 자세한 정보

아날로그 장치에는 PSTN(공중 전화망)에 연결된 전화, 팩스, 모뎀 및 TTY/TTD(텔레타이프/청각 장애자용 통신 장치) 장치가 포함됩니다. 아날로그 장치는 Enterprise Voice(Microsoft에서 제공하는 VoIP(Voice over Internet Protocol) 솔루션)를 활용하는 장치와 달리 디지털 패킷을 사용하여 정보를 전송하지 않습니다. 대신에 정보가 연속 신호를 사용하여 전송됩니다. 이 신호를 일반적으로 아날로그 신호라고 하며, 그래서 "아날로그 장치"라고 합니다.

Lync Server는 관리자가 조직의 아날로그 장치와 Active Directory 연락처 개체를 연결하여 아날로그 장치를 관리할 수 있도록 지원합니다. 장치가 연락처 개체에 연결되면 연락처에 정책 및 다이얼 플랜을 할당하여 아날로그 장치를 관리할 수 있습니다.

나중에는 아날로그 장치와 연결된 연락처 개체를 삭제해야 할 수 있습니다. 예를 들어 모든 팩스를 폐기했다면 이러한 장치와 연결된 아날로그 장치(연락처 개체)가 더 이상 필요 없습니다. **Remove-CsAnalogDevice** cmdlet을 사용하면 아날로그 장치를 삭제할 수 있습니다. 이 cmdlet을 실행하면 **Get-CsAnalogDevice** cmdlet에서 반환한 아날로그 장치의 목록에서 장치가 삭제됩니다. 또한 해당 장치와 연결된 연락처 개체가 Active Directory 도메인 서비스에서 삭제됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 그룹의 구성원은 **Remove-CsAnalogDevice** cmdlet을 로컬로 실행할 수 있습니다. 특정 사이트 또는 특정 Active Directory OU(조직 구성 단위)에 대해 이 cmdlet을 실행할 권한은 **Grant-CsOUPermission** cmdlet을 사용하여 할당할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsAnalogDevice"}

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
<td><p>제거할 아날로그 장치에 대한 고유한 식별자입니다. 아날로그 장치는 연결된 연락처 개체의 Active Directory DN(고유 이름)을 사용하여 식별됩니다. 이러한 장치는 기본적으로 공용 이름으로 GUID(Globally Unique Identifier)를 사용하므로 일반적으로 CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com과 유사한 ID를 가집니다. 따라서 <strong>Get-CsAnalogDevice</strong> cmdlet을 사용하여 아날로그 장치를 검색하고 반환된 개체를 <strong>Remove-CsAnalogDevice</strong> cmdlet에 파이프하는 것이 더 편리합니다.</p></td>
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

Microsoft.Rtc.Management.ADConnect.Schema.OCSADAnalogDeviceContact 개체입니다. **Remove-CsAnalogDevice** cmdlet은 아날로그 장치 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Remove-CsAnalogDevice** cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.OCSADAnalogDeviceContact 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsAnalogDevice](get-csanalogdevice.md)  
[Move-CsAnalogDevice](move-csanalogdevice.md)  
[New-CsAnalogDevice](new-csanalogdevice.md)  
[Set-CsAnalogDevice](set-csanalogdevice.md)

