---
title: Remove-CsCpsConfiguration
TOCTitle: Remove-CsCpsConfiguration
ms:assetid: 546343e1-a2e4-4bc0-bf6d-c8ae9bb3e690
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398358(v=OCS.15)
ms:contentKeyID: 49303654
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsCpsConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 통화 대기 서비스 구성을 제거합니다. 통화 대기는 사용자가 수신 전화 통화를 "대기"시킬 수 있는 서비스입니다. 통화를 대기하면 지정된 범위, 즉 파킹된 통화 번호의 번호에 통화가 전송되는 즉시 대기 상태가 됩니다. 원래 전화를 받았던 사람뿐만 아니라 모든 사람이 올바른 번호를 입력하여 대화를 다시 시작할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsCpsConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 **Remove-CsCpsConfiguration** cmdlet을 사용하여 ID가 site:Redmond1d인 통화 대기 서비스 구성을 삭제합니다. ID가 고유하므로 이 명령의 결과로 구성이 하나만 삭제됩니다.

    Remove-CsCpsConfiguration -Identity site:Redmond1

## 예제 2

예제 2에서는 서비스 범위에서 정의된 모든 통화 대기 서비스 구성이 삭제됩니다. 이 작업을 수행하기 위해 먼저 **Get-CsCpsConfiguration** cmdlet 및 Filter 매개 변수를 사용하여 사이트 범위에 정의된 모든 통화 대기 서비스 구성을 반환합니다. 와일드카드 site:\*는 ID가 문자열 값 site:으로 시작하는 설정만 반환되도록 합니다. 그런 다음, 필터링된 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CsCpsConfiguration** cmdlet에 파이프됩니다. 사이트에서 통화 대기 서비스 설정을 제거할 때마다 사이트는 전역 범위에 구성된 통화 대기 서비스 설정을 자동으로 사용하기 시작합니다.

    Get-CsCpsConfiguration -Filter site:* | Remove-CsCpsConfiguration

## 자세한 정보

이 cmdlet을 사용하여 통화 대기 서비스 구성을 제거합니다. 통화 대기 서비스 구성은 통화가 대기된 후 통화에 수행되는 작업을 지정합니다. 예를 들어 대기된 통화를 일정 기간 동안 받지 않을 경우 관리자 또는 응답 그룹과 같은 누군가에게 자동으로 전달할 수 있습니다. 통화를 잊지 않도록 일정 기간 후에 벨이 울리도록 통화를 구성할 수 있습니다. 또한 통화를 대기하는 동안 전화를 건 사람에게 음악이 들리도록 통화 대기 서비스를 구성할 수도 있습니다.

이 cmdlet을 사용하여 Global 구성을 비롯한 모든 통화 대기 구성을 제거할 수 있습니다. 그러나 전역 구성의 경우 구성이 실제로 제거되지는 않고 대신 기본값으로 다시 설정됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsCpsConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsCpsConfiguration"}

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
<td><p>제거할 통화 대기 응용 프로그램 구성의 고유 식별자입니다. 이 식별자는 Global 또는 site:&lt;sitename&gt;이어야 하고 여기서 &lt;sitename&gt;은 구성이 적용되는 사이트의 이름입니다.</p></td>
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
<td><p>변경 작업을 수행하기 전에 표시되는 모든 확인 메시지를 표시하지 않습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.CallParkServiceSettings.CallParkServiceSettings 개체입니다. 통화 대기 서비스 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.CallParkServiceSettings.CallParkServiceSettings 유형의 개체를 제거합니다.

## 참고 항목

#### 기타 리소스

[New-CsCpsConfiguration](new-cscpsconfiguration.md)  
[Set-CsCpsConfiguration](set-cscpsconfiguration.md)  
[Get-CsCpsConfiguration](get-cscpsconfiguration.md)  
[Set-CsCallParkServiceMusicOnHoldFile](set-cscallparkservicemusiconholdfile.md)

