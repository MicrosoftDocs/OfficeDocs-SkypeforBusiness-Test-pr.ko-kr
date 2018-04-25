---
title: Get-CsBandwidthPolicyServiceConfiguration
TOCTitle: Get-CsBandwidthPolicyServiceConfiguration
ms:assetid: 9cb9cf59-c47e-40f6-9f9e-235b83329a69
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412727(v=OCS.15)
ms:contentKeyID: 49304524
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsBandwidthPolicyServiceConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

하나 이상의 대역폭 정책 서비스 구성을 검색합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsBandwidthPolicyServiceConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsBandwidthPolicyServiceConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에서는 Lync Server 구현 내에 정의된 모든 대역폭 정책 서비스 구성을 검색합니다.

    Get-CsBandwidthPolicyServiceConfiguration

## 예제 2

이 예제에서는 Redmond 사이트에 대해 정의된 대역폭 정책 서비스 구성을 검색합니다(-Identity site:Redmond).

    Get-CsBandwidthPolicyServiceConfiguration -Identity site:Redmond

## 예제 3

이 예제에서는 Filter 매개 변수를 사용하여 사이트 수준에서 정의된 모든 대역폭 정책 서비스 구성을 검색합니다. 이 작업을 수행하기 위해 값 site:\*를 Filter 매개 변수에 전달합니다. 이는 site:으로 시작하고 그 뒤에 다른 문자가 오는 모든 대역폭 정책 서비스 구성의 Identity 속성을 검색합니다. 모든 사이트 수준 구성에는 site:으로 시작하고 그 뒤에 사이트 이름이 오는 Identity 값이 있으므로 이 필터는 모든 사이트의 모든 구성을 찾습니다.

    Get-CsBandwidthPolicyServiceConfiguration -Filter site:*

## 예제 4

예제 4에서는 로그 파일 크기가 4MB보다 커지는 것을 허용하는 모든 대역폭 정책 서비스 구성을 검색합니다. 이 예제에서는 먼저 **Get-CsBandwidthPolicyServiceConfiguration** cmdlet을 호출합니다. 예제 1과 마찬가지로 이 cmdlet은 Lync Server 배포 내에 정의된 모든 구성의 컬렉션을 검색합니다. 이 컬렉션은 **Where-Object** cmdlet에 파이프됩니다. **Where-Object** cmdlet은 한 번에 한 항목씩 컬렉션을 순환합니다. 컬렉션의 각 항목에 대해 **Where-Object** cmdlet은 MaxLogFileSizeMb 속성 값이 4보다 큰지(-gt) 확인합니다. 큰 경우 해당 항목은 컬렉션에 계속 있고 명령 출력에 포함됩니다. MaxLogFileSizeMb 값이 4보다 크지 않은 경우 해당 항목은 무시되고 반환되지 않습니다.

    Get-CsBandwidthPolicyServiceConfiguration | Where-Object {$_.MaxLogFileSizeMb -gt 4}

## 자세한 정보

CAC(통화 허용 제어)는 음성 또는 비디오 통화와 같은 실시간 통신 세션을 대역폭 제약 조건에 따라 설정하도록 허용할지 여부를 결정하는 방법입니다. Lync Server의 CAC 구현에는 지역 사이트 및 서브넷 간의 대역폭을 제한하기 위해 이러한 엔터티 간의 관계 및 링크와 함께 각 엔터티가 네트워크 내에 정의됩니다. 대역폭 정책 서비스는 Lync Server 배포 내에서 CAC 기능을 수행하여 통화를 설정하기에 대역폭이 충분한지 여부를 결정하는 구성 요소입니다. **Get-CsBandwidthPolicyServiceConfiguration** cmdlet은 하나 이상의 대역폭 정책 서비스에 대한 설정을 검색합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsBandwidthPolicyServiceConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsBandwidthPolicyServiceConfiguration"}

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
<td><p>Identity가 와일드카드 패턴과 일치하는 모든 구성을 찾기 위해 모든 대역폭 정책 서비스 구성의 Identity 속성을 검색하는 데 사용될 하나 이상의 와일드카드 문자가 포함된 문자열입니다. 예를 들어, 필터 값 site:*는 Identity 값이 문자열 site:으로 시작하고 문자 집합으로 끝나는 모든 구성을 검색합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>검색할 구성의 고유 식별자입니다. 이 식별자는 범위(전역 구성의 경우) 또는 범위와 이름(site:Redmond와 같은 사이트 수준 구성의 경우)으로 구성됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 대역폭 정책 서비스 구성을 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.BandwidthPolicyServiceConfiguration.BandwidthPolicyServiceConfiguration 유형의 개체 중 하나 이상을 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsBandwidthPolicyServiceConfiguration](new-csbandwidthpolicyserviceconfiguration.md)  
[Remove-CsBandwidthPolicyServiceConfiguration](remove-csbandwidthpolicyserviceconfiguration.md)  
[Set-CsBandwidthPolicyServiceConfiguration](set-csbandwidthpolicyserviceconfiguration.md)

