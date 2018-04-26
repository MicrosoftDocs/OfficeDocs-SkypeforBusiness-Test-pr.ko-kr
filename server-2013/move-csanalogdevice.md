---
title: Move-CsAnalogDevice
TOCTitle: Move-CsAnalogDevice
ms:assetid: c629c5f8-93e7-4fe4-ad51-52bc0ae99a46
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398816(v=OCS.15)
ms:contentKeyID: 49304982
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Move-CsAnalogDevice

 

_**마지막으로 수정된 항목:** 2015-03-09_

하나 이상의 아날로그 장치를 새 등록자 풀로 이동합니다. 아날로그 장치는 PSTN(공중 전화망)에 연결된 전화 또는 장치입니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Move-CsAnalogDevice -Identity <UserIdParameter> -Target <Fqdn> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-Force <SwitchParameter>] [-IgnoreBackendStoreException <SwitchParameter>] [-PassThru <SwitchParameter>] [-ProxyPool <Fqdn>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com인 아날로그 장치를 등록자 풀 atl-cs-001.litwareinc.com으로 이동합니다.

    Move-CsAnalogDevice -Identity "CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com" -Target atl-cs-001.litwareinc.com

## 예제 2

예제 2에서는 Active Directory 표시 이름이 "Building 14, Room 142"인 아날로그 장치를 등록자 풀 atl-cs-001.litwareinc.com으로 이동합니다. 이 작업을 수행하기 위해 먼저 매개 변수 없이 **Get-CsAnalogDevice** cmdlet이 호출되어 조직에서 사용 중인 모든 아날로그 장치 컬렉션을 반환합니다. 이 컬렉션은 표시 이름이 "Building 14, Room 142"인 모든 장치를 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 모든 장치를 등록자 풀 atl-cs-001.litwareinc.com으로 이동하는 **Move-CsAnalogDevice** cmdlet에 파이프됩니다.

    Get-CsAnalogDevice | Where-Object {$_.DisplayName -eq "Building 14, Room 142"} | Move-CsAnalogDevice -Target atl-cs-001.litwareinc.com

## 예제 3

예제 3에 표시된 명령은 표시 이름이 문자열 값 "Building 14"로 시작하는 모든 아날로그 장치를 이동합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsAnalogDevice** cmdlet을 호출하여 조직에서 현재 사용 중인 모든 아날로그 장치의 컬렉션을 반환합니다. 이 컬렉션은 표시 이름이 문자열 값 "Building 14"로 시작하는 모든 장치를 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 장치를 등록자 풀 atl-cs-001.litwareinc.com으로 이동하는 **Move-CsAnalogDevice** cmdlet에 파이프됩니다.

    Get-CsAnalogDevice | Where-Object {$_.DisplayName -like "Building 14*"} | Move-CsAnalogDevice -Target atl-cs-001.litwareinc.com

## 자세한 정보

아날로그 장치에는 PSTN(공중 전화망)에 연결된 전화, 팩스, 모뎀 및 TTY/TTD(텔레타이프/청각 장애자용 통신 장치) 장치가 포함됩니다. 아날로그 장치는 Enterprise Voice(Microsoft에서 제공하는 VoIP(Voice over Internet Protocol) 솔루션)를 활용하는 장치와 달리 디지털 패킷을 사용하여 정보를 전송하지 않습니다. 대신에 정보가 연속 신호를 사용하여 전송됩니다. 이 신호를 일반적으로 아날로그 신호라고 하며, 그래서 "아날로그 장치"라고 합니다.

Lync Server는 관리자가 아날로그 장치와 Active Directory 연락처 개체를 연결하여 아날로그 장치를 관리할 수 있도록 지원합니다. 장치가 연락처 개체에 연결되면 연락처에 정책 및 다이얼 플랜을 할당하여 아날로그 장치를 관리할 수 있습니다.

**Move-CsAnalogDevice** cmdlet을 사용하여 기존 아날로그 장치를 새 등록자 풀로 이동할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Move-CsAnalogDevice** cmdlet을 로컬로 실행할 수 있습니다. 특정 사이트 또는 특정 Active Directory OU(조직 구성 단위)에 대해 이 cmdlet을 실행할 권한은 **Grant-CsOUPermission** cmdlet을 사용하여 할당할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Move-CsAnalogDevice"}

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
<td><p>아날로그 장치의 고유 식별자입니다. 아날로그 장치는 연결된 연락처 개체의 Active Directory 고유 이름을 사용하여 식별됩니다. 기본적으로 아날로그 장치는 공용 이름으로 GUID(Globally Unique Identifier)를 사용합니다. 따라서 일반적으로 CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com과 유사한 ID가 지정됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Target</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>아날로그 장치를 이동해야 하는 등록자 풀의 FQDN(정규화된 도메인 이름)(예: atl-cs-001.litwareinc.com)입니다. 등록자 풀 이외에 호스팅 공급자의 FQDN도 대상이 될 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>아날로그 장치를 이동하기 위해 지정된 도메인 컨트롤러에 연결하는 데 사용됩니다. 특정 도메인 컨트롤러에 연결하려면 DomainController 매개 변수 뒤에 컴퓨터 이름(예: atl-cs-001) 또는 FQDN(예: atl-cs-001.litwareinc.com)을 포함합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 아날로그 장치를 이동하지만 연관된 데이터(예: 장치에 할당된 정책)를 모두 삭제합니다. 이 매개 변수가 있으면 장치가 연관된 모든 데이터와 함께 이동합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>IgnoreBackendStoreException</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수가 있으면 백 엔드 데이터베이스에서 발생했을 수 있는 모든 오류를 무시하고 오류가 발생했더라도 공통 영역 전화 이동을 시도하도록 컴퓨터에 명령합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이동할 사용자 계정을 나타내는 사용자 개체를 파이프라인을 통해 전달하는 데 사용됩니다. 기본적으로 <strong>Move-CsAnalogDevice</strong> cmdlet은 파이프라인을 통해 개체를 전달하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ProxyPool</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>이 매개 변수는 Microsoft Lync Online 2010에만 사용됩니다. Lync Server의 온-프레미스 구현에 사용하면 안 됩니다.</p></td>
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

문자열. **Move-CsAnalogDevice** cmdlet은 아날로그 장치의 ID를 나타내는 파이프라인된 문자열 값을 허용합니다.

## 반환 형식

기본적으로 **Move-CsAnalogDevice** cmdlet은 개체나 값을 반환하지 않습니다. 그러나 PassThru 매개 변수를 포함할 경우 Microsoft.Rtc.Management.ADConnect.Schema.OCSADAnalogDeviceContact 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Get-CsAnalogDevice](get-csanalogdevice.md)  
[New-CsAnalogDevice](new-csanalogdevice.md)  
[Remove-CsAnalogDevice](remove-csanalogdevice.md)  
[Set-CsAnalogDevice](set-csanalogdevice.md)

