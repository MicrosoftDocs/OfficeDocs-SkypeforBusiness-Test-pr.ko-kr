---
title: Get-CsDialInConferencingDtmfConfiguration
TOCTitle: Get-CsDialInConferencingDtmfConfiguration
ms:assetid: 764741e4-c1cb-4627-8774-95cf08f6cf98
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398578(v=OCS.15)
ms:contentKeyID: 49304073
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsDialInConferencingDtmfConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

전화 접속 회의에 사용되는 DTMF(Dual-Tone Multifrequency) 신호 설정을 반환합니다. DTMF는 전화 회의에 전화로 접속한 사용자가 전화기의 키패드를 사용하여 전화 회의 설정(예: 자신에 대한 음소거 및 음소거 해제, 전화 회의 잠금 및 잠금 해제)을 제어할 수 있도록 합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsDialInConferencingDtmfConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsDialInConferencingDtmfConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1의 명령은 Redmond 사이트에 대한 DTMF 설정을 반환합니다.

    Get-CsDialInConferencingDtmfConfiguration -Identity site:Redmond

## 예제 2

예제 2에서는 모든 DTMF 설정의 컬렉션을 반환한 다음 컬렉션의 각 항목에 대해 DTMF 명령에 대한 설명을 자신에게만 들리도록 재생하기 위해 눌러야 하는 키의 값을 표시합니다. 이 작업을 수행하기 위해 **Get-CsDialInConferencingDtmfConfiguration** cmdlet을 호출하여 현재 조직에서 사용 중인 모든 DTMF 설정에 대한 모든 속성 값의 컬렉션을 반환합니다. 이 컬렉션은 화면에 표시할 두 속성(Identity 및 HelpCommand)을 선택하는 **Select-Object** cmdlet에 파이프됩니다.

    Get-CsDialInConferencingDtmfConfiguration | Select-Object Identity, HelpCommand

## 예제 3

예제 3의 명령은 사이트 범위에 구성된 모든 DTMF 설정을 반환합니다. 이 작업은 Filter 매개 변수와 필터 값 "site:\*"를 사용하여 수행합니다. 이 필터 값은 Identity가 "site:"으로 시작하는 설정만 반환되도록 합니다. 정의상 이러한 설정은 사이트 범위에 구성된 설정입니다.

    Get-CsDialInConferencingDtmfConfiguration -Filter "site:*"

## 예제 4

예제 4에서는 AdmitAll 속성이 8(기본값)이 아닌 모든 DTMF 구성 설정을 반환합니다. 이 작업을 수행하기 위해 먼저 **Get-CsDialInConferencingDtmfConfiguration** cmdlet을 매개 변수 없이 호출하여 현재 사용 중인 모든 DTMF 설정의 컬렉션을 반환합니다. 이 컬렉션은 AdmitAll 속성이 8과 같지 않은 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsDialInConferencingDtmfConfiguration | Where-Object {$_.AdmitAll -ne 8}

## 자세한 정보

Lync Server를 사용하면 사용자가 전화를 통해 접속하여 전화 회의에 참가할 수 있습니다. 전화 접속 사용자는 비디오를 보거나 다른 전화 회의 참석자와 메신저 대화를 교환할 수 없지만 모임의 오디오 부분에는 전적으로 참여할 수 있습니다.

또한 전화 회의에 참가하는 것 외에 전화기의 키패드를 사용하여 해당 전화 회의의 선택된 부분을 관리할 수도 있습니다. 사용자가 관리할 수 있는 특정 전화 회의 설정과 관리할 수 없는 특정 전화 회의 설정은 사용자가 발표자인지 여부에 따라 다릅니다. 예를 들어 기본적으로 사용자는 키패드의 6 키를 눌러 자신에 대해 음소거 또는 음소거 해제를 수행할 수 있습니다. 참가자는 모임에 참석 중인 다른 사람들의 이름을 자신에게만 들리도록 재생할 수 있으며, 발표자는 모든 모임 참석자에 대해 음소거 및 음소거 해제를 수행하고 누군가가 전화 회의에 참가하거나 전화 회의에서 나갈 때 재생되는 알림을 설정/해제할 수 있습니다.

전화기의 키패드를 사용하여 항목을 선택하는 기능을 DTMF(Dual-Tone Multifrequency) 신호라고 합니다. 특정 전화 번호로 전화를 걸었는데 "영어로 통화하려면 1을 누르고, 스페인어로 통화하려면 2를 누르십시오."라는 안내에 따라 작업을 수행해야 하는 경우 DTMF 신호를 사용한 것입니다. **Get-CsDialInConferencingDtmfConfiguration** cmdlet을 사용하면 사용할 수 있는 모든 DTMF 명령의 목록과 이러한 명령을 수행하는 데 사용되는 키를 검색할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsDialInConferencingDtmfConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsDialInConferencingDtmfConfiguration"}

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
<td><p>한 개 또는 여러 개의 DTMF 구성 설정 컬렉션을 반환하기 위해 와일드카드 문자를 사용할 수 있습니다. 사이트 범위에 구성된 모든 설정의 컬렉션을 반환하려면 -Filter site:* 구문을 사용합니다. ID(필터링할 수 있는 유일한 속성)에 문자열 값 &quot;EMEA&quot;가 포함된 모든 설정 컬렉션을 반환하려면 -Filter *EMEA* 구문을 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환하려는 DTMF 설정 컬렉션에 대한 고유 식별자를 나타냅니다. 전역 설정을 참조하려면 -Identity global 구문을 사용합니다. 사이트 범위에 구성된 컬렉션을 참조하려면 -Identity site:Redmond 형태의 구문을 사용합니다. ID를 지정할 때는 와일드카드를 사용할 수 없습니다. 와일드카드를 사용해야 하는 경우 Filter 매개 변수를 대신 사용합니다.</p>
<p>이 매개 변수를 지정하지 않으면 <strong>Get-CsDialInConferencingDtmfConfiguration</strong> cmdlet이 조직에서 사용 중인 모든 DTMF 구성 설정 컬렉션을 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 DTMF 구성 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsDialInConferencingDtmfConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsDialInConferencingDtmfConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.DialInConferencingSettings.DialInConferencingDtmfConfiguration 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsDialInConferencingDtmfConfiguration](new-csdialinconferencingdtmfconfiguration.md)  
[Remove-CsDialInConferencingDtmfConfiguration](remove-csdialinconferencingdtmfconfiguration.md)  
[Set-CsDialInConferencingDtmfConfiguration](set-csdialinconferencingdtmfconfiguration.md)

