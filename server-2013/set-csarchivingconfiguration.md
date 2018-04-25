---
title: Set-CsArchivingConfiguration
TOCTitle: Set-CsArchivingConfiguration
ms:assetid: f5202dc2-b3b4-48ae-93d2-d19e71847994
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413030(v=OCS.15)
ms:contentKeyID: 49305539
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsArchivingConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

메신저 대화 보관 설정의 기존 컬렉션을 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsArchivingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsArchivingConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-ArchiveDuplicateMessages <$true | $false>] [-BlockOnArchiveFailure <$true | $false>] [-CachePurgingInterval <UInt32>] [-Confirm [<SwitchParameter>]] [-EnableArchiving <None | ImOnly | ImAndWebConf>] [-EnableExchangeArchiving <$true | $false>] [-EnablePurging <$true | $false>] [-Force <SwitchParameter>] [-KeepArchivingDataForDays <UInt32>] [-PurgeExportedArchivesOnly <$true | $false>] [-PurgeHourOfDay <UInt32>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 **Set-CsArchivingConfiguration** cmdlet을 사용하여 ID가 site:Redmond인 보관 구성 설정의 두 속성을 수정합니다. 먼저 이 명령은 ArchiveDuplicateMessages 속성을 False로 설정합니다. 그러면 서버에서 같은 메신저 대화 세션을 여러 번 보관할 수 없습니다. 또한 이 명령은 KeepArchivingDataForDays 매개 변수를 사용하여 메신저 대화를 30일 동안 보관하도록 지시합니다.

    Set-CsArchivingConfiguration -Identity site:Redmond -ArchiveDuplicateMessages $False -KeepArchivingDataForDays 30

## 예제 2

예제 2는 예제 1에 표시된 명령의 변형입니다. 그러나 이 예제에서는 사이트 범위에서 구성된 모든 보관 설정에 대해 ArchiveDuplicateMessages 및 KeepArchivingDataForDays 속성 값이 수정됩니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsArchivingConfiguration** cmdlet 및 Filter 매개 변수를 사용하여 사이트 범위에 구성된 모든 보관 설정의 컬렉션을 반환합니다. 필터 값 "site:\*"는 반환되는 데이터를 ID가 문자 "site:"으로 시작하는 설정으로 제한합니다. 필터링된 컬렉션은 컬렉션의 각 항목에 대한 두 속성 값을 수정하는 **Set-CsArchivingConfiguration** cmdlet에 파이프됩니다.

    Get-CsArchivingConfiguration -Filter "site:*" | Set-CsArchivingConfiguration -ArchiveDuplicateMessages $False -KeepArchivingDataForDays 30

## 예제 3

예제 3에서는 메신저 대화 세션과 웹 회의 보관을 모두 허용하는 모든 보관 구성 설정이 수정됩니다. 명령이 완료된 후에는 이러한 설정이 메신저 대화 세션 보관만 허용하게 됩니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsArchivingConfiguration** cmdlet을 호출하여 조직에서 현재 사용 중인 모든 보관 구성 설정의 컬렉션을 반환합니다. 이 컬렉션은 EnableArchiving 속성이 "ImAndWebConf"와 같은(-eq) 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 이 필터링된 컬렉션은 컬렉션의 각 항목을 가져오고 EnableArchiving 값을 "ImOnly"로 변경하는 **Set-CsArchivingConfiguration**에 파이프됩니다.

    Get-CsArchivingConfiguration | Where-Object {$_.EnableArchiving -eq "ImAndWebConf"} | Set-CsArchivingConfiguration -EnableArchiving "ImOnly"

## 자세한 정보

대부분의 조직에서는 조직의 사용자가 참가하는 모든 메신저 대화 세션 및 전화 회의의 대화 내용을 보관하는 것이 유용하다는 것을 인지하고 있습니다. 다른 조직의 경우 그러한 대화 내용을 보관하는 것이 의무이기도 합니다. 예를 들어 법에 따라 모든 전자 통신의 복사본을 보관해야 하는 금융 분야의 조직 대부분이 이에 해당합니다.

메신저 대화를 보관하려면 보관 서버를 하나 이상 설정해야 합니다. 보관 서버를 설정한 후에는 다음 두 단계를 추가로 수행해야 합니다. 먼저, 전역 범위에서 보관을 사용하도록 설정해야 합니다. 자세한 내용은 **Set-CsArchivingConfiguration** cmdlet 도움말 항목을 참조하십시오. 필요한 경우 다른 사이트의 사용자 지정 보관 설정도 구성할 수 있습니다.

둘째, 어떤 사용자의 메신저 대화 세션을 보관할지 나타내는 보관 정책을 사용해야 합니다. 메신저 대화 세션을 보관하도록 지정된 정책을 적용하지 않으면 메신저 대화 세션이 보관되지 않습니다.

Lync Server를 설치하면 전역 보관 구성 설정의 컬렉션이 만들어집니다. 이러한 설정은 기본적으로 전체 조직에 적용됩니다. 또는 **New-CsArchivingConfiguration** cmdlet을 사용하여 사이트별로 사용자 지정 구성 설정을 만들 수 있습니다. 두 방법 모두 **Set-CsArchivingConfiguration** cmdlet을 사용하여 기존 컬렉션이나 보관 구성 설정의 속성 값을 수정할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsArchivingConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsArchivingConfiguration"}

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
<td><p><em>ArchiveDuplicateMessages</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>&quot;풀 간&quot; 메신저 대화를 보관하는 방법을 지정합니다. 간단하게 예를 들어 보겠습니다. Ken Myer(Pool 1의 계정 사용)가 Pilar Ackerman(Pool 2의 계정 사용)에게 메신저 대화를 보냅니다. 차례로 Pilar가 Ken의 메신저 대화에 대한 회신을 보냅니다. ArchiveDuplicateMessages가 False로 설정되면 기본 제공 알고리즘에 따라 세션 대화 내용이 Pool 1이나 Pool 2 중 하나에만 기록됩니다. ArchiveDuplicateMessages가 True(기본값)로 설정되면 대화 내용이 두 풀에 모두 기록됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>BlockOnArchiveFailure</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 메신저 대화를 보관할 수 없을 때마다 메시지 서비스가 일시 중단됩니다. False(기본값)로 설정하면 메신저 대화를 보관할 수 없는 경우에도 메신저 대화가 계속됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>CachePurgingInterval</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>보관을 사용하도록 설정된 참가자가 없는 경우에 시스템에서 대화 내용을 삭제하는 빈도(시간)를 나타냅니다. 기본적으로 모든 그룹 메신저 대화 세션 및 전화 회의 세션은 실행 당시에 기록됩니다. 지정된 간격에 따라 시스템에서 이러한 세션의 참가자 중 보관을 사용하도록 설정된 참가자가 있는지 확인합니다. 시스템에서 보관을 사용하도록 설정된 참가자가 없는 세션을 발견하면 데이터베이스에서 대화 내용이 삭제됩니다.</p>
<p>CachePurgingInterval 속성은 4에서 168(포함)의 임의 정수로 설정할 수 있습니다. 기본값은 24입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableArchiving</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.Archiving.EnableArchiving</p></td>
<td><p>보관 데이터베이스에 저장할 항목(있는 경우)을 나타냅니다. 사용할 수 있는 값은 다음과 같습니다.</p>
<p>없음. 데이터베이스에 보관할 항목이 없습니다. 이 값은 기본값입니다.</p>
<p>ImOnly. 메신저 대화 세션이 데이터베이스에 보관됩니다.</p>
<p>ImAndWebConf. 메신저 대화 세션과 웹 회의 세션 모두 데이터베이스에 보관됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableExchangeArchiving</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 Lync Server 2013 메신저 대화 및 회의 대화 내용이 별도의 SQL Server 데이터베이스가 아닌 Microsoft Exchange Server 2013에 저장됩니다. Exchange 보관을 사용하도록 설정하면 사용자가 Lync Server 2013 보관 정책이 아닌 Exchange 보관 정책을 통해 관리됩니다.</p>
<p>기본값은 False입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnablePurging</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 보관된 메신저 대화가 다음 조건을 충족하는 경우 데이터베이스에서 정기적으로 제거됩니다. 1) KeepArchivingDataForDays 속성에서 지정한 값보다 오래된 경우 또는 2) 내보내어 삭제하도록 표시한 경우.</p>
<p>False로 설정하면 메신저 대화가 데이터베이스에서 자동으로 삭제되지 않습니다.</p></td>
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
<td><p>수정할 보관 구성 설정 컬렉션의 고유 식별자를 나타냅니다. 전역 설정을 수정하려면 이 매개 변수를 생략하거나 -Identity global 구문을 사용합니다. 사이트 범위에서 설정을 수정하려면 접두사 &quot;site:&quot;을 사용하고 그 뒤에 사이트 이름을 표시해야 합니다(예: -Identity &quot;site:Redmond&quot;).</p>
<p>Lync Server 2013에서만 사용할 수 있는 기능인 개별 등록자 풀에 할당된 설정을 수정하려면 다음과 유사한 구문을 사용합니다.</p>
<p>-Identity &quot;service:Registrar:atl-cs-001.litwareinc.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>보관 설정 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>KeepArchivingDataForDays</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>보관된 메신저 대화를 자동으로 삭제하기 전까지 데이터베이스에 보관할 일 수(1-2562)입니다. 기본값은 14입니다.</p>
<p>이 속성은 EnablePurging을 True로 설정한 경우에만 적용됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PurgeExportedArchivesOnly</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 시스템에서 내보낸(그리고 그에 따라 삭제하도록 표시된) 메신저 대화만 삭제합니다. 내보내지 않은 메신저 대화는 데이터베이스에 그대로 유지됩니다. 해당 메신저 대화가 KeepArchivingDataForDays 속성으로 지정한 값보다 오래된 경우에도 마찬가지입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PurgeHourOfDay</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>만료된 레코드가 보관 데이터베이스에서 삭제되는 하루 중 시간을 나타냅니다. 시간은 24시간제를 사용하여 지정합니다. 0은 자정(오전 12:00)을 나타내고 23은 오후 11:00를 나타냅니다 시간만 지정할 수 있습니다. 즉, 오전 4:00에 삭제 작업을 수행하도록 예약할 수는 있지만, 예를 들어 오전 4:30 또는 오전 4:15에 수행하도록 예약할 수는 없습니다. 기본값은 2(오전 2:00)입니다.</p>
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

Microsoft.Rtc.Management.WritableConfig.Settings.Archiving.ArchivingSettings 개체입니다. **Set-CsArchivingConfiguration** cmdlet은 보관 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

**Set-CsArchivingConfiguration** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Archiving.ArchivingSettings 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[Get-CsArchivingConfiguration](get-csarchivingconfiguration.md)  
[New-CsArchivingConfiguration](new-csarchivingconfiguration.md)  
[Remove-CsArchivingConfiguration](remove-csarchivingconfiguration.md)  
[Set-CsArchivingServer](set-csarchivingserver.md)

