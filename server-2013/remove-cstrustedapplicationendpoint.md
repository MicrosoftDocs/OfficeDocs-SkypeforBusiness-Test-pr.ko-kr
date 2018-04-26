---
title: Remove-CsTrustedApplicationEndpoint
TOCTitle: Remove-CsTrustedApplicationEndpoint
ms:assetid: c9b96690-d8c2-47f7-bff3-706dbf68d75a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398837(v=OCS.15)
ms:contentKeyID: 49305018
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsTrustedApplicationEndpoint

 

_**마지막으로 수정된 항목:** 2015-03-09_

신뢰할 수 있는 응용 프로그램 끝점을 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsTrustedApplicationEndpoint -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 ID(여기서는 표시 이름)가 Endpoint 1인 끝점 대화 상대를 제거합니다. ID는 고유해야 하므로 이 명령은 최대 하나의 끝점을 제거합니다.

    Remove-CsTrustedApplicationEndpoint -Identity "Endpoint 1"

## 예제 2

이 예제에서는 tapp2 응용 프로그램에 연결된 모든 신뢰할 수 있는 응용 프로그램 끝점을 제거합니다. 이 작업을 수행하기 위해 먼저 **Get-CsTrustedApplicationEndpoint** cmdlet을 호출하고 ID tapp2를 ApplicationId 매개 변수에 전달합니다. 그러면 tapp2 신뢰할 수 있는 응용 프로그램과 연결된 끝점 컬렉션이 반환됩니다. 이 컬렉션은 컬렉션의 각 끝점을 제거하는 **Remove-CsTrustedApplicationEndpoint** cmdlet에 파이프됩니다. 이 **Get-CsTrustedApplicationEndpoint** cmdlet 호출은 여러 풀에서 응용 프로그램 ID가 tapp2인 끝점을 검색하므로 이 명령으로 인해 여러 풀에 있는 신뢰할 수 있는 응용 프로그램 끝점이 제거될 수 있습니다.

    Get-CsTrustedApplicationEndpoint -ApplicationId tapp2 | Remove-CsTrustedApplicationEndpoint

## 자세한 정보

신뢰할 수 있는 응용 프로그램 끝점은 신뢰할 수 있는 응용 프로그램으로 통화를 경로 지정할 수 있는 Active Directory 대화 상대 개체입니다. 이 cmdlet은 Active Directory 도메인 서비스에서 기존 끝점 대화 상대 개체를 제거합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsTrustedApplicationEndpoint** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsTrustedApplicationEndpoint"}

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
<td><p>제거할 응용 프로그램 끝점의 ID(대화 상대의 고유 이름), SIP 주소 또는 표시 이름입니다.</p></td>
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

Microsoft.Rtc.Management.ADConnect.Schema.OCSADApplicationContact 개체입니다. 신뢰할 수 있는 응용 프로그램 끝점 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다. Microsoft.Rtc.Management.ADConnect.Schema.OCSADApplicationContact 유형의 개체를 제거합니다.

## 참고 항목

#### 기타 리소스

[New-CsTrustedApplicationEndpoint](new-cstrustedapplicationendpoint.md)  
[Set-CsTrustedApplicationEndpoint](set-cstrustedapplicationendpoint.md)  
[Get-CsTrustedApplicationEndpoint](get-cstrustedapplicationendpoint.md)

