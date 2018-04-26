---
title: Get-CsQoEConfiguration
TOCTitle: Get-CsQoEConfiguration
ms:assetid: e2ed87e0-a5ae-41a2-8572-bda0070c59dc
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399004(v=OCS.15)
ms:contentKeyID: 49305318
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsQoEConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

하나 이상의 QoE(체감 품질) 설정 컬렉션을 검색합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsQoEConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsQoEConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

이 예제에서는 **Get-CsQoEConfiguration** cmdlet을 사용하여 조직에서 사용하도록 구성된 모든 QoE 설정 컬렉션을 반환합니다.

    Get-CsQoEConfiguration

## 예제 2

예제 2에서는 Identity 매개 변수를 사용하여 **Get-CsQoEConfiguration** cmdlet에서 ID가 site:Redmond인 QoE 설정만 반환하도록 합니다.

    Get-CsQoEConfiguration -Identity site:Redmond

## 예제 3

예제 3에서는 Filter 매개 변수를 사용하여 사이트 범위에서 구성된 모든 QoE 설정을 반환합니다. "site:\*" 와일드카드는 ID가 문자열 값 site:으로 시작하는 모든 QoE 설정을 반환합니다. 이 조건을 충족하는 설정은 사이트 범위에서 구성된 설정입니다.

    Get-CsQoEConfiguration -Filter site:*

## 예제 4

예제 4에서는 KeepQoEDataForDays 속성이 30일 미만인 모든 QoE 설정 컬렉션을 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsQoEConfiguration** cmdlet을 사용하여 조직에 구성된 모든 QoE 설정 컬렉션을 반환합니다. 이 컬렉션은 반환되는 데이터를 KeepQoEDataForDays 값이 30일 미만인 설정으로 제한하는 필터를 적용하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsQoEConfiguration | Where-Object {$_.KeepQoEDataForDays -lt 30}

## 자세한 정보

QoE 품질 기준은 손실된 네트워크 패킷 수, 백그라운드 노이즈, "지터"(패킷 지연의 차이) 크기 등 조직의 오디오 및 비디오 통화 품질을 추적합니다. 이러한 품질 기준은 통화 정보 기록과 같은 다른 데이터와 별도로 데이터베이스에 저장되므로 다른 데이터 기록에 관계없이 QoE를 설정 및 해제할 수 있습니다. 이 cmdlet을 사용하여 전역 또는 사이트 수준에서 QoE를 구성하는 설정을 검색할 수 있습니다.

QoE는 모니터링 서버 역할의 일부입니다. 따라서 QoE 기록을 적용하거나 QoE 데이터를 수집하려면 먼저 Lync Server 설치에 모니터링 서버를 배포해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins, RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsQoEConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsQoEConfiguration"}

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
<td><p>와일드카드 문자를 사용하여 하나 이상의 QoE 구성 설정 컬렉션을 반환하는 데 사용됩니다. 사이트 범위에서 구성된 모든 설정 컬렉션을 반환하려면 -Filter site:* 구문을 사용하고, ID(필터링할 수 있는 유일한 속성)에 문자열 값 &quot;Western&quot;이 포함된 모든 설정 컬렉션을 반환하려면 -Filter *Western* 구문을 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>검색할 설정의 고유 식별자입니다. 가능한 값은 global 및 site:&lt;사이트 이름&gt;입니다. 여기서 &lt;사이트 이름&gt;은 변경 내용을 적용할 Lync Server 배포의 사이트 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소의 로컬 복제본에서 설정을 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

**Get-CsQoEConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.QoE.QoESettings 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsQoEConfiguration](new-csqoeconfiguration.md)  
[Remove-CsQoEConfiguration](remove-csqoeconfiguration.md)  
[Set-CsQoEConfiguration](set-csqoeconfiguration.md)

