---
title: Set-CsConferenceDisclaimer
TOCTitle: Set-CsConferenceDisclaimer
ms:assetid: 97afce6d-b031-466d-a170-3ca50d6df245
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398776(v=OCS.15)
ms:contentKeyID: 49304465
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsConferenceDisclaimer

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용되는 전화 회의 고지 사항의 속성 값을 수정합니다. 전화 회의 고지 사항은 Windows Internet Explorer와 같은 브라우저에 전화 회의 링크를 붙여 넣는 방식으로 하이퍼링크를 사용하여 전화 회의에 참가한 사용자에게 표시되는 메시지입니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsConferenceDisclaimer [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsConferenceDisclaimer [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Body <String>] [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Header <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1의 명령은 조직의 전화 회의 고지 사항에 대한 Header 속성과 Body 속성을 모두 수정합니다. 이러한 고지 사항은 하나만 사용할 수 있으므로 **Set-CsConferenceDisclaimer** cmdlet을 실행할 때 Identity는 지정할 필요가 없습니다.

    Set-CsConferenceDisclaimer -Header "Litwareinc.com Online Conference" -Body "Important note: Conferencing proceedings are recorded and archived."

## 자세한 정보

관리자는 전화 회의 설정을 구성할 때 참가자가 Lync Server에서 호스트하는 전화 회의에 참가하면 표시되는 법적 고지 사항을 포함할 수 있습니다. 이 고지 사항은 일반적으로 전화 회의와 관련된 법률 및 지적 재산권 법을 설명하는 데 사용됩니다. 사용자는 고지 사항에 명시된 조항에 동의하지 않으면 전화 회의에 참가할 수 없습니다. 그러나 이 고지 사항은 하이퍼링크를 사용하여 전화 회의에 참가하는 사용자에게만 표시됩니다.

Lync Server에서는 하나의 전역 전화 회의 고지 사항 인스턴스를 사용할 수 있습니다. **Set-CsConferenceDisclaimer** cmdlet을 사용하면 조직에서 사용되는 전화 회의 고지 사항을 수정할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsConferenceDisclaimer** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsConferenceDisclaimer"}

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
<td><p><em>Body</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>전화 회의 고지 시항의 내용입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Header</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>전화 회의 고지 사항에 부여된 제목입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>전화 회의 고지 사항의 고유한 ID입니다. 하나의 전역 전화 회의 고지 사항 인스턴스만 사용할 수 있으므로 <strong>Set-CsConferenceDisclaimer</strong> cmdlet을 호출할 때 Identity는 지정할 필요가 없습니다. 그러나 -Identity global 구문을 사용하여 전역 고지 사항을 참조할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>전화 회의 고지 시항 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.WebConf.ConferenceDisclaimer 개체입니다. **Set-CsConferenceDisclaimer** cmdlet은 전화 회의 고지 사항 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

**Set-CsConferenceDisclaimer** cmdlet은 개체나 값을 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.WebConf.ConferenceDisclaimer 개체의 기존 인스턴스를 수정합니다.

## 참고 항목

#### 기타 리소스

[Get-CsConferenceDisclaimer](get-csconferencedisclaimer.md)  
[Remove-CsConferenceDisclaimer](remove-csconferencedisclaimer.md)

