---
title: Remove-CsRoutingConfiguration
TOCTitle: Remove-CsRoutingConfiguration
ms:assetid: 80239fed-89ef-4ccc-be9b-d9149182d0c3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398643(v=OCS.15)
ms:contentKeyID: 49304189
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsRoutingConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

경로 지정 구성을 기본 설정으로 다시 설정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsRoutingConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 유일한 경로 지정 구성인 Global 경로 지정 구성을 기본 설정으로 다시 설정합니다. 이 작업은 정의된 모든 음성 경로를 삭제하므로 제거가 발생하기 전에 작업을 수행할지 묻는 메시지가 표시되도록 Confirm 매개 변수를 추가했습니다.

    Remove-CsRoutingConfiguration -Identity Global -Confirm

## 자세한 정보

음성 경로는 Enterprise Voice 사용자의 통화를 PSTN(공중 전화망) 또는 PBX(Private Branch Exchange)의 전화 번호로 경로 지정하는 방법을 Lync Server에 지정하는 명령을 포함합니다. 이 cmdlet은 유일한 경로 지정 구성이며 Lync Server 배포에 정의된 모든 음성 경로에 대한 컨테이너인 전역 경로 지정 구성을 제거합니다. 경로 지정 구성을 "제거"해도 실제로 제거되지는 않으며 유일한 인스턴스인 전역 인스턴스가 계속 남아 있습니다. 그러나 음성 경로 목록이 기본 설정으로 설정됩니다.

경고: 경로 지정 구성을 제거(즉, 음성 경로 목록을 기본값으로 설정)하면 Lync Server 배포에 대해 정의된 모든 음성 경로가 삭제되고 기본 설정을 가진 단일 경로로 대체됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsRoutingConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsRoutingConfiguration"}

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
<td><p>제거할 경로 지정 구성의 범위입니다. 이 값은 Global이어야 합니다.</p></td>
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

Microsoft.Rtc.Management.Policy.Voice.PSTNRoutingSettings 개체입니다. 경로 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 Microsoft.Rtc.Management.Policy.Voice.PSTNRoutingSettings 유형의 개체를 제거(다시 설정)합니다.

## 참고 항목

#### 기타 리소스

[New-CsRoutingConfiguration](new-csroutingconfiguration.md)  
[Set-CsRoutingConfiguration](set-csroutingconfiguration.md)  
[Get-CsRoutingConfiguration](get-csroutingconfiguration.md)  
[Remove-CsVoiceRoute](remove-csvoiceroute.md)  
[Get-CsVoiceRoute](get-csvoiceroute.md)

