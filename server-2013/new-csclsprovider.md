---
title: New-CsClsProvider
TOCTitle: New-CsClsProvider
ms:assetid: 9b0a90c1-27ab-49c8-88f2-a381cf14625e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ619187(v=OCS.15)
ms:contentKeyID: 49304501
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsClsProvider

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 중앙 로깅 추적 공급자를 만듭니다. 추적 공급자는 Lync Server의 문제 해결에 유용한 추적 메시지 또는 추적 이벤트를 생성하는 응용 프로그램 구성 요소입니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    New-CsClsProvider -Flags <String> -Level <All | Fatal | Error | Warning | Info | Verbose | Debug> -Name <String> -Type <WPP | EventLog | IISLog> [-Guid <String>] [-Role <String>]

## 예제

## 예제 1

예제 1의 명령은 새 중앙 로깅 시나리오 공급자를 만든 다음 이 공급자를 Redmond 사이트에 구성된 WAC 시나리오에 추가합니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 **New-CsClsProvider** cmdlet을 사용하여 WebInfrastructure라는 새 공급자를 만듭니다. 이 새 공급자는 변수 $provider에 저장됩니다. 그 다음 예제의 두 번째 명령은 새 공급자를 시나리오 site:Redmond/WAC에 추가합니다. 이 명령은 @{Add=$provider} 구문을 사용하기 때문에 새 공급자는 이미 구성되어 있는 다른 공급자와 함께 WAC 시나리오에 추가됩니다.

    $provider = New-CsClsProvider -Name "WebInfrastructure" -Type "WPP" -Level "Warning" -Flags "All"
    
    Set-CsClsScenario -Identity "site:Redmond/WAC" -Provider @{Add=$provider}

## 예제 2

예제 2의 명령은 예제 1에 나와 있는 명령의 변형입니다. 하지만 예제 2에서는 새 공급자가 WAC 시나리오에 구성되어 있는 일부 또는 전체 기존 공급자를 대체합니다. 이를 위해 @{Replace=$provider} 구문을 사용합니다.

    $provider = New-CsClsProvider -Name "WebInfrastructure" -Type "WPP" -Level "Warning" -Flags "All"
    
    Set-CsClsScenario -Identity "site:Redmond/WAC" -Provider @{Replace=$provider}

## 자세한 정보

중앙 로깅 서비스( Microsoft Lync Server 2010에서 사용하는 OCSLogger 및 OCSTracer 도구를 대체함)는 관리자가 Lync Server 2013을 실행하는 모든 컴퓨터와 풀에 대한 로깅 및 추적을 관리할 수 있게 해 줍니다. 중앙 로깅을 사용하면 관리자가 단일 명령을 사용하여 하나 이상의 풀 및 컴퓨터에 대해 로깅을 시작, 중지 및 구성할 수 있습니다. 예를 들어 명령 하나를 사용하여 모든 주소록 서버에서 주소록 서비스 로깅을 사용하도록 설정할 수 있습니다. 이는 서버마다 개별적으로 관리해야 하는(개별적으로 시작하고 중지하는 것도 포함) OCSLogger 및 OCSTracer 도구와 다릅니다. 또한 중앙 로깅 서비스에서는 관리자가 Windows PowerShell 명령줄 인터페이스 및 [Search-CsClsLogging](search-csclslogging.md) cmdlet을 사용하여 명령에서 추적 로그를 검색하는 방법도 있습니다.

중앙 로깅은 이전 버전의 Lync Server에서 제공되었던 것보다 대상이 상세하게 지정된 로깅 방식을 제공하는 미리 정의된 일련의 시나리오를 기반으로 작성되었습니다. 이러한 시나리오에 따라 서버 구성 요소 및 로깅이 자동으로 미리 결정되므로 RGS 시나리오를 사용하도록 설정하는 관리자는 오디오 회의 공급자 서비스가 아닌 응답 그룹 서비스와 관련된 정보만 기록할 수 있습니다.

각 중앙 로깅 시나리오는 추적 로그에 기록되는 메시지 및 이벤트를 생성할 추적 공급자가 하나 이상 있어야 합니다. Lync Server 2013은 사용자를 위해 사전 정의된 다양한 추적 공급자와 함께 제공됩니다. **New-CsClsProvider** cmdlet을 사용하면 Lync Server를 확장하는 개발자가 새로운 사용자 지정 응용 프로그램/구성 요소에 대한 중앙 로깅의 이점을 십분 활용할 수 있습니다.

[New-CsClsScenario](new-csclsscenario.md) cmdlet을 사용하여 사용자 지정 시나리오를 정의할 수도 있습니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsClsProvider"}

Lync Server 제어판: **New-CsClsProvider** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<td><p><em>Flags</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>추적에 사용되는 각 프로토콜 및 하위 구성 요소를 지정합니다. 예를 들어 SipStack 공급자에는 TF_COMPONENT, TF_RTCHTTP, TF_CONNECTION, TF_DIAG 플래그가 포함되어 있습니다.</p>
<p>대부분의 공급자는 사용 가능한 모든 플래그를 사용하도록 구성됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Level</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLoggingConfig.ProviderLevel</p></td>
<td><p>공급자가 기록하는 이벤트의 추적 레벨입니다. 허용되는 값은 다음과 같습니다.</p>
<p>* Fatal</p>
<p>* Error</p>
<p>* Warning</p>
<p>* Info</p>
<p>* Verbose</p>
<p>* Debug</p></td>
</tr>
<tr class="odd">
<td><p><em>Name</em></p></td>
<td><p>필수</p></td>
<td><p>System.String</p></td>
<td><p>새 공급자의 고유한 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Type</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLoggingConfig.ProviderType</p></td>
<td><p>공급자가 사용하는 추적 유형입니다. 허용되는 값은 다음과 같습니다.</p>
<p>* WPP (Windows software trace preprocessor)</p>
<p>* EventLog</p>
<p>* IISLog</p></td>
</tr>
<tr class="odd">
<td><p><em>Guid</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>공급자에 할당되는 GUID입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Role</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>공급자의 Lync Server 서버 역할입니다. 예를 들어 프런트 엔드 서버는 FE, 에지 서버는 Edge입니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. New-CsClsProvider cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

New-CsClsProvider cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.Provider 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[New-CsClsScenario](new-csclsscenario.md)  
[Set-CsClsScenario](set-csclsscenario.md)

