---
title: New-CsDiagnosticConfiguration
TOCTitle: New-CsDiagnosticConfiguration
ms:assetid: 9028d9c1-e812-4055-bdf0-59cb83c6f50f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398733(v=OCS.15)
ms:contentKeyID: 49304368
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsDiagnosticConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 진단 구성 설정을 만듭니다. 진단 구성 설정은 지정된 도메인 또는 URI(Uniform Resource Identifier)와 주고받는 트래픽을 Lync Server 로그 파일에 기록할지 결정하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsDiagnosticConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Filter <Filter>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-LogAllSipHeaders <$true | $false>] [-LoggingShare <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 Redmond 사이트에 대한 새 진단 구성 설정 컬렉션을 만듭니다.

    New-CsDiagnosticConfiguration -Identity site:Redmond

## 예제 2

예제 2에 표시된 명령은 새 진단 필터를 만든 다음 해당 필터를 새 진단 설정 컬렉션에 할당합니다. 첫 번째 명령은 메모리 전용 진단 필터를 만들기 위해 **New-CsDiagnosticsFilter** cmdlet을 호출합니다. 이 경우 FQDN fabrikam.com과 URI sip:user@fabrikam.com이 필터에 추가됩니다. 또한 이 명령은 Enabled 속성을 True($True)로 설정하여 필터를 사용하도록 설정합니다. 그런 다음 결과 가상 필터가 $x 변수에 저장됩니다.

명령 2에서는 **New-CsDiagnosticConfiguration** cmdlet을 사용하여 Redmond 사이트에 대한 새 진단 구성 설정 컬렉션을 만듭니다. 이러한 새 설정은 변수 $x에 저장된 진단 필터를 사용하게 됩니다.

    $x = New-CsDiagnosticsFilter -Fqdn fabrikam.com -Uri "sip:user@fabrikam.com" -Enabled $False 
    
    New-CsDiagnosticConfiguration -Identity site:Redmond -Filter $x

## 예제 3

예제 3에 표시된 명령은 초기에 메모리에만 있는 진단 구성 설정을 만드는 방법을 보여 줍니다. 이 작업을 수행하기 위해 첫 번째 명령은 **New-CsDiagnosticConfiguration** cmdlet을 설정의 ID를 지정하는 Identity 및 새 설정을 메모리에만 만들도록 지정하는 InMemory의 두 매개 변수와 함께 호출합니다. 결과 개체는 $x 변수에 저장됩니다.

이러한 가상 설정이 만들어진 후 두 번째 명령을 사용하여 LoggingShare 속성을 UNC 경로 \\atl-fs-001\\logs로 구성합니다. 그런 다음 최종 명령을 사용하여 가상 진단 구성 설정을 Redmond 사이트에 적용되는 실제 설정 컬렉션으로 변환합니다. 이 마지막 명령은 필수입니다. **Set-CsDiagnosticConfiguration** cmdlet을 호출하지 않으면 Redmond 사이트에 아무런 설정이 적용되지 않으며, 해당 Windows PowerShell 세션을 종료하거나 $x 변수를 삭제하는 즉시 가상 설정이 사라집니다.

    $x = New-CsDiagnosticConfiguration -Identity site:Redmond -InMemory
    $x.LoggingShare = "\\atl-fs-001\logs"
    Set-CsDiagnosticConfiguration -Instance $x

## 자세한 정보

Lync Server에 대해 로깅을 사용하도록 설정하면 기본적으로 모든 도메인 또는 URI에서 들어오거나 나가는 트래픽이 이러한 로그 파일에 포함됩니다. 이렇게 하면 로그 파일에 가능한 한 많은 정보가 기록됩니다.

그러나 너무 많은 정보가 기록되는 경우도 있습니다. 예를 들어 특정 도메인과 연결하는 데 문제가 있는 경우 사용자 네트워크와 해당 도메인 간의 트래픽 로깅을 제한하는 것이 좋습니다. 이렇게 하면 관련 기록을 쉽게 식별할 수 있으므로 문제를 더 쉽게 진단하고 해결할 수 있습니다.

진단 구성 설정을 사용하면 로그 파일에 기록되는 도메인 또는 URI를 지정할 수 있습니다. 예를 들어 지정된 도메인과 주고받는 트래픽만 로깅할 수 있습니다. Lync Server를 사용하여 사이트 범위에서 진단 구성 설정을 만들 수 있습니다. 따라서 다른 사이트에 적용한 것과 다른 설정을 Redmond 사이트에 적용할 수 있습니다.

전역 범위에서는 진단 구성 설정을 만들 수 없습니다. 이것은 전역 범위에 이러한 설정이 이미 호스트되어 있기 때문입니다. 마찬가지로, 지정한 사이트에 진단 구성 설정이 이미 포함되어 있는 경우 사이트 범위에서 새 설정 컬렉션을 만들 수 없습니다. 예를 들어 Redmond 사이트에 대한 새 컬렉션을 만들려고 하는데 해당 사이트에 진단 구성 설정이 이미 호스트되어 있으면 명령이 실패합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsDiagnosticConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsDiagnosticConfiguration"}

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
<td><p>만들려는 진단 구성 설정의 고유 식별자입니다. 새 설정은 사이트 범위에서만 만들어질 수 있으므로 -Identity &quot;site:Redmond&quot;와 유사한 구문을 사용해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.Diagnostics.Filter</p></td>
<td><p>진단 필터링이 활성화된 경우 트래픽을 로깅할 도메인 및 URI 컬렉션입니다. Filter 속성은 다음 세 개의 항목으로 구성됩니다.</p>
<p>Fqdn – 필터에 포함할 도메인 컬렉션입니다. 자세히 말해 SIP 주소의 호스트 부분입니다. 예를 들어 FQDN(정규화된 도메인 이름)은 fabrikam.com과 같을 수 있습니다. 또는 와일드카드를 사용하여 여러 도메인을 *.fabrikam.com과 같이 나타낼 수 있습니다. 단일 필터에 둘 이상의 도메인을 포함할 수 있습니다.</p>
<p>Uri – 필터에 포함할 URI 컬렉션입니다. Uri는 SIP 주소의 user@host 부분입니다. Uri는 다음 패턴으로 구성될 수 있습니다. user@fabrikam.com, user@*, *@fabrikam.com 패턴 중 하나로 구성될 수 있습니다. 단일 필터에 여러 개의 URI를 포함할 수 있습니다.</p>
<p>Enabled – 필터를 활성화해야 할지 여부를 나타냅니다.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
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

없음. **New-CsDiagnosticConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsDiagnosticConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Diagnostics.DiagnosticFilterSettings의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsDiagnosticConfiguration](get-csdiagnosticconfiguration.md)  
[New-CsDiagnosticsFilter](new-csdiagnosticsfilter.md)  
[Remove-CsDiagnosticConfiguration](remove-csdiagnosticconfiguration.md)  
[Set-CsDiagnosticConfiguration](set-csdiagnosticconfiguration.md)

