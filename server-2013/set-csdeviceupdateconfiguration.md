---
title: Set-CsDeviceUpdateConfiguration
TOCTitle: Set-CsDeviceUpdateConfiguration
ms:assetid: 4f200a03-984a-4c5b-a9c1-a866ba1851cd
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398320(v=OCS.15)
ms:contentKeyID: 49303600
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsDeviceUpdateConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

장치 업데이트 웹 서비스 구성 설정 컬렉션을 수정합니다. 이러한 설정은 관리자가 전화 및 Lync Server를 실행하는 기타 장치에 펌웨어 업데이트를 배포할 수 있도록 하는 Lync Server 구성 요소인 장치 업데이트 웹 서비스를 관리하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsDeviceUpdateConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsDeviceUpdateConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-LogCleanUpInterval <TimeSpan>] [-LogCleanUpTimeOfDay <DateTime>] [-LogFlushInterval <TimeSpan>] [-MaxLogCacheLimit <UInt32>] [-MaxLogFileSize <UInt32>] [-ValidLogFileExtensions <PSListModifier>] [-ValidLogFileTypes <PSListModifier>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 **Set-CsDeviceUpdateConfiguration** cmdlet을 사용하여 전역 구성 설정을 수정하는 방법을 보여 줍니다. 이 경우 두 개의 속성 값이 수정됩니다. MaxLogFileSize 속성은 2048000바이트로 설정되고 MaxLogCacheLimit 속성은 1024000바이트로 설정됩니다.

    Set-CsDeviceUpdateConfiguration -Identity global -MaxLogFileSize 2048000 -MaxLogCacheLimit 1024000

## 예제 2

예제 2에서는 ID가 site:Redmond인 장치 업데이트 구성 설정의 LogFlushInterval 속성을 수정합니다. 이 작업을 수행하기 위해 Identity 매개 변수를 사용하여 Redmond 사이트의 설정을 지정하고 LogFlushInterval 매개 변수를 사용하여 변경되는 속성 값을 나타냅니다. 이 경우 LogFlushInterval이 2분(00시간: 02분: 00초)으로 설정됩니다.

    Set-CsDeviceUpdateConfiguration -Identity site:Redmond -LogFlushInterval 00:02:00

## 예제 3

예제 3에서는 LogCleanUpInterval을 14일로 설정하기 위해 조직의 모든 장치 업데이트 구성 설정이 수정됩니다. 이 작업을 수행하기 위해 먼저 **Get-CsDeviceUpdateConfiguration** cmdlet을 사용하여 현재 사용 중인 모든 장치 업데이트 구성 설정의 컬렉션을 검색합니다. 그런 다음 이 컬렉션은 LogCleanUpInterval 매개 변수를 통해 컬렉션에 포함된 각 항목의 로그 정리 간격 시간을 14일(14일: 00시간: 00분: 00초)로 설정하는 **Set-CsDeviceUpdateConfiguration** cmdlet에 파이프됩니다.

    Get-CsDeviceUpdateConfiguration | Set-CsDeviceUpdateConfiguration -LogCleanUpInterval 14.00:00:00

## 예제 4

예제 4에서는 사이트 범위에서 구성된 모든 장치 업데이트 구성 설정의 속성 값을 수정하는 방법을 보여 줍니다. 이 경우 LogCleanUpInterval이 20일(20일: 00시간: 00분: 00초)로 설정됩니다. 이 작업을 수행하기 위해 Filter 매개 변수와 함께 **Get-CsDeviceUpdateConfiguration** cmdlet을 사용합니다. 필터 값 "site:\*"는 반환되는 데이터를 ID가 문자열 값 "site:"으로 시작하는 설정으로 제한합니다. 그런 다음 필터링된 컬렉션은 컬렉션에 포함된 각 항목의 로그 정리 간격 값을 변경하는 **Set-CsDeviceUpdateConfiguration** cmdlet에 파이프됩니다.

    Get-CsDeviceUpdateConfiguration -Filter "site:*" | Set-CsDeviceUpdateConfiguration -LogCleanUpInterval 20.00:00:00

## 예제 5

예제 5에서는 장치 업데이트 구성 설정에 사용되는 유효한 로그 파일 형식 목록에서 CELog를 제거합니다. 이 명령은 먼저 **Get-CsDeviceUpdateConfiguration** cmdlet을 사용하여 조직에서 현재 사용 중인 모든 장치 업데이트 구성 설정의 컬렉션을 검색합니다. 이 컬렉션은 ValidLogFileTypes 매개 변수를 사용하여 유효한 로그 파일 형식 목록에서 CELog를 제거하는 **Set-CsDeviceUpdateConfiguration** cmdlet에 파이프됩니다. ValidLogFileTypes에 전달된 매개 변수 값 @{Remove="CELog"}는 유효한 파일 형식 집합에서 CELog를 제거하도록 **Set-CsDeviceUpdateConfiguration** cmdlet에 지시합니다. 단일 명령으로 여러 개의 파일 형식을 제거하려면 추가 형식을 쉼표로 구분된 목록의 일부로 포함합니다.예를 들면 다음과 같습니다.

@{Remove="CELog","Watson"}

    Get-CsDeviceUpdateConfiguration | Set-CsDeviceUpdateConfiguration -ValidLogFileTypes @{Remove="CELog"}

## 자세한 정보

장치 업데이트 웹 서비스를 사용하면 관리자가 Lync Phone Edition을 실행하는 장치에 펌웨어 업데이트를 배포할 수 있습니다. 관리자는 주기적으로 Lync Server에 장치 업데이트 규칙 집합을 업로드하면 됩니다. 이러한 규칙을 테스트하고 승인한 후에는 규칙이 해당 장치(시스템에 연결된 경우)에 적용됩니다. 장치는 장치를 켤 때 업데이트를 확인한 다음 사용자가 로그온하면 다시 확인합니다. 이후에는 24시간마다 업데이트를 확인합니다.

장치 업데이트 구성 설정은 전역 범위 또는 사이트 범위에서 적용할 수 있습니다. **Set-CsDeviceUpdateConfiguration** cmdlet을 사용하면 설정 컬렉션을 변경할 수 있습니다. 예를 들어 이 cmdlet을 사용하여 시스템에서 자동으로 삭제하기 전에 보관되는 로그 파일의 보관 기간을 변경할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsDeviceUpdateConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsDeviceUpdateConfiguration"}

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
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>수정할 장치 업데이트 구성 설정의 고유 식별자입니다. 전역 설정을 참조하려면 -Identity global 구문을 사용합니다. 사이트 설정을 참조하려면 -Identity &quot;site:Redmond&quot;와 유사한 구문을 사용합니다. ID를 지정할 때는 와일드카드를 사용할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>DeviceUpdateSettings 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LogCleanUpInterval</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>시스템에서 장치 업데이트 로그 파일을 삭제하기 전에 해당 파일이 보관되는 기간을 지정합니다.</p>
<p>dd.hh:mm:ss 형식으로 값을 입력해야 합니다. 여기서 hh는 시간, mm은 분, ss는 초입니다. 일만 입력하려면 값 뒤에 마침표(.)를 입력해야 합니다.</p>
<p>최소값: 1.00:00:00(1일)</p>
<p>최대값: 365.00:00:00(1년)</p>
<p>기본값: 10.00:00:00(10일)</p></td>
</tr>
<tr class="even">
<td><p><em>LogCleanUpTimeOfDay</em></p></td>
<td><p>선택</p></td>
<td><p>System.DateTime</p></td>
<td><p>시스템에서 삭제해야 하는 만료된 로그 파일이 있는지 확인하는 시간을 나타냅니다. 만료된 로그 파일은 LogCleanupInterval 속성으로 지정된 값보다 오래된 모든 파일입니다.</p>
<p>LogCleanupTimeOfDay 매개 변수에 전달되는 값은 24시간 형식인 hh:mm이어야 합니다. 여기서 hh는 시간을 나타내고 mm은 분을 나타냅니다. 이 형식에서 자정은 00:00, 오전 8시 30분은 08:30, 오후 11시 52분은 23:52로 표현됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LogFlushInterval</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>로그 파일 캐시에 저장된 정보가 실제 로그 파일에 기록되는 빈도를 나타냅니다. 기본적으로 장치 업데이트 정보는 즉시 로그 파일에 기록되지 않고 1) 로그 플러시 시간 간격이 만료되거나 2) 캐시가 최대 크기에 도달할 때까지 메모리에 캐시됩니다. 이 값을 10분(00:10:00)으로 설정하면 캐시의 정보가 10분마다 로그 파일에 기록됩니다. 데이터가 기록된 후 캐시가 지워집니다.</p>
<p>hh:mm:ss 형식으로 값을 입력해야 합니다. 여기서 hh는 시간, mm은 분, ss는 초입니다.</p>
<p>최소값: 00:01:00(1분)</p>
<p>최대값: 1:00:00(1시간)</p>
<p>기본값: 00:05:00</p></td>
</tr>
<tr class="even">
<td><p><em>MaxLogCacheLimit</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>캐시가 지워지고 데이터가 로그 파일에 기록되기 전에 로그 파일 캐시에 보관될 수 있는 최대 정보량(바이트)을 나타냅니다. 기본적으로 로그 파일은 5분마다 &quot;플러시&quot;됩니다. 자세한 내용은 LogFlushInterval 매개 변수에 대한 설명을 참조하십시오. 그러나 캐시가 최대 크기에 도달하면 로그 플러시 간격이 만료되지 않은 경우에도 캐시의 정보가 자동으로 로그 파일에 기록되고 캐시가 지워집니다.</p>
<p>기본값: 512000</p></td>
</tr>
<tr class="odd">
<td><p><em>MaxLogFileSize</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>개별 로그 파일의 최대 크기(바이트)를 나타냅니다. 파일이 최대 크기에 도달하면 다음 일괄 처리 데이터가 자동으로 새 로그 파일에 기록됩니다. 로그 정리 간격이 만료될 때까지 이전 로그 파일이 보존됩니다.</p>
<p>기본값: 1024000</p></td>
</tr>
<tr class="even">
<td><p><em>ValidLogFileExtensions</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>장치 업데이트 웹 서비스에 사용할 수 있는 유효한 로그 파일 확장명을 나타냅니다. 이 목록은 수정 가능하지만, 다른 파일 확장명을 사용하는 로그 파일을 만드는 Lync Phone Edition 호환 장치가 없는 경우에는 목록을 수정할 이유가 없습니다.</p>
<p>기본값: .dmp, .clg, .clg2, .bak, .kdmp, .dat, .bin, .cat, .xml, .txt, .hex</p></td>
</tr>
<tr class="odd">
<td><p><em>ValidLogFileTypes</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>장치 업데이트 시스템에서 보존되는 로그 파일 형식을 나타냅니다. 기본 파일 형식은 다음과 같습니다.</p>
<p>Watson. 시스템 작동이 중단될 경우 장치에서 자동으로 생성되는 로그 파일입니다.</p>
<p>CELog. 기능 테스트 결과와 중요한 시스템 이벤트 기록이 포함된 Lync 전화 로그입니다.</p>
<p>다른 종류의 로그 파일을 만드는 Lync Phone Edition 호환 장치가 있는 경우 파일 형식을 추가할 수 있습니다. 또한 파일을 제거할 수도 있습니다. 예를 들어 CELog 파일을 저장하지 않으려는 경우 CELog 파일 형식을 제거할 수 있습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.DeviceUpdateConfiguration 개체입니다. **Set-CsDeviceUpdateConfiguration** cmdlet은 장치 업데이트 구성 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Set-CsDeviceUpdateConfiguration** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.DeviceUpdate.DeviceUpdateConfiguration 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[Get-CsDeviceUpdateConfiguration](get-csdeviceupdateconfiguration.md)  
[New-CsDeviceUpdateConfiguration](new-csdeviceupdateconfiguration.md)  
[Remove-CsDeviceUpdateConfiguration](remove-csdeviceupdateconfiguration.md)

