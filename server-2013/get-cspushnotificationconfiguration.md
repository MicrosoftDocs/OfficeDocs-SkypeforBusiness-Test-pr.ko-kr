---
title: Get-CsPushNotificationConfiguration
TOCTitle: Get-CsPushNotificationConfiguration
ms:assetid: ec2c17e5-ac4d-4d21-995a-642c5cf5c7bc
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh690049(v=OCS.15)
ms:contentKeyID: 49305427
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsPushNotificationConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 현재 사용 중인 푸시 알림 구성 설정에 대한 정보를 검색합니다. 푸시 알림 서비스(Apple 푸시 알림 서비스 및 Microsoft 푸시 알림 서비스)를 사용하면 새 메신저 대화 또는 새 음성 메일 같은 이벤트에 대한 알림을 iPhone 및 Windows Phone 등의 모바일 장치로 보낼 수 있습니다. 이는 이러한 장치에서 현재 Lync 응용 프로그램이 일시 중단되었거나 백그라운드에서 실행 중인 경우에도 마찬가지입니다. 이 cmdlet은 Lync Server 2010용 2011년 11월 누적 업데이트에서 도입되었습니다.

## 구문

    Get-CsPushNotificationConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsPushNotificationConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>] [-Tenant <Guid>]

## 예제

## 예제 1

예제 1에서는 조직에서 사용하도록 구성된 모든 푸시 알림 설정에 대한 정보를 반환합니다.

    Get-CsPushNotificationConfiguration

## 예제 2

예제 2에 표시된 명령은 Redmond 사이트에 대해 구성된 설정인 단일 푸시 알림 설정 컬렉션에 대한 정보를 반환합니다.

    Get-CsPushNotificationConfiguration -Identity "site:Redmond"

## 예제 3

예제 3에서는 명령이 사이트 범위에 할당된 모든 푸시 알림 설정을 반환합니다. 이를 위해 명령에서는 Filter 매개 변수와 필터 값 "site:\*"를 사용합니다. 이 필터 값은 해당 ID가 문자열 값 "site:"으로 시작하는 설정만 반환합니다.

    Get-CsPushNotificationConfiguration -Filter "site:*"

## 예제 4

예제 4에서는 iPhone에 대한 푸시 알림이 사용하지 않도록 설정된 모든 푸시 알림 설정을 반환합니다. 이를 위해 명령에서는 먼저 **Get-CsPushNotificationConfiguration** cmdlet을 사용하여 조직에서 현재 사용 중인 모든 푸시 알림 설정 컬렉션을 반환합니다. 그런 다음 이 컬렉션은 EnableApplePushNotificationService 속성이 False와 같은(-eq) 설정만 골라내는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsPushNotificationConfiguration | Where-Object {$_.EnableApplePushNotificationService -eq $False}

## 예제 5

예제 5에서는 Apple 푸시 알림 서비스 및/또는 Microsoft 푸시 알림 서비스가 사용하지 않도록 설정된 모든 푸시 알림 설정에 대한 정보를 반환합니다. 이 작업을 수행하기 위해 명령에서는 먼저 **Get-CsPushNotificationConfiguration** cmdlet을 사용하여 현재 사용 중인 모든 푸시 알림 설정 컬렉션을 반환합니다. 그런 다음 이 컬렉션은 두 가지 기준 중 하나 또는 둘 다 충족하는 설정을 골라내는 Where-Object cmdlet에 파이프됩니다. 이러한 기준 중 첫 번째는 EnableApplePushNotificationService 속성이 Fasle여야(-eq) 한다는 것이고, 두 번째는 EnableMicrosoftPushNotificationService 속성이 False여야 한다는 것입니다. -or 연산자는 Where-Object가 어느 한쪽 기준을 충족하는 설정을 검색하도록 합니다. 반환되는 데이터를 두 서비스가 모두 사용하지 않도록 지정된 설정으로 제한하려면 -and 연산자를 사용합니다.

Get-CsPushNotificationConfiguration | Where-Object {$\_.EnableApplePushNotificationService –eq $False –and $\_.EnableMicrosoftPushNotificationService –eq $False}

    Get-CsPushNotificationConfiguration | Where-Object {$_.EnableApplePushNotificationService -eq $False -or $_.EnableMicrosoftPushNotificationService -eq $False}

