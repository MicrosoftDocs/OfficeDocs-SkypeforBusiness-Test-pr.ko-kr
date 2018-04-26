---
title: Set-CsCdrConfiguration
TOCTitle: Set-CsCdrConfiguration
ms:assetid: 977f0d3e-796b-43a3-bc0c-82ea91741c52
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398774(v=OCS.15)
ms:contentKeyID: 49304462
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsCdrConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 CDR(통화 정보 기록) 설정 컬렉션을 수정합니다. CDR을 사용하여 피어-투-피어 메신저 대화 세션, VoIP(Voice over Internet Protocol) 전화 통화, 전화 회의 통화 등의 사용 현황을 추적할 수 있습니다. 이러한 사용 내역 데이터에는 누가 누구에게 전화를 걸었는지, 언제 전화를 걸었는지 및 얼마나 오래 통화했는지에 대한 정보가 포함됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsCdrConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsCdrConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-EnableCDR <$true | $false>] [-EnablePurging <$true | $false>] [-Force <SwitchParameter>] [-KeepCallDetailForDays <UInt32>] [-KeepErrorReportForDays <UInt32>] [-PurgeHourOfDay <UInt32>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 오래된 기록을 삭제할 시간을 설정합니다. 이 경우 시간은 23(24시간제 형식의 오후 11:00)으로 설정됩니다. Identity 매개 변수는 ID가 site:Redmond인 CDR 설정에 대해서만 이러한 변경이 적용되도록 하기 위해 사용됩니다.

    Set-CsCdrConfiguration -Identity site:Redmond -PurgeHourOfDay 23 

## 예제 2

예제 2는 예제 1에 나온 명령의 변형입니다. 이 경우에는 현재 조직에서 사용 중인 각 CDR 구성 설정 컬렉션에 대해 PurgeHourOfDay 속성이 수정됩니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsCdrConfiguration** cmdlet을 매개 변수 없이 호출하여 현재 사용 중인 모든 CDR 설정의 컬렉션을 반환합니다. 이 컬렉션은 컬렉션의 각 항목에서 PurgeHourOfDay 속성 값을 오후 11:00(23)로 변경하는 **Set-CsCdrConfiguration** cmdlet에 파이프됩니다.

    Get-CsCdrConfiguration | Set-CsCdrConfiguration -PurgeHourOfDay 23 

## 예제 3

예제 3에서는 예제 1에 사용된 명령의 또 다른 변형을 볼 수 있습니다. 이 예제에서는 사이트 범위에 구성된 모든 CDR 설정에 대해 PurgeHourOfDay 속성이 변경됩니다. 이 작업을 수행하기 위해 명령은 먼저 Filter 매개 변수와 함께 **Get-CsCdrConfiguration** cmdlet을 호출합니다. 필터 값 "site:\*"는 ID가 문자열 값 "site:"으로 시작하는 CDR 설정만 반환되도록 합니다. 필터링된 컬렉션은 해당 컬렉션의 각 항목에 대한 PurgeHourOfDay 속성 값을 변경하는 **Set-CsCdrConfiguration** cmdlet에 파이프됩니다.

    Get-CsCdrConfiguration -Filter "site:*"| Set-CsCdrConfiguration -PurgeHourOfDay 23

## 자세한 정보

CDR(통화 정보 기록)을 사용하면 VoIP(Voice over Internet Protocol) 전화 통화, 메신저 대화, 파일 전송, A/V(오디오/비디오) 회의 및 응용 프로그램 공유 세션과 같은 Lync Server 기능의 사용 내역을 추적할 수 있습니다. CDR(모니터링 서비스를 배포한 경우에만 사용할 수 있음)은 사용 정보를 보관합니다. 통화에 참여한 사람, 통화 시간, 파일 전송 여부 등에 대한 정보를 기록합니다. 그러나 통화 자체를 녹음하지는 않습니다.

CDR은 통화 오류 정보, 즉 피어-투-피어 세션과 전화 회의 통화에 대한 자세한 진단 데이터를 제공합니다.

관리자는 조직에서 CDR의 사용 여부를 결정할 수 있습니다. 모니터링 서비스가 배포된 경우 쉽게 CDR을 활성화하거나 비활성화할 수 있습니다. 또한 이 결정 사항을 전역적으로 적용(이 경우 CDR이 조직 전체에서 사용하거나 사용하지 않도록 설정됨)하거나 사이트별로 적용할 수 있습니다. 예를 들어 Redmond 사이트에서는 통화 정보 기록을 사용하고 Paris 사이트에서는 사용하지 않을 수 있습니다.

관리자는 CDR 데이터베이스도 관리할 수 있습니다. 예를 들어 CDR 레코드를 데이터베이스에서 삭제하기 전에 유지할 일 수를 지정할 수 있습니다. 이러한 변경 작업은 **Set-CsCdrConfiguration** cmdlet을 사용하여 수행할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsCdrConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsCdrConfiguration"}

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
<td><p><em>EnableCDR</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>CDR을 사용할 수 있는지 여부를 나타냅니다. 기본값은 True입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnablePurging</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>CDR을 CDR 데이터베이스에서 주기적으로 삭제할지 여부를 나타냅니다. True(기본값)이면 KeepCallDetailForDays(CDR 기록) 및 KeepErrorReportForDays(CDR 오류) 속성에 지정된 기간이 지난 후 기록이 삭제되고, False인 경우 CDR 레코드는 무기한 유지됩니다.</p></td>
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
<td><p>CDR 구성 설정 컬렉션에 할당할 고유 식별자입니다. 전역 설정을 참조하려면 -Identity global 구문을 사용합니다. 사이트 범위에서 구성된 컬렉션을 참조하려면 -Identity site:Redmond 형태의 구문을 사용합니다. ID를 지정할 때 와일드카드 문자를 사용할 수 없습니다.</p>
<p>이 매개 변수를 생략하면 <strong>Set-CsCdrConfiguration</strong> cmdlet은 전역 설정을 수정합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>CDR 설정 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>KeepCallDetailForDays</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>CDR 기록을 CDR 데이터베이스에 유지할 일 수를 나타냅니다. 지정된 일 수보다 오래된 기록은 모두 자동으로 삭제됩니다. 삭제는 EnablePurging 속성이 true로 설정된 경우에만 수행됩니다.</p>
<p>이 속성은 1에서 2562일(약 7년) 사이의 정수 값으로 설정할 수 있습니다. 기본값은 60입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>KeepErrorReportForDays</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>CDR 오류 보고서를 유지할 일 수를 나타냅니다. 지정된 일 수보다 오래된 보고서는 모두 자동으로 삭제됩니다. CDR 오류 보고서는 Lync 2013과 같은 클라이언트 응용 프로그램에서 업로드하는 진단 보고서입니다.</p>
<p>이 속성은 1에서 2562일(약 7년) 사이의 정수 값으로 설정할 수 있습니다. 기본값은 60입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PurgeHourOfDay</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>CDR 데이터베이스에서 만료된 레코드가 삭제되는 로컬 시간을 나타냅니다. 시간은 24시간제를 사용하여 지정합니다. 0은 자정(오전 12:00)을 나타내고 23은 오후 11:00를 나타냅니다. 시간만 지정할 수 있습니다. 즉, 오전 4:00에 삭제 작업을 수행하도록 예약할 수는 있지만, 예를 들어 오전 4:30 또는 오전 4:15에 수행하도록 예약할 수는 없습니다. 기본값은 2(오전 2:00)입니다. 삭제는 업무 외 시간에 수행되는 것이 좋습니다.</p>
<p>데이터베이스 삭제는 EnablePurging 속성이 True로 설정된 경우에만 수행됩니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.CallDetailRecording.CdrSettings. **Set-CsCdrConfiguration** cmdlet은 통화 정보 기록 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

**Set-CsCdrConfiguration** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.CallDetailRecording.CDRSettings 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[Get-CsCdrConfiguration](get-cscdrconfiguration.md)  
[New-CsCdrConfiguration](new-cscdrconfiguration.md)  
[Remove-CsCdrConfiguration](remove-cscdrconfiguration.md)

