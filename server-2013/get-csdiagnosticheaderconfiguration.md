---
title: Get-CsDiagnosticHeaderConfiguration
TOCTitle: Get-CsDiagnosticHeaderConfiguration
ms:assetid: a5b247b8-621a-463b-8034-f2f6970706fe
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412774(v=OCS.15)
ms:contentKeyID: 49304623
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsDiagnosticHeaderConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 현재 사용 중인 진단 헤더 구성 설정에 대한 정보를 반환합니다. 진단 헤더 구성 설정은 SIP 메시지에 헤더 정보가 함께 제공되는지 여부를 결정합니다. 이 정보는 문제 해결 및 오류 보고에 유용합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsDiagnosticHeaderConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsDiagnosticHeaderConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

위 명령은 조직에서 현재 사용 중인 모든 진단 헤더 구성 설정에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 매개 변수 없이 **Get-CsDiagnosticHeaderConfiguration** cmdlet을 호출합니다.

    Get-CsDiagnosticHeaderConfiguration

## 예제 2

예제 2에서는 ID가 site:Redmond인 단일 진단 헤더 구성 설정 컬렉션을 반환합니다.

    Get-CsDiagnosticHeaderConfiguration -Identity site:Redmond

## 예제 3

예제 3에 표시된 명령은 서비스 범위에서 구성된 모든 진단 헤더 설정을 반환합니다. 이 작업을 수행하기 위해 **Get-CsDiagnosticHeaderConfiguration** cmdlet 및 Filter 매개 변수를 호출합니다. 필터 값 "service:\*"는 ID가 "service:" 문자로 시작하는 설정만 반환되도록 합니다.

    Get-CsDiagnosticHeaderConfiguration -Filter "service:*"

## 예제 4

예제 4에서는 외부 네트워크로의 전송을 허용하는 모든 진단 헤더 구성 설정을 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsDiagnosticHeaderConfiguration** cmdlet을 호출합니다. 그러면 현재 사용 중인 모든 진단 헤더 설정 컬렉션이 반환됩니다. 이 컬렉션은 SendToExternalNetworks 속성이 True와 같은 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsDiagnosticHeaderConfiguration | Where-Object {$_.SendToExternalNetworks -eq $True}

## 예제 5

예제 5에 표시된 명령은 1) SendToExternalNetworks 속성 및/또는 2) SendToOutsideUnauthenticatedUsers가 True와 같은 진단 헤더 구성 설정에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsDiagnosticHeaderConfiguration** cmdlet을 사용하여 현재 사용 중인 모든 진단 헤더 설정 컬렉션을 반환합니다. 이 컬렉션은 SendToExternalNetworks 속성 및/또는 SendToOutsideUnauthenticatedUsers 속성이 True와 같은 설정을 선택하는 **Where-Object** cmdlet에 파이프됩니다.

\-or 연산자는 반환할 설정이 지정된 조건 중 하나를 충족해야 함을 나타냅니다. 지정된 조건을 모두 충족하는 설정을 반환하려면 대신 다음과 같이 -and 연산자를 사용합니다.

Where-Object {$\_.SendToExternalNetworks -eq $True -and $\_.SendToOutsideUnauthenticatedUsers -eq $True}

    Get-CsDiagnosticHeaderConfiguration | Where-Object {$_.SendToExternalNetworks -eq $True -or $_.SendToOutsideUnauthenticatedUsers -eq $True}

## 자세한 정보

SIP(Session Initiation Protocol) 메시지를 보낼 때 각 메시지에 ms-diagnostics 헤더를 추가할 수 있습니다. 최종 사용자에게 표시되지 않는 이 메시지에는 연결 문제 해결 또는 오류 보고에 유용한 정보가 포함되어 있습니다. 예를 들어 진단 헤더에는 특정 상황이 발생할 경우 클라이언트 응용 프로그램(예: Lync 2013)이 미리 정해진 대처 방법을 수행할 수 있도록 오류 코드가 포함될 수 있습니다.

내부 네트워크 내에서 전송된 SIP 메시지의 경우 이러한 진단 헤더를 포함하는 것이 좋습니다. 진단 헤더는 메시지 크기에 최소한의 영향을 주며, 연결 문제를 해결하려는 관리자에게 매우 유용한 도구가 될 수 있습니다. 그러나 내부 네트워크 외부 사용자에게 알리고 싶지 않은 SIP 서버의 FQDN(정규화된 도메인 이름)과 같은 정보를 포함할 수도 있습니다. 이 때문에 진단 헤더 구성 설정은 외부 네트워크 사용자(예: 페더레이션 도메인의 사용자) 및/또는 외부 사용자에게 진단 헤더를 전송할지 여부를 결정하도록 지원합니다. 외부 사용자는 내부 네트워크 외부에서 연결하고 아직 인증되지 않은 사용자를 의미합니다.

기본적으로 외부 네트워크 또는 인증되지 않은 사용자에게 전송되는 메시지에는 헤더가 포함되지 않습니다. 그러나 외부 네트워크 및/또는 인증되지 않은 사용자에게 헤더를 포함하도록 전역 진단 헤더 설정을 수정할 수 있습니다. 또는 사이트 범위 또는 서비스 범위(에지 서버 또는 등록자 서비스의 경우)에서 사용자 지정 설정을 만들 수 있습니다. 이러한 방식으로, 특정 사이트에서 전송되거나 에지 서버를 통해 전송되는 메시지에는 진단 헤더를 포함하고, 다른 사이트에서 전송되거나 다른 에지 서버를 통해 전송되는 메시지에는 헤더를 허용하지 않도록 선택할 수 있습니다.

**Get-CsDiagnosticHeaderConfiguration** cmdlet을 사용하면 조직에서 현재 사용 중인 진단 헤더 구성 설정에 대한 정보를 검색할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsDiagnosticHeaderConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsDiagnosticHeaderConfiguration"}

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
<td><p>반환할 설정 컬렉션을 지정할 때 와일드카드 문자를 사용할 수 있습니다. 예를 들어 -Filter &quot;site:*&quot; 구문은 사이트 범위에서 구성된 모든 설정을 반환합니다. -Filter &quot;service:*&quot; 구문은 서비스 범위에서 구성된 모든 설정을 반환합니다.</p>
<p>Filter 매개 변수와 Identity 매개 변수를 같은 명령에 함께 사용할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환할 진단 헤더 구성 설정의 고유 식별자입니다. 사이트 범위에서 구성된 설정을 반환하려면 -Identity &quot;site:Redmond&quot;와 유사한 구문을 사용합니다. 서비스 범위에서 구성된 설정을 반환하려면 -Identity &quot;service:EdgeServer:atl-edge-001.litwareinc.com&quot;과 같은 구문을 사용합니다. 전역 설정을 반환하려면 -Identity global 구문을 사용합니다.</p>
<p>이 매개 변수를 지정하지 않으면 현재 사용 중인 모든 진단 헤더 구성 설정이 반환됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 진단 헤더 구성 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsDiagnosticHeaderConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsDiagnosticHeaderConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Diagnostics.DiagnosticHeaderSettings 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsDiagnosticHeaderConfiguration](new-csdiagnosticheaderconfiguration.md)  
[Remove-CsDiagnosticHeaderConfiguration](remove-csdiagnosticheaderconfiguration.md)  
[Set-CsDiagnosticHeaderConfiguration](set-csdiagnosticheaderconfiguration.md)

