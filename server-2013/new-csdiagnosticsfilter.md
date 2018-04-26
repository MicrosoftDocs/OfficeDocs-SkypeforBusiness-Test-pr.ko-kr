---
title: New-CsDiagnosticsFilter
TOCTitle: New-CsDiagnosticsFilter
ms:assetid: f1af92b1-4d1f-4eb3-9874-7fa6f6ae39c5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413009(v=OCS.15)
ms:contentKeyID: 49305498
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsDiagnosticsFilter

 

_**마지막으로 수정된 항목:** 2015-03-09_

진단 구성 설정에 사용할 새 진단 필터를 만듭니다. 진단 구성 설정은 지정된 도메인 또는 URI(Uniform Resource Identifier)와 주고받는 트래픽을 Lync Server 로그 파일에 기록할지 결정하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsDiagnosticsFilter [-Enabled <$true | $false>] [-ExcludeConferenceMessages <$true | $false>] [-ExcludePresenceNotifications <$true | $false>] [-ExcludeRegisterMessages <$true | $false>] [-ExcludeSubscribeMessages <$true | $false>] [-ExcludeSuccessfulRequests <$true | $false>] [-Fqdn <PSListModifier>] [-Uri <PSListModifier>]

## 예제

## 예제 1

예제 1에 표시된 명령은 **New-CsDiagnosticsFilter** cmdlet을 사용하여 새 진단 필터를 만든 다음 해당 필터를 전역 진단 구성 설정에 할당합니다. 이 작업을 수행하기 위해 첫 번째 명령은 **New-CsDiagnosticsFilter** cmdlet을 호출하여 메모리에만 나타나는 진단 필터를 만듭니다. 이 필터는 필터에 FQDN fabrikam.com 및 URI user@fabrikam.com을 추가합니다. 또한 이 명령은 Enabled 속성을 True($True)로 설정하여 필터를 사용하도록 설정합니다. 그러면 결과 가상 필터가 $x 변수에 저장됩니다.

두 번째 명령에서는 **Set-CsDiagnosticConfiguration** cmdlet을 사용하여 전역 진단 구성 설정에 새 필터를 할당합니다. 이 경우 Filter 속성의 기존 값이 $x에 저장된 새로 만든 필터로 대체됩니다.

    $x = New-CsDiagnosticsFilter -Fqdn "fabrikam.com" -Enabled $False
    Set-CsDiagnosticConfiguration -Identity global -Filter $x 

## 예제 2

예제 2에 표시된 명령은 예제 1에 표시된 명령의 변형입니다. 예제 2에서는 그러나 필터의 Fqdn 속성에 두 FQDN(fabrikam.com 및 contoso.com)을 추가합니다. 이 작업을 수행하기 위해 쉼표로 구분된 두 이름을 Fqdn 매개 변수의 매개 변수 값으로 사용합니다.

    $x = New-CsDiagnosticsFilter -Fqdn "fabrikam.com","contoso.com" -Enabled $False
    Set-CsDiagnosticConfiguration -Identity global -Filter $x

## 자세한 정보

Lync Server에 대해 로깅을 사용하도록 설정하면 기본적으로 모든 도메인 또는 URI에서 들어오거나 나가는 트래픽이 이러한 로그 파일에 포함됩니다. 이렇게 하면 로그 파일에 가능한 한 많은 정보가 기록됩니다.

반면 너무 많은 정보가 기록될 수도 있습니다. 예를 들어 특정 도메인과 연결하는 데 문제가 있는 경우 사용자 네트워크와 해당 도메인 간의 트래픽 로깅을 제한하는 것이 좋습니다. 이렇게 하면 관련 기록을 쉽게 식별할 수 있으므로 문제를 더 쉽게 진단하고 해결할 수 있습니다.

진단 구성 설정을 사용하면 로그 파일에 기록되는 도메인 또는 URI를 지정할 수 있습니다. 예를 들어 지정된 도메인과 주고받는 트래픽만 로깅할 수 있습니다. 전역 설정 외에도 Lync Server를 통해 사이트 범위 또는 서비스 범위(에지 서버 또는 등록자 서비스)에서 진단 필터 설정을 만들 수 있습니다. 따라서 다른 사이트에 적용한 것과 다른 설정을 Redmond 사이트에 적용할 수 있습니다.

**New-CsDiagnosticsFilter** cmdlet을 사용하면 진단 설정 컬렉션에 필터를 추가할 수 있습니다. 이 컬렉션에는 로그 파일에 트래픽이 기록될 도메인 및 URI가 포함됩니다. 필터가 추가되면 필터의 도메인 및 URI와 관련된 정보만 기록됩니다. 로깅을 위해 다른 도메인 및 URI에서 나가는 트래픽은 무시됩니다.

**New-CsDiagnosticsFilter** cmdlet은 메모리에만 나타나는 진단 필터 인스턴스를 만듭니다. 이러한 가상 필터 중 하나를 만든 후에는 **New-CsDiagnosticConfiguration** cmdlet이나 **Set-CsDiagnosticConfiguration** cmdlet을 사용하여 컬렉션에 필터를 추가해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsDiagnosticsFilter** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsDiagnosticsFilter"}

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
<td><p><em>Enabled</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>필터를 사용할지 여부를 지정합니다. 기본값은 True($True)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ExcludeConferenceMessages</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 전화 회의 메시지(즉, To 또는 From 헤더에 전화 회의 URI가 있는 모든 메시지)에 대한 정보가 로그 파일에 기록되지 않습니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ExcludePresenceNotifications</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 현재 상태 알림(즉, NOTIFY 또는 BENOTIFY 메서드를 사용하는 모든 메시지)에 대한 정보가 로그 파일에 기록되지 않습니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ExcludeRegisterMessages</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 클라이언트 등록(즉, REGISTER 메서드를 사용하는 모든 메시지)에 대한 정보가 로그 파일에 기록되지 않습니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ExcludeSubscribeMessages</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 클라이언트 구독(즉, SUBSCRIBE 메서드를 사용하는 모든 메시지)에 대한 정보가 로그 파일에 기록되지 않습니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ExcludeSuccessfulRequests</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 성공한 SIP 요청에 대한 정보가 로그 파일에 기록되지 않고 실패한 요청에 대한 정보만 저장됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Fqdn</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>필터에 포함할 도메인 컬렉션입니다. 자세히 말해 이러한 도메인은 SIP 주소의 호스트 부분을 나타냅니다. FQDN 속성에 대해 사용할 수 있는 FQDN(정규화된 도메인 이름)은 fabrikam.com과 같을 수 있습니다. 또는 와일드카드를 사용하여 여러 도메인을 나타낼 수 있습니다(예: *.fabrikam.com). 단일 필터에 둘 이상의 도메인이 있을 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Uri</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>필터에 포함할 URI 컬렉션입니다. URI는 SIP 주소의 user@host 부분입니다. URI는 다음 패턴으로 구성될 수 있습니다.</p>
<p>user@fabrikam.com</p>
<p>user@*</p>
<p>*@fabrikam.com</p>
<p>단일 필터에 여러 URI를 포함할 수 있습니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsDiagnosticsFilter** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsDiagnosticsFilter** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Diagnostics.Filter 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[New-CsDiagnosticConfiguration](new-csdiagnosticconfiguration.md)  
[Set-CsDiagnosticConfiguration](set-csdiagnosticconfiguration.md)

