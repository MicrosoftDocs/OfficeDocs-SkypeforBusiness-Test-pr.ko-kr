---
title: New-CsMcxConfiguration
TOCTitle: New-CsMcxConfiguration
ms:assetid: 9eebea4a-64a3-424c-9b05-0579c4e8111e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh690035(v=OCS.15)
ms:contentKeyID: 49304548
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsMcxConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

사이트 또는 서비스 범위에서 Lync Server 2013 Mobility Service 구성 설정의 새 컬렉션을 만듭니다. iPhone 및 Windows Phone 같은 휴대폰 사용자는 Mobility Service를 통해 메신저 대화 및 현재 상태 정보를 교환하고, 음성 메일을 해당 무선 공급자를 통해서가 아닌 내부에서 저장 및 검색하고, 회사번호로 전화 기능 및 외부 전화 접속 회의 같은 Lync Server 기능을 활용하는 등의 작업을 수행할 수 있습니다. 이 cmdlet은 Lync Server 2010용 2011년 11월 누적 업데이트에서 도입되었습니다.

## 구문

    New-CsMcxConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-ExposedWebURL <External | Internal>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-PushNotificationProxyUri <String>] [-SessionExpirationInterval <UInt32>] [-SessionShortExpirationInterval <UInt32>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 Redmond 사이트에 대해 새 Mobility Service 구성 설정 컬렉션을 만들어 사이트에 자동으로 할당합니다. 이 예제에서는 기본 Mobility Service 구성 설정의 두 가지 항목을 변경하는데, 하나는 ExposedWebURL 속성을 Internal로 설정하는 것이고 다른 하나는 SessionShortExpirationInterval 속성을 7200초로 설정하는 것입니다.

    New-CsMcxConfiguration -Identity "site:Redmond" -ExposedWebURL Internal -SessionShortExpirationInterval 7200

## 예제 2

예제 2에서는 조직에서 현재 사용 중인 각 웹 서버에 대해 동일한 Mobility Service 구성 설정 집합을 만듭니다. 이 작업을 수행하기 위해 **Get-CsService** cmdlet과 함께 WebServer 매개 변수를 사용하여 모든 기존 웹 서버 컬렉션을 반환합니다. 그러면 이 컬렉션은 **For-Each** 개체 cmdlet에 파이프됩니다. 또한 **ForEach-Object** cmdlet은 컬렉션의 각 서버를 가져오고 **New-CsMcxConfiguration** cmdlet을 실행하여 해당 서버의 새 Mobility Service 구성 설정을 만듭니다.

    Get-CsService -WebServer | ForEach-Object {New-CsMcxConfiguration -Identity $_.Identity -ExposedWebURL Internal -SessionShortExpirationInterval 7200}

## 예제 3

예제 3에서는 InMemory 매개 변수를 사용하여 메모리에 Mobility Service 구성 설정 컬렉션을 새로 만들고, 이 컬렉션의 속성 값을 수정한 다음 컬렉션을 Lync Server에 저장하는 방법을 보여 줍니다. 이를 위해 컬렉션의 첫 번째 명령에서는 ID가 site:Redmond인 Mobility Service 구성 설정 컬렉션을 새로 만듭니다. 하지만 이러한 설정은 자동으로 만들어져 Redmond 사이트에 할당되는 대신 InMemory 매개 변수로 인해 메모리에만 만들어진 다음 변수 $x에 저장됩니다.

예제의 명령 2 및 3에서는 이 가상 Mobility Service 구성 컬렉션의 속성 값을 변경하는 방법을 보여 줍니다. 속성 값의 수정을 완료한 후에는 **Set-CsMcxConfiguration** cmdlet과 Instance 매개 변수를 사용하여 가상 설정을 Redmond 사이트에 할당되는 실제 Mobility Service 구성 설정 컬렉션으로 변환할 수 있습니다. **Set-CsMcxConfiguration** cmdlet을 호출하지 않으면 어떤 설정도 Redmond 사이트에 할당되지 않으며, Windows PowerShell 세션을 끝내거나 변수 $x를 삭제하는 즉시 가상 컬렉션이 사라집니다.

    $x = New-CsMcxConfiguration -Identity "site:Redmond" -InMemory
    $x.ExposedWebURL = "Internal"
    $x.SessionShortExpirationInterval = 7200
    Set-CsMcxConfiguration -Instance $x

## 자세한 정보

Mobility Service는 Lync Server의 많은 기능을 Apple iPhone, Windows Phone, Android 전화, Nokia 전화 같은 모바일 장치로 확장합니다. 무엇보다도 사용자는 이러한 전화를 사용하여 메신저 대화 및 현재 상태 정보를 교환하고, 새 음성 메일에 대한 알림을 수신할 수 있습니다. iPhone 또는 Windows Phone 사용자는 푸시 알림 서비스(Apple 푸시 알림 서비스 및 Microsoft 푸시 알림 서비스) 덕분에 Lync가 백그라운드에서 실행 중이더라도 이러한 알림을 수신할 수 있습니다. 또한 Mobility Service를 사용하면 조직에서 회사번호로 전화 기능을 사용할 수 있습니다. 회사번호로 전화 기능을 사용하면 휴대폰에서 전화를 걸지만 회사 전화 번호에서 전화가 걸려 온 것처럼 보이게 할 수 있습니다. 예를 들어 발신자 번호 시스템에서 사용자의 휴대폰 번호 대신 회사 전화 번호를 표시합니다.

Mobility Service 자체는 Mobility Service 구성 설정을 사용하여 관리하며, 이러한 설정은 전역 범위, 사이트 범위 또는 서비스 범위(웹 서버 서비스만 해당)에 적용할 수 있습니다. 또한 이 설정은 Mobility Service 세션의 최대 시간 길이, 조직 방화벽 외부에서 로그온하는 사용자가 Lync Server 자동 검색 서비스(Mobility Service 사용자를 적절한 등록자 풀로 보냄)를 사용할 수 있는지 여부, 푸시 알림 서비스 공급자의 위치 등을 제어합니다.

Lync Server를 설치하면 단일 Mobility Service 구성 설정 컬렉션이 전역 범위에 만들어집니다. 하지만 관리자는 **New-CsMcxConfiguration** cmdlet을 사용하여 사이트 범위나 서비스 범위에서 사용자 지정 구성 설정을 만들 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsMcxConfiguration** cmdlet을 로컬로 실행할 수 있습니다.

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
<td><p>만들 Mobility Service 구성 설정 컬렉션의 고유 식별자입니다. 사이트 범위에서 설정을 만들려면 접두사 &quot;site:&quot; 다음에 사이트 이름이 오도록 합니다. 예를 들면 다음과 같습니다.</p>
<p>-Identity &quot;site:Redmond&quot;</p>
<p>서비스 범위에서 구성되는 설정을 만들려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity service:WebServer:atl-cs-001.litwareinc.com</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ExposedWebURL</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.McxConfiguration.ExposedWebURL</p></td>
<td><p>자동 검색 서비스에서 사용하는 URL을 조직 방화벽 내/외부의 사용자가 모두 액세스할 수 있는지(External), 아니면 방화벽 내에 있는 사용자만 액세스할 수 있는지(Internal)를 나타냅니다.</p>
<p>허용되는 값은 Internal 또는 External이며, 기본값은 External입니다.</p></td>
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
<td><p>개체를 실제로 영구 변경 내용으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 명령의 출력을 변수에 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 이러한 변경 사항을 커밋할 수 있습니다.</p></td>
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

없음. **New-CsMcxConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

Microsoft.Rtc.Management.WriteableConfig.Settings.McxConfiguration.McxConfiguration 개체의 새 인스턴스를 만듭니다.

