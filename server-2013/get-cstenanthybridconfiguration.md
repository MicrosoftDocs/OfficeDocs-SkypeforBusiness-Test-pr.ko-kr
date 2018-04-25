---
title: Get-CsTenantHybridConfiguration
TOCTitle: Get-CsTenantHybridConfiguration
ms:assetid: 4b2e6781-8f46-4ba3-be76-3a95460e3132
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994034(v=OCS.15)
ms:contentKeyID: 52056847
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsTenantHybridConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

Microsoft Lync Online에 속한 사용자가 Enterprise Voice 기능(예: 미디어 바이패스, 고급 9-1-1, 통화 대기)에 액세스할 수 있도록 하는 하이브리드 구성 설정의 값을 반환합니다. 하이브리드 시나리오(분할 도메인 시나리오라고도 함)는 일부 사용자의 계정은 온-프레미스에 속해 있고 다른 사용자의 계정은 Lync Online에 속해 있는 Lync Server 배포입니다.

Get-CsTenantHybridConfiguration cmdlet은 비즈니스용 Skype Online에서만 사용할 수 있습니다.

## 구문

    Get-CsTenantHybridConfiguration [[-Identity] <XdsIdentity>] [-Tenant <guid>] [-LocalStore] [<CommonParameters>]Get-CsTenantHybridConfiguration [-Tenant <guid>] [-Filter <string>] [-LocalStore] [<CommonParameters>]

## 예제

## 예제 1

예제 1에 표시된 명령은 테넌트 하이브리드 구성 설정의 전역 컬렉션에 대한 속성 값을 반환합니다.

    Get-CsTenantHybridConfiguration -Identity "Global"

## 예제 2

예제 2에서는 TenantId가 "bf19b7db-6960-41e5-a139-2aa373474354"인 테넌트에 적용되는 사용자 지정 테넌트 하이브리드 구성 설정에 대한 속성 값이 반환됩니다.

    Get-CsTenantHybridConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354"

## 예제 3

예제 3에서는 모든 사용 가능한 테넌트에 대한 테넌트 하이브리드 구성 정보를 반환합니다. 이를 위해 명령은 먼저 **Get-CsTenant** cmdlet을 호출하여 이러한 모든 테넌트 컬렉션을 반환합니다. 그런 다음 이 컬렉션은 **ForEach-Object** cmdlet에 파이프됩니다. 이 cmdlet은 컬렉션에서 각 테넌트를 가져와 두 작업을 하나씩 실행합니다. 먼저 cmdlet이 테넌트의 Active Directory 표시 이름을 출력합니다. 이렇게 하면 각 설정 컬렉션을 쉽게 식별할 수 있습니다. 그런 다음 **ForEach-Object** cmdlet은 **Get-CsTenantHybridConfiguration** cmdlet을 실행하여 테넌트의 테넌트 하이브리드 구성 설정을 반환합니다.

    Get-CsTenant | ForEach-Object {$_.DisplayName; Get-CsTenantHybridConfiguration -Tenant $_.TenantId}

## 자세한 정보

하이브리드 또는 "분할 도메인" 배포에서 조직의 일부 사용자는 Lync Online에 속한 계정이 있고, 동시에 다른 사용자는 온-프레미스 버전의 Lync Server에 속한 계정이 있습니다. 기본적으로 Lync Online에 속한 사용자는 Enterprise Voice에서 제공하는 전체 기능 범위에 액세스할 수 없습니다. Lync Online 서버에서 Lync Server 배포 및 네트워크 구성 정보에 대한 직접 액세스가 허용되지 않기 때문입니다. 특히, Lync Online 사용자에게는 다음과 같은 항목에 대한 기본 액세스 권한이 없습니다.

  - Enhanced 9-1-1. 긴급 전화를 거는 데 사용되는 Lync Server 서비스입니다.

  - 통화 파킹. 사용자가 전화기 A에서 통화를 대기 상태로 설정한 다음 전화기 B에서 통화를 재개할 수 있는 Lync Server 서비스입니다.

  - 미디어 바이패스: PSTN(공중 전화망)에서 통화를 걸고 받아 중재 서버를 바이패스하여 코드 변환 및 네트워크 대기 시간을 최소화하도록 하는 서비스입니다.

  - PSTN 회의 전화 접속 및 외부 전화 접속: 사용자가 PSTN 전화 또는 모바일 장치를 사용하여 온라인 회의의 오디오 부분에 참가할 수 있도록 하는 서비스입니다.

  - 응답 그룹 응용 프로그램: 지원 센터 또는 고객 지원과 같은 엔터티로 전화 통화를 자동으로 경로 지정하는 기능을 제공합니다. 기본적으로 Lync Server 사용자는 응답 그룹 에이전트 역할을 할 수 없습니다.

Lync Online 사용자에게 이와 같은 Enterprise Voice 기능에 대한 액세스 권한을 부여하기 위해 관리자는 내부/외부 웹 서비스 URL 및 조직 액세스 에지 서버의 정규화된 도메인 이름과 같은 하이브리드 구성 설정에 적절한 값을 할당해야 합니다. 이러한 값은 **Set-CsTenantHybridConfiguration** cmdlet을 통해서만 구성할 수 있으며 Lync Online 서버에 이러한 고급 Enterprise Voice 기능을 사용하는 데 필요한 정보를 제공합니다.

**Get-CsTenantHybridConfiguration** cmdlet을 사용하여 조직에서 현재 사용 중인 테넌트 하이브리드 구성 설정에 대한 정보를 반환할 수 있습니다.

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
<td><p>테넌트 하이브리드 구성 설정 컬렉션을 반환하기 위해 와일드카드 문자를 사용할 수 있도록 합니다. 하이브리드 구성 설정의 단일 전역 컬렉션만 반환하도록 제한되므로 Filter 매개 변수를 사용할 필요가 없습니다. 하지만 <strong>Get-CsTenantHybridConfiguration</strong> cmdlet에 다음과 같은 구문을 사용할 수는 있습니다.</p>
<p>Get-CsTenantHybridConfiguration –Filter &quot;g*&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환될 테넌트 하이브리드 구성 설정의 고유 식별자입니다. 하이브리드 구성 설정의 단일 전역 컬렉션만 반환하도록 제한되므로 Identity 매개 변수를 사용하여 반환할 수 있는 컬렉션은 전역 컬렉션뿐입니다.</p>
<p>-Identity global</p>
<p>개별 테넌트에 대한 설정을 수정하려면 Identity 매개 변수 대신 Tenant 매개 변수를 사용합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 테넌트 하이브리드 구성 데이터를 검색합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>하이브리드 구성 설정이 반환되는 테넌트 계정의 GUID(Globally Unique Identifier)입니다. 예를 들면 다음과 같습니다.</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대해 테넌트 ID를 반환할 수 있습니다.</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p>
<p>Windows PowerShell 원격 세션을 사용 중이며 비즈니스용 Skype Online에만 연결되어 있는 경우에는 Tenant 매개 변수를 포함하지 않아도 됩니다. 대신, 연결 정보를 기반으로 테넌트 ID가 자동으로 채워집니다. Tenant 매개 변수는 하이브리드 배포에서 주로 사용됩니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsTenantHybridConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsTenantHybridConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.HybridConfiguration.TenantHybridConfiguration 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Set-CsTenantHybridConfiguration](set-cstenanthybridconfiguration.md)

