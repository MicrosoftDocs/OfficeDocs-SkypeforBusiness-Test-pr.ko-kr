---
title: Remove-CsLisPort
TOCTitle: Remove-CsLisPort
ms:assetid: b8a648af-1064-4a1e-8462-f267b7b72be1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412899(v=OCS.15)
ms:contentKeyID: 49304826
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsLisPort

 

_**마지막으로 수정된 항목:** 2015-03-09_

LIS(위치 정보 서버) 포트와 위치 간의 연결을 제거합니다. 이 연결은 E9-1-1(Enhanced 9-1-1) Enterprise Voice 구현에서 응급 서비스 운영자에게 발신자의 위치를 알리는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsLisPort -ChassisID <String> -PortID <String> -PortIDSubType <InterfaceAlias | InterfaceName | LocallyAssigned> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 MAC 주소(ChassisID)가 99-99-99-99-99-99이고, PortID가 4200이며 PortIDSubType이 1인 LIS 포트를 제거합니다. PortIDSubType의 값 1은 InterfaceAlias 값으로 변환됩니다. 이 매개 변수 및 값을 -PortIDSubType InterfaceAlias와 같이 입력할 수도 있습니다.

이 포트가 위치와 연결되어 있는 경우 해당 위치는 제거되지 않고 포트만 위치 매핑에서 제거됩니다.

    Remove-CsLisPort -ChassisID 99-99-99-99-99-99 -PortID 4200 -PortIDSubType 1

## 예제 2

이 예제에서는 번지가 없는 모든 포트 위치를 제거합니다. 이 예제는 먼저 모든 LIS 포트 컬렉션을 반환하는 **Get-CsLisPort** cmdlet을 호출합니다. 이 컬렉션은 해당 컬렉션에서 HouseNumber 속성이 비어 있는 항목, 즉 HouseNumber가 빈 문자열(“”)과 같은(-eq) 항목을 찾는 **Where-Object** cmdlet에 파이프됩니다. 마지막으로 번지가 없는 이 포트 위치 컬렉션을 해당 컬렉션의 모든 항목을 제거하는 **Remove-CsLisPort** cmdlet에 파이프합니다.

예제 1에서와 같이 위치는 위치 구성 데이터베이스에서 제거되지 않고 이러한 위치를 참조하는 포트만 제거됩니다. 이 경우에는 위치 데이터베이스에 제거해야 하는 유효하지 않은 위치(HouseNumber가 위치의 필수 속성이므로 유효하지 않음)가 있음을 의미합니다. **Remove-CsLisLocation** cmdlet을 호출하여 위치를 제거할 수 있습니다.

    Get-CsLisPort | Where-Object {$_.HouseNumber -eq ""} | Remove-CsLisPort

## 자세한 정보

Enhanced 9-1-1을 통해 응급 운영자는 발신자에게 위치를 묻지 않고도 발신자 위치를 확인할 수 있습니다. 발신자가 VoIP(Voice over Internet Protocol) 연결을 통해 전화를 건 경우에는 여러 가지 연결 요소를 기반으로 정보를 추출해야 합니다. VoIP 관리자는 발신자의 위치를 확인하는 위치 맵(와이어맵(wiremap)이라고 함)을 구성해야 합니다. 이 cmdlet은 위치 구성 데이터베이스에서 포트를 제거하여 실제 위치와 전화가 경로 지정되는 포트 간의 연결을 제거합니다.

포트 위치를 제거하면 포트의 실제 위치가 제거되는 것이 아니라 포트만 제거됩니다. 위치를 제거하려면 **Remove-CsLisLocation** cmdlet을 호출합니다. 포트를 제거해도 특정 ChassisID를 가진 스위치는 제거되지 않습니다. 스위치를 제거하려면 **Remove-CsLisSwitch** cmdlet을 호출합니다.

존재하지 않는 포트를 제거하려고 하면 아무 작업도 수행되지 않으며 오류나 경고 메시지가 나타나지 않습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsLisPort** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsLisPort"}

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
<td><p><em>ChassisID</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>포트 스위치의 MAC(미디어 액세스 제어) 주소입니다. 이 값은 nn-nn-nn-nn-nn-nn 형식(예: 12-34-56-78-90-ab)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PortID</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>제거할 포트의 ID입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PortIDSubType</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Lis.PortIDSubType</p></td>
<td><p>제거할 포트의 하위 유형입니다. 이 값은 숫자 값 또는 문자열로 입력할 수 있지만 유효한 하위 유형이어야 합니다. 사용할 수 있는 하위 유형은 다음과 같습니다.</p>
<p>1: InterfaceAlias</p>
<p>5: InterfaceName</p>
<p>7: LocallyAssigned</p></td>
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

LIS 포트 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다. System.Management.Automation.PSCustomObject 유형의 개체를 제거합니다.

## 참고 항목

#### 기타 리소스

[Set-CsLisPort](set-cslisport.md)  
[Get-CsLisPort](get-cslisport.md)  
[Remove-CsLisLocation](remove-cslislocation.md)  
[Remove-CsLisSwitch](remove-cslisswitch.md)

