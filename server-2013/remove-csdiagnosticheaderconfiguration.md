---
title: Remove-CsDiagnosticHeaderConfiguration
TOCTitle: Remove-CsDiagnosticHeaderConfiguration
ms:assetid: d71b79f1-49f2-4a6c-8b3e-ca909e8d5f49
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398941(v=OCS.15)
ms:contentKeyID: 49305182
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsDiagnosticHeaderConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 현재 사용 중인 진단 헤더 구성 설정 컬렉션을 하나 이상 제거합니다. 진단 헤더 구성 설정은 문제 해결 및 오류 보고에 유용할 수 있는 헤더 정보를 SIP 메시지에 포함할지 여부를 결정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsDiagnosticHeaderConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 ID가 site:Redmond인 진단 헤더 구성 설정을 제거합니다.

    Remove-CsDiagnosticHeaderConfiguration -Identity site:Redmond

## 예제 2

예제 2에 표시된 명령은 서비스 범위에서 적용된 모든 진단 헤더 구성 설정을 삭제합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsDiagnosticHeaderConfiguration** cmdlet 및 Filter 매개 변수를 호출합니다. 필터 값 "service:\*"는 반환되는 데이터를 ID가 "service:" 문자로 시작하는 설정으로 제한합니다. 그런 다음 필터링된 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CsDiagnosticHeaderConfiguration** cmdlet에 파이프됩니다.

    Get-CsDiagnosticHeaderConfiguration -Filter service:* | Remove-CsDiagnosticHeaderConfiguration

## 예제 3

예제 3에서는 외부 네트워크로의 전송을 허용하는 모든 진단 헤더 구성 설정을 삭제합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsDiagnosticHeaderConfiguration** cmdlet을 사용하여 현재 사용 중인 모든 진단 헤더 설정 컬렉션을 반환합니다. 이 컬렉션은 SendToExternalNetworks 속성이 True와 같은 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 이러한 설정은 외부 네트워크로의 전송을 허용하는 각 설정을 삭제하는 **Remove-CsDiagnosticHeaderConfiguration** cmdlet에 파이프됩니다.

    Get-CsDiagnosticHeaderConfiguration | Where-Object {$_.SendToExternalNetworks -eq $True} | Remove-CsDiagnosticHeaderConfiguration

## 자세한 정보

관리자는 조직에서 보내는 각 SIP 메시지에 ms-diagnostics 헤더를 추가할 수 있습니다. 최종 사용자에게 표시되지 않는 이 메시지에는 연결 문제 해결 또는 오류 보고에 유용한 정보가 포함되어 있습니다. 예를 들어 진단 헤더에는 특정 상황이 발생한 경우 클라이언트 응용 프로그램이 미리 정해진 일련의 작업을 수행할 수 있도록 오류 코드가 포함될 수 있습니다.

내부 네트워크 내에서 전송된 SIP 메시지의 경우 이러한 진단 헤더를 포함하는 것이 좋습니다. 진단 헤더는 메시지 크기에 최소한의 영향을 주며, 연결 문제를 해결하려는 관리자에게 매우 유용한 도구가 될 수 있습니다. 그러나 내부 네트워크 외부 사용자에게 알리고 싶지 않은 SIP 서버의 FQDN(정규화된 도메인 이름)과 같은 정보를 포함할 수도 있습니다. 이 때문에 진단 헤더 구성 설정은 외부 네트워크 사용자(예: 페더레이션 도메인의 사용자) 및/또는 외부 사용자에게 진단 헤더를 전송할지 여부를 결정하도록 지원합니다. 외부 사용자는 내부 네트워크 외부에서 연결하고 아직 인증되지 않은 사용자를 의미합니다.

또는 사이트 범위 또는 서비스 범위(에지 서버 또는 등록자 서비스의 경우)에서 사용자 지정 설정을 만들 수 있습니다. 이러한 방식으로, 특정 사이트에서 전송되거나 에지 서버를 통해 전송되는 메시지에는 진단 헤더를 포함하고, 다른 사이트에서 전송되거나 다른 에지 서버를 통해 전송되는 메시지에는 헤더를 허용하지 않도록 선택할 수 있습니다.

사이트 또는 서비스 범위에서 만든 새 컬렉션은 나중에 **Remove-CsDiagnosticHeaderConfiguration** cmdlet을 사용하여 제거할 수 있습니다. 이 cmdlet을 전역 컬렉션에 대해 실행할 수도 있습니다. 그러나 전역 컬렉션은 제거할 수 없기 때문에 이 경우 전역 컬렉션이 제거되지는 않습니다. 대신 전역 컬렉션에 포함된 두 가지 속성 SendToExternalNetworks 및 SendToOutsideUnauthenticatedUsers가 각각 기본값(False)으로 다시 설정됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsDiagnosticHeaderConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsDiagnosticHeaderConfiguration"}

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
<td><p>제거할 진단 헤더 구성 설정의 고유 식별자입니다. 사이트 범위에서 구성된 설정을 제거하려면 -Identity &quot;site:Redmond&quot;와 유사한 구문을 사용하고, 서비스 범위에서 구성된 설정을 제거하려면 -Identity &quot;service:EdgeServer:atl-edge-001.litwareinc.com&quot;과 유사한 구문을 사용하십시오.</p>
<p>전역 구성 설정에 대해 <strong>Remove-CsDiagnosticHeaderConfiguration</strong> cmdlet을 실행할 수도 있습니다. 이 경우 -Identity global 구문을 사용합니다. 그러나 실제로는 전역 설정이 제거되지 않고 전역 설정에 있는 속성이 해당 기본값으로 다시 설정됩니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.Diagnostics.DiagnosticHeaderSettings 개체입니다. **Remove-CsDiagnosticHeaderConfiguration** cmdlet은 진단 헤더 설정 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. **Remove-CsDiagnosticHeaderConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Diagnostics.DiagnosticHeaderSettings 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsDiagnosticHeaderConfiguration](get-csdiagnosticheaderconfiguration.md)  
[New-CsDiagnosticHeaderConfiguration](new-csdiagnosticheaderconfiguration.md)  
[Set-CsDiagnosticHeaderConfiguration](set-csdiagnosticheaderconfiguration.md)

