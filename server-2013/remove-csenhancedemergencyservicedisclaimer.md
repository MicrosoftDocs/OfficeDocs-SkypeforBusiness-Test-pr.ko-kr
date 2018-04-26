---
title: Remove-CsEnhancedEmergencyServiceDisclaimer
TOCTitle: Remove-CsEnhancedEmergencyServiceDisclaimer
ms:assetid: 30a5aa8c-04b8-4c1f-92b3-88c86bf69a52
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425810(v=OCS.15)
ms:contentKeyID: 49303212
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsEnhancedEmergencyServiceDisclaimer

 

_**마지막으로 수정된 항목:** 2015-03-09_

E9-1-1(Enhanced 9-1-1) 구현에 대한 위치 정보를 확인하기 위해 전체적으로 사용되는 고지 사항 텍스트를 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsEnhancedEmergencyServiceDisclaimer -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 명령은 향상된 응급 서비스 고지 사항 텍스트를 제거합니다. 전역 고지 사항은 제거되지 않고 그대로 있으며, 단순히 Body 속성이 빈 문자열로 설정됩니다.

    Remove-CsEnhancedEmergencyServiceDisclaimer -Identity global

## 자세한 정보

Enterprise Voice 구현에서 E9-1-1 서비스를 제공하려면 발신자의 위치를 식별할 수 있도록 포트, 서브넷, 스위치 및 무선 액세스 지점에 위치를 매핑해야 합니다. 발신자가 이러한 매핑된 지점 중 하나의 외부에서 연결한 경우 응급 서비스를 받으려면 자신의 위치를 수동으로 입력해야 합니다. 이 cmdlet은 위치 정보를 입력하지 않는 사용자에게 표시될 텍스트 문자열을 제거합니다. 이 메시지는 사용자 위치 정책의 LocationRequired 속성이 Disclaimer로 설정된 경우에만 표시됩니다. 위치 정책 설정은 **Get-CsLocationPolicy** cmdlet을 호출하여 검색할 수 있습니다. 이 경우 이 cmdlet을 호출하면 빈 메시지가 사용자에게 표시됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsEnhancedEmergencyServiceDisclaimer** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsEnhancedEmergencyServiceDisclaimer"}

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
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>이 값은 필수이며 Global로 설정되어야 합니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.Location.EnhancedEmergencyServiceDisclaimer 개체입니다. E9-1-1 고지 사항 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값이나 개체를 반환하지 않고 Microsoft.Rtc.Management.WritableConfig.Policy.Location.EnhancedEmergencyServiceDisclaimer 유형의 개체를 수정합니다.

## 참고 항목

#### 기타 리소스

[Set-CsEnhancedEmergencyServiceDisclaimer](set-csenhancedemergencyservicedisclaimer.md)  
[Get-CsEnhancedEmergencyServiceDisclaimer](get-csenhancedemergencyservicedisclaimer.md)  
[Get-CsLocationPolicy](get-cslocationpolicy.md)

