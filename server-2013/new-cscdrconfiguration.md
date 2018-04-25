---
title: New-CsCdrConfiguration
TOCTitle: New-CsCdrConfiguration
ms:assetid: e5890ac3-7a6c-4609-a866-84c39b76d3a9
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399018(v=OCS.15)
ms:contentKeyID: 49305339
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsCdrConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 CDR(통화 정보 기록) 설정 집합을 만듭니다. CDR을 사용하면 피어-투-피어 메신저 대화 세션, VoIP(Voice over Internet Protocol) 전화 통화 및 전화 회의 통화와 같은 사용 내역을 추적할 수 있습니다. 이러한 사용 내역 데이터에는 누가 누구에게 전화를 걸었는지, 언제 전화를 걸었는지 및 얼마나 오래 통화했는지에 대한 정보가 포함됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsCdrConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-EnableCDR <$true | $false>] [-EnablePurging <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-KeepCallDetailForDays <UInt32>] [-KeepErrorReportForDays <UInt32>] [-PurgeHourOfDay <UInt32>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1의 명령은 **New-CsCdrConfiguration** cmdlet을 사용하여 ID가 site:Redmond인 새 CDR 설정 집합을 만듭니다. 또한 ID를 site:Redmond로 지정하는 것 외에 새 설정의 EnableCDR 속성을 False로 설정합니다. 사이트 설정은 전역 설정에 우선하기 때문에 CDR이 전역 범위에서 사용하도록 설정되었는지 여부에 관계없이 Redmond 사이트에는 CDR이 사용되지 않습니다.

    New-CsCdrConfiguration -Identity site:Redmond -EnableCDR $False

## 예제 2

예제 2에서는 InMemory 매개 변수를 사용하여 처음에 메모리에만 존재하는 CDR 구성 설정의 새 컬렉션을 만드는 방법을 보여 줍니다. 이 작업을 수행하기 위해 예제에서는 먼저 **New-CsCdrConfiguration** cmdlet 및 InMemory 매개 변수를 사용하여 ID가 site:Redmond인 설정의 가상 컬렉션을 만듭니다. 이 가상 컬렉션은 $x 변수에 저장됩니다. 컬렉션을 변수에 저장하지 않으면 만드는 즉시 사라집니다.

가상 컬렉션이 만들어지면 둘째 줄에 표시된 명령이 EnableCDR 속성 값을 False($False)로 설정합니다. 그런 다음 셋째 줄에서 **Set-CsCdrConfiguration** cmdlet을 사용하여 가상 컬렉션 $x를 Redmond 사이트에 적용되는 CDR 구성 설정의 실제 컬렉션으로 변환합니다. **Set-CsCdrConfiguration** cmdlet을 호출하지 않은 경우에는 Windows PowerShell 세션을 종료하거나 변수 $x를 삭제하자마자 가상 컬렉션이 사라집니다.

    $x = New-CsCdrConfiguration -Identity site:Redmond -InMemory
    $x.EnableCDR = $False
    Set-CsCdrConfiguration -Instance $x

## 자세한 정보

CDR(통화 정보 기록)을 사용하면 VoIP(Voice over IP) 전화 통화, 메신저 대화, 파일 전송, A/V(오디오/비디오) 회의 및 응용 프로그램 공유 세션과 같은 Lync Server 기능의 사용 내역을 추적할 수 있습니다. CDR은 모니터링 서비스를 배포한 경우에만 사용할 수 있으며 사용 정보를 추적합니다. 예를 들어 통화에 참여한 사람, 통화 시간, 파일 전송 여부 등에 대한 정보를 기록합니다. 그러나 통화 자체를 녹음하지는 않습니다.

또한 CDR은 통화 오류 정보를 추적하며 피어-투-피어 세션과 전화 회의 통화에 대한 자세한 진단 데이터를 제공합니다.

관리자는 조직에서 CDR의 사용 여부를 결정할 수 있습니다. 모니터링 서비스가 배포된 경우 쉽게 CDR을 활성화하거나 비활성화할 수 있습니다. 뿐만 아니라 이 결정을 전체적으로 적용하여 조직 전체에서 CDR을 활성화 또는 비활성화하거나, 사이트 단위로 적용할 수 있습니다. 예를 들어 Redmond 사이트에서는 CDR을 사용하고 Paris 사이트에서는 CDR을 사용하지 않을 수 있습니다.

**New-CsCdrConfiguration** cmdlet을 사용하면 사이트 범위에서 새 CDR 설정 컬렉션을 만들 수 있습니다. 전역 범위에서는 새 설정을 만들 수 없습니다. 사이트에서는 단일 CDR 설정 컬렉션만 호스트할 수 있습니다. 즉, Redmond 사이트에 CDR 구성 설정 집합이 이미 있는 경우 이 사이트에 대한 새 컬렉션을 만들 수 없습니다. 새 컬렉션을 만들려고 하면 명령이 실패합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsCdrConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsCdrConfiguration"}

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
<td><p>CDR 구성 설정의 새 컬렉션에 할당할 고유 식별자를 나타냅니다. 사이트 범위에서만 새 컬렉션을 생성할 수 있기 때문에 ID의 접두사는 항상 &quot;site:&quot;이며 그 뒤에 사이트 이름이 옵니다(예: &quot;site:Redmond&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableCDR</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>CDR을 사용할 수 있는지 여부를 나타냅니다. 기본값은 True입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnablePurging</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>CDR을 CDR 데이터베이스에서 주기적으로 삭제할지 여부를 나타냅니다. True(기본값)이면 KeepCallDetailForDays(CDR 기록) 및 KeepErrorReportForDays(CDR 오류)에 지정된 기간이 지난 후 기록이 삭제되고, False이면 CDR 레코드는 무기한 유지됩니다.</p></td>
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
<td><p><em>KeepCallDetailForDays</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>CDR 기록을 CDR 데이터베이스에 유지할 일 수를 나타냅니다. 지정된 일 수보다 오래된 기록은 모두 자동으로 삭제됩니다. 단, EnablePurging 속성을 True로 설정한 경우에만 삭제가 실행됩니다.</p>
<p>KeepCallDetailForDays는 1에서 2562일(약 7년) 사이의 정수 값으로 설정할 수 있습니다. 기본값은 60입니다.</p></td>
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
<td><p>만료된 기록이 CDR 데이터베이스에서 삭제되는 로컬 시간을 나타냅니다. 시간은 24시간제를 사용하여 지정합니다. 0은 자정(오전 12:00)을 나타내고 23은 오후 11:00를 나타냅니다. 시간만 지정할 수 있습니다. 즉, 오전 4:00에 삭제 작업을 수행하도록 예약할 수는 있지만, 예를 들어 오전 4:30 또는 오전 4:15에 수행하도록 예약할 수는 없습니다. 기본값은 2(오전 2:00)입니다. 업무 시간 외에 삭제 작업을 수행하는 것이 좋습니다.</p>
<p>데이터베이스 삭제 작업은 EnablePurging 속성이 True로 설정된 경우에만 수행됩니다.</p></td>
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

없음. **New-CsCdrConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.CallDetailRecording.CdrSettings 개체의 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsCdrConfiguration](get-cscdrconfiguration.md)  
[Remove-CsCdrConfiguration](remove-cscdrconfiguration.md)  
[Set-CsCdrConfiguration](set-cscdrconfiguration.md)

