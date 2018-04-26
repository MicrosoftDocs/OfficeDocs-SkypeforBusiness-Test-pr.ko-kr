---
title: Get-CsDiagnosticConfiguration
TOCTitle: Get-CsDiagnosticConfiguration
ms:assetid: f642bdca-82bb-4c72-9558-7e5ec43565fd
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413034(v=OCS.15)
ms:contentKeyID: 49305544
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsDiagnosticConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 현재 사용 중인 진단 구성 설정에 대한 정보를 반환합니다. 진단 구성 설정은 지정된 도메인 또는 URI(Uniform Resource Identifier)와 주고받는 트래픽을 Lync Server 로그 파일에 기록할지 결정하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsDiagnosticConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsDiagnosticConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에서는 조직에서 현재 사용 중인 모든 진단 구성 설정에 대한 정보가 반환됩니다. 이 작업을 수행하기 위해 매개 변수 없이 **Get-CsDiagnosticConfiguration** cmdlet을 호출합니다.

    Get-CsDiagnosticConfiguration

## 예제 2

예제 2에서는 Redmond 사이트(-Identity site:Redmond)에 적용된 진단 구성 설정에 대한 정보를 반환합니다.

    Get-CsDiagnosticConfiguration -Identity site:Redmond

## 예제 3

예제 3에 표시된 명령은 Redmond 사이트의 진단 구성 설정 내에 포함된 개별 필터에 대한 정보를 표시합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsDiagnosticConfiguration** cmdlet을 사용하여 Redmond 사이트의 설정을 반환합니다. 그런 다음 이 정보가 ExpandProperty 매개 변수를 사용하여 Filter 속성 값을 "확장"하는 **Select-Object** cmdlet에 파이프됩니다. Filter 속성을 확장하면 진단 구성 설정에서 유지 관리되는 개별 필터의 속성 및 속성 값에 액세스할 수 있습니다.

    Get-CsDiagnosticConfiguration -Identity site:Redmond | Select-Object -ExpandProperty Filter

## 예제 4

예제 4에 표시된 명령은 전역 진단 구성 설정에서 발견된 필터의 하위 집합을 반환합니다. 특히 Uri 속성에 SIP 주소 sip:diagnostics@litwareinc.com이 포함된 필터를 반환합니다. 이를 수행하기 위해 명령은 먼저 **Get-CsDiagnosticConfiguration** cmdlet을 사용하여 진단 구성 설정의 전역 인스턴스에 대한 모든 필터 정보를 반환합니다. 이 정보는 Filter 속성을 확장하는 **Select-Object** cmdlet에 파이프됩니다. 그런 다음 개별 필터 개체가 Uri 속성에 SIP 주소 sip:diagnostics@litwareinc.com이 포함된 필터만 추출하는 **Select-Object** cmdlet에 파이프됩니다.

    Get-CsDiagnosticConfiguration -Identity global | Select-Object -ExpandProperty Filter | Where-Object {$_.Uri -contains "sip:diagnostics@litwareinc.com"}

## 예제 5

예제 5는 예제 4에 표시된 명령의 변형입니다. 그러나 예제 5에서는 Uri 속성에 SIP 주소 sip:diagnostics@litwareinc.com이 포함되지 않은 경우에만 필터가 반환됩니다. 이 작업을 수행하기 위해 명령은 **Get-CsDiagnosticConfiguration** cmdlet을 호출하여 구성 설정의 전역 인스턴스에 대한 모든 진단 구성 정보를 반환합니다. 이 정보는 Filter 속성을 확장하는 **Select-Object** cmdlet에 파이프됩니다. 그런 다음 이러한 필터 개체가 Uri 속성에 SIP 주소 sip:diagnostics@litwareinc.com이 포함되지 않은 필터만 선택하는 **Select-Object** cmdlet에 파이프됩니다.

    Get-CsDiagnosticConfiguration -Identity global | Select-Object -ExpandProperty Filter | Where-Object {$_.Uri -notcontains "sip:diagnostics@litwareinc.com"}

## 자세한 정보

Lync Server에 대해 로깅을 사용하도록 설정하면 기본적으로 모든 도메인 또는 URI에서 들어오거나 나가는 트래픽이 이러한 로그 파일에 포함됩니다. 이렇게 하면 로그 파일에 가능한 한 많은 정보가 기록됩니다.

그러나 너무 많은 정보가 기록되는 경우도 있습니다. 예를 들어 특정 도메인과 연결하는 데 문제가 있는 경우 사용자 네트워크와 해당 도메인 간의 트래픽 로깅을 제한하는 것이 좋습니다. 이렇게 하면 관련 기록을 쉽게 식별할 수 있으므로 문제를 더 쉽게 진단하고 해결할 수 있습니다.

진단 구성 설정을 사용하면 로그 파일에 기록되는 도메인 또는 URI를 지정할 수 있습니다. Lync Server를 사용하여 사이트 범위에서 진단 구성 설정을 만들 수 있습니다. 따라서 다른 사이트에 적용한 것과 다른 설정을 Redmond 사이트에 적용할 수 있습니다.

**Get-CsDiagnosticConfiguration** cmdlet을 사용하면 조직에서 현재 사용 중인 진단 구성 설정에 대한 정보를 반환할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsDiagnosticConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsDiagnosticConfiguration"}

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
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>반환할 설정 컬렉션을 지정할 때 와일드카드 문자를 활용하는 데 사용됩니다. 예를 들어 -Filter &quot;site:*&quot; 구문은 사이트 범위에서 구성된 모든 설정을 -Filter &quot;site:*&quot; 구문을 사용하고,</p>
<p>Filter 매개 변수와 Identity 매개 변수를 같은 명령에 함께 사용할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환할 진단 구성 설정의 고유 식별자입니다. 사이트 범위에 구성된 설정을 반환하려면 -Identity &quot;site:Redmond&quot;와 유사한 구문을 사용합니다. 전역 설정을 반환하려면 -Identity global 구문을 사용합니다.</p>
<p>이 매개 변수가 지정되지 않으면 현재 사용 중인 모든 진단 구성 설정이 반환됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 진단 구성 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsDiagnosticConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsDiagnosticConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Diagnostics.DiagnosticFilterSettings 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsDiagnosticConfiguration](new-csdiagnosticconfiguration.md)  
[Remove-CsDiagnosticConfiguration](remove-csdiagnosticconfiguration.md)  
[Set-CsDiagnosticConfiguration](set-csdiagnosticconfiguration.md)

