---
title: Remove-CsQoEConfiguration
TOCTitle: Remove-CsQoEConfiguration
ms:assetid: 3b50e857-c524-4aad-b191-d324fc7c837c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425879(v=OCS.15)
ms:contentKeyID: 49303364
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsQoEConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

QoE(Quality of Experience) 설정 컬렉션을 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsQoEConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 **Remove-CsQoEConfiguration** cmdlet을 사용하여 Redmond 사이트에 할당된 QoE 설정을 제거합니다. Identity 매개 변수를 사용하면 지정된 사이트에 할당된 설정만 제거됩니다.

    Remove-CsQoEConfiguration -Identity site:Redmond

## 예제 2

예제 2에 표시된 명령은 사이트 범위에서 할당된 모든 QoE 설정을 제거합니다. 이 작업을 수행하기 위해 이 명령은 먼저 **Get-CsQoEConfiguration** cmdlet 및 Filter 매개 변수를 사용하여 적절한 QoE 설정을 검색합니다. 와일드카드 문자열 "site:\*"는 Identity가 문자열 값 site:으로 시작하는 설정만 반환되도록 합니다. 그런 다음 필터링된 컬렉션은 컬렉션의 모든 항목을 삭제하는 **Remove-CsQoEConfiguration** cmdlet에 전달됩니다.

    Get-CsQoEConfiguration -Filter site:* | Remove-CsQoEConfiguration

## 예제 3

예제 3에서는 KeepQoEDataForDays 속성이 30보다 작은 모든 QoE 설정이 삭제됩니다. 이 작업을 수행하기 위해 먼저 매개 변수 없이 **Get-CsQoEConfiguration** cmdlet을 호출하여 조직에서 현재 사용 중인 모든 QoE 설정 컬렉션을 반환합니다. 이 컬렉션은 KeepQoEDataForDays 속성이 30보다 작은(-lt) 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CsQoEConfiguration** cmdlet에 파이프됩니다.

    Get-CsQoEConfiguration | Where-Object {$_.KeepQoEDataForDays -lt 30} | Remove-CsQoEConfiguration

## 자세한 정보

QoE 품질 기준은 손실된 네트워크 패킷 수, 백그라운드 노이즈, "지터"(패킷 지연의 차이) 크기 등 조직의 오디오 및 비디오 통화 품질을 추적합니다. 이러한 품질 기준은 통화 정보 기록과 같은 다른 데이터와 별도로 데이터베이스에 저장되므로 다른 데이터 기록에 관계없이 QoE를 설정 및 해제할 수 있습니다. 이 cmdlet을 사용하여 사이트 수준에서 QoE를 구성하는 설정을 제거할 수 있습니다. 전역 QoE 구성에 대해 이 cmdlet을 호출하면 모든 속성이 기본값으로 다시 설정됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsQoEConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsQoEConfiguration"}

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
<td><p>제거할 설정의 고유 식별자입니다. 가능한 값은 global 및 site:&lt;사이트 이름&gt;이며, 여기서 &lt;사이트 이름&gt;은 제거할 설정이 포함된 Lync Server 배포의 사이트 이름입니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.QoE.QoESettings 개체입니다. QoE 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값이나 개체를 반환하지 않습니다. 대신 Microsoft.Rtc.Management.WritableConfig.Settings.QoE.QoESettings 개체의 인스턴스를 제거합니다.

## 참고 항목

#### 기타 리소스

[New-CsQoEConfiguration](new-csqoeconfiguration.md)  
[Set-CsQoEConfiguration](set-csqoeconfiguration.md)  
[Get-CsQoEConfiguration](get-csqoeconfiguration.md)

