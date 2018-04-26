---
title: Get-CsLisCivicAddress
TOCTitle: Get-CsLisCivicAddress
ms:assetid: 6538b811-6b74-4c57-95f7-e1496df62e7f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398459(v=OCS.15)
ms:contentKeyID: 49303857
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsLisCivicAddress

 

_**마지막으로 수정된 항목:** 2015-03-09_

E9-1-1(Enhanced 9-1-1)용 위치 구성 데이터베이스에 있는 하나 이상의 위치에서 주소 부분만 검색합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsLisCivicAddress

## 예제

## 예제 1

이 예제에서는 위치 데이터베이스에서 모든 구/군/시 주소를 검색합니다. **Get-CsLisCivicAddress** cmdlet은 Verbose와 같은 공용 Windows PowerShell 매개 변수 외에는 매개 변수를 허용하지 않습니다. 따라서 **Get-CsLisCivicAddress** cmdlet을 호출하면 모든 구/군/시 주소가 반환됩니다. 더 세부적인 결과를 검색하는 방법은 예제 2의 명령을 참조하십시오.

    Get-CsLisCivicAddress

## 예제 2

이 예제에서는 Redmond 시의 모든 구/군/시 주소를 검색합니다. 이 예제에서는 **Get-CsLisCivicAddress** cmdlet을 호출하여 위치 데이터베이스에서 모든 구/군/시 주소의 컬렉션을 검색합니다. 그런 다음 이 컬렉션은 컬렉션에서 City 속성 값이 Redmond와 같은(-eq) 항목만 반환하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsLisCivicAddress | Where-Object {$_.City -eq "Redmond"}

## 예제 3

예제 3에서는 MSAG(마스터 주소 가이드)를 대상으로 유효성 검사를 마친 모든 LIS(위치 정보 서버) 구/군/시 주소를 검색합니다.

    Get-CsLisCivicAddress | Where-Object {$_.MSAGValid -eq $true}

## 자세한 정보

E9-1-1은 긴급 통화에 응답할 때 발신자에게 위치를 묻지 않고도 발신자의 지역 위치를 확인할 수 있는 기술입니다. Lync Server에서 위치는 발신자의 포트, 서브넷, 스위치 또는 특정 위치에 대한 무선 액세스 지점을 매핑하여 확인됩니다. 이 cmdlet은 이러한 위치와 연결된 주소를 하나 이상 검색합니다.

이 cmdlet은 고유한 주소만 반환한다는 점에서 **Get-CsLisLocation** cmdlet과는 다릅니다. 회사 이름이나 위치 이름은 반환하지 않으며 주소 정보만 반환합니다. 또한 주소의 유효성을 마스터 주소 가이드를 대상으로 확인했는지 여부를 나타내는 플래그(MSAGValid)도 반환합니다. 이 플래그는 **Test-CsLisCivicAddress** cmdlet을 실행하여 자동으로 업데이트할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsLisCivicAddress** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsLisCivicAddress"}

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

이 cmdlet은 System.Management.Automation.PSCustomObject 유형의 개체를 한 개 이상 검색합니다.

## 참고 항목

#### 기타 리소스

[Test-CsLisCivicAddress](test-csliscivicaddress.md)  
[Get-CsLisLocation](get-cslislocation.md)

