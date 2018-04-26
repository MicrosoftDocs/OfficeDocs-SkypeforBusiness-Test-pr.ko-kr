---
title: New-CsDiagnosticHeaderConfiguration
TOCTitle: New-CsDiagnosticHeaderConfiguration
ms:assetid: 5322e63e-c02c-4dec-8206-04f701258d6b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398350(v=OCS.15)
ms:contentKeyID: 49303640
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsDiagnosticHeaderConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 진단 헤더 구성 설정 컬렉션을 만듭니다. 진단 헤더 구성 설정은 SIP 메시지에 문제 해결과 오류 보고에 유용한 헤더 정보가 동반될지 여부를 결정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsDiagnosticHeaderConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-SendToExternalNetworks <$true | $false>] [-SendToOutsideUnauthenticatedUsers <$true | $false>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 Redmond 사이트(-Identity site:Redmond)에 대한 새 진단 헤더 구성을 만듭니다. ID를 지정하는 것 외에도 명령은 SendToOutsideAuthenticatedUsers 매개 변수와 매개 변수 값 $True를 사용합니다. 그러면 내부 네트워크 외부의 인증되지 않은 사용자에게 정보를 보낼 수 있습니다.

    New-CsDiagnosticHeaderConfiguration -Identity site:Redmond -SendToOutsideUnauthenticatedUsers $True

## 예제 2

예제 2에 표시된 명령은 처음에 메모리에만 있는 진단 헤더 설정 컬렉션을 만드는 방법을 보여 줍니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 Identity 및 InMemorys 매개 변수와 함께 **New-CsDiagnosticHeaderConfiguration** cmdlet을 호출합니다. 만들어진 개체는 변수 $x에 저장됩니다.

가상 설정이 만들어진 후에는 두 번째와 세 번째 명령을 사용하여 SendToOutsideUnauthenticatedUsers 속성 및 SendToExternalNetworks 속성의 값을 각각 수정합니다. 마지막으로 네 번째 명령을 사용하여 가상 진단 헤더 구성 설정을 Redmond 사이트에 적용되는 실제 설정 컬렉션으로 변환합니다. 이 마지막 명령은 필수입니다. **Set-CsDiagnosticHeaderConfiguration** cmdlet을 호출하지 않으면 사이트에 아무런 설정이 적용되지 않으며, 해당 Windows PowerShell 세션을 종료하거나 변수 $x를 삭제하는 즉시 가상 설정이 사라집니다.

    $x = New-CsDiagnosticHeaderConfiguration -Identity site:Redmond -InMemory
    $x.SendToOutsideUnauthenticatedUsers = $True
    $x.SendToExternalNetworks = $True
    Set-CsDiagnosticHeaderConfiguration -Instance $x

## 자세한 정보

관리자는 조직에서 보내는 각 SIP 메시지에 ms-diagnostics 헤더를 추가할 수 있습니다. 최종 사용자에게 표시되지 않는 이 메시지에는 연결 문제 해결 또는 오류 보고에 유용한 정보가 포함되어 있습니다. 예를 들어 진단 헤더에는 특정 상황이 발생할 경우 클라이언트 응용 프로그램(예: Lync)이 미리 정해진 대처 방법을 수행할 수 있도록 오류 코드가 포함될 수 있습니다.

내부 네트워크 내에서 보내는 SIP 메시지의 경우 이러한 진단 헤더를 포함하지 않을 이유가 없습니다. 진단 헤더는 메시지 크기에 최소한의 영향을 주며, 연결 문제를 해결하려는 관리자에게 매우 유용한 도구가 될 수 있습니다. 그러나 내부 네트워크 외부 사용자에게 알리고 싶지 않은 SIP 서버의 FQDN(정규화된 도메인 이름)과 같은 정보를 포함할 수도 있습니다. 이 때문에 진단 헤더 구성 설정은 외부 네트워크 사용자(예: 페더레이션 도메인의 사용자) 및/또는 외부 사용자에게 진단 헤더를 전송할지 여부를 결정하도록 지원합니다. 외부 사용자는 내부 네트워크 외부에서 연결하고 아직 인증되지 않은 사용자를 의미합니다.

기본적으로 외부 네트워크 또는 인증되지 않은 사용자에게 전송되는 메시지에는 진단 헤더가 포함되지 않습니다. 그러나 외부 네트워크 및/또는 인증되지 않은 사용자에게 보내는 메시지에 헤더를 포함하도록 전역 진단 헤더 설정을 수정할 수 있습니다. 또는 사이트 범위 또는 서비스 범위( 에지 서버 또는 등록자 서비스의 경우)에서 사용자 지정 설정을 만들 수 있습니다. 이러한 방법으로 특정 사이트에서 보내거나 특정 에지 서버를 통해 보내는 메시지에는 진단 헤더를 포함하고, 다른 사이트에서 보내거나 다른 에지 서버를 통해 보내는 메시지에는 헤더를 허용하지 않을 수 있습니다.

사용자 지정 진단 헤더 설정은 **New-CsDiagnosticHeaderConfiguration** cmdlet을 사용하여 만듭니다. 앞서 언급했듯이 사이트 범위나 서비스 범위( 에지 서버 및 등록자 서비스에만 해당)에 새 설정을 만들 수 있습니다. 사이트나 서비스별로 이러한 설정 컬렉션을 하나만 가질 수 있습니다. 예를 들어 Redmond 사이트에 대한 새 컬렉션을 만들려고 하는데 해당 사이트에 이미 진단 헤더 설정 컬렉션이 있는 경우가 있습니다. 이 경우 명령이 실패하게 됩니다. 마찬가지로 전역 범위에 새 컬렉션을 만들려고 해도 명령이 실패합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsDiagnosticHeaderConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsDiagnosticHeaderConfiguration"}

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
<td><p>만들 진단 헤더 구성 설정에 대한 고유한 식별자입니다. 사이트 범위에서 새 설정 컬렉션을 만들려면 -Identity &quot;site:Redmond&quot;와 유사한 구문을 사용합니다. 서비스 범위에서 새 설정 컬렉션을 만들려면 -Identity &quot;service:EdgeServer:atl-cs-001.litwareinc.com&quot;과 유사한 구문을 사용합니다.</p>
<p>전역 범위에는 새 설정을 만들 수 없습니다. 또한 지정한 사이트나 서비스(예: site:Redmond)가 이미 설정 컬렉션을 호스트하는 경우 사이트나 서비스 범위에 새 설정을 만들 수 없습니다.</p></td>
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
<td><p><em>SendToExternalNetworks</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 외부 사용자에게 보내는 메시지에 진단 헤더가 연결됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SendToOutsideUnauthenticatedUsers</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 외부 사용자에게 보내는 메시지에 진단 헤더가 연결됩니다. 외부 사용자는 내부 네트워크 외부(예: 프록시 서버를 통해)에서 연결하고 인증되지 않은 사용자입니다.</p>
<p>기본값은 False입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsDiagnosticHeaderConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsDiagnosticHeaderConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Diagnostics.DiagnosticHeaderSettings 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsDiagnosticConfiguration](get-csdiagnosticconfiguration.md)  
[Remove-CsDiagnosticHeaderConfiguration](remove-csdiagnosticheaderconfiguration.md)  
[Set-CsDiagnosticHeaderConfiguration](set-csdiagnosticheaderconfiguration.md)

