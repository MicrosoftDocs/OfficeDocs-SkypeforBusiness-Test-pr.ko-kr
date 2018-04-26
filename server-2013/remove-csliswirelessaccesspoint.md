---
title: Remove-CsLisWirelessAccessPoint
TOCTitle: Remove-CsLisWirelessAccessPoint
ms:assetid: 656190b0-bde0-4a92-a6b5-b96a389c4863
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398461(v=OCS.15)
ms:contentKeyID: 49303853
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsLisWirelessAccessPoint

 

_**마지막으로 수정된 항목:** 2015-03-09_

LIS(위치 정보 서버) WAP(무선 액세스 지점)를 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsLisWirelessAccessPoint -BSSID <String> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 BSSID가 99-99-99-99-99-99인 LIS WAP 위치를 제거합니다.

이 WAP가 위치와 연결된 경우 해당 위치가 제거되지 않으며 위치 매핑에서 WAP만 제거됩니다.

    Remove-CsLisWirelessAccessPoint -BSSID 99-99-99-99-99-99

## 예제 2

이 예제에서는 빌딩 30의 모든 WAP를 제거합니다. 예제는 먼저 모든 WAP 컬렉션을 반환하는 **Get-CsLisWirelessAccessPoint** cmdlet을 호출합니다. 이 컬렉션은 컬렉션에서 Location 속성의 값에 문자열 Bldg30이 포함된 항목을 찾는 **Where-Object** cmdlet에 파이프됩니다. 즉, Location이 Bldg30과 비슷한(-like) 항목을 찾습니다. 마지막으로 이 빌딩 30의 WAP의 컬렉션은 해당 컬렉션의 모든 항목을 제거하는 **Remove-CsLisWirelessAccessPoint** cmdlet에 파이프됩니다.

예제 1에서와 같이 위치는 위치 구성 데이터베이스에서 제거되지 않고 이러한 위치를 참조하는 WAP만 제거됩니다.

    Get-CsLisWirelessAccessPoint | Where-Object {$_.Location -like "*Bldg30*"} | Remove-CsLisWirelessAccessPoint

## 자세한 정보

Enhanced 9-1-1을 통해 응급 운영자는 발신자에게 위치를 묻지 않고도 발신자 위치를 확인할 수 있습니다. 발신자가 VoIP(Voice over Internet Protocol) 연결을 통해 전화를 건 경우에는 여러 가지 연결 요소를 기반으로 정보를 추출해야 합니다. VoIP 관리자는 발신자의 위치를 확인하는 위치 맵(와이어맵(wiremap)이라고 함)을 구성해야 합니다. 이 cmdlet은 위치 구성 데이터베이스에서 WAP를 제거합니다. WAP를 제거하더라도 해당 WAP와 연결된 위치가 제거되지는 않습니다. **Remove-CsLisLocation** cmdlet을 사용하여 위치를 제거할 수 있습니다.

존재하지 않는 WAP를 제거하려고 하면 아무 작업도 수행되지 않으며 오류나 경고 메시지가 나타나지 않습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsLisWirelessAccessPoint** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsLisWirelessAccessPoint"}

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
<td><p><em>BSSID</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>제거하려는 무선 액세스 지점의 BSSID(Basic Service Set Identifier)입니다. 이 값은 nn-nn-nn-nn-nn-nn 형식(예: 12-34-56-78-90-ab)입니다.</p></td>
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

LIS 무선 액세스 지점 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 System.Management.Automation.PSCustomObject 유형의 개체를 제거합니다.

## 참고 항목

#### 기타 리소스

[Set-CsLisWirelessAccessPoint](set-csliswirelessaccesspoint.md)  
[Get-CsLisWirelessAccessPoint](get-csliswirelessaccesspoint.md)  
[Remove-CsLisLocation](remove-cslislocation.md)

