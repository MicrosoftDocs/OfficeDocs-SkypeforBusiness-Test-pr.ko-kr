---
title: Get-CsAVEdgeConfiguration
TOCTitle: Get-CsAVEdgeConfiguration
ms:assetid: f1a0db80-158c-47bd-8a8e-30e3f095fb2a
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413008(v=OCS.15)
ms:contentKeyID: 49305492
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsAVEdgeConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 A/V 에지 서비스를 실행 중인 컴퓨터의 구성 정보를 반환합니다. A/V 에지 서버라고도 하는 이러한 컴퓨터의 구성 설정을 사용하면 내부 사용자가 외부 사용자, 즉 내부 네트워크에 로그온하지 않은 사용자와 오디오 및 비디오 데이터를 공유할 수 있으며, 파일을 교환하고 데스크톱 공유 세션에 참여할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsAVEdgeConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsAVEdgeConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 현재 조직에 사용할 수 있게 구성된 모든 A/V 에지 구성 설정 컬렉션을 반환합니다. **Get-CsAVEdgeConfiguration** cmdlet을 추가 매개 변수 없이 호출하면 항상 A/V 에지 구성 설정의 전체 컬렉션이 반환됩니다.

    Get-CsAVEdgeConfiguration

## 예제 2

예제 2에서는 ID가 site:Redmond인 A/V 에지 구성 설정의 단일 컬렉션을 반환합니다.

    Get-CsAVEdgeConfiguration -Identity site:Redmond

## 예제 3

예제 3에서는 사이트 범위에 구성된 모든 A/V 에지 구성 설정의 컬렉션을 반환합니다. 이 작업을 수행하기 위해 **Get-CsAVEdgeConfiguration** cmdlet을 Filter 매개 변수와 함께 호출합니다. 필터 값 "site:\*"는 ID가 "site:" 문자로 시작하는 설정에 대한 데이터만 반환하도록 제한합니다. 정의에 따라 이는 반환되는 데이터를 사이트 범위에 구성된 설정으로 제한합니다.

    Get-CsAVEdgeConfiguration -Filter "site:*"

## 예제 4

예제 4에서 반환되는 유일한 A/V 에지 구성 설정은 MaxBandwidthPerUserKB 속성이 10,000KB/초보다 큰 설정입니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsAVEdgeConfiguration** cmdlet을 매개 변수 없이 호출합니다. 그러면 현재 사용 중인 모든 A/V 에지 구성 설정 컬렉션이 반환됩니다. 이 컬렉션은 MaxBandwidthPerUserKB가 10,000KB/초보다 큰 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsAVEdgeConfiguration | Where-Object {$_.MaxBandwidthPerUserKB -gt 10000}

## 예제 5

예제 5는 예제 4에 표시된 명령과 유사합니다. 그러나 예제 5에서는 MaxBandwidthPerUserKB 속성이 10000KB/초와 똑같은 A/V 에지 설정만 반환됩니다.

    Get-CsAVEdgeConfiguration | Where-Object {$_.MaxBandwidthPerUserKB -eq 10000}

## 예제 6

예제 6에 표시된 명령은 MaxTokenLifetime 속성이 8시간(08시간: 00분: 00초)보다 작은 A/V 에지 구성 설정만 반환합니다. 명령은 먼저 **Get-CsAVEdgeConfiguration** cmdlet을 매개 변수 없이 호출하여 조직에서 사용 중인 모든 A/V 에지 구성 설정 컬렉션을 반환합니다. 이 컬렉션은 MaxTokenLifetime이 8시간(08:00:00)보다 작은 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsAVEdgeConfiguration | Where-Object {$_.MaxTokenLifetime -lt "08:00:00"}

## 자세한 정보

A/V 에지 서버를 사용하면 회사 방화벽을 통해 오디오 및 비디오 트래픽을 교환할 수 있습니다. 특히 사용자가 인터넷을 통해 Lync Server에 액세스한 다음 방화벽 내에서 시스템에서 로그온한 사용자와 오디오 및 비디오 데이터를 교환할 수 있습니다. 에지 서버 구성 설정은 전역 범위, 사이트 범위 및 서비스 범위에서 할당될 수 있습니다. A/V 에지 구성 설정을 사용하여 관리자는 사용자 인증의 갱신 전 유효 기간을 관리하고 단일 사용자 또는 단일 포트에서 사용할 수 있는 대역폭의 크기를 제한하는 등의 작업을 수행할 수 있습니다.

**Get-CsAVEdgeConfiguration** cmdlet을 사용하면 조직에서 현재 사용 중인 A/V 에지 구성 설정에 대한 정보를 검색할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsAVEdgeConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsAVEdgeConfiguration"}

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
<td><p>반환할 A/V 에지 구성 설정을 지정할 때 와일드카드 문자를 활용하는 데 사용됩니다. 예를 들어 사이트 범위에서 구성된 모든 설정을 반환하려면 -Filter site:* 구문을 사용합니다. 서비스에서 구성된 모든 설정 컬렉션을 반환하려면 -Filter &quot;service:*&quot; 구문을 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>검색할 A/V 에지 구성 설정 컬렉션의 고유 식별자입니다. 전역 컬렉션을 검색하려면 -Identity global 구문을 사용합니다. 사이트 컬렉션을 검색하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. 서비스 범위에서 구성된 설정은 -Identity service:EdgeServer:atl-cs-001.litwareinc.com과 유사한 구문을 사용하여 참조해야 합니다. 정책 ID를 지정할 때는 와일드카드를 사용할 수 없습니다.</p>
<p>이 매개 변수가 포함되지 않은 경우 <strong>Get-CsAVEdgeConfiguration</strong> cmdlet이 조직에서 현재 사용 중인 모든 에지 구성 설정의 컬렉션을 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 A/V 에지 구성 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsAVEdgeConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsAVEdgeConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Edge.MediaRelaySettings 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsAVEdgeConfiguration](new-csavedgeconfiguration.md)  
[Remove-CsAVEdgeConfiguration](remove-csavedgeconfiguration.md)  
[Set-CsAVEdgeConfiguration](set-csavedgeconfiguration.md)

