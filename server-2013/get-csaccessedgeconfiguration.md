---
title: Get-CsAccessEdgeConfiguration
TOCTitle: Get-CsAccessEdgeConfiguration
ms:assetid: 75a8a7e9-728f-4abd-87e9-593713ae39ee
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398574(v=OCS.15)
ms:contentKeyID: 49304068
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsAccessEdgeConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 액세스 에지 서비스를 실행하는 컴퓨터(액세스 에지 서버라고도 함)의 구성 설정에 대한 정보를 반환합니다. 액세스 에지 서버는 내부 네트워크 외부의 사용자가 내부 네트워크 내부의 사용자와 통신할 수 있는 방법을 제공합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsAccessEdgeConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsAccessEdgeConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에서는 **Get-CsAccessEdgeConfiguration** cmdlet의 기본 사용을 보여 줍니다. cmdlet을 추가 매개 변수 없이 호출하면 액세스 에지 서버 구현의 모든 속성 값이 반환됩니다. 액세스 에지 서버 구성 데이터 집합이 하나만 있으므로 Identity 또는 Filter 매개 변수를 포함할 필요가 없습니다.

    Get-CsAccessEdgeConfiguration

## 예제 2

예제 2에서는 액세스 에지 서버 구성인 AllowAnonymousUsers, AllowFederatedUsers 및 AllowOutsideUsers에 대한 세 가지 속성 값만 반환합니다. 이를 위해 명령은 먼저 **Get-CsAccessEdgeConfiguration** cmdlet을 사용하여 모든 액세스 에지 서버 속성 값을 반환합니다. 이 정보는 문자열 값 "Allow"로 시작하는 속성만 선택하는 **Select-Object** cmdlet에 파이프됩니다. 그러면 해당 속성 값만 화면에 표시됩니다.

    Get-CsAccessEdgeConfiguration | Select-Object Allow*

## 예제 3

예제 3에 표시된 명령은 단일 액세스 에지 서버 구성 속성 EnablePartnerDiscovery의 값을 반환합니다. 이 작업을 수행하기 위해 먼저 **Get-CsAccessEdgeConfiguration** cmdlet을 호출하여 모든 액세스 에지 서버 구성 속성 값을 반환합니다. **Get-CsAccessEdgeConfiguration** cmdlet에 대한 이 호출은 Windows PowerShell이 다른 작업을 수행하기 전에 이 명령을 완료할 수 있도록 괄호로 묶입니다. 모든 속성 값이 반환된 후 표준 "점 표기법"(개체 이름, 마침표, 속성 이름이 차례로 표시됨)을 사용하여 단일 속성 EnablePartnerDiscovery의 값을 표시합니다.

    (Get-CsAccessEdgeConfiguration).EnablePartnerDiscovery

## 자세한 정보

액세스 에지 서버(액세스 프록시 서버라고도 함)는 Lync Server의 기능을 내부 네트워크에 로그온하지 않은 사용자에게 확장하는 방법을 제공합니다. 예를 들어 내부 네트워크를 통해서가 아니라 인터넷을 통해 Lync Server에 로그온한 인증된 원격 사용자가 있는 경우 액세스 에지 서버를 설정해야 합니다. 또한 다른 조직과 페더레이션을 설정하려는 경우나 사용자에게 Yahoo\!, AOL 또는 Windows Live와 같은 공용 메신저 서비스에 계정이 있는 사람들과 통신하는 권한을 제공하려는 경우 에지 서버가 필요합니다. 액세스 에지 서버는 경계 네트워크에 배치되며, 내부 네트워크의 내부 사용자와 외부 사용자 사이에 SIP 연결을 설정 및 검증하는 데 사용됩니다.

Lync Server에서는 구성 설정의 단일 전역 컬렉션을 사용하여 액세스 에지 서버를 관리합니다. **Get-CsAccessEdgeConfiguration** cmdlet을 사용하면 이러한 전역 설정에 대한 정보를 반환할 수 있습니다. **Get-CsAccessEdgeConfiguration** cmdlet에서 반환되는 속성 값은 에지 서버에 대해 구성한 경로 지정 유형에 따라 달라집니다. 자세한 내용은 **Set-CsAccessEdgeConfiguration** 도움말 항목을 참조하십시오.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsAccessEdgeConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsAccessEdgeConfiguration"}

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
<td><p>반환할 액세스 에지 구성 설정을 지정할 때 와일드카드를 사용할 수 있습니다. 이러한 설정의 단일 전역 인스턴스만 가질 수 있으므로 Filter 매개 변수를 사용할 필요가 없습니다. 그러나 원하는 경우 Identity &quot;g*&quot;와 유사한 같은 구문을 사용하여 전역 설정을 검색할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환할 액세스 에지 구성 설정의 고유 식별자입니다. 이러한 설정의 단일 전역 인스턴스만 가질 수 있으므로 <strong>Get-CsAccessEdgeConfiguration</strong> cmdlet을 호출할 때 ID를 포함할 필요가 없습니다. 그러나 -Identity global 구문을 사용하여 전역 설정을 검색할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 액세스 서버 구성 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsAccessEdgeConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsAccessEdgeConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayAccessEdgeSettingsDnsSrvRouting 개체 또는 Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayAccessEdgeSettingsDefaultRoute 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Set-CsAccessEdgeConfiguration](set-csaccessedgeconfiguration.md)

