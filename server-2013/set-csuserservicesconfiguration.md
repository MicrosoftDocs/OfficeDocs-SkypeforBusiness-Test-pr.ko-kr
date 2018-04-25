---
title: Set-CsUserServicesConfiguration
TOCTitle: Set-CsUserServicesConfiguration
ms:assetid: 51d76f29-4b2b-4208-962c-c5420414ad1b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398340(v=OCS.15)
ms:contentKeyID: 49303621
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsUserServicesConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 User Services 구성 설정 컬렉션을 수정합니다. User Services 서비스는 현재 상태 정보를 유지 관리하고 전화 회의를 관리하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsUserServicesConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsUserServicesConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-AnonymousUserGracePeriod <TimeSpan>] [-Confirm [<SwitchParameter>]] [-DeactivationGracePeriod <TimeSpan>] [-DefaultSubscriptionExpiration <Int64>] [-Force <SwitchParameter>] [-MaintenanceTimeOfDay <DateTime>] [-MaxContacts <UInt16>] [-MaxPersonalNotes <UInt32>] [-MaxScheduledMeetingsPerOrganizer <UInt32>] [-MaxSubscriptionExpiration <Int64>] [-MaxSubscriptions <UInt16>] [-MinSubscriptionExpiration <Int64>] [-PresenceProviders <PSListModifier>] [-SubscribeToCollapsedDG <$true | $false>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Redmond 사이트(-identity site:Redmond)에 대한 User Services 구성 설정을 수정합니다. 이 예제에서 AnonymousUserGracePeriod는 30분(00시간: 30분: 00초)으로 설정됩니다.

    Set-CsUserServicesConfiguration -Identity site:Redmond -AnonymousUserGracePeriod "00:30:00"

## 예제 2

예제 2에서는 Redmond 사이트에 적용된 User Services 구성 설정에 대한 MaintenanceTimeOfDay 속성을 수정합니다. 이를 위해 MaintenanceTimeOfDay 매개 변수와 매개 변수 값 13:30을 사용합니다. 이 값은 하루 중 유지 관리 시간을 오후 1:30(24시간제 형식의 경우 13시간 30분)으로 설정합니다.

    Set-CsUserServicesConfiguration -Identity site:Redmond -MaintenanceTimeOfDay "13:30"

## 예제 3

예제 3에서는 서비스 범위에서 적용된 모든 User Services 구성 설정을 검색한 다음 이러한 각 항목에 대해 허용된 연락처 수를 수정합니다. 이 작업을 수행하기 위해 먼저 **Get-CsUserServicesConfiguration** cmdlet 및 Filter 매개 변수를 사용하여 서비스 범위에서 구성된 모든 설정을 검색합니다. 필터 값 "service:\*"는 반환되는 데이터를 ID가 "service:" 문자로 시작하는 설정으로 제한합니다. 그런 다음 필터링된 컬렉션은 컬렉션에 있는 각 항목의 MaxContacts 속성을 300으로 설정하는 **Set-CsUserServicesConfiguration** cmdlet에 전달됩니다.

    Get-CsUserServicesConfiguration -Filter "service:*" | Set-CsUserServicesConfiguration -MaxContacts 300

## 예제 4

예제 4에서는 사용자에게 300개 이상의 연락처를 허용하는 모든 User Services 구성 설정을 수정합니다. 수정한 후에는 300개 이상의 연락처를 허용하는 설정이 없어집니다. 이 작업을 수행하기 위해 먼저 매개 변수 없이 **Get-CsUserServicesConfiguration** cmdlet을 호출합니다. 그러면 조직에서 현재 사용 중인 모든 User Services 구성 설정의 컬렉션이 반환됩니다. 이 컬렉션은 MaxContacts 속성이 300보다 큰 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 필터링된 컬렉션에 있는 각 항목의 최대 허용 연락처 수를 300으로 변경하는 **Set-CsUserServicesConfiguration** cmdlet에 파이프됩니다.

    Get-CsUserServicesConfiguration | Where-Object {$_.MaxContacts -gt 300} | Set-CsUserServicesConfiguration -MaxContacts 300

## 자세한 정보

Lync Server는 User Services 서비스를 사용하여 사용자의 현재 상태 정보를 유지 관리하고 모임 및 전화 회의를 관리합니다. 그런 다음 **CsUserServicesConfiguration** cmdlet을 사용하여 전역, 사이트 및 서비스 범위에서 User Services 구성 설정을 관리합니다. User Services 구성 설정을 호스트할 수 있는 서비스는 User Services 서비스 자체뿐입니다. 이러한 설정은 사용자가 가질 수 있는 연락처 수, 사용자가 한 번에 예약할 수 있는 모임 수, 전화 회의가 활성 상태로 남아 있을 수 있는 시간 등을 결정합니다.

**Set-CsUserServicesConfiguration** cmdlet을 사용하면 관리자가 현재 사용 중인 모든 User Services 구성 설정에 대한 정보를 수정할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsUserServicesConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsUserServicesConfiguration"}

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
<td><p><em>AnonymousUserGracePeriod</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>인증된 사용자가 같은 모임에 없어도 익명(인증되지 않은) 사용자가 모임에 남아 있을 수 있는 시간을 나타냅니다. 예를 들어 이 값이 15분으로 설정되면 익명 사용자는 인증된 사용자가 참가하기 전까지 최대 15분 동안 전화 회의에 남아 있을 수 있습니다. 유예 기간이 만료되기 전에 인증된 사용자가 참가하지 않으면 익명 사용자는 모임에서 제거됩니다. 이 설정은 예약된 모임 및 Lync에서 모임 시작을 클릭하여 만든 임시 모임에 모두 적용됩니다.</p>
<p>AnonymousUserGracePeriod는 일.시간:분:초(예: 30분의 경우 0.00:30:00) 형식을 사용하여 지정해야 합니다. 유예 기간은 0초에서 1일 사이의 값으로 설정할 수 있습니다. 기본값은 90분(01:30:00)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DeactivationGracePeriod</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>모임이 활성 상태로 유지될 수 있는 최대 시간입니다. 이 값은 일 수.시간:분:초와 같은 형식으로 표시합니다. 예를 들어, 모임을 60분 동안 유지하려면 2.12:00:00(2일: 12시간: 00분: 00초) 형식을 사용합니다.</p>
<p>DeactivationGracePeriod는 8시간-365일(포함)이어야 합니다. 기본값은 1일입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DefaultSubscriptionExpiration</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int64</p></td>
<td><p>사용자가 현재 상태 정보와 같은 데이터를 요청할 때마다 구독이 만들어집니다. 요청이 제출되면 사용자(또는 보다 정확하게 사용자의 클라이언트 응용 프로그램)는 구독이 갱신되기 전에 유효 상태로 남아 있는 시간 길이를 요청할 수 있습니다. 해당 요청이 제출되지 않은 경우 구독은 DefaultSubscriptionExpiration 속성에 의해 지정된 값으로 설정됩니다.</p>
<p>기본 구독 시간은 300초(5분)-86400초(24시간)(포함) 사이의 정수 값으로 표현해야 합니다. 기본값은 28800초(8시간)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>수정할 User Services 구성 설정의 고유한 식별자입니다. 전역 설정을 수정하려면 -Identity global 구문을 사용합니다. 사이트 범위에서 구성된 설정을 수정하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. 서비스 수준에서 설정을 수정하려면 -Identity service:UserServer:atl-cs-001.litwareinc.com과 유사한 구문을 사용합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>UserServicesSettings 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MaintenanceTimeOfDay</em></p></td>
<td><p>선택</p></td>
<td><p>System.DateTime</p></td>
<td><p>정기적으로 예약된 데이터베이스 유지 관리 작업(예: 오래된 레코드 삭제)을 수행할 시간을 나타냅니다. 이 값은 날짜-시간 값으로 지정해야 합니다. 24시간 형식(예: &quot;14:00&quot;)이나 12시간 형식(예: &quot;2:00 PM&quot;)을 사용할 수 있습니다.</p>
<p>MaintenanceTimeOfDay의 기본값은 오전 1:00(01:00:00)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaxContacts</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>사용자가 유지할 수 있는 최대 연락처 수입니다. 기본값은 250입니다. MaxContacts 속성은 사용자가 유지할 수 있는 절대적인 수치의 최대 연락처 수를 나타냅니다. 그러나 <strong>CsClientPolicy</strong> cmdlet을 사용하여 특정 사용자에게는 최대 연락처 수를 MaxContacts의 값보다 작은 값으로 제한할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MaxPersonalNotes</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>사용자의 메모 기록에 저장된 최대 개인 메모 수를 나타냅니다. 기본적으로 메모 기록에는 최근 3개의 개인 메모가 유지 관리됩니다. 기록에 유지 관리할 수 있는 최대 메모 수는 10개입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaxScheduledMeetingsPerOrganizer</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>한 사용자가 지정된 시간에 주최자 역할을 할 수 있는 최대 모임 수입니다. 기본값은 1000입니다. 즉, 사용자가 이미 1000개의 모임에서 주최자인 경우 새 모임(모임 번호 1001)을 예약하려는 시도는 실패하게 됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MaxSubscriptionExpiration</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int64</p></td>
<td><p>사용자가 현재 상태 정보와 같은 데이터를 요청할 때마다 구독이 만들어집니다. 요청이 제출되면 사용자(또는 보다 정확하게 사용자의 클라이언트 응용 프로그램)는 구독이 갱신되기 전에 유효 상태로 남아 있는 시간 길이를 요청할 수 있습니다. MaxSubscriptionExpiration 속성은 클라이언트에게 부여할 수 있는 최대 시간을 나타냅니다. 예를 들어 최대 시간이 28800초로 설정되고 클라이언트가 86400초의 시간 초과 간격을 요청하면 클라이언트에 허용되는 최대 만료 기간은 28800초로 지정됩니다.</p>
<p>최대 구독 시간은 300초(5분)-86400초(24시간)(포함) 사이의 정수 값으로 표현해야 합니다. 기본값은 43200초(12시간)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaxSubscriptions</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt16</p></td>
<td><p>사용자가 한 번에 열 수 있는 최대 SIP 구독 대화 상자 수입니다. 구독 대화 상자는 SIP 리소스에 대한 요청을 나타냅니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MinSubscriptionExpiration</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int64</p></td>
<td><p>사용자가 현재 상태 정보와 같은 데이터를 요청할 때마다 구독이 만들어집니다. 요청이 제출되면 사용자(또는 보다 정확하게 사용자의 클라이언트 응용 프로그램)는 구독이 갱신되기 전에 유효 상태로 남아 있는 시간 길이를 요청할 수 있습니다. MinSubscriptionExpiration 속성은 클라이언트에게 부여할 수 있는 최소 시간을 나타냅니다. 예를 들어 최소 시간이 1200초로 설정되고 클라이언트가 200초의 시간 초과 간격을 요청하면 클라이언트에 허용되는 최소 만료 기간은 1200초로 지정됩니다.</p>
<p>최소 구독 시간은 300초(5분)-86400초(24시간)(포함) 사이의 정수 값으로 표현해야 합니다. 기본값은 1200초(20분)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PresenceProviders</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>사용자 서비스 구성 설정에 대한 현재 상태 공급자 컬렉션입니다. 현재 상태 공급자는 <strong>New-CsPresenceProvider</strong> cmdlet을 사용하여 사용자 서비스 구성 설정의 컬렉션에 추가하는 것이 가장 좋습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SubscribeToCollapsedDG</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True(기본값)로 설정하면 클라이언트 응용 프로그램이 연락처 목록에서 현재 확장되지 않은 메일 그룹을 구독할 수 있습니다. 이 경우 클라이언트가 그룹의 각 구성원에 대한 현재 상태 정보를 최신 상태로 유지할 수 있습니다. False로 설정된 경우 클라이언트 응용 프로그램은 &quot;축소된&quot; 그룹을 구독할 수 없습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.UserServicesSettings 개체입니다. **Set-CsUserServicesConfiguration** cmdlet은 User Services 설정 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Set-CsUserServicesConfiguration** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.UserServices.UserServicesSettings 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[Get-CsUserServicesConfiguration](get-csuserservicesconfiguration.md)  
[New-CsUserServicesConfiguration](new-csuserservicesconfiguration.md)  
[Remove-CsUserServicesConfiguration](remove-csuserservicesconfiguration.md)

