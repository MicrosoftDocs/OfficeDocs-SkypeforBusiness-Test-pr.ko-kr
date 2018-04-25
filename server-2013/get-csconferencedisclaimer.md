---
title: Get-CsConferenceDisclaimer
TOCTitle: Get-CsConferenceDisclaimer
ms:assetid: 2382aaef-9c5e-43f8-99de-6c880134db7d
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425714(v=OCS.15)
ms:contentKeyID: 49303062
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsConferenceDisclaimer

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 사용 중인 전화 회의 고지 사항에 대한 정보를 반환합니다. 전화 회의 고지 사항은 하이퍼링크를 사용하여 전화 회의에 참가하는 사용자에게 표시되는 메시지입니다. 예를 들어 Windows Internet Explorer와 같은 브라우저에 전화 회의 링크를 붙여 넣어 전화 회의에 참가하는 사용자가 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsConferenceDisclaimer [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsConferenceDisclaimer [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

예제 1에 표시된 명령은 조직에서 사용하도록 구성된 전화 회의 고지 사항에 대한 정보를 반환합니다. 고지 사항은 전역 범위에 구성된 단일 항목으로 제한되므로 이 명령을 실행할 때는 ID를 지정할 필요가 없습니다.

    Get-CSConferenceDisclaimer

## 자세한 정보

관리자는 전화 회의 설정을 구성할 때 참가자가 Lync Server에서 호스트하는 전화 회의에 참가하면 표시되는 법적 고지 사항을 포함할 수 있습니다. 이 고지 사항은 일반적으로 전화 회의와 관련된 법률 및 지적 재산권 법을 설명하는 데 사용되며 사용자는 고지 사항에 명시된 조항에 동의해야 전화 회의에 참가할 수 있습니다. 이 고지 사항은 하이퍼링크를 사용하여 전화 회의에 참가하는 사용자에게만 표시됩니다.

**Get-CsConferenceDisclaimer** cmdlet을 사용하면 조직에서 사용 중인 고지 사항의 본문과 제목을 볼 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsConferenceDisclaimer** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsConferenceDisclaimer"}

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
<td><p>전화 회의 고지 사항을 참조할 때 와일드 카드 값을 활용하는 데 사용됩니다. 전화 회의 고지 사항은 단일, 전역 인스턴스만 가질 수 있으므로 Filter 매개 변수를 사용할 이유가 전혀 없습니다. 그러나 -Filter &quot;g*&quot; 구문을 사용하여 전역 고지 사항을 참조할 수 있습니다. 이 구문은 ID가 &quot;g&quot; 문자로 시작하는 모든 전화 회의 고지 사항을 가져옵니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>전화 회의 고지 사항의 고유한 ID입니다. 하나의 전역 전화 회의 고지 사항 인스턴스만 사용할 수 있으므로 <strong>Get-CsConferenceDisclaimer</strong> cmdlet을 호출할 때 Identity는 지정할 필요가 없습니다. 그러나 -Identity global 구문을 사용하여 전역 고지 사항을 참조할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 전화 회의 고지 사항 데이터를 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

**Get-CsConferenceDisclaimer** cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.WebConf.ConferenceDisclaimer 개체의 인스턴스를 반환합니다.

## 참고 항목

#### 기타 리소스

[Remove-CsConferenceDisclaimer](remove-csconferencedisclaimer.md)  
[Set-CsConferenceDisclaimer](set-csconferencedisclaimer.md)

