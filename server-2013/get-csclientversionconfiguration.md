---
title: Get-CsClientVersionConfiguration
TOCTitle: Get-CsClientVersionConfiguration
ms:assetid: ed39feda-ebcf-4ed6-a970-64543f150b16
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399072(v=OCS.15)
ms:contentKeyID: 49305436
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsClientVersionConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용 중인 클라이언트 버전 구성 설정의 지정된 컬렉션에 대한 정보를 검색합니다. 클라이언트 버전 구성 설정은 Lync Server에서 시스템에 로그온하는 각 클라이언트 응용 프로그램의 버전 번호를 확인할지 여부를 결정합니다. 클라이언트 버전 필터링을 설정한 경우에는 해당 클라이언트 버전 정책에 구성된 설정에 따라 클라이언트 응용 프로그램에서 시스템에 액세스할 수 있는지 여부가 결정됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsClientVersionConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsClientVersionConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

첫 번째 예제에서는 추가 매개 변수를 지정하지 않고 **Get-CsClientVersionConfiguration** cmdlet을 호출합니다. 그러면 **Get-CsClientVersionConfiguration** cmdlet이 조직에서 현재 사용 중인 모든 클라이언트 버전 구성 설정 컬렉션을 반환합니다.

    Get-CsClientVersionConfiguration

## 예제 2

이 예제에서 **Get-CsClientVersionConfiguration** cmdlet은 ID가 site:Redmond인 모든 클라이언트 버전 구성 설정을 반환합니다. ID는 고유해야 하므로 이 명령은 두 개 이상의 항목을 반환하지 않습니다.

    Get-CsClientVersionConfiguration -Identity site:Redmond

## 예제 3

예제 3에서는 사이트 범위에서 적용된 모든 클라이언트 버전 구성 설정을 반환합니다. 이 작업은 Filter 매개 변수와 필터 값 "site:\*"를 사용하여 수행합니다. 이 필터 값은 **Get-CsClientVersionConfiguration** cmdlet이 문자열 값 "site:"으로 시작하는 ID를 가진 설정만 반환하도록 지시합니다.

    Get-CsClientVersionConfiguration -Filter "site:*"

## 예제 4

예제 4에서는 현재 사용하지 않도록 설정된 모든 클라이언트 버전 구성 설정을 반환합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsClientVersionConfiguration** cmdlet을 사용하여 조직에서 사용하도록 구성된 모든 클라이언트 버전 설정 컬렉션을 반환합니다. 이 컬렉션은 Enabled 속성이 False와 같은 설정으로 컬렉션을 제한하는 필터를 적용하는 **Where-Object** cmdlet에 파이프됩니다.

    Get-CsClientVersionConfiguration | Where-Object {$_.Enabled -eq $False}

## 자세한 정보

Lync Server에서는 사용자가 시스템에 로그온하는 데 사용할 수 있는 클라이언트 소프트웨어 및 해당 소프트웨어의 버전 번호를 지정할 때 관리자에게 많은 선택권을 제공합니다. 예를 들어 사용자가 Lync를 사용하여 Lync Server에 로그온해야 하는 기술적인 이유는 없습니다. 기술적인 면에서는 Microsoft Office Communicator 2007 R2를 사용하여 로그온할 수도 있습니다.

그러나 사용자가 Office Communicator 2007 R2를 사용하여 로그온하지 않도록 하는 것이 좋은 몇 가지 비기술적인 이유가 있을 수 있습니다. 예를 들어 Office Communicator 2007 R2는 Lync에서 제공하는 일부 기능을 지원하지 않으므로 Office Communicator 2007 R2를 사용하여 로그온한 사용자에게는 Lync를 사용하여 로그온한 사용자와 다른 환경이 제공됩니다. 이것은 사용자에게 문제가 될 수 있으며 다양한 클라이언트 응용 프로그램을 지원해야 하는 지원 센터 직원에게도 문제가 될 수 있습니다.

이러한 점이 조직에 문제가 되는 경우 클라이언트 버전 필터링을 사용하여 Lync Server에 로그온하는 데 사용할 수 있는 클라이언트 응용 프로그램을 지정할 수 있습니다. Lync Server를 설치하면 전체 클라이언트 버전 구성 설정 집합이 설치되고 사용하도록 설정됩니다. 이러한 설정은 클라이언트 버전 필터링을 사용할지 여부를 결정하는 데 사용됩니다. 이러한 전역 설정 외에 사이트 범위에 클라이언트 버전 구성 설정을 적용할 수 있습니다. 이 경우 사이트 설정이 전역 설정보다 우선합니다.

**Get-CsClientVersionConfiguration** cmdlet을 사용하면 조직에서 현재 사용 중인 클라이언트 버전 구성 설정에 대한 정보를 검색할 수 있습니다. 이 cmdlet은 허용되거나 허용되지 않는 클라이언트 응용 프로그램에 대한 정보를 반환하지 않습니다. 이 정보를 검색하려면 **Get-CsClientVersionPolicy** cmdlet을 사용합니다.

클라이언트 버전 구성은 보안 기능이 아닙니다. 이 기술은 클라이언트 응용 프로그램의 자체 보고를 기반으로 하며, 응용 프로그램이 실제 해당 응용 프로그램인지, 이 응용 프로그램의 버전 번호가 올바른지 등을 확인하지 않습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins, RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsClientVersionConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsClientVersionConfiguration"}

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
<td><p>와일드카드 문자를 사용하여 하나 이상의 클라이언트 버전 구성 설정 컬렉션을 반환하는 데 사용됩니다. 사이트 범위에서 구성된 모든 설정 컬렉션을 반환하려면 -Filter site:* 구문을 사용하고, ID(필터링할 수 있는 유일한 속성)에 문자열 값 &quot;EMEA&quot;가 포함된 모든 설정 컬렉션을 반환하려면 -Filter *EMEA* 구문을 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환할 클라이언트 버전 구성 설정 컬렉션의 고유 식별자를 나타냅니다. 전역 설정을 참조하려면 -Identity global 구문을 사용하고, 사이트 범위에서 구성된 컬렉션을 참조하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. ID를 지정할 때는 와일드카드를 사용할 수 없습니다. 와일드카드를 사용해야 하는 경우 대신 Filter 매개 변수를 포함합니다.</p>
<p>이 매개 변수를 지정하지 않으면 <strong>Get-CsClientVersionConfiguration</strong> cmdlet이 조직에서 사용 중인 모든 클라이언트 버전 구성 설정 컬렉션을 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 클라이언트 버전 구성 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsClientVersionConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsClientVersionConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.ClientVersionConfiguration 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsClientVersionConfiguration](new-csclientversionconfiguration.md)  
[Remove-CsClientVersionConfiguration](remove-csclientversionconfiguration.md)  
[Set-CsClientVersionConfiguration](set-csclientversionconfiguration.md)

