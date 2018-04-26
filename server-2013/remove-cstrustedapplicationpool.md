---
title: Remove-CsTrustedApplicationPool
TOCTitle: Remove-CsTrustedApplicationPool
ms:assetid: 93aa3381-e3fc-45df-840e-3d6d61a52fb3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398750(v=OCS.15)
ms:contentKeyID: 49304410
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsTrustedApplicationPool

 

_**마지막으로 수정된 항목:** 2015-03-09_

신뢰할 수 있는 응용 프로그램을 호스트하는 컴퓨터가 포함된 풀을 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsTrustedApplicationPool -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 FQDN이 TrustPool.litwareinc.com인 풀을 제거합니다. Identity 매개 변수를 사용하여 제거할 풀의 FQDN을 지정합니다. ID는 고유하므로 이 명령은 하나의 풀만 제거합니다.

    Remove-CsTrustedApplicationPool -Identity TrustPool.litwareinc.com

## 예제 2

이 예제에서는 풀의 FQDN이 문자열 “trust”로 시작하는 신뢰할 수 있는 풀을 모두 제거합니다. 명령의 첫 번째 부분은 Lync Server 인프라에 있는 모든 신뢰할 수 있는 응용 프로그램 풀의 컬렉션을 검색하는 **Get-CsTrustedApplicationPool** cmdlet에 대한 호출입니다. 이 컬렉션은 **Where-Object** cmdlet에 파이프됩니다. **Where-Object** cmdlet은 컬렉션의 각 항목에서 PoolFqdn이 와일드카드 문자열 trust\*와 일치하는지 여부를 확인합니다. 그러면 PoolFqdn이 문자열 trust로 시작하고 그 뒤에 임의의 문자가 이어지는 모든 신뢰할 수 있는 응용 프로그램 풀의 컬렉션을 얻을 수 있습니다. 마지막으로 이 컬렉션은 컬렉션의 모든 항목을 제거하는 **Remove-CsTrustedApplicationPool** cmdlet에 파이프됩니다.

    Get-CsTrustedApplicationPool | Where-Object {$_.PoolFqdn -match "trust*"} | Remove-CsTrustedApplicationPool

## 자세한 정보

Lync Server 배포 내에서 신뢰할 수 있는 응용 프로그램을 실행하는 컴퓨터는 신뢰할 수 있는 응용 프로그램 전용으로 사용되는 별도의 풀에 추가하는 것이 좋습니다. 그러나 다용도로 사용되는 기존 풀에 신뢰할 수 있는 응용 프로그램 컴퓨터를 추가할 수도 있습니다. 이 cmdlet은 기존 신뢰할 수 있는 응용 프로그램 풀을 제거합니다. 그러나 등록자 값이 없는 신뢰할 수 있는 응용 프로그램 풀은 제거할 수 없습니다. 신뢰할 수 있는 응용 프로그램 풀에 등록자가 할당되지 않은 경우 **Set-CsTrustedApplicationPool** cmdlet을 사용하여 등록자 값을 추가한 다음 풀을 제거해야 합니다.

풀을 제거하면 해당 풀과 연결된 컴퓨터, 응용 프로그램 및 응용 프로그램 끝점도 모두 제거됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsTrustedApplicationPool** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsTrustedApplicationPool"}

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
<td><p>제거할 풀의 FQDN(정규화된 도메인 이름) 또는 서비스 ID입니다.</p></td>
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

Microsoft.Rtc.Management.Xds.DisplayExternalServer 개체입니다. 신뢰할 수 있는 응용 프로그램 풀 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다. Microsoft.Rtc.Management.Xds.DisplayExternalServer 유형의 개체를 제거합니다.

## 참고 항목

#### 기타 리소스

[New-CsTrustedApplicationPool](new-cstrustedapplicationpool.md)  
[Set-CsTrustedApplicationPool](set-cstrustedapplicationpool.md)  
[Get-CsTrustedApplicationPool](get-cstrustedapplicationpool.md)

