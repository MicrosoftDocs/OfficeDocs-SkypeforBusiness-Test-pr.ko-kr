---
title: Get-CsUCPhoneConfiguration
TOCTitle: Get-CsUCPhoneConfiguration
ms:assetid: 014bba9e-b5c4-477d-9273-c993e7a7ee9e
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398070(v=OCS.15)
ms:contentKeyID: 49302611
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsUCPhoneConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Phone Edition 관리 옵션에 대한 정보를 반환합니다. 여기에는 필요한 보안 모드, 지정한 기간 동안 사용하지 않을 경우 전화를 자동으로 잠글지 여부 등이 포함됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsUCPhoneConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsUCPhoneConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 현재 사용 중인 모든 UC 전화 구성 설정을 반환합니다. 추가 매개 변수 없이 **Get-CsUCPhoneConfiguration** cmdlet을 호출하면 항상 전체 전화 구성 설정 컬렉션이 반환됩니다.

    Get-CsUCPhoneConfiguration

## 예제 2

예제 2에서는 ID가 site:Redmond인 UC 전화 구성 설정만 반환됩니다. ID가 고유해야 하므로 이 명령은 전화 구성 설정 컬렉션을 두 개 이상 반환하지 않습니다.

    Get-CsUCPhoneConfiguration -Identity site:Redmond

## 예제 3

예제 3에서는 사이트 범위에서 구성된 모든 UC 전화 설정이 반환됩니다. 이 작업을 수행하기 위해 Filter 매개 변수와 함께 **Get-CsUCPhoneConfiguration** cmdlet을 호출합니다. 필터 값 "site:\*"는 Identity 속성(필터링할 수 있는 유일한 속성)이 문자열 값 "site:"으로 시작하는 설정에 대한 데이터만 반환되도록 제한합니다. 정의상, ID가 문자열 값 "site:"으로 시작하는 설정은 사이트 범위에서 구성된 설정입니다.

    Get-CsUCPhoneConfiguration -Filter site:*

## 예제 4

예제 4에서는 SIP 보안 모드가 Medium으로 설정된 UC 전화 구성 설정을 반환합니다. SIP 보안은 Low, Medium 또는 High로 설정할 수 있습니다. 먼저 조직에서 사용하도록 구성된 모든 UC 전화 설정 컬렉션을 반환하기 위해 추가 매개 변수 없이 **Get-CsUCPhoneConfiguration** cmdlet을 사용합니다. 이 컬렉션은 SIPSecurityMode 속성이 Medium과 같은 설정만 선택하는 **Where-Object**에 파이프됩니다.

    Get-CsUCPhoneConfiguration | Where-Object {$_.SIPSecurityMode -eq "Medium"}

## 예제 5

예제 5에서는 1) 전화 잠금이 적용되어 있지 않음 및/또는 2) 최소 PIN 길이가 6자리 미만임 조건 중 하나 또는 둘 다를 충족하는 모든 UC 전화 설정이 반환됩니다. 이 작업을 수행하기 위해 먼저 **Get-CsUCPhoneConfiguration** cmdlet을 호출하여 조직에서 현재 사용 중인 모든 UC 전화 설정의 컬렉션을 반환합니다. 이 컬렉션은 **Where-Object** cmdlet에 파이프되며, 여기서 1) EnforcePhoneLock 속성이 False와 같거나 그리고/또는 2) MinPhoneLength 속성이 6보다 작은 항목이 선택됩니다.

\-or 연산자는 **Where-Object** cmdlet에 조건 중 하나 또는 둘 다를 충족하는 설정을 선택하도록 지정합니다. 두 조건을 모두 충족하는 설정(이 경우 전화 잠금이 적용되어 있지 않고 PIN 길이가 6보다 작음)을 선택하려면 다음과 같이 -and 연산자를 사용합니다.

Where-Object {$\_.EnforcePhoneLock -eq $False -and $\_.MinPhonePinLength -lt 6}

    Get-CsUCPhoneConfiguration | Where-Object {$_.EnforcePhoneLock -eq $False -or $_.MinPhonePinLength -lt 6}

## 자세한 정보

Lync Phone Edition은 전화와 Lync Server의 병합을 나타냅니다. Lync Phone Edition은 VoIP(Voice over Internet Protocol) 전화로 작동할 수 있는 특정 하드웨어(즉, Lync 호환 전화)를 사용합니다. 또한 이 하드웨어는 Lync와 같은 끝점 역할을 할 수도 있습니다. 현재 상태를 설정하고, Lync 대화 상대의 상태를 확인하고, 새 대화 상대를 검색하고, Lync를 사용하여 수행하던 기타 여러 작업을 수행할 수 있습니다.

CsUCPhoneConfiguration cmdlet을 사용하여 Lync Phone Edition 전화를 관리할 수 있습니다. 예를 들어 전화에 로그온하는 데 사용되는 개인식별번호(PIN)의 최소 길이 및 전화가 지정된 시간 동안 비활성 상태일 경우 자동으로 잠글지 여부 등을 제어할 수 있습니다.

전화 구성 설정은 전역 범위 또는 사이트 범위에 적용할 수 있습니다. 사이트 범위에서 적용된 설정이 전역 범위에서 적용된 설정보다 우선합니다. **Get-CsUCPhoneConfiguration** cmdlet을 사용하면 조직 전체에서 현재 사용 중인 전화 설정에 대한 정보를 검색할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsUCPhoneConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsUCPhoneConfiguration"}

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
<td><p>한 개 또는 여러 개의 UC 전화 구성 설정 컬렉션을 반환하기 위해 와일드카드 문자를 사용할 수 있습니다. 사이트 범위에서 구성된 모든 설정 컬렉션을 반환하려면 -Filter site:* 구문을 사용합니다. ID(필터링할 수 있는 유일한 속성)에 문자열 값 &quot;EMEA&quot;가 포함된 모든 설정 컬렉션을 반환하려면 -Filter *EMEA* 구문을 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환할 UC(Unified Communications) 전화 구성 설정 컬렉션의 고유 식별자를 나타냅니다. 전역 설정을 참조하려면 -Identity global 구문을 사용합니다. 사이트 범위에서 구성된 컬렉션을 참조하려면 -Identity &quot;site:Redmond&quot;와 유사한 구문을 사용합니다. ID를 지정할 때는 와일드카드를 사용할 수 없습니다. 와일드카드를 사용해야 하는 경우 대신 Filter 매개 변수를 포함합니다.</p>
<p>이 매개 변수를 지정하지 않으면 <strong>Get-CsUCPhoneConfiguration</strong> cmdlet은 조직에서 사용 중인 모든 UC 전화 구성 설정 컬렉션을 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 UC 전화 구성 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsUCPhoneConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsUCPhoneConfiguration** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Voice.UcPhoneSettings 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsUCPhoneConfiguration](new-csucphoneconfiguration.md)  
[Remove-CsUCPhoneConfiguration](remove-csucphoneconfiguration.md)  
[Set-CsUCPhoneConfiguration](set-csucphoneconfiguration.md)

