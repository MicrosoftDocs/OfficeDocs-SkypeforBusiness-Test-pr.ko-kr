---
title: Remove-CsExUmContact
TOCTitle: Remove-CsExUmContact
ms:assetid: d79f7082-f58b-4cc3-a90d-230111e32850
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398946(v=OCS.15)
ms:contentKeyID: 49305191
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsExUmContact

 

_**마지막으로 수정된 항목:** 2015-03-09_

호스트된 Exchange 통합 메시징(UM)에 대한 자동 전화 교환 또는 구독자 액세스 연락처를 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsExUmContact -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 SIP 주소가 exumsa1@fabrikam.com인 Exchange UM 연락처를 제거합니다.

    Remove-CsExUmContact -Identity sip:exumsa1@fabrikam.com

## 예제 2

이 예제에서는 LineURI 값이 tel:425로 시작하는 모든 Exchange UM 연락처를 제거합니다. 이 명령의 첫 번째 부분은 LineURI -like "tel:425\*" 식을 필터로 사용하여 **Get-CsExUmContact** cmdlet을 Filter 매개 변수와 함께 호출합니다. 해당 필터는 와일드카드 문자열 tel:425\*와 일치하는 LineURI를 가진 Exchange UM 연락처 개체를 검색하도록 지정합니다. 다시 말해서 문자열 tel:425로 시작하고 임의의 문자 집합으로 끝나는 모든 회선 URI입니다. 해당 개체 컬렉션이 검색되고 나면 컬렉션의 모든 항목을 제거하는 **Remove-CsExUmContact** cmdlet에 컬렉션이 파이프됩니다.

    Get-CsExUmContact -Filter {LineURI -like "tel:425*"} | Remove-CsExUmContact

## 자세한 정보

Lync Server는 Exchange UM과 함께 작동하여 자동 전화 교환 및 구독자 액세스와 같은 여러 가지의 음성 관련 기능을 제공합니다. Exchange UM이 온-프레미스가 아니라 호스트된 서비스로 제공되는 경우 자동 전화 교환 및 구독자 액세스 기능을 적용하려면 Windows PowerShell을 사용하여 연락처 개체를 만들어야 합니다. 만든 모든 개체는 **Remove-CsExUmContact** cmdlet을 사용하여 제거할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 그룹의 구성원은 **Remove-CsExUmContact** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsExUmContact"}

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
<td><p>제거할 연락처 개체의 고유 식별자입니다. 연락처 ID는 네 가지 형식 중 하나를 사용하여 지정할 수 있는데, 이러한 형식은 1) 연락처의 SIP 주소, 2) 연락처의 UPN(사용자 계정 이름), 3) 도메인\로그온 형태인 연락처의 도메인 이름 및 로그인 이름(예: litwareinc\exum1) 및 4) 연락처의 Active Directory 표시 이름(예: Team Auto Attendant)입니다.</p>
<p>전체 데이터 형식: Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
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

Microsoft.Rtc.Management.ADConnect.Schema.OCSADExUmContact 개체입니다. Exchange UM 연락처 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 개체를 반환하지 않습니다. Microsoft.Rtc.Management.ADConnect.Schema.OCSADExUmContact 유형의 개체를 제거합니다.

## 참고 항목

#### 기타 리소스

[New-CsExUmContact](new-csexumcontact.md)  
[Set-CsExUmContact](set-csexumcontact.md)  
[Get-CsExUmContact](get-csexumcontact.md)  
[Move-CsExUmContact](move-csexumcontact.md)

