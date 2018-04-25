---
title: Set-CsTenantHybridConfiguration
TOCTitle: Set-CsTenantHybridConfiguration
ms:assetid: 805ac9ee-df40-40e1-baaa-adffb6bd8cf6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994046(v=OCS.15)
ms:contentKeyID: 52056879
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsTenantHybridConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

하이브리드 시나리오에서 Microsoft Lync Online에 속한 사용자에게 미디어 바이패스, 고급 9-1-1, 통화 파킹 등의 온-프레미스 Enterprise Voice 기능에 액세스할 수 있는 권한을 부여하기 위해 사용됩니다. 하이브리드 시나리오(분할 도메인 시나리오라고도 함)는 일부 사용자는 온-프레미스에 속한 계정이 있고 다른 사용자는 Lync Online에 속한 계정이 있는 Lync Server 배포입니다.

이 cmdlet은 비즈니스용 Skype Online에서만 사용할 수 있습니다.

## 구문

    Set-CsTenantHybridConfiguration [[-Identity] <XdsIdentity>] [-Tenant <guid>] [-PeerDestination <string>] [-HybridConfigServiceInternalUrl <string>] [-HybridConfigServiceExternalUrl <string>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]Set-CsTenantHybridConfiguration [-Tenant <guid>] [-PeerDestination <string>][-HybridConfigServiceInternalUrl <string>] [-HybridConfigServiceExternalUrl <string>] [-Instance <psobject>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]

## 예제

## 예제 1

예제 1에 나와 있는 명령은 테넌트 하이브리드 구성 설정의 전역 모음에 대한 내부 서비스 URL을 설정합니다. 전역 설정을 구성하려면 "global" 매개 변수 값과 함께 Identity 매개 변수를 포함합니다.

    Set-CsTenantHybridConfiguration -Identity "global" - HybridConfigServiceInternalUrl "https://internal.litwareinc.com"

## 예제 2

예제 2에는 특정 테넌트에 대한 내부 서비스 URL이 구성되어 있습니다. 이 예제에서 테넌트에는 TenantID "bf19b7db-6960-41e5-a139-2aa373474354"가 있습니다. 개별 테넌트에 속성 값을 명시적으로 할당한 경우 테넌트가 전역 설정 대신 개별 테넌트 하이브리드 구성 설정에 의해 제어됩니다.

    Set-CsTenantHybridConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" HybridConfigServiceInternalUrl "https://internal.litwareinc.com"

## 예제 3

예제 3에 나와 있는 명령은 조직의 모든 테넌트에 대한 내부 서비스 URL을 구성합니다. 이를 위해 명령은 먼저 **Get-CsTenant** cmdlet을 사용해 사용할 수 있는 모든 테넌트 모음을 반환합니다. 그러면 해당 모음이 **ForEach-Object** cmdlet에 파이프됩니다. 그런 다음 **ForEach-Object** cmdlet이 모음의 각 테넌트에 대해 **Set-CsTenantHybridConfiguration** cmdlet을 실행해 해당 테넌트 각각에 대한 내부 서비스 URL을 "https://internal.litwareinc.com"으로 설정합니다.

    Get-CsTenant | ForEach-Object {Set-CsTenantHybridConfiguration -Tenant $_.TenantID -HybridConfigServiceInternalUrl "https://internal.litwareinc.com"}

## 자세한 정보

하이브리드 또는 "분할 도메인" 배포에서 조직의 일부 사용자는 Lync Online에 속한 계정이 있고, 동시에 다른 사용자는 Lync Server에 속한 계정이 있습니다. 기본적으로 Lync Online에 속한 사용자는 Enterprise Voice에서 제공하는 전체 기능에 액세스할 수 없습니다. Lync Online 서버에 온-프레미스 Lync Server 배포 및 네트워크 구성 정보에 직접 액세스할 수 있는 권한이 없기 때문입니다. 그 중에서 Lync Online 사용자는 다음과 같은 기능에 기본적으로 액세스할 수 없습니다.

  - 고급 9-1-1. 긴급 전화를 거는 데 사용되는 Lync Server 서비스입니다.

  - 통화 파킹. 사용자가 전화기 A에서 통화를 대기 상태로 설정한 다음 전화기 B에서 통화를 재개할 수 있는 Lync Server 서비스입니다.

  - 미디어 바이패스. 이를 통해 PSTN(공중 전화망)으로 들어오고 나가는 통화가 중재 서버를 무시할 수 있어 트랜스코딩과 네트워크 대기 시간을 최소화하는 데 도움이 됩니다.

  - PSTN 회의 전화 접속. 이를 통해 사용자가 PSTN 전화기나 모바일 장치를 사용하여 온라인 회의의 오디오 부분에 참석할 수 있습니다.

  - 응답 그룹 응용 프로그램. 지원 센터 또는 고객 지원과 같은 엔터티로 전화 통화를 자동으로 경로 지정하는 기능을 제공합니다. 기본적으로 Lync Online 사용자는 응답 그룹 에이전트 역할을 할 수 없습니다.

Lync Online 사용자에게 이와 같은 Enterprise Voice 기능에 대한 액세스 권한을 부여하려면 관리자가 하이브리드 구성 설정에 내부 및 외부 웹 서비스 URL과 조직의 액세스 에지 서버에 대한 정규화된 도메인 이름 같은 적절한 값을 할당해야 합니다. **Set-CsTenantHybridConfiguration** cmdlet을 통해서만 구성할 수 있는 이러한 값은 Lync Online 서버에 이와 같은 고급 Enterprise Voice 기능을 사용하는 데 필요한 정보를 제공합니다.

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
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p></p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>HybridConfigServiceExternalUrl</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>외부 웹 서비스 URL입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>HybridConfigServiceInternalUrl</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>내부 웹 서비스 URL입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>수정하려는 테넌트 하이브리드 구성 설정의 고유한 ID입니다. 하이브리드 구성 설정의 전역 모음은 하나로 제한되므로 Identity 매개 변수를 사용해 수정할 수 있는 유일한 모음은 전역 모음입니다.</p>
<p>-Identity global</p>
<p>개별 테넌트의 설정을 수정하려면 Identity 매개 변수가 아닌 Tenant 매개 변수를 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.PSObject</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PeerDestination</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>온-프레미스 액세스 에지 서버의 정규화된 도메인 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>선택</p></td>
<td><p>System.Guid</p></td>
<td><p>하이브리드 구성 설정을 수정 중인 테넌트 계정의 GUID(Globally Unique Identifier)입니다. 예를 들면 다음과 같습니다.</p>
<p>-Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>다음 명령을 실행하여 각 테넌트에 대한 테넌트 ID를 반환할 수 있습니다.</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p>
<p>Windows PowerShell의 원격 세션을 사용 중이며 비즈니스용 Skype Online에만 연결되어 있으면 Tenant 매개 변수를 포함하지 않아도 됩니다. 대신 연결 정보를 기반으로 테넌트 ID가 자동으로 채워집니다. Tenant 매개 변수는 기본적으로 하이브리드 배포에서 사용됩니다.</p></td>
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

없음. **Set-CsTenantHybridConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

없음. 대신 **Set-CsTenantHybridConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.HybridConfiguration.TenantHybridConfiguration 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsTenantHybridConfiguration](get-cstenanthybridconfiguration.md)

