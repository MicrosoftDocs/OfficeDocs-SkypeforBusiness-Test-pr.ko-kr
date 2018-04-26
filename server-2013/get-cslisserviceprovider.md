---
title: Get-CsLisServiceProvider
TOCTitle: Get-CsLisServiceProvider
ms:assetid: 060b0b32-5787-487b-b1d9-7a0c7dd44d80
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398116(v=OCS.15)
ms:contentKeyID: 49302691
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsLisServiceProvider

 

_**마지막으로 수정된 항목:** 2015-03-09_

위치 유효성을 검사하기 위해 E9-1-1(Enhanced 9-1-1) 네트워크 경로 지정 공급자가 제공한 웹 서비스에 대한 정보를 검색합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsLisServiceProvider

## 예제

## 예제 1

**Get-CsLisServiceProvider** cmdlet에는 Verbose와 같은 Windows PowerShell 일반 매개 변수 외에 다른 매개 변수가 사용되지 않습니다. E9-1-1 구현에는 항상 하나의 서비스 공급자가 있으므로 이 cmdlet은 해당 서비스 공급자가 제공한 웹 서비스에 대한 정보를 검색합니다.

    Get-CsLisServiceProvider

## 자세한 정보

E9-1-1을 사용하는 Enterprise Voice 구현에서는 적절한 PSAP(Public Safety Answering Point)로 통화가 경로 지정되도록 먼저 E9-1-1 네트워크 경로 지정 공급자를 통해 응급 통화가 경로 지정되어야 합니다. PSAP는 경찰서, 소방서, 응급 구조대 등 가장 가까운 응급 서비스로 통화를 전달하는 미국의 기관입니다. 이를 위해 공급자는 마스터 주소 가이드와 대조하여 모든 위치가 유효한지 확인할 수 있는 위치 목록을 조직으로부터 제공 받아야 합니다. 이 cmdlet은 공급자 이름, 조직에서 위치를 보내는 데 사용할 웹 서비스의 URL 등 공급자에 대한 정보를 검색합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsLisServiceProvider** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsLisServiceProvider"}

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

[Remove-CsLisServiceProvider](remove-cslisserviceprovider.md)  
[Set-CsLisServiceProvider](set-cslisserviceprovider.md)

