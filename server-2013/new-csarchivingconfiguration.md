---
title: New-CsArchivingConfiguration
TOCTitle: New-CsArchivingConfiguration
ms:assetid: 66cab8b7-c3b3-4c1b-a77a-28f295ff6010
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398471(v=OCS.15)
ms:contentKeyID: 49303873
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsArchivingConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

메신저 대화 보관 설정의 새 집합을 생성합니다. 이러한 설정을 사용하여 메신저 대화 세션의 자동 저장을 활성화하거나 비활성화할 수 있습니다. 또한 보관할 수 없는 메신저 대화를 차단할 수도 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsArchivingConfiguration -Identity <XdsIdentity> [-ArchiveDuplicateMessages <$true | $false>] [-BlockOnArchiveFailure <$true | $false>] [-CachePurgingInterval <UInt32>] [-Confirm [<SwitchParameter>]] [-EnableArchiving <None | ImOnly | ImAndWebConf>] [-EnableExchangeArchiving <$true | $false>] [-EnablePurging <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-KeepArchivingDataForDays <UInt32>] [-PurgeExportedArchivesOnly <$true | $false>] [-PurgeHourOfDay <UInt32>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 보관 구성 설정의 새 컬렉션을 생성하고 이러한 설정을 Redmond 사이트에 적용합니다. EnableArchiving 매개 변수를 추가하고 매개 변수 값을 "ImOnly"로 설정하면 명령이 Redmond 사이트에 대한 메신저 대화 세션 보관을 활성화합니다(웹 회의 보관은 활성화되지 않음).

    New-CsArchivingConfiguration -Identity site:Redmond -EnableArchiving "ImOnly"

## 예제 2

예제 2에서는 InMemory 매개 변수를 사용하여 처음에 메모리에만 존재하는 보관 구성 설정의 컬렉션을 생성하는 방법을 보여 줍니다. 이를 위해 예제에서는 ID가 site:Redmond인 설정의 새 컬렉션을 생성하고 이 컬렉션을 변수 $x에 저장합니다. 첫 번째 명령이 실행된 후에는 컬렉션이 메모리에만 존재합니다. 해당 명령을 실행하면 **Get-CsArchivingConfiguration** cmdlet에서 site:Redmond에 대한 항목이 표시되지 않습니다.

두 번째 명령은 이 가상 설정 컬렉션의 EnableArchiving 속성을 "ImOnly"로 설정하여 메신저 대화 세션 보관을 활성화합니다. 마지막으로 세 번째 명령은 **Set-CsArchivingConfiguration** cmdlet을 사용하여 가상 보관 설정을 Redmond 사이트에 적용된 설정의 실제 컬렉션으로 변환합니다. **Set-CsArchivingConfiguration** cmdlet을 호출하지 않으면 이러한 설정이 메모리에만 남고 Windows PowerShell 세션이 종료되거나 변수 $x가 삭제된 후 사라집니다.

    $x = New-CsArchivingConfiguration -Identity site:Redmond -InMemory
    $x.EnableArchiving = "ImOnly"
    Set-CsArchivingConfiguration -Instance $x

## 자세한 정보

많은 조직에서는 사용자가 수행하는 모든 메신저 대화 세션의 사본을 보관하는 것이 유용하다는 사실을 알게 됩니다. 다른 조직의 경우 그러한 사본을 의무적으로 보관해야 합니다. 예를 들어, 재무 분야에서는 많은 조직이 법에 따라 모든 전자 통신의 복사본을 보관해야 합니다.

Lync Server에서는 메신저 대화 및 웹 회의 세션 보관과 관련된 유연한 기능을 제공합니다. 보관 서버를 배포한 경우 여러 가지 **CsArchivingConfiguration** cmdlet을 사용하여 메신저 대화 세션 보관을 설정 및 해제하고 보관 데이터베이스를 관리할 수 있습니다. 또한 보관에 실패한 경우 메신저 대화를 일시 중단하여 모든 전자 통신의 레코드를 유지할 수 있습니다.

Lync Server를 설치하면 전역 보관 설정의 컬렉션이 만들어집니다. 이러한 설정은 기본적으로 전체 조직에 적용됩니다. 또는 **New-CsArchivingConfiguration** cmdlet을 사용하여 사이트별로 사용자 지정 구성 설정을 만들 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsArchivingConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsArchivingConfiguration"}

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
<td><p>보관 구성 설정의 새 컬렉션에 할당할 고유 식별자입니다. Lync Server 2013에서는 사이트 범위 또는 서비스 범위에서 새 컬렉션을 만들 수 있습니다. Microsoft Lync Server 2010에서는 사이트 범위에서만 이러한 설정을 만들 수 있습니다. 사이트 범위에서 새 설정을 만들려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity &quot;site:Redmond&quot;</p>
<p>등록자 서비스에 한해 서비스 범위에서 설정을 만들려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity &quot;service:Registrar:atl-cs-001.litwareinc.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>ArchiveDuplicateMessages</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>교차 풀 메신저 대화를 보관하는 방법을 지정합니다. 예를 들어 Pool 1에 계정이 있는 Ken Myer는 Pool 2에 계정이 있는 Pilar Ackerman에게 메신저 대화를 보냅니다. 그런 다음 Pilar는 Ken의 메신저 대화에 대한 회신을 보냅니다. ArchiveDuplicateMessages가 False로 설정되면 기본 제공 알고리즘에 따라 세션 대화 내용이 Pool 1이나 Pool 2 중 하나에만 기록됩니다. ArchiveDuplicateMessages가 True(기본값)로 설정되면 대화 내용이 두 풀에 모두 기록됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>BlockOnArchiveFailure</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정된 경우, 메신저 대화 세션을 보관할 수 없으면 메시지 서비스가 일시 중지됩니다. False(기본값)로 설정되면 세션을 보관할 수 없는 경우에도 메신저 대화가 계속됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>CachePurgingInterval</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>보관을 사용하도록 설정된 참가자가 없는 경우에 시스템에서 대화 내용을 삭제하는 빈도(시간)를 나타냅니다. 기본적으로 모든 그룹 메신저 대화 세션 및 전화 회의 세션은 실행 당시에 기록됩니다. 지정된 간격에 따라 시스템에서 이러한 세션의 참가자 중 보관을 사용하도록 설정된 참가자가 있는지 확인합니다. 시스템에서 보관을 사용하도록 설정된 참가자가 없는 세션을 발견하면 데이터베이스에서 대화 내용이 삭제됩니다.</p>
<p>CachePurgeInterval 속성은 4-168(포함)의 임의의 정수로 설정할 수 있습니다. 기본값은 24입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableArchiving</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.Archiving.EnableArchiving</p></td>
<td><p>보관 데이터베이스에 저장할 항목(있는 경우)을 나타냅니다. 사용할 수 있는 값은 다음과 같습니다.</p>
<p>없음. 데이터베이스에 보관할 항목이 없습니다. 이 값은 기본값입니다.</p>
<p>ImOnly. 메신저 대화 세션이 데이터베이스에 보관됩니다.</p>
<p>ImAndWebConf. 메신저 대화 세션과 웹 회의 세션 모두 데이터베이스에 보관됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableExchangeArchiving</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 Lync Server 2013 메신저 대화 및 회의 대화 내용이 별도의 SQL Server 데이터베이스가 아닌 Microsoft Exchange Server 2013에 저장됩니다. Exchange 보관을 사용하도록 설정하면 사용자가 Lync Server 보관 정책이 아닌 Exchange 보관 정책을 통해 관리됩니다.</p>
<p>기본값은 False입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnablePurging</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정되면 다음과 같은 경우 보관된 메신저 대화가 정기적으로 데이터베이스에서 제거됩니다. 1) KeepArchivingDataForDays 속성에서 지정한 값보다 오래된 경우 또는 2) 내보내어 삭제하도록 표시한 경우.</p>
<p>False로 설정된 경우 메신저 대화가 자동으로 데이터베이스에서 삭제되지 않습니다.</p></td>
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
<td><p>True로 설정하면 시스템에서 내보낸(그리고 그에 따라 삭제하도록 표시된) 메신저 대화만 삭제합니다. 내보내지 않은 메신저 대화는 KeepArchivingDataForDays 속성에 지정된 값보다 오래된 경우에도 데이터베이스에 남아 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PurgeHourOfDay</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>만료된 레코드가 보관 데이터베이스에서 삭제되는 하루 중 시간을 나타냅니다. 시간은 24시간제를 사용하여 지정합니다. 0은 자정(오전 12:00)을 나타내고 23은 오후 11:00를 나타냅니다 시간만 지정할 수 있습니다. 즉, 오전 4:00에 제거가 수행되도록 예약할 수 있지만 오전 4:30 또는 오전 4:15에 제거가 수행되도록 예약할 수는 없습니다. 기본값은 2(오전 2:00)입니다.</p>
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

없음. **New-CsArchivingConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsArchivingConfiguration** cmdlet은 Microsoft.Rtc.Management.WriteableConfig.Settings.Archiving.ArchivingSettings 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsArchivingConfiguration](get-csarchivingconfiguration.md)  
[Remove-CsArchivingConfiguration](remove-csarchivingconfiguration.md)  
[Set-CsArchivingConfiguration](set-csarchivingconfiguration.md)  
[Set-CsArchivingServer](set-csarchivingserver.md)

