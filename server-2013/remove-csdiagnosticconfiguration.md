---
title: Remove-CsDiagnosticConfiguration
TOCTitle: Remove-CsDiagnosticConfiguration
ms:assetid: b15293bf-d0d1-4322-ab1d-10b54636746a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412853(v=OCS.15)
ms:contentKeyID: 49304750
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsDiagnosticConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 현재 사용 중인 진단 구성 설정 컬렉션을 하나 이상 제거합니다. 진단 필터 설정은 지정된 도메인 또는 URI(Uniform Resource Identifier)와 주고받는 트래픽을 Lync Server 로그 파일에 기록할지 결정하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsDiagnosticConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 ID가 site:Redmond인 진단 구성 설정을 삭제합니다.

    Remove-CsDiagnosticConfiguration -Identity site:Redmond

## 예제 2

예제 2에 표시된 명령은 사이트 범위에서 구성된 모든 진단 구성 설정을 삭제합니다. 이 작업을 수행하기 위해 명령은 **Get-CsDiagnosticConfiguration** cmdlet을 Filter 매개 변수와 함께 호출합니다. 필터 값 "site:\*"는 반환된 데이터를 ID가 문자 "service:"으로 시작하는 설정으로 제한합니다. 필터링된 컬렉션은 해당 컬렉션의 각 항목을 제거하는 **Remove-CsDiagnosticConfiguration** cmdlet에 파이프됩니다.

    Get-CsDiagnosticConfiguration -Filter site:* | Remove-CsDiagnosticConfiguration

## 예제 3

예제 3에서는 명령이 조직에서 현재 사용 중인 모든 진단 구성 설정을 삭제합니다. 이 작업을 수행하기 위해 먼저 **Get-CsDiagnosticConfiguration** cmdlet을 매개 변수 없이 호출하여 조직에서 현재 사용 중인 모든 진단 구성 설정 컬렉션을 반환합니다. 이러한 항목은 컬렉션의 각 항목을 제거하는 **Remove-CsDiagnosticConfiguration** cmdlet에 파이프됩니다.

    Get-CsDiagnosticConfiguration | Remove-CsDiagnosticConfiguration

## 자세한 정보

Lync Server에 대해 로깅을 사용하도록 설정하면 기본적으로 모든 도메인 또는 URI에서 들어오거나 나가는 트래픽이 이러한 로그 파일에 포함됩니다. 이렇게 하면 로그 파일에 가능한 한 많은 정보가 기록됩니다.

그러나 너무 많은 정보가 기록되는 경우도 있습니다. 예를 들어 특정 도메인과 연결하는 데 문제가 있는 경우 사용자 네트워크와 해당 도메인 간의 트래픽 로깅을 제한하는 것이 좋습니다. 이렇게 하면 관련 기록을 쉽게 식별할 수 있으므로 문제를 더 쉽게 진단하고 해결할 수 있습니다.

진단 구성 설정을 사용하면 로그 파일에 기록되는 도메인 또는 URI를 지정할 수 있습니다. 진단 필터를 사용하도록 설정하면 지정된 도메인과 주고받는 트래픽만 로깅됩니다. Lync Server를 사용하여 진단 구성 설정을 만들고 사이트 범위에서 진단 필터를 적용할 수 있습니다. 따라서 Redmond 사이트 등에 필터링을 적용하고 다른 사이트에서는 필터링을 사용하지 않도록 설정할 수 있습니다.

**Remove-CsDiagnosticConfiguration** cmdlet을 사용하여 사이트 범위에서 만든 진단 구성 설정을 제거할 수 있습니다. 전역 진단 구성 설정에 대해 **Remove-CsDiagnosticConfiguration** cmdlet을 실행할 수도 있습니다. 그러나 이 경우 Lync Server에서 전역 컬렉션 삭제를 허용하지 않으므로 컬렉션이 삭제되지 않습니다. 대신, 전역 컬렉션을 제거하면 해당 컬렉션의 속성이 기본값으로 다시 설정됩니다. 이는 전역 컬렉션에 추가된 모든 필터가 제거됨을 의미합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsDiagnosticConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsDiagnosticConfiguration"}

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
<td><p>제거할 진단 구성 설정에 대한 고유 식별자입니다. 사이트 범위에서 구성된 설정을 제거하려면 -Identity &quot;site:Redmond&quot;와 유사한 구문을 사용합니다.</p>
<p>전역 구성 설정에 대해 <strong>Remove-CsDiagnosticConfiguration</strong> cmdlet을 실행할 수도 있습니다. 이 경우 -Identity global 구문을 사용합니다. 그러나 전역 설정이 실제로 제거되는 것이 아니라 전역 설정 내의 속성이 기본값으로 다시 설정됩니다.</p>
<p></p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.Diagnostics.DiagnosticFilterSettings 개체입니다. **Remove-CsDiagnosticConfiguration** cmdlet은 진단 필터 설정 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. **Remove-CsDiagnosticConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Diagnostics.DiagnosticFilterSettings 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsDiagnosticConfiguration](get-csdiagnosticconfiguration.md)  
[New-CsDiagnosticConfiguration](new-csdiagnosticconfiguration.md)  
[Set-CsDiagnosticConfiguration](set-csdiagnosticconfiguration.md)

