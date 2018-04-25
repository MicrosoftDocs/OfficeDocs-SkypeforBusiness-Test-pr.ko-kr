---
title: Remove-CsNetworkInterSitePolicy
TOCTitle: Remove-CsNetworkInterSitePolicy
ms:assetid: daf1afc8-cce4-4192-8ba4-05d26817198e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398963(v=OCS.15)
ms:contentKeyID: 49305236
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsNetworkInterSitePolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

CAC(통화 허용 제어) 구성 내에 직접 연결된 사이트 간 대역폭 제한을 정의하는 네트워크 사이트 간 정책을 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsNetworkInterSitePolicy -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 ID가 Reno\_Portland인 네트워크 사이트 정책을 제거합니다.

    Remove-CsNetworkInterSitePolicy -Identity Reno_Portland

## 예제 2

예제 2에서는 CAC 구성 내에 정의된 모든 네트워크 사이트 정책을 제거합니다. 먼저 **Get-CsNetworkInterSitePolicy** cmdlet을 호출하여 모든 네트워크 사이트 정책 컬렉션을 검색합니다. 이 컬렉션은 컬렉션의 각 항목을 제거하는 **Remove-CsNetworkInterSitePolicy** cmdlet에 파이프됩니다.

    Get-CsNetworkInterSitePolicy | Remove-CsNetworkInterSitePolicy

## 자세한 정보

네트워크 사이트에서 직접 연결을 공유하는 경우 이 두 사이트 간에 오디오 및 비디오 연결에 대한 대역폭 제한이 정의될 수 있습니다. 이 cmdlet은 직접 연결된 두 사이트에 대역폭 제한 정책을 적용하는 네트워크 사이트 정책을 제거합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsNetworkInterSitePolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsNetworkInterSitePolicy"}

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
<td><p>제거할 네트워크 사이트 정책의 고유 식별자입니다. 네트워크 사이트 정책은 전역 범위에서만 만들어지므로 이 식별자는 범위를 지정할 필요가 없습니다. 대신 해당 사이트 정책을 식별하는 고유 이름인 문자열을 포함합니다.</p></td>
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
<td><p>변경 내용을 적용하기 전에 표시될 수 있는 확인 메시지를 숨깁니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkSitePolicyType 개체입니다. 네트워크 사이트 간 정책 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다. Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.InterNetworkSitePolicyType 유형의 개체를 제거합니다.

## 참고 항목

#### 기타 리소스

[New-CsNetworkInterSitePolicy](new-csnetworkintersitepolicy.md)  
[Set-CsNetworkInterSitePolicy](set-csnetworkintersitepolicy.md)  
[Get-CsNetworkInterSitePolicy](get-csnetworkintersitepolicy.md)

