---
title: Remove-CsDialInConferencingAccessNumber
TOCTitle: Remove-CsDialInConferencingAccessNumber
ms:assetid: a6d5a6f4-5ad1-4253-b1c4-27f81851046f
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412782(v=OCS.15)
ms:contentKeyID: 49304642
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsDialInConferencingAccessNumber

 

_**마지막으로 수정된 항목:** 2015-03-09_

기존 전화 접속 회의 액세스 번호를 제거합니다. 전화 접속 회의는 사용자가 "일반" 전화기나 휴대폰(즉, 공중 전화망의 장치)을 사용하여 온라인 회의의 오디오 부분에 참가할 수 있는 방법을 제공합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsDialInConferencingAccessNumber -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 ID가 sip:RedmondDialIn@litwareinc.com인 전화 접속 회의 액세스 번호를 삭제합니다.

    Remove-CsDialInConferencingAccessNumber -Identity sip:RedmondDialIn@litwareinc.com

## 예제 2

예제 2에서는 모든 무료 전화 접속 회의 액세스 번호(이 예제의 경우 LineUri가 "tel:+1800"으로 시작하는 모든 번호)를 삭제합니다. 이 작업을 수행하기 위해 **Get-CsDialInConferencingAccessNumber** cmdlet 및 Filter 매개 변수를 사용하여 조직에서 사용하도록 구성된 모든 무료 액세스 번호의 컬렉션을 반환합니다. 필터 값 {LineUri -like "tel:+1800\*"}는 LineUri 속성이 "tel:+1800" 문자열 값으로 시작하는 번호에 대한 데이터만 반환하도록 제한합니다. 그런 다음 이 필터링된 컬렉션은 컬렉션의 각 번호를 삭제하는 **Remove-CsDialInConferencingAccessNumber** cmdlet에 파이프됩니다.

    Get-CsDialInConferencingAccessNumber -Filter {LineUri -like "tel:+1800*"} | Remove-CsDialInConferencingAccessNumber

## 예제 3

예제 3에서는 Redmond 지역의 모든 전화 접속 회의 액세스 번호를 삭제합니다. 이 작업을 수행하기 위해 먼저 **Get-CsDialInConferencingAccessNumber** cmdlet 및 Region 매개 변수를 호출하여 Redmond 지역의 모든 액세스 번호 컬렉션, 즉 지역 목록에 Redmond가 포함된 모든 액세스 번호 컬렉션을 반환합니다. 이 컬렉션은 컬렉션의 모든 액세스 번호를 삭제하는 **Remove-CsDialInConferencingAccessNumber** cmdlet에 파이프됩니다.

    Get-CsDialInConferencingAccessNumber -Region "Redmond" | Remove-CsDialInConferencingAccessNumber

## 예제 4

예제 4에서는 특정 지역과 연관되지 않은 모든 전화 접속 회의 액세스 번호를 삭제합니다. 이 작업을 수행하기 위해 Region 매개 변수 및 매개 변수 값 $Null과 함께 **Get-CsDialInConferencingAccessNumber** cmdlet을 호출합니다. 그러면 Regions 속성이 비어 있는 액세스 번호 컬렉션이 반환됩니다. 이 컬렉션은 컬렉션의 모든 번호를 삭제하는 **Remove-CsDialInConferencingAccessNumber** cmdlet에 파이프됩니다.

    Get-CsDialInConferencingAccessNumber -Region $Null | Remove-CsDialInConferencingAccessNumber

## 예제 5

예제 5에 표시된 명령은 기본 언어가 이탈리아어로 설정되지 않은 모든 전화 접속 회의 액세스 번호를 삭제합니다. 이 작업을 수행하기 위해 먼저 매개 변수 없이 **Get-CsDialInConferencingAccessNumber** cmdlet을 호출하여 조직에서 사용하도록 구성된 모든 전화 접속 회의 액세스 번호 컬렉션을 반환합니다. 이 컬렉션은 PrimaryLanguage 속성이 Italian("it-IT")과 같지 않은 모든 번호를 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 필터링된 컬렉션은 컬렉션의 모든 액세스 번호를 삭제하는 **Remove-CsDialInConferencingAccessNumber** cmdlet에 파이프됩니다.

    Get-CsDialInConferencingAccessNumber | Where-Object {$_.PrimaryLanguage -ne "it-IT"} | Remove-CsDialInConferencingAccessNumber

