---
title: Get-CsDialInConferencingLanguageList
TOCTitle: Get-CsDialInConferencingLanguageList
ms:assetid: 39355144-c8de-4ad3-9568-6426d3b97ccb
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425869(v=OCS.15)
ms:contentKeyID: 49303338
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsDialInConferencingLanguageList

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Server 전화 접속 회의에서 사용하도록 지원되는 지역/소수 언어를 비롯한 언어의 목록을 반환합니다. 이러한 언어는 전화를 통해 전화 회의에 참가하고 있는 사용자에게 오디오 메시지와 지침을 릴레이하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsDialInConferencingLanguageList [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsDialInConferencingLanguageList [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에서는 **Get-CsDialInConferencingLanguageList** cmdlet에 쿼리를 수행하여 지원되는 언어 목록에 특정 언어가 나오는지 확인하는 방법을 보여 줍니다. 이 예제에서는 **Get-CsDialInConferencingLanguageList** cmdlet을 호출하여 지원되는 모든 언어에 대한 정보를 반환한 다음 Windows PowerShell 연산자 -contains를 사용하여 지원되는 언어 목록에 "en-US" 언어 코드가 있는지 확인합니다. 있는 경우 **Get-CsDialInConferencingLanguageList** cmdlet은 "True" 값을 다시 보고합니다. 지원되는 언어 목록에 "en-US"가 없는 경우 cmdlet은 "False" 값을 다시 보고합니다.

    (Get-CsDialInConferencingLanguageList).Languages -contains "en-US"

## 예제 2

예제 2에 표시된 명령은 지원되는 언어의 전체 목록을 반환합니다. DialInConferencingLanguageList 개체는 Languages 속성에 이 정보를 저장합니다. 각 언어를 화면에 표시하기 위해 이 명령은 먼저 **Get-CsDialInConferencingLanguageList** cmdlet을 사용하여 모든 언어 목록의 컬렉션과 해당 속성을 반환합니다. 여기에서는 **Get-CsDialInConferencingLanguageList** cmdlet 호출을 괄호로 묶어서 Windows PowerShell이 다른 작업을 수행하기 전에 이 작업을 수행하도록 합니다. 정보가 반환된 다음에는 표준 "점 표기법"(개체 이름 다음 마침표가 오고 다음 속성 이름이 오는 방식)을 사용하여 Languages 속성에 저장된 모든 값을 표시합니다.

    (Get-CsDialInConferencingLanguageList).Languages

## 자세한 정보

Lync Server에서는 사용자가 전화로 회의에 참가할 수 있습니다. 이러한 전화 접속 사용자는 화상을 보거나 메신저 대화를 교환할 수는 없지만 모임의 오디오 부분에는 완전하게 참여할 수 있습니다. 사용자가 전화로 회의에 연결하면 환영 메시지가 재생되고 모임에 참가하는 방법에 대한 지침이 전달됩니다. 예를 들어 전화 회의가 구성된 방법에 따라 이름을 말하고 샤프(\#) 키를 누르라는 메시지가 재생될 수 있습니다. Lync Server에서 추가 메시지나 명령을 수행해야 하는 경우가 있을 수 있습니다. 예를 들어 사용자가 전화 키패드에서 1을 누르면 시스템이 사용자가 선택할 수 있는 다른 모든 키패드 옵션의 목록을 읽습니다.

관리자는 전화 접속 회의에서 메시지와 지침을 릴레이하는 데 사용되는 언어를 구성할 수 있습니다. **Get-CsDialInConferencingLanguageList** cmdlet은 지원되는 언어의 목록을 반환합니다. 목록은 5자 언어 코드를 사용하여 반환됩니다(예: 카탈로니아어의 경우 ca-ES).

지원되는 언어 목록은 읽기 전용입니다. 전화 접속 회의에 지원되는 새로운 언어를 추가할 수 없기 때문에 이 목록에 새 언어를 추가하는 것은 불가능합니다. 또한 사용 가능한 언어 목록은 전역 수준에서 구성되며, 사이트마다 다른 목록을 할당할 수 없습니다. 그러나 다른 전화 접속 회의 액세스 번호에 다른 언어를 할당하는 것은 가능합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsDialInConferencingLanguageList** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsDialInConferencingLanguageList"}

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
<td><p>전화 접속 회의 언어 목록을 지정할 때 와일드 카드 문자를 활용하는 데 사용됩니다. 이러한 개체는 한 개(global)뿐이므로 Filter 또는 Identity 매개 변수를 사용하지 않더라도 언어 목록이 반환됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>반환할 전화 접속 회의 언어 목록을 나타냅니다. 아직까지는 global이라는 한 가지 개체만 있습니다. 따라서 <strong>Get-CsDialInConferencingLanguageList</strong> cmdlet을 호출할 때 이 매개 변수를 포함할 필요가 없습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 언어 목록을 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **Get-CsDialInConferencingLanguageList** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

**Get-CsDialInConferencingLanguageList** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.DialInConferencingSettings.DialInConferencingLanguageList 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[New-CsDialInConferencingAccessNumber](new-csdialinconferencingaccessnumber.md)  
[Set-CsDialInConferencingAccessNumber](set-csdialinconferencingaccessnumber.md)

