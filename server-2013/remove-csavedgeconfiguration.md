---
title: Remove-CsAVEdgeConfiguration
TOCTitle: Remove-CsAVEdgeConfiguration
ms:assetid: 98bceec5-ed9d-4574-b6bf-f51e0f414ca7
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398786(v=OCS.15)
ms:contentKeyID: 49304477
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsAVEdgeConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

액세스 에지 서비스를 실행하는 컴퓨터(A/V 에지 서버라고도 함)에 적용된 기존 구성 설정 컬렉션을 제거하는 데 사용됩니다. A/V 에지 서버를 사용하면 내부 사용자가 외부 사용자, 즉 내부 네트워크에 로그온하지 않은 사용자와 오디오 및 비디오 데이터를 공유할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsAVEdgeConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 site:Redmond인 A/V 에지 구성 설정을 제거합니다. 설정이 제거되면 Redmond 사이트의 A/V 에지 서버에 전역 구성 설정이 적용됩니다.

    Remove-CsAVEdgeConfiguration -Identity site:Redmond

## 예제 2

예제 2에서는 서비스 범위에 적용된 모든 A/V 에지 구성 설정을 제거합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsAVEdgeConfiguration** cmdlet을 Filter 매개 변수와 함께 호출합니다. 필터 값 "service:\*"는 서비스 범위에 구성된 설정만 반환되도록 합니다. 그런 다음 필터링된 컬렉션은 **Remove-CsAVEdgeConfiguration** cmdlet에 파이프되며, 여기서 컬렉션의 각 항목이 삭제됩니다.

    Get-CsAVEdgeConfiguration -Filter "service:*" | Remove-CsAVEdgeConfiguration

## 예제 3

예제 3의 명령은 MaxBandwidthPerUserKB 속성 값이 5,000KB/초 미만인 모든 A/V 에지 구성 설정을 삭제합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsAVEdgeConfiguration** cmdlet을 추가 매개 변수 없이 호출하여 현재 조직에서 사용 중인 모든 A/V 에지 설정의 컬렉션을 반환합니다. 이 컬렉션은 MaxBandwidthPerUserKB 속성이 5000 미만인 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 해당 컬렉션의 각 항목을 삭제하는 **Remove-CsAVEdgeConfiguration** cmdlet에 파이프됩니다.

    Get-CsAVEdgeConfiguration | Where-Object {$_.MaxBandwidthPerUserKB -lt 5000} | Remove-CsAVEdgeConfiguration

## 자세한 정보

A/V 에지 서버를 사용하면 회사 방화벽을 통해 오디오 및 비디오 트래픽을 교환할 수 있습니다. 특히 사용자가 인터넷을 통해 Lync Server에 액세스한 다음 방화벽 내에서 시스템에서 로그온한 사용자와 오디오 및 비디오 데이터를 교환할 수 있습니다. 에지 서버 구성 설정은 전역 범위, 사이트 범위 및 서비스 범위에서 할당될 수 있습니다. A/V 에지 구성 설정을 사용하여 관리자는 사용자 인증의 갱신 전 유효 기간을 관리하고 단일 사용자 또는 단일 포트에서 사용할 수 있는 대역폭의 크기를 제한하는 등의 작업을 수행할 수 있습니다.

**Remove-CsAVEdgeConfiguration** cmdlet을 사용하면 사이트 또는 서비스 범위에 적용된 A/V 에지 구성 설정을 삭제할 수 있습니다. 전역 설정에 대해서도 이 cmdlet을 실행할 수 있지만 이러한 전역 설정은 삭제되지 않습니다. 대신 전역 컬렉션 내에 포함된 속성이 기본값으로 다시 설정됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsAVEdgeConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsAVEdgeConfiguration"}

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
<td><p>제거할 A/V 에지 구성 설정 컬렉션에 대한 고유 식별자입니다. 전역 컬렉션을 &quot;제거&quot;하려면 -Identity global 구문을 사용합니다. 앞서 언급했듯이 전역 설정은 제거할 수 없으며 속성을 기본값으로 다시 설정하는 것만 가능합니다. 사이트 컬렉션을 제거하려면 -Identity site:Redmond 형태의 구문을 사용합니다. 서비스 범위에서 구성된 설정은</p>
<p>-Identity service:EdgeServer:atl-cs-001.litwareinc.com과 유사한 구문을 사용하여 참조해야 합니다.</p>
<p>정책 ID를 지정할 때는 와일드카드를 사용할 수 없습니다.</p></td>
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
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.Edge.MediaRelaySettings 개체입니다. **Remove-CsAVEdgeConfiguration** cmdlet은 미디어 릴레이 설정 개체의 파이프라인된 입력을 허용합니다. 이러한 개체는 **Get-CsAVEdgeConfiguration** cmdlet을 실행하여 검색합니다.

## 반환 형식

**Remove-CsAVEdgeConfiguration** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Edge.MediaRelaySettings 개체의 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsAVEdgeConfiguration](get-csavedgeconfiguration.md)  
[New-CsAVEdgeConfiguration](new-csavedgeconfiguration.md)  
[Set-CsAVEdgeConfiguration](set-csavedgeconfiguration.md)

