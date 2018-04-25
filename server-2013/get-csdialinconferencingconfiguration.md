---
title: Get-CsDialInConferencingConfiguration
TOCTitle: Get-CsDialInConferencingConfiguration
ms:assetid: 75a959f7-5712-4dbc-b7ac-5a15b9b2f404
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398575(v=OCS.15)
ms:contentKeyID: 49304063
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsDialInConferencingConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

사용자가 전화 접속 회의에 참가하거나 회의에서 나갈 때 Lync Server에서 응답하는 방식에 대한 정보를 검색합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsDialInConferencingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsDialInConferencingConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에서는 조직에서 현재 사용되고 있는 모든 전화 접속 회의 구성 설정의 컬렉션을 반환합니다. **Get-CsDialInConferencingConfiguration** cmdlet을 추가 매개 변수 없이 호출하면 항상 전화 접속 회의 설정의 전체 컬렉션이 반환됩니다.

    Get-CsDialInConferencingConfiguration

## 예제 2

예제 2에서는 Identity가 site:Redmond인 전화 접속 회의 구성 설정을 반환합니다.

    Get-CsDialInConferencingConfiguration -Identity site:Redmond

## 예제 3

예제 3에서는 Filter 매개 변수를 사용하여 사이트 범위에서 구성된 모든 전화 접속 회의 설정을 반환합니다. 필터 값 "site:\*"는 **Get-CsDialInConferencingConfiguration** cmdlet이 ID가 문자열 값 "site:"으로 시작하는 설정만 반환하도록 지시합니다. 기본적으로 "site:"으로 시작하는 ID를 가진 전화 접속 회의 설정은 사이트 범위에서 구성된 설정을 나타냅니다.

    Get-CsDialInConferencingConfiguration -Filter "site:*"

## 예제 4

예제 4에서는 **Get-CsDialInConferencingConfiguration** cmdlet과 **Where-Object** cmdlet을 사용하여 EnableNameRecording 속성이 False로 설정된 모든 전화 접속 회의 구성 설정의 컬렉션을 반환합니다. 이 작업을 수행하기 위해 **Get-CsDialInConferencingConfiguration** cmdlet을 매개 변수 없이 호출하여 모든 전화 접속 회의 설정의 컬렉션을 반환합니다. 이 컬렉션은 EnableNameRecording 속성이 False와 같은 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsDialInConferencingConfiguration | Where-Object {$_.EnableNameRecording -eq $False}

## 자세한 정보

사용자가 전화 접속 회의에 입장(또는 퇴장)할 때 Lync Server는 다양한 방식으로 응답할 수 있습니다. 예를 들어 전화 회의에 입장하기 전에 참가자에게 자신의 이름을 기록하도록 요청할 수 있습니다. 마찬가지로 관리자는 전화 접속 참가자가 전화 회의에 퇴장 또는 입장할 때 Lync Server에서 다른 사람에게 이를 알리도록 할지 여부를 결정할 수 있습니다.

이러한 전화 회의 "참가 동작"은 전화 접속 회의 구성 설정을 사용하여 관리됩니다. 이러한 설정은 전역 범위 또는 사이트 범위에서 구성할 수 있습니다. 사이트 범위에서 구성된 설정이 전역 범위에서 구성된 설정보다 우선합니다. **Get-CsDialInConferencingConfiguration** cmdlet을 사용하면 조직에서 현재 사용되고 있는 전화 접속 회의 구성 설정에 대한 정보를 검색할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsDialInConferencingConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsDialInConferencingConfiguration"}

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
<td><p>전화 접속 회의 구성 설정을 지정할 때 와일드카드 문자를 사용하는 방법을 제공합니다. 예를 들어, 사이트 범위에서 적용된 모든 구성 설정의 컬렉션을 반환하려면 -Filter &quot;site:*&quot; 구문을 사용합니다. ID에 &quot;EMEA&quot;라는 단어가 포함된 모든 설정을 반환하려면 -Filter &quot;*EMEA*&quot; 구문을 사용합니다. Filter 매개 변수는 설정의 Identity에서만 작동합니다. 다른 전화 접속 회의 구성 속성에 대해서는 필터링할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>검색할 전화 접속 회의 구성 설정의 Identity를 나타냅니다. 전역 설정을 참조하려면 -Identity global 구문을 사용합니다. 사이트 설정을 참조하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. ID를 지정할 때는 와일드카드를 사용할 수 없습니다. 이 작업을 수행하려면 대신 Filter 매개 변수를 사용합니다.</p>
<p>매개 변수 없이 호출한 경우 <strong>Get-CsDialInConferencingConfiguration</strong> cmdlet은 조직에서 사용 중인 모든 전화 접속 회의 구성 설정에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 전화 접속 회의 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsDialInConferencingConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsDialInConferencingConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.DialInConferencingSettings.DialInConferencingConfiguration 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsDialInConferencingConfiguration](new-csdialinconferencingconfiguration.md)  
[Remove-CsDialInConferencingConfiguration](remove-csdialinconferencingconfiguration.md)  
[Set-CsDialInConferencingConfiguration](set-csdialinconferencingconfiguration.md)

