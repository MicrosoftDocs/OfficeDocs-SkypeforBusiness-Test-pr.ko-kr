---
title: Remove-CsClsConfiguration
TOCTitle: Remove-CsClsConfiguration
ms:assetid: f10005f4-ae5c-4d9e-800f-48183b5182be
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ619191(v=OCS.15)
ms:contentKeyID: 49305481
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsClsConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

중앙 로깅 구성 설정 컬렉션을 하나 이상 제거합니다. 관리자는 중앙 로깅을 통해 여러 컴퓨터에서 이벤트 추적을 동시에 사용하거나 사용하지 않도록 설정할 수 있습니다. 이 cmdlet은 Lync Server 2013에서 도입되었습니다.

## 구문

    Remove-CsClsConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1의 명령은 Redmond 사이트에 적용되는 중앙 로깅 구성 설정을 제거합니다.

    Remove-CsClsConfiguration -Identity "site:Redmond"

## 예제 2

예제 2에서는 해당 사이트 범위에 적용되는 모든 중앙 로깅 구성 설정이 제거됩니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsClsConfiguration** cmdlet을 Filter 매개 변수와 함께 호출합니다. 필터 값 "site:\*"는 반환되는 데이터를 사이트 범위에 구성된 설정으로 제한합니다. 이러한 설정은 **Remove-CsClsConfiguration** cmdlet으로 파이프되고 이 cmdlet에 의해 제거됩니다.

    Get-CsClsConfiguration -Filter "site:*" | Remove-CsClsConfiguration

## 예제 3

예제 3은 20메가바이트보다 큰 ETL 파일에 허용되는 모든 중앙 로깅 구성 설정을 삭제합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsClsConfiguration** cmdlet을 호출합니다. 이렇게 하면 조직에서 사용 중인 모든 중앙 로깅 설정의 컬렉션이 반환됩니다. 이러한 설정은 **Where-Object** cmdlet으로 파이프되고, 이 cmdlet은 EtlFileRollverSizeMB 속성이 20메가바이트보다 큰(-gt) 설정만 가려냅니다. 기준을 충족하는 설정은 **Remove-CsClsConfiguration** cmdlet으로 파이프되고 이 cmdlet에 의해 제거됩니다.

    Get-CsClsConfiguration | Where-Object {$_.EtlFileRolloverSizeMB -gt 20} | Remove-CsClsConfiguration

## 자세한 정보

중앙 로깅 서비스( Microsoft Lync Server 2010에서 사용하는 OCSLogger 및 OCSTracer 도구를 대체함)는 관리자가 Lync Server 2013을 실행하는 모든 컴퓨터와 풀에 대한 로깅 및 추적을 관리할 수 있게 해 줍니다. 중앙 로깅을 사용하면 관리자가 단일 명령을 사용하여 하나 이상의 풀 및 컴퓨터에 대해 로깅을 시작, 중지 및 구성할 수 있습니다. 예를 들어 명령 하나를 사용하여 모든 주소록 서버에서 주소록 서비스 로깅을 사용하도록 설정할 수 있습니다. 이는 서버마다 개별적으로 관리해야 하는(개별적으로 시작하고 중지하는 것도 포함) OCSLogger 및 OCSTracer 도구와 다릅니다. 또한 중앙 로깅 서비스에서는 관리자가 Windows PowerShell 명령줄 인터페이스 및 [Search-CsClsLogging](search-csclslogging.md) cmdlet을 사용하여 명령에서 추적 로그를 검색하는 방법도 있습니다.

중앙 로깅은 이전 버전의 Lync Server에서 제공되었던 것보다 대상이 상세하게 지정된 로깅 방식을 제공하는 미리 정의된 일련의 시나리오를 기반으로 작성되었습니다. 이러한 시나리오에 따라 서버 구성 요소 및 로깅이 자동으로 미리 결정되므로 RGS 시나리오를 사용하도록 설정하는 관리자는 오디오 회의 공급자 서비스가 아닌 응답 그룹 서비스와 관련된 정보만 기록할 수 있습니다.

[New-CsClsScenario](new-csclsscenario.md) cmdlet을 사용하여 사용자 지정 시나리오를 정의할 수도 있습니다.

중앙 로깅은 중앙 로깅 서비스 구성 설정 컬렉션을 사용하여 관리합니다. Lync Server 2013을 설치하면 이러한 구성 설정의 전역 집합이 설치됩니다. 또한 관리자가 사이트 범위에서 사용자 지정 설정 컬렉션을 추가할 수도 있습니다. 이후에 **Remove-CsClsConfiguration** cmdlet을 사용하여 이러한 사이트 범위 설정을 제거할 수 있습니다. 이 cmdlet은 전역 설정 컬렉션에 대해서도 실행할 수 있지만 이 경우에는 컬렉션이 제거되지 않습니다. 대신 컬렉션의 모든 속성이 기본값으로 다시 설정됩니다.

사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsClsConfiguration"}

**Lync Server 제어판:** **Remove-CsClsConfiguration** cmdlet에 의해 수행되는 기능은 Lync Server 제어판에서는 사용할 수 없습니다.

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
<th>형식</th>
<th>설명</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>제거할 중앙 로깅 구성 설정 컬렉션의 고유 ID입니다. 전역 설정을 제거하려면 다음 구문을 사용합니다.</p>
<p>-Identity &quot;global&quot;</p>
<p>전역 정책은 제거할 수 없습니다. 대신 모든 정책 속성이 기본값으로 재설정됩니다.</p>
<p>사이트 범위에서 구성된 컬렉션을 제거하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity &quot;site:Redmond&quot;</p>
<p>ID를 지정할 때는 와일드카드를 사용할 수 없습니다.</p></td>
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

**Remove-CsClsConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.CentralizedLoggingConfiguration 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. **Remove-CsClsConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.CentralizedLogging.CentralizedLoggingConfiguration 개체의 기존 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsClsConfiguration](get-csclsconfiguration.md)  
[New-CsClsConfiguration](new-csclsconfiguration.md)  
[Set-CsClsConfiguration](set-csclsconfiguration.md)

