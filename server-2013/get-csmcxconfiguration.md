---
title: Get-CsMcxConfiguration
TOCTitle: Get-CsMcxConfiguration
ms:assetid: a09c0d49-5377-4a22-89e6-2751030ccf20
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh690031(v=OCS.15)
ms:contentKeyID: 49304563
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsMcxConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 현재 사용 중인 Lync Server Mobility Service 구성 설정에 대한 정보를 검색할 수 있습니다. iPhone 및 Windows Phone 같은 휴대폰 사용자는 Mobility Service를 통해 메신저 대화 및 현재 상태 정보를 교환하고, 음성 메일을 해당 무선 공급자를 통해서가 아닌 내부에서 저장 및 검색하고, 회사번호로 전화 기능 및 외부 전화 접속 회의 같은 Lync Server 기능을 활용하는 등의 작업을 수행할 수 있습니다. 이 cmdlet은 Lync Server 2010용 2011년 11월 누적 업데이트에서 도입되었습니다.

## 구문

    Get-CsMcxConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsMcxConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1의 명령은 조직에서 현재 사용 중인 모든 Mobility Service 구성 설정에 대한 정보를 반환합니다.

    Get-CsMcxConfiguration

## 예제 2

예제 2에서는 Mobility Service 구성 설정의 전역 컬렉션에 대한 정보만 반환됩니다.

    Get-CsMcxConfiguration -Identity "global"

## 예제 3

예제 3에서는 서비스 범위에 할당된 모든 Mobility Service 구성 설정에 대한 정보를 반환합니다. 이를 위해 문자열 값 "service:\*"와 함께 Filter 매개 변수를 포함합니다. 이 필터 값은 ID가 문자열 값 "service:"로 시작하는 모든 Mobility Service 구성 설정을 반환합니다.

    Get-CsMcxConfiguration -Filter "service:*"

## 예제 4

예제 4에서는 ExposedWebURL 속성이 External인 Mobility Service 구성 설정만 반환됩니다. 이 작업을 수행하기 위해 명령은 먼저 매개 변수 없이 **Get-CsMcxConfiguration** cmdlet을 호출하여 조직에서 현재 사용 중인 모든 Mobility Service 구성 설정 컬렉션을 반환합니다. 그런 다음 이 컬렉션은 ExposedWebURL 속성이 External과 같은(-eq) 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsMcxConfiguration | Where-Object {$_.ExposedWebURL -eq "External"}

## 예제 5

예제 5에서는 SessionExpirationInterval 속성이 기본값인 259200초(72시간)보다 작은 값으로 설정된 모든 Mobility Service 구성 설정을 반환합니다. 이 작업을 수행하기 위해 먼저 **Get-CsMcxConfiguration** cmdlet을 사용하여 모든 기존 Mobility Service 구성 설정 컬렉션을 반환합니다. 그런 다음 이 컬렉션은 SessionExpirationInterval 속성이 259200 미만인 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsMcxConfiguration | Where-Object {$_.SessionExpirationInterval -lt 259200}

## 자세한 정보

Lync Server Mobility Service는 Lync Server의 많은 기능을 Apple iPhone, Windows Phone, Android 전화, Nokia 전화 같은 모바일 장치로 확장합니다. 무엇보다도 사용자는 이러한 전화를 사용하여 메신저 대화 및 현재 상태 정보를 교환하고, 새 음성 메일에 대한 알림을 수신할 수 있습니다. iPhone 또는 Windows Phone 사용자는 푸시 알림 서비스(Apple 푸시 알림 서비스 및 Microsoft 푸시 알림 서비스) 덕분에 Lync가 백그라운드에서 실행 중이더라도 이러한 알림을 수신할 수 있습니다. 또한 Mobility Service를 사용하면 조직에서 회사번호로 전화 기능을 사용할 수 있습니다. 회사번호로 전화 기능을 사용하면 휴대폰에서 전화를 걸지만 회사 전화 번호에서 전화가 걸려 온 것처럼 보이게 할 수 있습니다. 예를 들어 발신자 번호 시스템에서 사용자의 휴대폰 번호 대신 회사 전화 번호를 표시합니다.

Mobility Service 자체는 Mobility Service 구성 설정을 사용하여 관리하며, 이러한 설정은 전역 범위, 사이트 범위 또는 서비스 범위(웹 서버 서비스만 해당)에 적용할 수 있습니다. 또한 이 설정은 Mobility Service 세션의 최대 시간 길이, 조직 방화벽 외부에서 로그온하는 사용자가 Lync Server 자동 검색 서비스(Mobility Service 사용자를 적절한 등록자 풀로 보냄)를 사용할 수 있는지 여부, 푸시 알림 서비스 공급자의 위치 등을 제어합니다. **Get-CsMcxConfiguration** cmdlet을 사용하면 관리자가 조직에서 현재 사용 중인 모든 Mobility Service 구성 설정에 대한 정보를 검색할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsMcxConfiguration** cmdlet을 로컬로 실행할 수 있습니다.

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
<td><p><em>Filter</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>Mobility Service 구성 설정 컬렉션을 반환하기 위해 와일드카드 문자를 사용할 수 있습니다. 예를 들어 사이트 범위에서 구성된 모든 설정 컬렉션을 반환하려면 다음 구문을 사용합니다.</p>
<p>-Filter site:*</p>
<p>서비스 범위에서 구성된 모든 설정 컬렉션을 반환하려면 다음 구문을 사용합니다.</p>
<p>-Filter service:*</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환할 Mobility Service 구성 설정 컬렉션의 고유 식별자를 나타냅니다. 전역 설정을 참조하려면 다음 구문을 사용합니다.</p>
<p>-Identity global</p>
<p>사이트 범위에서 구성된 컬렉션을 참조하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity site:Redmond</p>
<p>서비스 범위에서 구성된 컬렉션을 참조하려면 다음과 같은 구문을 사용합니다.</p>
<p>-Identity service:WebServer:atl-cs-001.litwareinc.com</p>
<p>ID를 지정할 때는 와일드카드를 사용할 수 없습니다. 와일드카드를 사용해야 하는 경우 대신 Filter 매개 변수를 사용합니다.</p>
<p>이 매개 변수를 지정하지 않으면 <strong>Get-CsMcxConfiguration</strong> cmdlet이 조직에서 사용 중인 모든 Mobility Service 구성 설정 컬렉션을 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 Mobility Service 구성 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

**Get-CsMcxConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsMcxConfiguration** cmdlet은 Microsoft.Rtc.Management.WriteableConfig.Settings.McxConfiguration.McxConfiguration 개체의 인스턴스를 반환합니다.

