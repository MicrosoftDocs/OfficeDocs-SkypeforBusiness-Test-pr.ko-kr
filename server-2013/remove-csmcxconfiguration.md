---
title: Remove-CsMcxConfiguration
TOCTitle: Remove-CsMcxConfiguration
ms:assetid: 71904a62-a1f1-4466-9921-0a175909e117
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh690026(v=OCS.15)
ms:contentKeyID: 49304012
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsMcxConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 2013 Mobility Service 구성 설정의 지정된 컬렉션을 제거합니다. iPhone 및 Windows Phone 같은 휴대폰 사용자는 Mobility Service를 통해 메신저 대화 및 현재 상태 정보를 교환하고, 음성 메일을 해당 무선 공급자를 통해서가 아닌 내부에서 저장 및 검색하고, 회사번호로 전화 기능 및 외부 전화 접속 회의 같은 Lync Server 기능을 활용하는 등의 작업을 수행할 수 있습니다. 이 cmdlet은 Lync Server 2010용 2011년 11월 누적 업데이트에서 도입되었습니다.

## 구문

    Remove-CsMcxConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Redmond 사이트에 할당된 Mobility Service 구성 설정의 컬렉션을 삭제합니다.

    Remove-CsMcxConfiguration -Identity "site:Redmond"

## 예제 2

예제 2에서는 서비스 범위에 할당된 모든 Mobility Service 구성 설정이 제거됩니다. 이를 위해 **Get-CsMcxConfiguration** cmdlet과 함께 Filter 매개 변수가 사용됩니다. 필터 값 "service:\*"는 ID가 문자열 값 "service:"로 시작하는 설정만 반환되도록 합니다. 이렇게 필터링된 컬렉션은 **Remove-CsMcxConfiguration** cmdlet에 파이프되고 이 cmdlet을 통해 삭제됩니다.

    Get-CsMcxConfiguration -Filter "service:*" | Remove-CsMcxConfiguration

## 예제 3

예제 3에서는 ExposedWebURL 속성이 Internal로 설정된 모든 Mobility Service 구성 설정을 삭제합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsMcxConfiguration** cmdlet을 호출합니다. 그러면 조직에서 현재 사용 중인 모든 Mobility Service 구성 설정의 컬렉션이 반환됩니다. 그런 다음 이 컬렉션은 ExposedWebURL이 Internal과 같은(-eq) 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 또한 이렇게 필터링된 컬렉션은 필터링된 컬렉션의 각 항목을 삭제하는 **Remove-CsMcxConfiguration** cmdlet에 파이프됩니다.

    Get-CsMcxConfiguration | Where-Object {$_.ExposedWebURL -eq "Internal"} | Remove-CsMcxConfiguration

## 예제 4

예제 4에서는 할당된 푸시 알림 프록시 URI가 없는 모든 Mobility Service 구성 설정을 Lync Server에서 제거합니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsMcxConfiguration** cmdlet을 사용하여 현재 사용 중인 모든 Mobility Service 구성 설정의 컬렉션을 반환합니다. 그러면 이 컬렉션은 PushNotificationProxyUri 속성이 Null 값과 같은(-eq) 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 이러한 기준을 충족하는 모든 설정이 **Remove-CsMcxConfiguration** cmdlet에 파이프되고 이 cmdlet에 의해 삭제됩니다.

    Get-CsMcxConfiguration | Where-Object {$_.PushNotificationProxyUri -eq $Null} | Remove-CsMcxConfiguration

## 자세한 정보

Mobility Service는 Lync Server의 많은 기능을 Apple iPhone, Windows Phone, Android 전화, Nokia 전화 같은 모바일 장치로 확장합니다. 무엇보다도 사용자는 이러한 전화를 사용하여 메신저 대화 및 현재 상태 정보를 교환하고, 새 음성 메일에 대한 알림을 수신할 수 있습니다. iPhone 또는 Windows Phone 사용자는 푸시 알림 서비스(Apple 푸시 알림 서비스 및 Microsoft 푸시 알림 서비스) 덕분에 Lync가 백그라운드에서 실행 중이더라도 이러한 알림을 수신할 수 있습니다. 또한 Mobility Service를 사용하면 조직에서 회사번호로 전화 기능을 사용할 수 있습니다. 회사번호로 전화 기능을 사용하면 휴대폰에서 전화를 걸지만 회사 전화 번호에서 전화가 걸려 온 것처럼 보이게 할 수 있습니다. 예를 들어 발신자 번호 시스템에서 사용자의 휴대폰 번호 대신 회사 전화 번호를 표시합니다.

Mobility Service 자체는 Mobility Service 구성 설정을 사용하여 관리하며, 이러한 설정은 전역 범위, 사이트 범위 또는 서비스 범위(웹 서버 서비스만 해당)에 적용할 수 있습니다. 또한 이 설정은 Mobility Service 세션의 최대 시간 길이, 조직 방화벽 외부에서 로그온하는 사용자가 자동 검색 서비스(Mobility Service 사용자를 적절한 등록자 풀로 보냄)를 사용할 수 있는지 여부, 푸시 알림 서비스 공급자의 위치 등을 제어합니다.

Lync Server를 설치하면 단일 Mobility Service 구성 설정 컬렉션이 전역 범위에 만들어집니다. 하지만 관리자는 사이트 범위나 서비스 범위에서 사용자 지정 구성 설정을 만들 수 있습니다. 나중에 이러한 사용자 지정 설정은 **Remove-CsMcxConfiguration** cmdlet을 사용하여 제거할 수 있습니다. 서비스 설정을 제거하는 경우 이전에 이러한 설정을 통해 관리되던 Mobility Service 서버는 사이트 설정(있는 경우)이나 전역 설정을 통해 관리됩니다. 사이트 설정을 제거하면 전역 설정을 통해 서버가 관리됩니다.

**Remove-CsMcxConfiguration** cmdlet은 전역 설정에 대해서도 실행할 수 있습니다. 그러나 이 경우 전역 설정은 제거되지 않습니다. 대신 전역 컬렉션의 속성이 기본값으로 다시 설정되기만 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsMcxConfiguration** cmdlet을 로컬로 실행할 수 있습니다.

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
<td><p>제거할 Mobility Service 구성 설정의 고유 식별자입니다. 전역 설정을 &quot;제거&quot;하려면 다음 구문을 사용합니다.</p>
<p>-Identity global</p>
<p>전역 설정은 실제로 제거할 수 없으며, 속성을 기본값으로 다시 설정할 수만 있습니다.</p>
<p>사이트 범위에서 설정을 제거하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity site:Redmond</p>
<p>서비스 범위에서 구성된 설정을 제거하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity service:WebServer:atl-cs-001.litwareinc.com</p>
<p>ID를 지정할 때는 와일드카드를 사용할 수 없습니다.</p></td>
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
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>실제로 명령을 수행하지는 않고 명령을 실행했을 때 발생할 결과에 대해 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.WriteableConfig.Settings.McxConfiguration.McxConfiguration. **Remove-CsMcxConfiguration** cmdlet은 McxConfiguration 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

없음. 대신 이 cmdlet은 Microsoft.Rtc.Management.WriteableConfig.Settings.McxConfiguration.McxConfiguration 개체의 인스턴스를 삭제합니다.