## 자세한 정보

Apple 푸시 알림 서비스 및 Microsoft 푸시 알림 서비스는 자신의 Apple iPhone 또는 Windows Phone에서 Lync를 실행하는 사용자가 Lync가 일시 중단되었거나 백그라운드에서 실행 중이더라도 Lync 이벤트에 대한 알림을 수신할 수 있도록 합니다. 예를 들어 사용자는 다음에 대한 이벤트 알림을 수신할 수 있습니다.

\- 새 메신저 대화 세션 또는 전화 회의 초대

\- 새 메신저 대화

\- 새 음성 메일

푸시 알림 서비스를 사용하지 않는 사용자는 Lync가 포그라운드에서 활성 응용 프로그램으로 사용되는 경우에만 이러한 알림을 수신하게 됩니다.

관리자는 iPhone 사용자 및/또는 Windows Phone 사용자에 대해 푸시 알림을 사용하거나 사용하지 않도록 설정할 수 있습니다. 기본적으로 푸시 알림은 iPhone 사용자 및 Windows Phone 사용자 모두에 대해 사용하지 않도록 설정됩니다. 관리자는 **Set-CsPushNotificationConfiguration** cmdlet을 사용하여 전역 범위에서 푸시 알림을 사용하거나 사용하지 않도록 설정할 수 있습니다. 또한 **New-CsPushNotificationConfiguration** cmdlet을 사용하여 사이트 범위에서 사용자 지정 푸시 알림 설정을 만들 수 있습니다.

**Get-CsPushNotificationConfiguration** cmdlet을 사용하면 조직에서 현재 사용 중인 푸시 알림 구성 설정에 대한 정보를 반환할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsPushNotificationConfiguration** cmdlet을 로컬로 실행할 수 있습니다.

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
<td><p>하나 이상의 푸시 알림 구성 설정 컬렉션을 반환하기 위해 와일드카드 문자를 사용할 수 있습니다. 사이트 범위에서 구성된 모든 설정 컬렉션을 반환하려면 다음 구문을 사용합니다.</p>
<p>-Filter site:*</p>
<p>ID(필터링할 수 있는 유일한 속성)에 문자열 값 &quot;Canada&quot;가 포함된 모든 설정 컬렉션을 반환하려면 다음 구문을 사용합니다.</p>
<p>-Filter &quot;*Canada*&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환할 푸시 알림 설정 컬렉션의 고유 식별자를 나타냅니다. 전역 설정을 참조하려면 다음 구문을 사용합니다.</p>
<p>-Identity global</p>
<p>사이트 범위에서 구성된 컬렉션을 참조하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity site:Redmond</p>
<p>ID를 지정할 때는 와일드카드를 사용할 수 없습니다. 와일드카드를 사용해야 하는 경우 대신 Filter 매개 변수를 포함합니다.</p>
<p>이 매개 변수를 지정하지 않으면 <strong>Get-CsPushNotificationConfiguration</strong> cmdlet이 조직에서 사용 중인 모든 푸시 알림 구성 설정 컬렉션을 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 푸시 알림 구성 데이터를 검색합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>해당 푸시 알림 구성 설정을 수정할 Office 365 테넌트 계정의 GUID(Globally Unique Identifier)입니다. 예를 들면 다음과 같습니다.</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대해 테넌트 ID를 반환할 수 있습니다.</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p>
<p>Windows PowerShell 원격 세션을 사용 중이며 비즈니스용 Skype Online에만 연결되어 있는 경우에는 Tenant 매개 변수를 포함하지 않아도 됩니다. 대신, 연결 정보를 기반으로 테넌트 ID가 자동으로 채워집니다. Tenant 매개 변수는 하이브리드 배포에서 주로 사용됩니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

**Get-CsPushNotificationConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsPushNotificationConfiguration** cmdlet은 Microsoft.Rtc.Management.WriteableConfig.Settings.PushNotificationConfiguration.PushNotificationConfiguration 개체의 인스턴스를 반환합니다.

