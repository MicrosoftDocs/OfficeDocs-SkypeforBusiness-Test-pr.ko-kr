---
title: New-CsAVEdgeConfiguration
TOCTitle: New-CsAVEdgeConfiguration
ms:assetid: b6bcf426-9037-4679-99dc-e94bfb8f72a6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412884(v=OCS.15)
ms:contentKeyID: 49304800
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsAVEdgeConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

A/V 에지 서비스를 실행하는 컴퓨터의 새 구성 설정 컬렉션을 만듭니다. 이러한 컴퓨터를 A/V 에지 서버라고도 합니다. A/V 에지 서버를 사용하면 내부 사용자가 외부 사용자, 즉 내부 네트워크에 로그온하지 않은 사용자와 오디오 및 비디오 데이터를 공유할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsAVEdgeConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-MaxBandwidthPerPortKb <UInt32>] [-MaxBandwidthPerUserKb <UInt32>] [-MaxTokenLifetime <TimeSpan>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Redmond 사이트의 새로운 A/V 에지 구성 설정 컬렉션을 만듭니다. 이 예제에서는 MaxTokenLifetime 속성을 4시간(04시간: 00분: 00초)으로 설정합니다.

    New-CsAVEdgeConfiguration -Identity site:Redmond -MaxTokenLifetime "04:00:00"

## 예제 2

예제 2에서는 새 A/V 에지 구성 설정 컬렉션을 메모리에 만든 다음 나중에 이러한 가상 설정을 실제 A/V 에지 설정 컬렉션으로 변환하는 방법을 보여 줍니다. 이 작업을 수행하기 위해 이 예제의 첫 번째 명령은 Redmond 사이트의 새로운 설정 컬렉션을 만듭니다. 이때 이러한 설정이 메모리에만 만들어지고 Redmond 사이트에 즉시 적용되지 않도록 InMemory 매개 변수를 추가합니다. 이러한 설정은 메모리에만 존재하기 때문에 변수에 저장되어야 합니다. 이 경우 변수는 $x입니다.

두 번째 명령에서는 MaxTokenLifetime 속성 값을 4시간(04시간: 00분: 00초)으로 설정합니다. 그런 다음 세 번째 명령은 **Set-CsAVEdgeConfiguration** cmdlet을 사용하여 $x에 저장된 설정을 Redmond 사이트에 적용합니다.

    $x = New-CsAVEdgeConfiguration -Identity site:Redmond -InMemory
    $x.MaxTokenLifetime = "04:00:00"
    Set-CsAVEdgeConfiguration -Instance $x

## 자세한 정보

A/V 에지 서버를 사용하면 회사 방화벽을 통해 오디오 및 비디오 트래픽을 교환할 수 있습니다. 특히 사용자가 인터넷을 통해 Lync Server에 액세스한 다음 방화벽 내에서 시스템에서 로그온한 사용자와 오디오 및 비디오 데이터를 교환할 수 있습니다. 에지 서버 구성 설정은 전역 범위, 사이트 범위 및 서비스 범위에서 할당될 수 있습니다. A/V 에지 구성 설정을 사용하여 관리자는 사용자 인증의 갱신 전 유효 기간을 관리하고 단일 사용자 또는 단일 포트에서 사용할 수 있는 대역폭의 크기를 제한할 수 있습니다.

**New-CsAVEdgeConfiguration** cmdlet을 사용하면 사이트 또는 서비스 범위에서 A/V 에지 구성 설정의 새 컬렉션을 만들 수 있습니다. 또한 위에서 언급했듯이 전역 범위에서 A/V 에지 설정을 구성할 수도 있습니다. 그러나 전역 범위에는 새 컬렉션을 만들 수 없습니다.

특정 사이트 또는 서비스에서는 A/V 에지 구성 설정 컬렉션을 최대 하나만 호스트할 수 있습니다. 예를 들어 ID가 site:Redmond인 새 컬렉션을 만들려는 경우 Redmond 사이트에서 A/V 에지 설정 컬렉션을 이미 호스트하고 있으면 작업이 실패합니다.

Microsoft 지원 담당자가 지시하지 않은 경우 기본 A/V 에지 구성 설정을 변경하지 않는 것이 좋습니다. 따라서 사이트 또는 서비스 설정의 새 컬렉션을 만들 필요가 없을 수도 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsAVEdgeConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsAVEdgeConfiguration"}

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
<td><p>만들려는 A/V 에지 구성 설정 컬렉션의 고유 식별자입니다. 사이트 범위에서 적용할 설정 컬렉션을 만들려면 -Identity site:Redmond와 유사한 구문을 사용합니다. A/V 에지 구성 설정 컬렉션이 Redmond 사이트에 이미 적용된 경우에는 이 명령이 실패합니다. 서비스 범위에 구성된 설정은 -Identity service:EdgeServer:atl-cs-001.litwareinc.com과 유사한 구문을 사용하여 참조해야 합니다.</p></td>
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
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaxBandwidthPerPortKb</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>단일 포트에 할당할 수 있는 대역폭의 최대 크기(초당 킬로바이트)를 나타냅니다. 최대 대역폭은 1에서 4294967296(4096기가비트) 사이의 정수 값으로 설정할 수 있으며, 기본값은 3000입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MaxBandwidthPerUserKb</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>사용자 한 명에게 할당할 수 있는 대역폭의 최대 크기(초당 킬로비트)를 나타냅니다. 최대 대역폭은 1에서 4294967296(4096기가비트) 사이의 정수 값으로 설정할 수 있으며, 기본값은 10000입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaxTokenLifetime</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>인증 토큰을 사용할 수 있는 최대 시간입니다. 이 시간이 지나면 인증 토큰이 만료되므로 갱신해야 합니다. 토큰 수명은 일 수.시간:분:초와 같은 형식으로 표시합니다. 예를 들어 13일은 일 수 뒤에 마침표(.)를 찍고 콜론(:)을 사용하여 시간, 분, 초를 구분한 다음과 같은 형식으로 표현해야 합니다.</p>
<p>13.00:00:00</p>
<p>기본값인 8시간은 다음과 같이 표현해야 합니다.</p>
<p>08:00:00</p>
<p>허용되는 최소 토큰 수명은 1분(00:01:00)이고, 최대 수명은 180일(180.00:00:00)입니다.</p>
<p></p></td>
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

없음. **New-CsAVEdgeConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.Edge.MediaRelaySettings 개체의 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsAVEdgeConfiguration](get-csavedgeconfiguration.md)  
[Remove-CsAVEdgeConfiguration](remove-csavedgeconfiguration.md)  
[Set-CsAVEdgeConfiguration](set-csavedgeconfiguration.md)

