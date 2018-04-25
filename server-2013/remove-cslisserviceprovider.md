---
title: Remove-CsLisServiceProvider
TOCTitle: Remove-CsLisServiceProvider
ms:assetid: d26302bf-7794-4125-af80-ba7c92096b6d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398904(v=OCS.15)
ms:contentKeyID: 49305123
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsLisServiceProvider

 

_**마지막으로 수정된 항목:** 2015-03-09_

위치 확인을 위해 E9-1-1(Enhanced 9-1-1) 네트워킹 경로 지정 공급자가 제공하는 웹 서비스에 대한 정보가 포함된 개체를 반환합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsLisServiceProvider [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 E9-1-1 구현에서 서비스 공급자 웹 서비스를 제거합니다. 이 cmdlet에서 제거할 서비스 공급자는 하나만 정의됩니다.

    Remove-CsLisServiceProvider

## 자세한 정보

E9-1-1을 사용하는 Enterprise Voice 구현에서는 적절한 PSAP(Public Safety Answering Point)로 통화가 경로 지정되도록 먼저 E9-1-1 네트워크 경로 지정 공급자를 통해 응급 통화가 경로 지정되어야 합니다. PSAP는 경찰서, 소방서, 응급 구조대 등 가장 가까운 응급 서비스로 통화를 전달하는 미국의 기관입니다. 이를 위해 공급자는 마스터 주소 가이드와 대조하여 모든 위치가 유효한지 확인할 수 있는 위치 목록을 조직으로부터 제공 받아야 합니다. 이 cmdlet은 공급자에 대한 항목을 제거합니다. 즉, 이 cmdlet을 실행하고 나면 공급자의 웹 서비스에 액세스하지 못하게 됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsLisServiceProvider** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsLisServiceProvider"}

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
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
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

LIS(위치 정보 서버) 서비스 공급자 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 개체나 값을 반환하지 않습니다. System.Management.Automation.PSCustomObject 유형의 개체를 제거합니다.

## 참고 항목

#### 기타 리소스

[Set-CsLisServiceProvider](set-cslisserviceprovider.md)  
[Get-CsLisServiceProvider](get-cslisserviceprovider.md)

