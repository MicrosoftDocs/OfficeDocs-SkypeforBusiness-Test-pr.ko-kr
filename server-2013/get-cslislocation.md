---
title: Get-CsLisLocation
TOCTitle: Get-CsLisLocation
ms:assetid: aede2266-5af4-4973-9db1-a7b505c62057
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412834(v=OCS.15)
ms:contentKeyID: 49304721
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsLisLocation

 

_**마지막으로 수정된 항목:** 2015-03-09_

위치 구성 데이터베이스에서 E9-1-1(Enhanced 9-1-1)에 대한 하나 이상의 위치를 검색합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsLisLocation [-Unreferenced <SwitchParameter>]

## 예제

## 예제 1

**Get-CsLisLocation** cmdlet을 매개 변수 없이 호출하면 위치 구성 데이터베이스 내에 정의된 모든 위치가 검색됩니다.

    Get-CsLisLocation

## 예제 2

Unreferenced 매개 변수에는 값이 사용되지 않습니다. 이는 포트, 스위치, 서브넷 또는 무선 액세스 지점과 연결되지 않은 위치만 반환하도록 **Get-CsLisLocation** cmdlet에 지시하는 스위치일 뿐입니다.

    Get-CsLisLocation -Unreferenced

## 예제 3

특정 LIS 위치를 검색하려면 **Get-CsLisLocation** cmdlet을 호출하여 모든 위치를 검색한 다음 해당 위치 컬렉션을 **Where-Object** cmdlet에 파이프하여 검색하려는 특정 위치로 컬렉션 범위를 좁혀야 합니다. 예제 3에서는 **Get-CsLisLocation** cmdlet 및 **Where-Object** cmdlet을 사용하여 Location 속성이 NorthCampus 문자열과 같은 모든 위치를 검색합니다. 여기에서는 -ceq 비교 연산자가 사용되었습니다. 이 연산자는 대/소문자 구분 비교를 수행합니다. 이는 Location 값이 NorthCampus인 위치만 반환되며 northcampus, Northcampus 등은 반환되지 않는다는 의미입니다.

    Get-CsLisLocation | Where-Object {$_.Location -ceq "NorthCampus"}

## 자세한 정보

E9-1-1은 긴급 통화를 받는 사람이 발신자에게 묻지 않고도 발신자의 지리적 위치를 확인할 수 있도록 지원합니다. Lync Server에서 위치는 발신자의 포트, 서브넷, 스위치 또는 특정 위치에 대한 무선 액세스 지점을 매핑하여 확인됩니다. 이 cmdlet은 이러한 위치를 하나 이상 검색합니다.

**Get-CsLisLocation** cmdlet은 주소 정보 외에도 위치의 이름 및 해당 위치와 연결된 회사 이름을 검색한다는 점에서 **Get-CsLisCivicAddress** cmdlet과 다릅니다. **Get-CsLisCivicAddress** cmdlet은 주소 정보만 검색합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsLisLocation** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsLisLocation"}

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
<td><p><em>Unreferenced</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 포함하면 포트, 서브넷, 스위치 또는 무선 액세스 지점과 연결되지 않은 위치만 검색됩니다. 즉, 이 매개 변수를 포함하면 <strong>Set-CsLisLocation</strong> cmdlet을 호출하여 만들었거나 더 이상 존재하지 않는 LIS(위치 정보 서버) 포트, 서브넷, 스위치 또는 무선 액세스 지점에 할당된 모든 위치가 검색됩니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

이 cmdlet은 System.Management.Automation.PSCustomObject 유형의 개체를 한 개 이상 반환합니다.

## 참고 항목

#### 기타 리소스

[Remove-CsLisLocation](remove-cslislocation.md)  
[Set-CsLisLocation](set-cslislocation.md)  
[Get-CsLisCivicAddress](get-csliscivicaddress.md)

