---
title: Remove-CsTrustedApplicationComputer
TOCTitle: Remove-CsTrustedApplicationComputer
ms:assetid: c9c0604b-a94e-42b9-9db3-bc3dbe686e41
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398838(v=OCS.15)
ms:contentKeyID: 49305020
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsTrustedApplicationComputer

 

_**마지막으로 수정된 항목:** 2015-03-09_

신뢰할 수 있는 응용 프로그램 컴퓨터를 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsTrustedApplicationComputer -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 FQDN이 Trust1.litwareinc.com인 컴퓨터를 제거합니다.

    Remove-CsTrustedApplicationComputer -Identity Trust1.litwareinc.com

## 예제 2

이 예제에서는 FQDN이 Trust 문자열로 시작하는 모든 신뢰할 수 있는 컴퓨터를 제거합니다. 먼저 **Get-CsTrustedApplicationComputer** cmdlet을 호출하고 Filter 매개 변수에 Trust\* 값을 전달합니다. 이렇게 하면 Trust로 시작하고 임의의 문자 집합으로 끝나는 FQDN을 가진 모든 신뢰할 수 있는 응용 프로그램 컴퓨터가 검색됩니다. 이 컴퓨터 컬렉션은 컬렉션의 각 항목(각 컴퓨터)을 제거하는 **Remove-CsTrustedApplicationComputer** cmdlet에 파이프됩니다. 이러한 컴퓨터를 제거하면 풀이 비는 경우에는 풀에서 컴퓨터가 제거되지 않습니다.

    Get-CsTrustedApplicationComputer -Filter Trust* | Remove-CsTrustedApplicationComputer

## 자세한 정보

Lync Server 배포 내에서 신뢰할 수 있는 응용 프로그램을 실행하는 컴퓨터는 신뢰할 수 있는 응용 프로그램 전용으로 사용되는 별도의 풀에 추가하는 것이 좋습니다. 그러나 다용도로 사용되는 기존 풀에 신뢰할 수 있는 응용 프로그램 컴퓨터를 추가할 수도 있습니다. 이 cmdlet을 사용하여 신뢰할 수 있는 응용 프로그램 컴퓨터를 제거할 수 있습니다.

이 cmdlet을 사용하여 신뢰할 수 있는 응용 프로그램 컴퓨터를 제거하면 신뢰할 수 있는 응용 프로그램 컴퓨터 목록뿐만 아니라 Lync Server에서 사용할 수 있는 컴퓨터 목록에서도 해당 컴퓨터가 제거됩니다. 즉, **Get-CsTrustedApplicationComputer** cmdlet 또는 **Get-CsComputer** cmdlet을 호출하면 해당 컴퓨터가 더 이상 나열되지 않습니다. 신뢰할 수 있는 응용 프로그램 컴퓨터가 풀에 있는 유일한 컴퓨터인 경우에는 제거할 수 없습니다. 풀에 있는 유일한 컴퓨터를 제거하려면 **Remove-CsTrustedApplicationPool** cmdlet을 호출하여 전체 풀을 제거해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsTrustedApplicationComputer** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsTrustedApplicationComputer"}

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
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>제거할 컴퓨터의 FQDN(정규화된 도메인 이름)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.Xds.DisplayComputer 개체입니다. 신뢰할 수 있는 응용 프로그램 컴퓨터 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다. Microsoft.Rtc.Management.Xds.DisplayComputer 유형의 개체를 제거합니다.

## 참고 항목

#### 기타 리소스

[New-CsTrustedApplicationComputer](new-cstrustedapplicationcomputer.md)  
[Get-CsTrustedApplicationComputer](get-cstrustedapplicationcomputer.md)  
[Remove-CsTrustedApplicationPool](remove-cstrustedapplicationpool.md)  
[Get-CsTrustedApplicationPool](get-cstrustedapplicationpool.md)

