---
title: Remove-CsPushNotificationConfiguration
TOCTitle: Remove-CsPushNotificationConfiguration
ms:assetid: 77574e30-a75f-4aaa-b2d8-ccbabda31797
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh690028(v=OCS.15)
ms:contentKeyID: 49304085
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsPushNotificationConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

푸시 알림 설정의 기존 컬렉션을 삭제할 수 있습니다. 푸시 알림 서비스(Apple 푸시 알림 서비스 및 Microsoft 푸시 알림 서비스)를 사용하면 새 메신저 대화 또는 새 음성 메일 같은 이벤트에 대한 알림을 iPhone 및 Windows Phone 등의 모바일 장치로 보낼 수 있습니다. 이는 이러한 장치에서 현재 Lync 응용 프로그램이 일시 중단되었거나 백그라운드에서 실행 중인 경우에도 마찬가지입니다. 이 cmdlet은 Lync Server 2010용 2011년 11월 누적 업데이트에서 도입되었습니다.

## 구문

    Remove-CsPushNotificationConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Redmond 사이트에 할당된 푸시 알림 설정의 컬렉션을 삭제합니다.

    Remove-CsPushNotificationConfiguration -Identity "site:Redmond"

## 예제 2

예제 2에서는 사이트 범위에 구성된 모든 푸시 알림 설정을 삭제합니다. 이 작업을 수행하기 위해 cmdlet은 먼저 **Get-CsPushNotificationConfiguration** cmdlet과 Filter 매개 변수를 사용하여 사이트 범위에 구성된 모든 설정 컬렉션을 반환합니다. 필터 값 "site:\*"는 반환되는 항목을 ID가 문자열 값 "site:"으로 시작되는 설정으로 제한합니다. 그러면 사이트 범위 설정이 **Remove-CsPushNotificationConfiguration** cmdlet에 파이프되고 이 cmdlet을 통해 삭제됩니다.

    Get-CsPushNotificationConfiguration -Filter "site:*" | Remove-CsPushNotificationConfiguration

## 예제 3

예제 3에서는 Microsoft 푸시 알림 서비스의 푸시 알림이 사용하지 않도록 설정된 모든 푸시 알림 구성 설정을 제거하는 방법을 보여줍니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsPushNotificationConfiguration** cmdlet을 사용하여 현재 사용 중인 모든 푸시 알림 설정 컬렉션을 반환합니다. 그러면 이 컬렉션은 EnableMicrosoftPushNotificationService 속성이 False와 같은(-eq) 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 이렇게 필터링된 컬렉션은 컬렉션의 각 항목을 삭제하는 **Remove-CsPushNotificationConfiguration** cmdlet에 파이프됩니다.

    Get-CsPushNotificationConfiguration | Where-Object {$_.EnableMicrosoftPushNotificationService -eq $False} | Remove-CsPushNotificationConfiguration

## 자세한 정보

Apple 푸시 알림 서비스 및 Microsoft 푸시 알림 서비스는 자신의 Apple iPhone 또는 Windows Phone에서 Lync를 실행하는 사용자가 Lync가 일시 중단되었거나 백그라운드에서 실행 중이더라도 Lync 이벤트에 대한 알림을 수신할 수 있도록 합니다. 예를 들어 사용자는 다음에 대한 이벤트 알림을 수신할 수 있습니다.

\- 새 메신저 대화 세션 또는 전화 회의 초대

\- 새 메신저 대화

\- 새 음성 메일

푸시 알림 서비스를 사용하지 않는 사용자는 Lync가 포그라운드에서 활성 응용 프로그램으로 사용되는 경우에만 이러한 알림을 수신하게 됩니다.

관리자는 iPhone 사용자 및/또는 Windows Phone 사용자에 대해 푸시 알림을 사용하거나 사용하지 않도록 설정할 수 있습니다. 기본적으로 푸시 알림은 iPhone 사용자 및 Windows Phone 사용자 모두에 대해 사용하지 않도록 설정됩니다. 관리자는 **Set-CsPushNotificationConfiguration** cmdlet을 사용하여 전역 범위에서 푸시 알림을 사용하거나 사용하지 않도록 설정할 수 있습니다. 또한 **New-CsPushNotificationConfiguration** cmdlet을 사용하여 사이트 범위에서 사용자 지정 푸시 알림 설정을 만들 수 있습니다.

이러한 사용자 지정 설정은 나중에 **Remove-CsPushNotificationConfiguration** cmdlet을 사용하여 삭제할 수 있습니다. 사이트 범위에서 구성된 설정을 삭제하면 해당 사이트의 사용자는 자동으로 전역 푸시 알림 설정을 통해 관리됩니다.

**Remove-CsPushNotificationConfiguration** cmdlet은 전역 설정에 대해서도 실행할 수 있습니다. 그러나 이 경우 전역 설정은 제거되지 않습니다. 대신 전역 설정의 속성이 모두 기본값으로 다시 설정됩니다. 이렇게 되면 Apple 푸시 알림 서비스 및 Microsoft 푸시 알림 서비스 모두에서 푸시 알림이 사용하지 않도록 설정됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsPushNotificationConfiguration** cmdlet을 로컬로 실행할 수 있습니다.

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
<td><p>제거할 푸시 알림 구성 설정 컬렉션의 고유 식별자입니다. 전역 컬렉션을 제거하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity global</p>
<p>전역 설정은 실제로 제거할 수 없으며, 속성을 기본값으로 다시 설정할 수만 있습니다.</p>
<p>사이트 컬렉션을 제거하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity site:Redmond</p>
<p>정책 ID를 지정할 때는 와일드카드를 사용할 수 없습니다.</p></td>
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
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>삭제할 푸시 알림 구성 설정에 대한 비즈니스용 Skype Online 테넌트 계정의 GUID(Globally Unique identifier)입니다. 예를 들면 다음과 같습니다.</p>
<p>-Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대해 테넌트 ID를 반환할 수 있습니다.</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
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

Microsoft.Rtc.Management.WriteableConfig.Settings.PushNotificationConfiguration.PushNotificationConfiguration. **Remove-CsPushNotificationConfiguration** cmdlet은 PushNotificationConfiguration 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Remove-CsPushNotificationConfiguration** cmdlet은 Microsoft.Rtc.Management.WriteableConfig.Settings.PushNotificationConfiguration.PushNotificationConfiguration 개체의 인스턴스를 삭제합니다.

