---
title: Set-CsDiagnosticConfiguration
TOCTitle: Set-CsDiagnosticConfiguration
ms:assetid: 26463da9-cd6a-4ea3-961c-2570a8801cba
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425734(v=OCS.15)
ms:contentKeyID: 49303091
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsDiagnosticConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존의 진단 구성 설정을 수정합니다. 진단 필터 설정은 지정된 도메인 또는 URI(Uniform Resource Identifier)와 주고받는 트래픽을 Lync Server 로그 파일에 기록할지 결정하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsDiagnosticConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsDiagnosticConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Filter <Filter>] [-Force <SwitchParameter>] [-LogAllSipHeaders <$true | $false>] [-LoggingShare <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 **New-CsDiagnosticsFilter** cmdlet을 사용하여 새 진단 필터를 만든 다음 해당 새 필터를 전역 진단 구성 설정에 할당합니다. 이 작업을 수행하기 위해 첫 번째 명령은 **New-CsDiagnosticsFilter** cmdlet을 호출하여 메모리에만 나타나는 진단 필터를 만듭니다. 이 필터는 FQDN fabrikam.com과 URI sip:user@fabrikam.com을 사용합니다. 그런 다음 "가상" 필터는 변수 $x에 저장됩니다.

명령 2에서는 **Set-CsDiagnosticConfiguration** cmdlet을 사용하여 전역 진단 구성 설정에 새 필터를 할당합니다. 이 경우 Filter 속성의 기존 값이 새로 만든 필터로 대체됩니다.

    $x = New-CsDiagnosticsFilter -Fqdn fabrikam.com -Uri sip:user@fabrikam.com 
    Set-CsDiagnosticConfiguration -Identity global -Filter $x

## 예제 2

예제 2에서는 전역 진단 구성 설정의 Filter 속성에 새 FQDN을 추가하는 방법을 보여 줍니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 **Get-CsDiagnosticConfiguration** cmdlet을 사용하여 전역 설정에 대한 Filter 속성 값을 검색합니다. 이를 위해 **Get-CsDiagnosticConfiguration** cmdlet에 대한 호출을 괄호로 묶습니다. 그러면 Windows PowerShell 명령줄 인터페이스가 해당 명령을 우선적으로 실행합니다. 전역 설정이 반환된 후 Filter 속성 값이 추출되고 변수 $x에 저장됩니다.

두 번째 명령에서는 Add 메서드를 사용하여 새 FQDN(fabrikam.com)을 필터에 추가합니다. 이 작업이 완료되면 예제의 마지막 명령이 **Set-CsDiagnosticConfiguration** cmdlet을 사용하여 수정된 진단 모음을 저장합니다. 최종적으로 fabrikam.com이 이미 Filter 속성에 포함된 FQDN에 추가됩니다.

    $x = (Get-CsDiagnosticConfiguration -Identity global).Filter
    $x.Fqdn.Add("fabrikam.com")
    Set-CsDiagnosticConfiguration -Identity global -Filter $x

## 예제 3

예제 3에 표시된 명령은 FQDN(fabrikam.com)을 전역 진단 필터 구성 설정의 Filter 속성에서 제거합니다. 예제의 첫 번째 명령은 **Get-CsDiagnosticConfiguration** cmdlet을 사용하여 전역 설정에 대한 Filter 속성의 현재 값을 검색합니다. 이 값은 변수 $x에 저장됩니다. 값이 검색된 후 Remove 메서드를 사용하여 FQDN fabrikam.com을 제거합니다. FQDN이 제거된 후 **Set-CsDiagnosticConfiguration** cmdlet을 사용하여 $x에 저장된 수정된 필터를 전역 설정에 기록합니다.

    $x = (Get-CsDiagnosticConfiguration -Identity global).Filter
    $x.Fqdn.Remove("fabrikam.com")
    Set-CsDiagnosticConfiguration -Identity global -Filter $x

## 예제 4

예제 4에서는 전역 진단 구성 설정의 Filter 속성에서 모든 항목을 제거합니다. 이 작업을 수행하기 위해 Filter 속성을 Null 값으로 설정합니다.

    Set-CsDiagnosticConfiguration -Identity global -Filter $Null

## 자세한 정보

Lync Server에 대해 로깅을 사용하도록 설정하면 기본적으로 모든 도메인 또는 URI에서 들어오거나 나가는 트래픽이 이러한 로그 파일에 포함됩니다. 이렇게 하면 로그 파일에 가능한 한 많은 정보가 기록됩니다.

그러나 너무 많은 정보가 기록되는 경우도 있습니다. 예를 들어 특정 도메인과 연결하는 데 문제가 있는 경우 사용자 네트워크와 해당 도메인 간의 트래픽 로깅을 제한하는 것이 좋습니다. 이렇게 하면 관련 기록을 쉽게 식별할 수 있으므로 문제를 더 쉽게 진단하고 해결할 수 있습니다.

진단 구성 설정을 사용하면 로그 파일에 기록되는 도메인 또는 URI를 지정할 수 있습니다. Lync Server를 사용하여 사이트 범위에서 진단 구성 설정을 만들 수 있습니다. 따라서 다른 사이트에 적용한 것과 다른 설정을 Redmond 사이트에 적용할 수 있습니다.

**Set-CsDiagnosticConfiguration** cmdlet을 사용하여 지정된 컬렉션에서 필터를 추가하거나 제거할 수도 있습니다. 필터는 트래픽을 기록해야 하는 도메인을 표시하는 데 사용됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsDiagnosticConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsDiagnosticConfiguration"}

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
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.Diagnostics.Filter</p></td>
<td><p>트래픽을 기록할 도메인 및 URI의 컬렉션입니다. Filter 속성은 다음 세 개의 항목으로 구성되며 <strong>New-CsDiagnosticsFilter</strong> cmdlet을 사용하여 만들어야 합니다.</p>
<p>Fqdn - 필터에 포함할 도메인 컬렉션입니다. 자세히 말해 SIP 주소의 호스트 부분입니다. 예를 들어 FQDN(정규화된 도메인 이름)은 fabrikam.com과 같을 수 있습니다. 또는 와일드카드를 사용하여 여러 도메인을 *.fabrikam.com과 같이 나타낼 수 있습니다. 단일 필터에 둘 이상의 도메인을 포함할 수 있습니다.</p>
<p>Uri - 필터에 포함할 URI 컬렉션입니다. URI는 SIP 주소의 user@host 부분을 나타냅니다. URI는 다음 패턴으로 구성될 수 있습니다. user@fabrikam.com, user@*, *@fabrikam.com 패턴 중 하나로 구성될 수 있습니다. 단일 필터에 여러 개의 URI를 포함할 수 있습니다.</p>
<p>Enabled - 필터를 활성화해야 할지 여부를 나타냅니다.</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>수정할 진단 구성 설정의 고유 식별자입니다. 사이트 범위에서 구성된 설정을 수정하려면 -Identity &quot;site:Redmond&quot;와 유사한 구문을 사용합니다. 또한 전역 설정을 수정하려면 -Identity global 구문을 사용합니다.</p>
<p>이 매개 변수를 지정하지 않으면 <strong>Set-CsDiagnosticConfiguration</strong> cmdlet이 전역 설정을 자동으로 수정합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>DiagnosticFilterSettings 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>LogAllSipHeaders</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>False로 설정하면 핵심 SIP 헤더만 로그에 기록됩니다. 이 값을 False로 설정하면 로그 파일의 크기를 줄일 수 있습니다. 값을 True로 설정하면 모든 SIP 헤더가 기록됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LoggingShare</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>진단 로그를 업로드할 수 있는 공유 폴더입니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.Diagnostics.DiagnosticFilterSettings 개체입니다. **Set-CsDiagnosticConfiguration** cmdlet은 진단 구성 설정 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Set-CsDiagnosticConfiguration** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Diagnostics.DiagnosticFilterSettings 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[Get-CsDiagnosticConfiguration](get-csdiagnosticconfiguration.md)  
[New-CsDiagnosticConfiguration](new-csdiagnosticconfiguration.md)  
[New-CsDiagnosticsFilter](new-csdiagnosticsfilter.md)  
[Remove-CsDiagnosticConfiguration](remove-csdiagnosticconfiguration.md)

