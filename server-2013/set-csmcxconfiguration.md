---
title: Set-CsMcxConfiguration
TOCTitle: Set-CsMcxConfiguration
ms:assetid: eaff70d9-97fa-482c-b9fb-a90263685b29
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh690050(v=OCS.15)
ms:contentKeyID: 49305419
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsMcxConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server Mobility Service 구성 설정의 기존 컬렉션을 수정할 수 있습니다. iPhone 및 Windows Phone 같은 휴대폰 사용자는 Mobility Service를 통해 메신저 대화 및 현재 상태 정보를 교환하고, 음성 메일을 해당 무선 공급자를 통해서가 아닌 내부에서 저장 및 검색하고, 회사번호로 전화 기능 및 외부 전화 접속 회의 같은 Lync 기능을 활용하는 등의 작업을 수행할 수 있습니다. 이 cmdlet은 Lync Server 2010용 2011년 11월 누적 업데이트에서 도입되었습니다.

## 구문

    Set-CsMcxConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsMcxConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-ExposedWebURL <External | Internal>] [-Force <SwitchParameter>] [-PushNotificationProxyUri <String>] [-SessionExpirationInterval <UInt32>] [-SessionShortExpirationInterval <UInt32>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 Redmond 사이트에 할당된 Mobility Service 구성 설정의 ExposedWebURL 속성을 External로 설정합니다.

    Set-CsMcxConfiguration -Identity site:Redmond -ExposedWebURL External

## 예제 2

예제 2에서는 단일 명령으로 조직에서 현재 사용 중인 모든 Mobility Service 구성 설정에 동일한 속성 값을 할당하는 방법을 보여 줍니다. 이를 위해 명령에서는 먼저 매개 변수 없이 **Get-CsMcxConfiguration** cmdlet을 사용하여 모든 기존 Mobility Service 구성 설정의 컬렉션을 반환합니다. 그런 다음 이 컬렉션은 해당 컬렉션의 각 항목에 대한 ExposedWebURL 속성을 External로 설정하는 **Set-CsMcxConfiguration**에 파이프됩니다.

    Get-CsMcxConfiguration | Set-CsMcxConfiguration -ExposedWebURL External

## 예제 3

예제 3에서는 SessionShortExpirationInterval이 3600초를 초과하는 모든 Mobility Service 구성 설정을 수정하여 이 속성 값을 3600으로 설정합니다. 이렇게 하면 실제로 조직의 모든 Mobility Service 구성 설정에 대한 최대값이 3600초로 지정됩니다. 이 작업을 수행하기 위해 먼저 매개 변수 없이 **Get-CsMcxConfiguration** cmdlet을 호출하여 현재 사용 중인 모든 Mobility Service 구성 설정의 컬렉션을 반환합니다. 그런 후 이 컬렉션은 SessionShortExpirationInterval 속성이 3600보다 큰(-gt) 설정만 선택하는 Where-Object cmdlet에 파이프됩니다. 그런 다음 이렇게 필터링된 컬렉션은 해당 컬렉션의 각 항목에 대한 SessionShortExpirationInterval 속성을 3600으로 설정하는 **Set-CsMcxConfiguration** cmdlet에 파이프됩니다.

    Get-CsMcxConfiguration | Where-Object {$_.SessionShortExpirationInterval -gt 3600} | Set-CsMcxConfiguration -SessionShortExpirationInterval 3600

## 자세한 정보

Lync Server Mobility Service는 Lync의 많은 기능을 Apple iPhone, Windows Phone, Android 전화, Nokia 전화 같은 모바일 장치로 확장합니다. 무엇보다도 사용자는 이러한 전화를 사용하여 메신저 대화 및 현재 상태 정보를 교환하고, 새 음성 메일에 대한 알림을 수신할 수 있습니다. iPhone 또는 Windows Phone 사용자는 푸시 알림 서비스(Apple 푸시 알림 서비스 및 Microsoft 푸시 알림 서비스) 덕분에 Lync Server이 백그라운드에서 실행 중이더라도 이러한 알림을 수신할 수 있습니다. 또한 Mobility Service를 사용하면 조직에서 회사번호로 전화 기능을 사용할 수 있습니다. 회사번호로 전화 기능을 사용하면 휴대폰에서 전화를 걸지만 회사 전화 번호에서 전화가 걸려 온 것처럼 보이게 할 수 있습니다. 예를 들어 발신자 번호 시스템에서 사용자의 휴대폰 번호 대신 회사 전화 번호를 표시합니다.

Mobility Service 자체는 Mobility Service 구성 설정을 사용하여 관리하며, 이러한 설정은 전역 범위, 사이트 범위 또는 서비스 범위(웹 서버 서비스만 해당)에 적용할 수 있습니다. 또한 이 설정은 Mobility Service 세션의 최대 시간 길이, 조직 방화벽 외부에서 로그온하는 사용자가 Lync Server 자동 검색 서비스(Mobility Service 사용자를 적절한 등록자 풀로 보냄)를 사용할 수 있는지 여부, 푸시 알림 서비스 공급자의 위치 등을 제어합니다.

관리자는 **Set-CsMcxConfiguration** cmdlet을 사용하여 기존 Mobility Service 구성 설정을 수정할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsMcxConfiguration** cmdlet을 로컬로 실행할 수 있습니다.

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
<td><p><em>ExposedWebURL</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.McxConfiguration.ExposedWebURL</p></td>
<td><p>자동 검색 서비스에서 사용하는 URL을 조직 방화벽 내/외부의 사용자가 모두 액세스할 수 있는지(External), 아니면 방화벽 내에 있는 사용자만 액세스할 수 있는지(Internal)를 나타냅니다.</p>
<p>허용되는 값은 Internal 또는 External이며, 기본값은 External입니다.</p></td>
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
<td><p>수정할 Mobility Service 구성 설정 컬렉션의 고유 식별자를 나타냅니다. 전역 설정을 수정하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity global</p>
<p>사이트 범위에서 설정을 수정하려면 접두사 &quot;site:&quot; 다음에 사이트 이름이 오도록 합니다. 예를 들면 다음과 같습니다.</p>
<p>-Identity &quot;site:Redmond&quot;</p>
<p>서비스 범위에서 구성된 설정을 수정하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity service:WebServer:atl-cs-001.litwareinc.com</p>
<p>이 매개 변수를 지정하지 않으면 <strong>Set-CsMcxConfiguration</strong> cmdlet은 전역 설정을 수정합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>MCX 구성 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PushNotificationProxyUri</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>푸시 알림 요청을 Apple 푸시 알림 서비스 및 Microsoft 푸시 알림 서비스로 전달할 수 있는 서비스 공급자의 URI입니다. PushNotificationProxyUri는 다음과 같은 SIP 주소 형태여야 합니다.</p>
<p>-PushNotificationProxyUri &quot;sip:push@push.lync.com&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>SessionExpirationInterval</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>iPhone 또는 Widows Phone 사용자에 대한 모바일 세션의 시간 길이(초)입니다. 이러한 전화에서 Lync가 백그라운드에서 실행 중인 경우 사용자는 세션 만료 간격이 아직 만료되지 않은 한 푸시 알림을 수신하게 됩니다.</p>
<p>모바일 장치에서는 세션 시간 제한에 도달하기 전에 장치가 여전히 활성 상태임을 나타내는 알림을 서버로 보내야 합니다. 이렇게 하지 않으면 장치가 비활성 상태로 나타나고 사용자는 시스템에 다시 로그온해야 합니다.</p>
<p>이 속성은 120~4294967295(포함) 사이의 정수 값으로 설정할 수 있습니다. 기본값은 259200초(3일)입니다. SessionExpirationInterval 속성 값은 SessionShortExpirationInterval 속성 값보다 커야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SessionShortExpirationInterval</em></p></td>
<td><p>선택</p></td>
<td><p>System.UInt32</p></td>
<td><p>Android 또는 Nokia 전화 사용자에 대한 모바일 세션의 시간 길이(초)입니다.</p>
<p>모바일 장치에서는 세션 시간 제한에 도달하기 전에 장치가 여전히 활성 상태임을 나타내는 알림을 서버로 보내야 합니다. 이렇게 하지 않으면 장치가 비활성 상태로 나타나고 사용자는 시스템에 다시 로그온해야 합니다.</p>
<p>이 속성은 120~4294967295(포함) 사이의 정수 값으로 설정할 수 있습니다. 기본값은 3600초(1시간)입니다. SessionExpirationInterval 속성 값은 SessionShortExpirationInterval 속성 값보다 커야 합니다.</p></td>
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

Microsoft.Rtc.Management.WriteableConfig.Settings.McxConfiguration.McxConfiguration 개체입니다. **Set-CsMcxConfiguration** cmdlet은 McxConfiguration 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

없음. 대신 **Set-CsMcxConfiguration** cmdlet은 Microsoft.Rtc.Management.WriteableConfig.Settings.McxConfiguration.McxConfiguration 개체의 기존 인스턴스를 수정합니다.

