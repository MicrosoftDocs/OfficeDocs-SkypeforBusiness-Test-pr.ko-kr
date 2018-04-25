---
title: Get-CsPinPolicy
TOCTitle: Get-CsPinPolicy
ms:assetid: 1d627ba5-6333-466c-82a1-859deaf8d690
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398262(v=OCS.15)
ms:contentKeyID: 49302994
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsPinPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용하도록 구성된 클라이언트 개인식별번호(PIN) 인증 정책에 대한 정보를 반환합니다. PIN 인증을 통해 사용자는 사용자 이름 및 암호 대신 PIN을 제공하여 Lync Server에 액세스할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsPinPolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsPinPolicy [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 사용하도록 구성된 모든 PIN 정책 컬렉션을 반환합니다. 매개 변수 없이 **Get-CsPinPolicy** cmdlet을 호출하면 항상 전체 PIN 정책 집합이 반환됩니다.

    Get-CsPinPolicy

## 예제 2

예제 2에서는 Identity가 site:Redmond인 단일 PIN 정책을 반환합니다.

    Get-CsPinPolicy -Identity "site:Redmond"

## 예제 3

예제 3에 표시된 명령은 Filter 매개 변수를 사용하여 사용자별 범위에서 구성된 모든 정책을 반환합니다. 이 작업을 수행하기 위해 필터 값 "tag:\*"를 사용합니다. 이 값은 Identity가 "tag:" 문자로 시작하는 정책만 반환하도록 **Get-CsPinPolicy** cmdlet에 지시합니다.

    Get-CsPinPolicy -Filter "tag:*"

## 예제 4

예제 4에서는 AllowCommonPatterns 속성이 True인 모든 PIN 정책을 반환합니다. 이 예제에서는 먼저 추가 매개 변수 없이 **Get-CsPinPolicy** cmdlet을 호출하여 조직에서 사용하도록 구성된 모든 PIN 정책 컬렉션을 반환합니다. 이 컬렉션은 AllowCommonPatterns 속성이 True와 같은 정책만 선택하는 **Where-Object** cmdlet에 전달됩니다.

    Get-CsPinPolicy | Where-Object {$_.AllowCommonPatterns -eq $True}

## 예제 5

예제 4와 마찬가지로, 예제 5에 표시된 명령은 **Where-Object** cmdlet을 사용하여 기존 PIN 정책의 하위 집합을 반환합니다. 이 예제의 **Where-Object** cmdlet은 PinLifetime 속성이 30보다 큰 정책만 검색합니다. 즉, PIN 만료 시간이 30일보다 큰 정책만 반환됩니다.

    Get-CsPinPolicy | Where-Object {$_.PinLifetime -gt 30}

## 자세한 정보

Lync Server를 사용하면 사용자가 전화를 통해 시스템에 연결하거나 PSTN(공중 전화망) 전화 회의에 참가할 수 있습니다. 일반적으로 사용자가 시스템에 로그온하거나 전화 회의에 참가하려면 사용자 이름 또는 암호를 입력해야 하지만 영숫자 키패드가 없는 전화기를 사용하는 경우 사용자 이름 및 암호를 입력하기 어려울 수 있습니다. 따라서 Lync Server는 사용자에게 숫자로만 구성된 PIN을 제공할 수 있도록 지원합니다. PIN을 묻는 메시지가 표시되면 사용자 이름 및 암호 대신 PIN을 입력하여 시스템에 로그온하거나 전화 회의에 참가할 수 있습니다.

Lync Server에서는 PIN 정책을 사용하여 PIN 인증 속성을 관리합니다. 예를 들어 PIN의 최소 길이를 지정하고 연속된 숫자(예: 123456과 같은 PIN) 등의 "공통 패턴"을 사용하는 PIN의 허용 여부를 결정할 수 있습니다. **Get-CsPinPolicy** cmdlet을 사용하여 조직에서 사용하도록 현재 구성된 PIN 정책에 대한 정보를 검색할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsPinPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsPinPolicy"}

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
<td><p>PIN 정책에 대해 와일드카드 검색을 수행할 수 있습니다. 예를 들어 사이트 범위에 구성된 모든 정책을 찾아보려면 site:* 필터를 사용합니다. 사이트 정책 Seattle, Seville 및 Saskatoon(모두 문자 &quot;S&quot;로 시작함)을 찾으려면 site:S* 필터를 사용합니다. 이 매개 변수는 Identity 속성에 대해서만 필터링할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>정책이 만들어질 때 정책에 할당된 고유 ID입니다. PIN 정책은 전역, 사이트 또는 사용자별 범위에서 할당할 수 있습니다. 전역 인스턴스를 참조하려면 -Identity global 구문을 사용합니다. 사이트 범위의 정책을 참조하려면 -Identity site:Redmond 구문을 사용합니다. 사용자별 범위의 정책을 참조하려면 -Identity RedmondPolicy와 유사한 구문을 사용합니다.</p>
<p>별표(*)와 같은 와일드카드 문자는 Identity 매개 변수에 사용할 수 없습니다. 정책에 대해 와일드카드 검색을 수행하려면 Filter 매개 변수를 대신 사용합니다.</p>
<p>Identity 및 Filter 매개 변수를 둘 다 지정하지 않으면 <strong>Get-CsPinPolicy</strong> cmdlet에서 조직에서 사용하도록 구성된 모든 PIN 정책에 대한 정보를 반환합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 PIN 정책 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsPinPolicy** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsPinPolicy** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.UserPin.UserPinPolicy 개체의 인스턴스를 하나 이상 반환합니다.

## 참고 항목

#### 기타 리소스

[Grant-CsPinPolicy](grant-cspinpolicy.md)  
[New-CsPinPolicy](new-cspinpolicy.md)  
[Remove-CsPinPolicy](remove-cspinpolicy.md)  
[Set-CsPinPolicy](set-cspinpolicy.md)

