---
title: Remove-CsLisSubnet
TOCTitle: Remove-CsLisSubnet
ms:assetid: f8a87038-cc71-4fec-8496-574da0aa963f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413053(v=OCS.15)
ms:contentKeyID: 49305583
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsLisSubnet

 

_**마지막으로 수정된 항목:** 2015-03-09_

LIS(위치 정보 서버) 서브넷을 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsLisSubnet -Subnet <String> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 IP 주소가 192.10.10.0인 서브넷의 LIS 서브넷 위치 항목을 제거합니다. 이 예제의 명령은 유일한 필수 매개 변수인 Subnet을 포함합니다. 이 예제의 Subnet 값은 IPv4 주소 192.10.10.0입니다.

이 서브넷이 위치와 연결되어 있는 경우 해당 위치는 제거되지 않고 서브넷만 위치 매핑에서 제거됩니다.

    Remove-CsLisSubnet -Subnet 192.10.10.0

## 예제 2

이 예제에서는 Bldg30/Room1000 위치와 연결된 모든 서브넷을 제거합니다. 이 예제는 먼저 모든 LIS 서브넷 컬렉션을 반환하는 **Get-CsLisSubnet** cmdlet을 호출합니다. 이 컬렉션은 해당 컬렉션에서 Location 속성이 Bldg30/Room1000 문자열과 같은(-eq) 항목을 찾는 **Where-Object** cmdlet에 파이프됩니다. 마지막으로 해당 Location이 있는 이 서브넷 위치 컬렉션을 해당 컬렉션의 모든 항목을 제거하는 **Remove-CsLisSubnet** cmdlet에 파이프합니다.

예제 1에서와 같이 위치는 위치 구성 데이터베이스에서 제거되지 않고 이러한 위치를 참조하는 서브넷만 제거됩니다. **Remove-CsLisLocation** cmdlet을 호출하여 위치를 제거할 수 있습니다.

    Get-CsLisSubnet | Where-Object {$_.Location -eq "Bldg30/Room1000"} | Remove-CsLisSubnet

## 자세한 정보

E9-1-1(Enhanced 9-1-1)을 통해 응급 운영자는 발신자에게 위치를 묻지 않고도 발신자 위치를 확인할 수 있습니다. 발신자가 VoIP(Voice over Internet Protocol) 연결을 통해 전화를 건 경우에는 여러 가지 연결 요소를 기반으로 정보를 추출해야 합니다. VoIP 관리자는 발신자의 위치를 확인하는 위치 맵(와이어맵(wiremap)이라고 함)을 구성해야 합니다. 이 cmdlet은 위치 구성 데이터베이스에서 서브넷을 제거합니다. 서브넷을 제거해도 해당 서브넷과 연결된 위치는 제거되지 않습니다. **Remove-CsLisLocation** cmdlet을 사용하여 위치를 제거할 수 있습니다.

존재하지 않는 서브넷을 제거하려고 하면 아무 작업도 수행되지 않으며 오류나 경고 메시지가 나타나지 않습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsLisSubnet** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsLisSubnet"}

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
<td><p><em>Subnet</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>제거할 서브넷의 IP 주소입니다. 이 값은 IPv4 주소(192.0.2.0과 같은 마침표로 구분된 숫자)가 됩니다.</p></td>
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

LIS(위치 정보 서버) 서브넷 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 System.Management.Automation.PSCustomObject 유형의 개체를 제거합니다.

## 참고 항목

#### 기타 리소스

[Set-CsLisSubnet](set-cslissubnet.md)  
[Get-CsLisSubnet](get-cslissubnet.md)  
[Remove-CsLisLocation](remove-cslislocation.md)

