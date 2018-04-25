---
title: New-CsUserServicesConfiguration
TOCTitle: New-CsUserServicesConfiguration
ms:assetid: bdcb11b5-b8bf-4d63-a8a5-11f2b43686dd
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412926(v=OCS.15)
ms:contentKeyID: 49304883
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsUserServicesConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자 서비스 구성 설정의 새 컬렉션을 만듭니다. User Services 서비스는 현재 상태 정보를 유지 관리하고 전화 회의를 관리하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsUserServicesConfiguration -Identity <XdsIdentity> [-AnonymousUserGracePeriod <TimeSpan>] [-Confirm [<SwitchParameter>]] [-DeactivationGracePeriod <TimeSpan>] [-DefaultSubscriptionExpiration <Int64>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-MaintenanceTimeOfDay <DateTime>] [-MaxContacts <UInt16>] [-MaxPersonalNotes <UInt32>] [-MaxScheduledMeetingsPerOrganizer <UInt32>] [-MaxSubscriptionExpiration <Int64>] [-MaxSubscriptions <UInt16>] [-MinSubscriptionExpiration <Int64>] [-PresenceProviders <PSListModifier>] [-SubscribeToCollapsedDG <$true | $false>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Redmond 사이트(-Identity site:Redmond)의 새로운 User Services 구성 설정 컬렉션을 만듭니다. 이 명령은 ID를 지정할 뿐만 아니라 최대 연락처 수(-MaxContacts 500)와 유지 관리 수행 시간(-MaintenanceTimeOfDay "11:00 PM")도 설정합니다. Redmond 사이트에 User Services 설정이 이미 구성되어 있는 경우에는 이 명령이 실패합니다. 사이트별 설정의 컬렉션은 하나만 사용하도록 제한되기 때문입니다.

    New-CsUserServicesConfiguration -Identity site:Redmond -MaxContacts 500 -MaintenanceTimeOfDay "11:00 PM"

## 예제 2

예제 2에서도 Redmond 사이트의 새 User Services 구성 설정 컬렉션을 만듭니다. 그러나 이 예제에서는 처음에 메모리에만 컬렉션을 만들고 Redmond 사이트에는 나중에 적용합니다. 이 작업을 수행하기 위해 예제의 첫 번째 명령은 **New-CsUserServicesConfiguration** cmdlet 및 InMemory 매개 변수를 사용하여 메모리에만 존재하고 ID가 site:Redmond인 새 컬렉션을 만듭니다. 이 컬렉션은 메모리에만 존재하므로 User Services 개체는 변수에 저장해야 합니다. 이 경우 $x 변수가 사용됩니다.

가상 컬렉션이 만들어진 후에는 두 번째 및 세 번째 명령을 사용하여 MaxContacts 및 MaintenanceTimeOfDay 속성 값을 수정합니다. 그러면 예제의 마지막 명령에서는 **Set-CsUserServicesConfiguration** cmdlet을 사용하여 이러한 가상 설정을 Redmond 사이트에 적용되는 사용자 서비스 구성 설정의 실제 컬렉션으로 변환합니다. 이 마지막 단계는 매우 중요합니다. **Set-CsUserServicesConfiguration** cmdlet을 호출하지 않으면 어떠한 설정도 Redmond 사이트에 적용되지 않고 Windows PowerShell 세션을 종료하거나 변수 $x를 삭제하자마자 가상 설정이 사라집니다.

    $x = New-CsUserServicesConfiguration -Identity site:Redmond -InMemory
    $x.MaxContacts = 500 
    $x.MaintenanceTimeOfDay = "11:00 PM"
    Set-CsUserServicesConfiguration -Instance $x

## 자세한 정보

Lync Server는 User Services 서비스를 사용하여 사용자의 현재 상태 정보를 유지 관리하고 모임 및 전화 회의를 관리합니다. 그런 다음 **CsUserServicesConfiguration** cmdlet을 사용하여 전역, 사이트 및 서비스 범위에서 User Services 구성 설정을 관리합니다. User Services 구성 설정을 호스트할 수 있는 서비스는 User Services 서비스 자체뿐입니다. 이러한 설정은 사용자가 가질 수 있는 연락처 수, 사용자가 한 번에 예약할 수 있는 모임 수, 전화 회의가 활성 상태로 남아 있을 수 있는 시간 등을 결정합니다.

**New-CsUserServicesConfiguration** cmdlet은 관리자가 사이트 범위나 서비스 범위에서 User Services 구성 설정의 새 컬렉션을 만드는 방법을 제공합니다. 전역 범위에서는 새 컬렉션을 만들 수 없습니다. 특정 사이트 또는 서비스에는 User Services 구성 설정 컬렉션을 최대 하나만 포함할 수 있습니다. 예를 들어 Redmond 사이트에 대한 설정을 만들려고 할 경우 해당 사이트에서 이미 User Services 구성 설정의 컬렉션을 호스트하고 있으면 명령이 실패합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsUserServicesConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 명령줄 인터페이스 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsUserServicesConfiguration"}

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
<td><p>만들 User Services 구성 설정의 고유 식별자입니다. 사이트 범위에서 설정을 만들려면 -Identity site:Redmond와 유사한 구문을 사용하십시오. 서비스 수준에서 설정을 만들려면 -Identity service:UserServer:atl-cs-001.litwareinc.com과 유사한 구문을 사용하십시오.</p></td>
</tr>
<tr class="even">
<td><p><em>AnonymousUserGracePeriod</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>인증된 사용자가 같은 모임에 없어도 익명(인증되지 않은) 사용자가 모임에 남아 있을 수 있는 시간을 나타냅니다. 예를 들어 이 값이 15분으로 설정되면 익명 사용자는 인증된 사용자가 참가하기 전까지 최대 15분 동안 전화 회의에 남아 있을 수 있습니다. 유예 기간이 만료되기 전에 인증된 사용자가 참가하지 않으면 익명 사용자는 모임에서 제거됩니다. 이 설정은 예약된 모임 및 Microsoft Lync에서 모임 시작을 클릭하여 만든 임시 모임에 모두 적용됩니다.</p>
<p>AnonymousUserGracePeriod는 일.시간:분:초(예: 30분의 경우 0.00:30:00) 형식을 사용하여 지정해야 합니다. 유예 기간은 0초-1일의 모든 값으로 설정할 수 있습니다. 기본값은 90분(01:30:00)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DeactivationGracePeriod</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>모임이 활성 상태로 유지될 수 있는 최대 시간입니다. 이 값은 일 수.시간:분:초와 같은 형식으로 표시합니다. 예를 들어 모임을 60시간 동안 지속되도록 설정하려면 2.12:00:00(2일. 12시간: 00분: 00초) 형식을 사용합니다.</p>
<p>DeactivationGracePeriod는 8시간-365일(포함)이어야 합니다. 기본값은 1일(1.00:00:00)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DefaultSubscriptionExpiration</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int64</p></td>
<td><p>사용자가 현재 상태 정보와 같은 데이터를 요청할 때마다 구독이 만들어집니다. 요청을 할 때 사용자(좀 더 정확하게 표현하자면 사용자의 클라이언트 응용 프로그램)는 구독을 갱신해야 할 때까지 구독이 유효한 상태로 유지되는 시간을 요청할 수 있습니다. 그러한 요청이 발급되지 않으면 구독은 DefaultSubscriptionExpiration 속성에서 지정하는 값으로 설정됩니다.</p>
<p>기본 구독 시간은 300초(5분)-86400초(24시간)(포함) 사이의 정수 값으로 표현해야 합니다. 기본값은 28800초(8시간)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MaintenanceTimeOfDay</em></p></td>
<td><p>선택</p></td>
<td><p>System.DateTime</p></td>
<td><p>정기적으로 예약된 데이터베이스 유지 관리 작업(예: 오래된 레코드 삭제)을 수행할 시간을 나타냅니다. 이 값은 날짜-시간 값으로 지정해야 합니다. 24시간제 형식(예: &quot;14:00&quot;) 또는 12시간제 형식(예: &quot;2:00 PM&quot;)을 사용할 수 있습니다.</p>
<p>MaintenanceTimeOfDay의 기본값은 오전 1:00(01:00:00)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaxContacts</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>사용자가 가질 수 있는 최대 연락처 수입니다.기본값은 250입니다. MaxContacts 속성은 사용자가 가질 수 있는 절대 최대 연락처 수를 나타냅니다. 그러나 CsClientPolicy cmdlet을 사용하여 특정 사용자에게는 최대 연락처 수를 MaxContacts의 값보다 작은 값으로 제한할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MaxPersonalNotes</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>사용자의 메모 기록에 저장되는 최대 개인 메모 수를 나타냅니다. 기본적으로 메모 기록에는 최근 3개의 개인 메모가 유지 관리됩니다. 기록에 유지 관리할 수 있는 최대 메모 수는 10개입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaxScheduledMeetingsPerOrganizer</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>한 사용자가 지정된 시간에 이끌이 역할을 할 수 있는 최대 모임 수입니다. 기본값은 1000입니다. 즉, 사용자가 이미 1000개의 모임에서 이끌이인 경우 새 모임(모임 번호 1001)을 예약하려는 시도는 실패하게 됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MaxSubscriptionExpiration</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int64</p></td>
<td><p>사용자가 현재 상태 정보와 같은 데이터를 요청할 때마다 구독이 만들어집니다. 요청을 할 때 사용자(좀 더 정확하게 표현하자면 사용자의 클라이언트 응용 프로그램)는 구독을 갱신해야 할 때까지 구독이 유효한 상태로 유지되는 시간을 요청할 수 있습니다. MaxSubscriptionExpiration 속성은 클라이언트에게 부여할 수 있는 최대 시간을 나타냅니다. 예를 들어 최대 시간이 28800초로 설정되고 클라이언트가 86400초의 시간 초과 간격을 요청하면 클라이언트에 허용되는 최대 만료 기간은 28800초로 지정됩니다.</p>
<p>최대 구독 시간은 300초(5분)-86400초(24시간)(포함) 사이의 정수 값으로 표현해야 합니다. 기본값은 43200초(12시간)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaxSubscriptions</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>사용자가 한 번에 열 수 있는 최대 SIP 구독 대화 상자 수입니다. 구독 대화 상자는 SIP 리소스에 대한 요청을 나타냅니다. 기본값은 200입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MinSubscriptionExpiration</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int64</p></td>
<td><p>사용자가 현재 상태 정보와 같은 데이터를 요청할 때마다 구독이 만들어집니다. 요청을 할 때 사용자(좀 더 정확하게 표현하자면 사용자의 클라이언트 응용 프로그램)는 구독을 갱신해야 할 때까지 구독이 유효한 상태로 유지되는 시간을 요청할 수 있습니다. MinSubscriptionExpiration 속성은 클라이언트에게 부여할 수 있는 최소 시간을 나타냅니다. 예를 들어 최소 시간이 1200초로 설정되고 클라이언트가 200초의 시간 초과 간격을 요청하면 클라이언트에 허용되는 최소 만료 기간은 1200초로 지정됩니다.</p>
<p>최소 구독 시간은 300초(5분)-86400초(24시간)(포함) 사이의 정수 값으로 표현해야 합니다. 기본값은 1200초(20분)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PresenceProviders</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>새 사용자 서비스 구성 설정에 대한 현재 상태 공급자 컬렉션입니다. 현재 상태 공급자는 <strong>New-CsPresenceProvider</strong> cmdlet을 사용하여 사용자 서비스 구성 설정의 컬렉션에 추가하는 것이 가장 좋습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SubscribeToCollapsedDG</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True(기본값)로 설정하면 클라이언트 응용 프로그램에서 현재 연락처 목록에 확장되지 않은 메일 그룹을 구독할 수 있습니다. 그러면 클라이언트가 각 그룹 구성원의 최신 현재 상태 정보를 유지 관리할 수 있습니다. False로 설정하면 클라이언트 응용 프로그램에서 &quot;축소된&quot; 그룹을 구독할 수 없습니다.</p></td>
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

없음. **New-CsUserServicesConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsUserServicesConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.UserServicesSettings 개체의 새 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsUserServicesConfiguration](get-csuserservicesconfiguration.md)  
[Remove-CsUserServicesConfiguration](remove-csuserservicesconfiguration.md)  
[Set-CsUserServicesConfiguration](set-csuserservicesconfiguration.md)

