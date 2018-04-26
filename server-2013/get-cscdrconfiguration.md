---
title: Get-CsCdrConfiguration
TOCTitle: Get-CsCdrConfiguration
ms:assetid: 4af8ffa2-63d3-4873-8dac-5afede090d4f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398298(v=OCS.15)
ms:contentKeyID: 49303549
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsCdrConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

CDR(통화 정보 기록) 설정에 대한 정보를 반환합니다. CDR을 사용하여 피어-투-피어 메신저 대화 세션, VoIP(Voice over Internet Protocol) 전화 통화, 전화 회의 통화 등의 사용 현황을 추적할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsCdrConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsCdrConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

이 예제에서는 **Get-CsCdrConfiguration** cmdlet을 사용하여 조직에서 사용하도록 구성된 모든 CDR 설정 컬렉션을 반환합니다.

    Get-CsCdrConfiguration

## 예제 2

예제 2에서는 Identity 매개 변수를 사용하여 Identity가 site:Redmond인 CDR 설정의 단일 컬렉션을 반환합니다.

    Get-CsCdrConfiguration -Identity site:Redmond

## 예제 3

예제 3에서는 Filter 매개 변수를 사용하여 사이트 범위에서 구성된 모든 CDR 설정을 반환합니다. 필터 값 "site:\*"는 Identity가 문자열 값 "site:"으로 시작하는 모든 CDR 설정을 반환합니다. 정의상, 이러한 설정은 사이트 범위에서 구성된 설정입니다.

    Get-CsCdrConfiguration -Filter site:*

## 예제 4

예제 4에서는 KeepCallDetailForDays 속성이 30일보다 작은 모든 CDR 설정의 컬렉션을 반환합니다. 이 작업을 수행하기 위해 먼저 **Get-CsCdrConfiguration** cmdlet을 사용하여 조직에 구성된 모든 CDR 설정의 컬렉션을 반환합니다. 이 컬렉션은 KeepCallDetailForDays 값이 30일보다 작은 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsCdrConfiguration | Where-Object {$_.KeepCallDetailForDays -lt 30}

## 자세한 정보

CDR(통화 정보 기록)을 사용하면 VoIP(Voice over IP) 전화 통화, 메신저 대화, 파일 전송, A/V(오디오/비디오) 회의 및 응용 프로그램 공유 세션과 같은 Lync Server 기능의 사용 내역을 추적할 수 있습니다. CDR은 모니터링 서비스를 배포한 경우에만 사용할 수 있으며 통화에 참여한 사람, 통화 시간, 파일 전송 여부 등에 대한 정보를 기록합니다. 그러나 통화 자체를 녹음하지는 않습니다.

또한 CDR은 통화 오류 정보, 즉 피어-투-피어 세션과 전화 회의 통화에 대한 자세한 진단 데이터를 제공합니다.

관리자는 조직에서 CDR을 사용할지 여부를 결정할 수 있습니다. 모니터링 서비스가 배포된 경우 CDR을 사용하거나 사용하지 않도록 설정할 수 있습니다. 뿐만 아니라 이 결정을 전체적으로 적용하여 조직 전체에서 CDR을 활성화 또는 비활성화하거나, 사이트 단위로 적용할 수 있습니다. 예를 들어 Redmond 사이트에서는 CDR을 사용하고 Paris 사이트에서는 CDR을 사용하지 않을 수 있습니다.

**Get-CsCdrConfiguration** cmdlet을 사용하면 조직에서 CDR을 사용하는 방식에 대한 자세한 정보를 가져올 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsCdrConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsCdrConfiguration"}

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
<td><p>CDR 구성 설정 컬렉션을 반환하기 위해 와일드카드 문자를 사용할 수 있습니다. 예를 들어 사이트 범위에서 구성된 모든 설정 컬렉션을 반환하려면 -Filter site:* 구문을 사용합니다. Identity에 문자열 값 &quot;Western&quot;이 포함된 모든 설정 컬렉션을 반환하려면 -Filter *Western* 구문을 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환할 CDR 구성 설정 컬렉션의 고유 식별자를 나타냅니다. 전역 설정을 참조하려면 -Identity global 구문을 사용합니다. 사이트 범위에서 구성된 컬렉션을 참조하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. ID를 지정할 때는 와일드카드를 사용할 수 없습니다. 와일드카드를 사용해야 하는 경우 Filter 매개 변수를 대신 사용합니다.</p>
<p>이 매개 변수를 지정하지 않으면 <strong>Get-CsCdrConfiguration</strong> cmdlet은 현재 조직에서 사용 중인 모든 CDR 구성 설정의 컬렉션을 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 CDR 구성 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsCdrConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsCdrConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.CallDetailRecording.CdrSettings 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsCdrConfiguration](new-cscdrconfiguration.md)  
[Remove-CsCdrConfiguration](remove-cscdrconfiguration.md)  
[Set-CsCdrConfiguration](set-cscdrconfiguration.md)

