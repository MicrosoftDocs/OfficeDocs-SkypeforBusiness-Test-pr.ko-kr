---
title: Remove-CsNetworkSite
TOCTitle: Remove-CsNetworkSite
ms:assetid: 07b543a6-3aa0-4fce-85f9-9ddc75d7b14f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398135(v=OCS.15)
ms:contentKeyID: 49302713
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsNetworkSite

 

_**마지막으로 수정된 항목:** 2015-03-09_

CAC(통화 허용 제어) 또는 E9-1-1(Enhanced 9-1-1)에 대해 정의된 네트워크 사이트를 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsNetworkSite -Identity <XdsGlobalRelativeIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 ID가 Vancouver인 사이트를 CAC 또는 E9-1-1 구성에서 제거합니다.

    Remove-CsNetworkSite -Identity Vancouver

## 예제 2

예제 2에서는 LowBWProfile이라는 대역폭 정책 프로필을 사용하는 모든 사이트를 CAC 또는 E9-1-1 구성에서 제거합니다. 먼저 **Get-CsNetworkSite** cmdlet을 호출하여 모든 네트워크 사이트를 검색합니다. 이 사이트 컬렉션은 BWPolicyProfileID가 LowBWProfile과 같은(-eq) 사이트로 컬렉션 검색 범위를 좁히는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 새 컬렉션은 이러한 사이트를 제거하는 **Remove-CsNetworkSite** cmdlet에 파이프됩니다.

    Get-CsNetworkSite | Where-Object {$_.BWPolicyProfileID -eq "LowBWProfile"} | Remove-CsNetworkSite

## 자세한 정보

네트워크 사이트는 각 CAC 또는 E9-1-1 배포 영역 내에 구성된 사무실 또는 위치입니다. 이 cmdlet은 CAC 또는 E9-1-1 구성에서 사이트를 제거합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsNetworkSite** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsNetworkSite"}

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
<td><p>제거할 네트워크 사이트의 고유 식별자입니다. 사이트는 전역 범위에서만 만들어지므로 범위는 지정할 필요가 없습니다. 사이트 ID만 지정하면 됩니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.DisplayNetworkSiteType 개체입니다. 네트워크 사이트 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다. Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.DisplayNetworkSiteType 유형의 개체를 제거합니다.

## 참고 항목

#### 기타 리소스

[New-CsNetworkSite](new-csnetworksite.md)  
[Set-CsNetworkSite](set-csnetworksite.md)  
[Get-CsNetworkSite](get-csnetworksite.md)

