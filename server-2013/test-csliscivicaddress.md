---
title: Test-CsLisCivicAddress
TOCTitle: Test-CsLisCivicAddress
ms:assetid: 4079e767-3339-40c9-b7cd-08ec6c9d2c25
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425914(v=OCS.15)
ms:contentKeyID: 49303426
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsLisCivicAddress

 

_**마지막으로 수정된 항목:** 2015-03-09_

마스터 주소 가이드를 대상으로 하나 이상의 구/군/시 주소를 테스트합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Test-CsLisCivicAddress [-City <String>] [-Confirm [<SwitchParameter>]] [-Country <String>] [-HouseNumber <String>] [-HouseNumberSuffix <String>] [-PostalCode <String>] [-PostDirectional <String>] [-PreDirectional <String>] [-State <String>] [-StreetName <String>] [-StreetSuffix <String>] [-UpdateValidationStatus <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 명령은 마스터 주소 가이드를 대상으로 이러한 매개 변수에 지정된 값과 일치하는 속성이 있는 주소의 유효성을 검사합니다. 끝 부분에는 UpdateValidationStatus 매개 변수를 포함하여 주소의 MSAGValid 속성을 업데이트합니다.

    Test-CsLisCivicAddress -HouseNumber 1234 -HouseNumberSuffix "" -PreDirectional "" -StreetName Main -StreetSuffix St -PostDirectional "" -City Redmond -State WA -PostalCode 99999 -Country US -UpdateValidationStatus

## 예제 2

이 예제에서는 모든 LIS 구/군/시 주소를 테스트하는 방법을 보여 줍니다. 이 예제에서는 **Get-CsLisCivicAddress** cmdlet을 호출하여 위치 데이터베이스에 정의된 모든 구/군/시 주소를 검색합니다. 그런 다음 이러한 주소는 E9-1-1 네트워크 경로 지정 공급자 웹 서비스를 통해 각 주소의 유효성을 검사하는 **Test-CsLisCivicAddress** cmdlet에 파이프됩니다.

    Get-CsLisCivicAddress | Test-CsLisCivicAddress -UpdateValidationStatus

## 자세한 정보

E9-1-1(Enhanced 9-1-1)을 사용하는 Enterprise Voice 구현에서는 서브넷, 포트, 스위치 또는 무선 액세스 지점을 위치로 매핑하는 위치 맵을 바탕으로 사용자 위치를 확인합니다. 매핑된 위치에 연결되어 있지 않으면 위치를 수동으로 입력하라는 메시지가 사용자에게 표시될 수 있습니다. E9-1-1 네트워크 경로 지정 공급자는 MSAG(마스터 주소 가이드)를 대상으로 이러한 위치의 주소가 유효한지 검사해야 합니다. 이 cmdlet은 해당 공급자의 웹 서비스를 사용하여 매핑된 주소의 유효성을 검사합니다. **Set-CsLisServiceProvider** cmdlet을 호출하여 서비스 공급자를 설정할 수 있습니다.

구/군/시 주소의 MSAGValid 속성을 업데이트하려면 **Test-CsLisCivicAddress** cmdlet을 호출할 때 UpdateValidationStatus 매개 변수를 포함해야 합니다. 구/군/시 주소를 검색하려면 **Get-CsLisCivicAddress** cmdlet을 사용합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Test-CsLisCivicAddress** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsLisCivicAddress"}

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
<td><p><em>City</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>위치의 구/군/시입니다.</p>
<p>최대 길이: 64자</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Country</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 위치가 속한 국가/지역입니다.</p>
<p>최대 길이: 2자</p></td>
</tr>
<tr class="even">
<td><p><em>HouseNumber</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>위치의 번지입니다. 회사의 경우 회사가 위치한 거리의 번지를 의미합니다.</p>
<p>최대 길이: 10자</p></td>
</tr>
<tr class="odd">
<td><p><em>HouseNumberSuffix</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>1/2 또는 A와 같은 번지에 대한 추가 정보입니다(예: 1234 1/2 Oak Street 또는 1234 A Elm Street).</p>
<p>최대 길이: 5자</p></td>
</tr>
<tr class="even">
<td><p><em>PostalCode</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 위치와 연결된 우편 번호입니다.</p>
<p>최대 길이: 10자</p></td>
</tr>
<tr class="odd">
<td><p><em>PostDirectional</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>거리 이름의 방향 표시입니다. 예를 들어 Main Street NE 또는 7th Avenue NW에서 NE나 NW에 해당합니다.</p>
<p>최대 길이: 2자</p></td>
</tr>
<tr class="even">
<td><p><em>PreDirectional</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>거리 이름 앞에 오는 거리 이름의 방향 표시입니다. (예: NE Main Street 또는 NW 7th Avenue의 NE 또는 NW).</p>
<p>최대 길이: 2자</p></td>
</tr>
<tr class="odd">
<td><p><em>State</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 위치와 연결된 시/도입니다.</p>
<p>최대 길이: 2자</p></td>
</tr>
<tr class="even">
<td><p><em>StreetName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 위치의 거리 이름입니다.</p>
<p>최대 길이: 60자</p></td>
</tr>
<tr class="odd">
<td><p><em>StreetSuffix</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>Street, Avenue 또는 Court와 같이 거리 이름에서 지정된 거리의 종류입니다.</p>
<p>최대 길이: 10자</p></td>
</tr>
<tr class="even">
<td><p><em>UpdateValidationStatus</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>이 매개 변수를 포함하면 이 cmdlet을 통해 주소의 유효성을 검사했는지 여부에 따라 구/군/시 주소의 MSAGValid 속성이 변경됩니다. 주소가 유효한 경우 MSAGValid가 True로 설정됩니다. 이 매개 변수를 생략하면 MSAGValid 값이 변경되지 않습니다.</p></td>
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

LIS(위치 정보 서버) 도시 주소 개체를 포함하는 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다.

## 참고 항목

#### 기타 리소스

[Get-CsLisCivicAddress](get-csliscivicaddress.md)

