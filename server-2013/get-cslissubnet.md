---
title: Get-CsLisSubnet
TOCTitle: Get-CsLisSubnet
ms:assetid: 670b50b9-a5ab-4b70-bdb9-bdf3c1b09d0b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398473(v=OCS.15)
ms:contentKeyID: 49303875
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsLisSubnet

 

_**마지막으로 수정된 항목:** 2015-03-09_

위치 구성 데이터베이스에서 하나 이상의 서브넷을 검색합니다. 각 서브넷은 위치와 연결될 수 있으며, 이 경우 이 cmdlet은 서브넷의 위치 정보도 검색합니다. 이 위치 연결은 E9-1-1(Enhanced 9-1-1) Enterprise Voice 구현에서 응급 서비스 운영자에게 발신자 위치를 알리는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsLisSubnet

## 예제

## 예제 1

예제 1에서는 Lync Server 배포에 정의된 LIS(위치 정보 서버) 서브넷을 모두 검색합니다.

    Get-CsLisSubnet

## 예제 2

이 예제에서는 IP 주소가 192.0.10.0인 서브넷에 대한 모든 정보를 검색합니다. 먼저 **Get-CsLisSubnet** cmdlet을 호출하여 모든 서브넷 위치 연결을 검색합니다. 이 서브넷 위치 컬렉션은 **Where-Object** cmdlet에 파이프됩니다. **Where-Object** cmdlet은 컬렉션에 있는 각 항목의 Subnet 속성을 통해 값이 192.0.10.0과 같은지(-eq) 여부를 확인합니다. 서브넷 ID는 고유하므로 이 명령은 최대 한 개의 개체를 반환합니다.

    Get-CsLisSubnet | Where-Object {$_.Subnet -eq "192.0.10.0"}

## 자세한 정보

Enhanced 9-1-1을 통해 응급 운영자는 발신자에게 위치를 묻지 않고도 발신자 위치를 확인할 수 있습니다. 발신자가 VoIP(Voice over Internet Protocol) 연결을 통해 전화를 건 경우에는 여러 가지 연결 요소를 기반으로 정보를 추출해야 합니다. VoIP 관리자는 발신자의 위치를 확인하는 위치 맵(와이어맵(wiremap)이라고 함)을 구성해야 합니다. 이 cmdlet은 실제 위치와 통화가 경로 지정된 서브넷 위치 사이의 연결에서 정보를 검색합니다.

이 cmdlet은 Windows PowerShell 일반 매개 변수 외 다른 매개 변수를 사용하지 않으며 위치 매핑에 대한 서브넷의 모든 인스턴스를 검색합니다. 검색되는 정보의 범위를 좁히려면 이 cmdlet의 출력을 **Where-Object** cmdlet 또는 **Select-Object** cmdlet 등의 다른 Windows PowerShell cmdlet에 파이프해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsLisSubnet** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsLisSubnet"}

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
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>이 cmdlet은 일반 Windows PowerShell 매개 변수만 제공합니다.</p></td>
<td><p></p></td>
<td><p></p></td>
<td> </td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

이 cmdlet은 System.Management.Automation.PSCustomObject 유형의 개체를 검색합니다.

## 참고 항목

#### 기타 리소스

[Remove-CsLisSubnet](remove-cslissubnet.md)  
[Set-CsLisSubnet](set-cslissubnet.md)

