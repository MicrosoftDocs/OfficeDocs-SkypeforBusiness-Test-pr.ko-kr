---
title: New-CsPushNotificationConfiguration
TOCTitle: New-CsPushNotificationConfiguration
ms:assetid: 8bf61c72-7902-4075-9388-47a7dd4e649c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh690027(v=OCS.15)
ms:contentKeyID: 49304319
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsPushNotificationConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

사이트 범위에서 푸시 알림 구성 설정 컬렉션을 새로 만들 수 있습니다. 푸시 알림 서비스(Apple 푸시 알림 서비스 및 Microsoft 푸시 알림 서비스)를 사용하면 새 메신저 대화 또는 새 음성 메일 같은 이벤트에 대한 알림을 iPhone 및 Windows Phone 등의 모바일 장치로 보낼 수 있습니다. 이는 이러한 장치에서 현재 Lync 응용 프로그램이 일시 중단되었거나 백그라운드에서 실행 중인 경우에도 마찬가지입니다. 이 cmdlet은 Lync Server 2010용 2011년 11월 누적 업데이트에서 도입되었습니다.

## 구문

    New-CsPushNotificationConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-EnableApplePushNotificationService <$true | $false>] [-EnableMicrosoftPushNotificationService <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-Tenant <Guid>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Redmond 사이트에 대해 푸시 알림 설정 컬렉션을 새로 만들고 Apple 푸시 알림 서비스와 Microsoft 푸시 알림 서비스 모두의 푸시 알림을 사용하도록 설정합니다. 이들 두 서비스의 푸시 알림을 사용하도록 설정하기 위해 EnableApplePushNotificationService 및 EnableMicrosoftPushNotificationService 속성을 모두 True로 설정합니다.

    New-CsPushNotificationConfiguration -Identity "site:Redmond" -EnableApplePushNotificationService $True -EnableMicrosoftPushNotificationService -$True

## 예제 2

예제 2에서는 각 Lync Server 사이트에 대해 푸시 구성 설정 집합을 만드는 방법을 보여줍니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsSite** cmdlet을 사용하여 모든 Lync Server 사이트의 컬렉션을 반환합니다. 그러면 이 컬렉션이 **ForEach-Object** cmdlet에 파이프되는데, 이 cmdlet은 컬렉션의 각 사이트를 가져오고, **New-CsPushNotificationConfiguration** cmdlet을 호출하고, 해당 사이트에 대한 푸시 알림 구성 설정 집합을 새로 만듭니다. 이미 푸시 알림 구성 설정 컬렉션을 호스트하고 있는 사이트에 대해서는 이 명령이 실패합니다.

    Get-CsSite | ForEach-Object {New-CsPushConfigurationNotification -Identity $_.Identity}

## 예제 3

예제 3에서는 InMemory 매개 변수를 사용하여 처음에 메모리에만 존재하는 푸시 알림 구성 설정의 컬렉션을 생성하는 방법을 보여줍니다. 이를 위해 예제에서는 ID가 site:Redmond인 설정의 새 컬렉션을 만들고 이 컬렉션을 변수 $x에 저장합니다. 첫 번째 명령이 실행된 후에는 컬렉션이 메모리에만 존재합니다. **Get-CsPushNotificationConfiguration** cmdlet을 실행하는 경우 site:Redmond에 대한 항목이 표시되지 않습니다.

다음 두 명령에서는 이 가상 설정 컬렉션의 EnableApplePushNotificationService 및 EnableMicrosoftPushNotificationService 속성을 둘 다 True로 설정하여 Apple 푸시 알림 서비스 및 Microsoft 푸시 알림 서비스 모두의 푸시 알림을 사용하도록 설정합니다. 끝으로, 마지막 명령에서는 **Set-CsPushNotificationConfiguration** cmdlet을 사용하여 가상 푸시 알림 설정을 Redmond 사이트에 적용되는 실제 설정 컬렉션으로 변환합니다. **Set-CsPushNotificationConfiguration** cmdlet을 호출하지 않는 경우 이러한 설정은 메모리에만 존재하게 되며, Windows PowerShell 세션이 종료되거나 변수 $x가 삭제되면 사라집니다.

    $x = New-CsPushNotificationConfiguration -Identity "site:Redmond" -InMemory
    $x.EnableApplePushNotificationService = $True 
    $x.EnableMicrosoftPushNotificationService = $True
    Set-CsPushNotificationConfiguration -Instance $x

## 자세한 정보

Apple 푸시 알림 서비스 및 Microsoft 푸시 알림 서비스는 자신의 Apple iPhone 또는 Windows Phone에서 Lync를 실행하는 사용자가 Lync가 일시 중단되었거나 백그라운드에서 실행 중이더라도 Lync 이벤트에 대한 알림을 수신할 수 있도록 합니다. 예를 들어 사용자는 다음에 대한 이벤트 알림을 수신할 수 있습니다.

\- 새 메신저 대화 세션 또는 전화 회의 초대

\- 새 메신저 대화

\- 새 음성 메일

푸시 알림 서비스를 사용하지 않는 사용자는 Lync가 포그라운드에서 활성 응용 프로그램으로 사용되는 경우에만 이러한 알림을 수신하게 됩니다.

관리자는 iPhone 사용자 및/또는 Windows Phone 사용자에 대해 푸시 알림을 사용하거나 사용하지 않도록 설정할 수 있습니다. 기본적으로 푸시 알림은 iPhone 사용자 및 Windows Phone 사용자 모두에 대해 사용하지 않도록 설정됩니다. 관리자는 **Set-CsPushNotificationConfiguration** cmdlet을 사용하여 전역 범위에서 푸시 알림을 사용하거나 사용하지 않도록 설정할 수 있습니다. 또한 **New-CsPushNotificationConfiguration** cmdlet을 사용하여 사이트 범위에서 사용자 지정 푸시 알림 설정을 만들 수 있습니다. 이렇게 하면 관리자가 다른 사이트에서는 푸시 알림을 사용하지 못하게 하면서 특정 사이트(예: Redmond)의 사용자에게 이러한 알림을 제공할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsPushNotificationConfiguration** cmdlet을 로컬로 실행할 수 있습니다.

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
<td><p>푸시 알림 설정은 사이트 범위에서만 만들 수 있습니다. 사이트에 대한 새 설정 컬렉션을 지정하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity &quot;site:Redmond&quot;</p>
<p>Redmond 사이트에서 이미 푸시 알림 설정 컬렉션을 호스트하고 있으면 이 명령은 실패합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableApplePushNotificationService</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하는 경우 iPhone 사용자는 Apple 푸시 알림 서비스로부터 푸시 알림을 수신하게 되며, False로 설정하면 이러한 알림을 수신하지 못하게 됩니다.</p>
<p>기본값은 False입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableMicrosoftPushNotificationService</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하는 경우 Windows Phone 사용자는 Microsoft 푸시 알림 서비스로부터 푸시 알림을 수신하게 되며, False로 설정하면 이러한 알림을 수신하지 못하게 됩니다.</p>
<p>기본값은 False입니다.</p></td>
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
<td><p>개체를 실제로 영구 변경 내용으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 명령의 출력을 변수에 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 이러한 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>새 푸시 알림 구성 설정이 만들어지는 비즈니스용 Skype Online 테넌트 계정의 GUID(Globally unique identifier)입니다. 예를 들면 다음과 같습니다.</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대해 테넌트 ID를 반환할 수 있습니다.</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
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

없음. **New-CsPushNotificationConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**New-CsPushNotificationConfiguration** cmdlet은 Microsoft.Rtc.Management.WriteableConfig.Settings.PushNotificationConfiguration.PushNotificationConfiguration 개체의 새 인스턴스를 만듭니다.

