---
title: Remove-CsLisSwitch
TOCTitle: Remove-CsLisSwitch
ms:assetid: 53456988-4b37-4f34-825d-bebee5124856
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398352(v=OCS.15)
ms:contentKeyID: 49303645
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsLisSwitch

 

_**마지막으로 수정된 항목:** 2015-03-09_

LIS(위치 정보 서버) 네트워크 스위치를 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsLisSwitch -ChassisID <String> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 MAC 주소(ChassisID)가 99-99-99-99-99-99인 LIS 스위치를 제거합니다.

이 ChassisID를 참조하는 포트가 있는 경우 이 명령은 실패합니다. 또한 이 스위치가 위치와 연결된 경우, 해당 위치가 제거되지는 않으며 위치 매핑에서 스위치만 제거됩니다.

    Remove-CsLisSwitch -ChassisID 99-99-99-99-99-99

## 예제 2

이 예제에서는 도시명이 없는 모든 스위치를 제거합니다. 이 예제에서는 먼저 **Get-CsLisSwitch** cmdlet을 호출하여 모든 스위치의 컬렉션을 반환합니다. 이 컬렉션은 해당 컬렉션에서 City 속성이 비어 있는 항목, 즉 City가 빈 문자열(“”)과 같은(-eq) 항목을 찾는 **Where-Object** cmdlet에 파이프됩니다. 마지막으로 이 스위치의 컬렉션을 **Remove-CsLisSwitch** cmdlet에 파이프하여 해당 컬렉션의 모든 항목을 제거합니다.

여기에서도 예제 1과 같이 위치 데이터베이스에서 위치가 제거되지는 않으며 이러한 위치를 참조하는 스위치만 제거됩니다. 이 경우 위치 데이터베이스에 삭제해야 하는 잘못된 위치가 생깁니다. City는 위치의 필수 속성이기 때문입니다. **Remove-CsLisLocation** cmdlet을 호출하여 위치를 제거할 수 있습니다.

    Get-CsLisSwitch | Where-Object {$_.City -eq ""} | Remove-CsLisSwitch

## 자세한 정보

E9-1-1(Enhanced 9-1-1)을 통해 응급 운영자는 발신자에게 위치를 묻지 않고도 발신자 위치를 확인할 수 있습니다. 발신자가 VoIP(Voice over Internet Protocol) 연결을 통해 전화를 건 경우에는 여러 가지 연결 요소를 기반으로 정보를 추출해야 합니다. VoIP 관리자는 발신자의 위치를 확인하는 위치 맵(와이어맵이라고 함)을 구성해야 합니다. 이 cmdlet은 위치 구성 데이터베이스에서 스위치를 제거합니다. 스위치를 제거하더라도 실제 위치가 제거되지 않으며 스위치만 제거됩니다. 위치를 제거하려면 **Remove-CsLisLocation** cmdlet을 호출합니다.

스위치의 ChassisID가 포트에서 사용 중인 경우 스위치를 제거할 수 없습니다. 포트에서 어떤 ChassisID가 사용 중인지 알아보려면 Get-CsLisPort | Select-Object ChassisID 명령을 실행하면 됩니다. 먼저 지정한 ChassisID를 사용하는 모든 포트를 제거해야 스위치를 제거할 수 있습니다.

존재하지 않는 스위치를 제거하려고 하면 아무 작업도 수행되지 않으며 오류나 경고 메시지가 나타나지 않습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsLisSwitch** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsLisSwitch"}

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
<td><p>네트워크 스위치의 MAC(미디어 액세스 제어) 주소입니다. 이 값은 nn-nn-nn-nn-nn-nn 형식(예: 12-34-56-78-90-ab)입니다.</p></td>
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

LIS 스위치 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다. System.Management.Automation.PSCustomObject 유형의 개체를 제거합니다.

## 참고 항목

#### 기타 리소스

[Set-CsLisSwitch](set-cslisswitch.md)  
[Get-CsLisSwitch](get-cslisswitch.md)  
[Remove-CsLisLocation](remove-cslislocation.md)  
[Get-CsLisPort](get-cslisport.md)

