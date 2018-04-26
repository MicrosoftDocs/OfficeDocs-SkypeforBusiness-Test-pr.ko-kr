---
title: New-CsTrustedApplicationComputer
TOCTitle: New-CsTrustedApplicationComputer
ms:assetid: 5c44a596-7fca-49d3-a7cf-e22656698a28
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398405(v=OCS.15)
ms:contentKeyID: 49303763
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsTrustedApplicationComputer

 

_**마지막으로 수정된 항목:** 2015-03-09_

신뢰할 수 있는 응용 프로그램을 호스트하는 컴퓨터를 기존 풀에 추가합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsTrustedApplicationComputer -Identity <XdsGlobalRelativeIdentity> -Pool <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 FQDN Trust1.litwareinc.com이 포함된 새 컴퓨터를 TrustPool.litwareinc.com 풀에 추가합니다. Identity 매개 변수를 사용하여 새 컴퓨터의 FQDN을 지정하고 Pool 매개 변수를 사용하여 풀의 FQDN을 지정합니다. 신뢰할 수 있는 응용 프로그램 풀인 기존 풀이 있어야 합니다. 참고: 신뢰할 수 있는 응용 프로그램 풀을 만들려면 **New-CsTrustedApplicationPool** cmdlet을 호출하십시오.

    New-CsTrustedApplicationComputer -Identity Trust1.litwareinc.com -Pool TrustPool.litwareinc.com

## 자세한 정보

Lync Server 배포 내에서 신뢰할 수 있는 응용 프로그램을 실행하는 컴퓨터는 신뢰할 수 있는 응용 프로그램 전용으로 사용되는 별도의 풀에 추가하는 것이 좋습니다. 그러나 다용도로 사용되는 기존 풀에 신뢰할 수 있는 응용 프로그램 컴퓨터를 추가할 수도 있습니다. 기본적으로 풀을 만들 때 풀과 동일한 FQDN(정규화된 도메인 이름)을 사용하는 컴퓨터도 생성됩니다. 새 컴퓨터를 만들고 풀에 추가하려면 이 cmdlet을 사용합니다.

이 cmdlet이 제대로 실행되려면 기존의 신뢰할 수 있는 응용 프로그램 풀이 있어야 합니다. 또한 ExternalServer 역할 이외의 서비스 역할이 포함된 풀에 또 다른 신뢰할 수 있는 응용 프로그램 컴퓨터를 추가할 수 없습니다. 예를 들어 풀이 Registrar 또는 CentralMgmt 역할을 지원하는 경우 풀에는 하나의 신뢰할 수 있는 응용 프로그램 컴퓨터만 포함할 수 있습니다. 또한 **New-CsTrustedApplicationPool** cmdlet을 호출하여 풀을 만들 때 기본 컴퓨터에 대해 컴퓨터 FQDN을 지정하지 않은 경우 컴퓨터는 풀과 동일한 FQDN을 갖게 되고 다른 컴퓨터는 추가할 수 없습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsTrustedApplicationComputer** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsTrustedApplicationComputer"}

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
<td><p>신뢰할 수 있는 응용 프로그램을 호스트하는 컴퓨터의 FQDN입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Pool</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>신뢰할 수 있는 응용 프로그램 컴퓨터를 호스트하는 풀의 FQDN입니다. <strong>Get-CsTrustedApplicationPool</strong> cmdlet을 실행하여 사용 가능한 풀을 찾을 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
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

없음.

## 반환 형식

Microsoft.Rtc.Management.Xds.DisplayComputer 유형의 개체를 만듭니다.

## 참고 항목

#### 기타 리소스

[Remove-CsTrustedApplicationComputer](remove-cstrustedapplicationcomputer.md)  
[Get-CsTrustedApplicationComputer](get-cstrustedapplicationcomputer.md)  
[New-CsTrustedApplicationPool](new-cstrustedapplicationpool.md)  
[Get-CsTrustedApplicationPool](get-cstrustedapplicationpool.md)