## 예제 6

예제 6에서는 표시 이름이 "Default Dial-In Access Number"인 전화 접속 회의 액세스 번호를 삭제합니다. 이 작업을 수행하기 위해 Filter 매개 변수 및 필터 값 {DisplayName -eq "Default Dial-In Access Number"}와 함께 **Get-CsDialInConferencingAccessNumber** cmdlet을 호출합니다. 이 필터 값은 DisplayName 속성이 "Default Dial-In Access Number"와 같은 액세스 번호에 대한 데이터만 반환하도록 제한합니다. 반환된 개체는 해당 액세스 번호를 삭제하는 **Remove-CsDialInConferencingAccessNumber** cmdlet에 파이프됩니다.

    Get-CsDialInConferencingAccessNumber -Filter {DisplayName -eq "Default Dial-In Access Number"} | Remove-CsDialInConferencingAccessNumber

## 자세한 정보

전화 접속 회의를 통해 사용자는 모든 종류의 전화기(예: 표준 "유선 전화", 휴대폰, VoIP(Voice over Internet Protocol) 전화 등)를 사용하여 전화 회의의 오디오 부분에 참가할 수 있습니다. 그러면 컴퓨터나 인터넷 연결이 없어도 모임에 참가할 수 있습니다. 사용자는 모든 오디오 기능을 이용할 수 있습니다. 즉, 다른 참가자에게 말하고 모든 진행 상황을 들을 수 있습니다. 하지만 공유 슬라이드, 화상 대화 또는 기타 시각적 요소는 볼 수 없습니다.

사용자에게 전화 접속 회의 기능을 제공하려면 전화 접속 회의 액세스 번호를 만들어야 합니다. 사용자가 모임에 연결하기 위해 전화를 걸어야 하는 전화 번호입니다. 전화 접속 회의 액세스 번호는 **New-CsDialInConferencingAccessNumber** cmdlet을 사용하여 만듭니다. 새 전화 접속 회의 액세스 번호를 만드는 작업은 실제로는 Active Directory 도메인 서비스에 새 대화 상대 개체를 만드는 작업입니다. 이 대화 상대 개체는 액세스 번호 및 모든 해당 특성을 나타내는 데 사용됩니다. **Remove-CsDialInConferencingAccessNumber** cmdlet을 사용하여 **New-CsDialInConferencingAccessNumber** cmdlet으로 만든 모든 전화 접속 회의 번호를 삭제할 수 있습니다. **Remove-CsDialInConferencingAccessNumber** cmdlet을 실행하면 전화 접속 회의 액세스 번호 컬렉션의 번호가 삭제될 뿐 아니라 지정된 액세스 번호를 나타내는 Active Directory 대화 상대 개체도 삭제됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsDialInConferencingAccessNumber** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsDialInConferencingAccessNumber"}

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
<td><p><em>Identity</em></p></td>
<td><p>필수</p></td>
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>제거할 전화 접속 회의 액세스 번호의 SIP 주소(즉, 번호를 나타내는 대화 상대 개체)입니다. ID를 지정할 때는 sip: 접두사를 포함할 수 있습니다(예: -Identity &quot; sip:RedmondDialIn@litwareinc.com&quot;).</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
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

Microsoft.Rtc.Management.Xds.AccessNumber 개체입니다. **Remove-CsDialInConferencingAccessNumber** cmdlet은 액세스 번호 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

**Remove-CsDialInConferencingAccessNumber** cmdlet은 Microsoft.Rtc.Management.Xds.AccessNumber 개체의 인스턴스를 삭제합니다.

## 참고 항목

#### 기타 리소스

[Get-CsDialInConferencingAccessNumber](get-csdialinconferencingaccessnumber.md)  
[New-CsDialInConferencingAccessNumber](new-csdialinconferencingaccessnumber.md)  
[Set-CsDialInConferencingAccessNumber](set-csdialinconferencingaccessnumber.md)

