---
title: Remove-CsLocationPolicy
TOCTitle: Remove-CsLocationPolicy
ms:assetid: 8fb98533-6474-4071-a74c-ce3f6fa2d326
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398727(v=OCS.15)
ms:contentKeyID: 49304367
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsLocationPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

지정한 위치 정책을 제거합니다. 위치 정책은 911 통화에 응답하는 사람이 전화를 거는 데 사용된 장치나 전화의 전화 번호를 기준으로 발신자의 지리적 위치를 확인할 수 있도록 하는 Enhanced 9-1-1 서비스와 함께 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsLocationPolicy -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 **Remove-CsLocationPolicy** cmdlet을 사용하여 ID가 Reno인 위치 정책을 삭제합니다. 사용자별 정책이 제거되면 해당 정책이 할당되었던 사용자나 그룹은 자동으로 사이트에 대해 구성된 정책을 대신 사용합니다. 사이트에 대한 정책이 구성되지 않은 경우 이러한 사용자와 그룹은 전역 위치 정책을 사용합니다.

    Remove-CsLocationPolicy -Identity Reno

## 예제 2

예제 2에서는 EnhancedEmergencyServicesEnabled 속성이 False인 모든 위치 정책을 삭제합니다. 즉, E9-1-1을 활성화하지 않는 모든 위치 정책을 삭제합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsLocationPolicy** cmdlet을 사용하여 조직에서 현재 사용되고 있는 모든 위치 정책을 검색합니다. 이 컬렉션은 검색된 데이터를 EnhancedEmergencyServicesEnabled 속성이 False와 같은 정책으로 제한하는 필터를 적용하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 계속해서 컬렉션의 각 정책을 삭제하는 **Remove-CsLocationPolicy** cmdlet에 전달됩니다.

    Get-CsLocationPolicy | Where-Object {$_.EnhancedEmergencyServicesEnabled -eq $false} | Remove-CsLocationPolicy

## 자세한 정보

위치 정책은 E9-1-1 기능과 관련된 설정을 적용하는 데 사용되며, 사용자가 E9-1-1을 사용하도록 설정되어 있는지 여부를 확인하고, 설정된 경우 응급 통화에 대한 행동을 결정합니다. 예를 들어 위치 정책을 사용하여 응급 통화 번호(한국의 경우 119)를 정의하고, 회사 보안 부서에 자동으로 알림을 제공할지 여부, 통화를 경로 지정할 방법 등을 지정할 수 있습니다. 이 cmdlet은 기존 위치 정책을 제거합니다.

이 cmdlet은 사이트 및 사용자별 위치 정책을 제거할 뿐만 아니라 전역 위치 정책을 제거하는 데도 사용됩니다. 그러나 이 경우 정책은 실제로 제거되지 않으며 단순히 정책 설정이 기본값으로 다시 설정됩니다.

이 cmdlet을 사용자에게 할당된 사용자별 위치 정책에 대해 실행하면 삭제 확인 메시지가 표시됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsLocationPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsLocationPolicy"}

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
<td><p>제거할 위치 정책의 고유한 식별자입니다. 해당 정책을 기본값으로 다시 설정하는 전역 위치 정책을 제거하려면 Global 값을 사용합니다. 사이트 범위에서 만들어진 정책의 경우 이 값은 site:&lt;사이트 이름&gt; 형식으로 지정됩니다. 여기서 사이트 이름은 Lync Server 배포에 정의된 사이트 이름입니다(예: site:Redmond). 사용자별 범위에서 생성된 정책의 경우 이 값은 정책의 이름입니다(예: Bldg30Floor3Sector1).</p></td>
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
<td><p>이 매개 변수를 지정하면 확인 프롬프트가 무시되고 경고 통지 없이 삭제가 수행됩니다. 예를 들어, 사용자별 위치 정책이 하나 이상의 사용자에게 할당된 경우 이 매개 변수가 명령에 포함되어 있지 않으면 삭제하기 전에 확인 프롬프트가 표시됩니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.Location.LocationPolicy 개체입니다. 위치 정책 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Location.LocationPolicy 개체의 인스턴스를 제거합니다.

## 참고 항목

#### 기타 리소스

[New-CsLocationPolicy](new-cslocationpolicy.md)  
[Set-CsLocationPolicy](set-cslocationpolicy.md)  
[Get-CsLocationPolicy](get-cslocationpolicy.md)  
[Grant-CsLocationPolicy](grant-cslocationpolicy.md)  
[Test-CsLocationPolicy](test-cslocationpolicy.md)

