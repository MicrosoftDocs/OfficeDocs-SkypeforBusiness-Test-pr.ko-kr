---
title: Set-CsVoicemailReroutingConfiguration
TOCTitle: Set-CsVoicemailReroutingConfiguration
ms:assetid: c16a0d47-318b-46e4-991c-e4842403dbe3
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412948(v=OCS.15)
ms:contentKeyID: 49304921
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsVoicemailReroutingConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

Exchange UM 구독자 액세스 및 자동 전화 교환 기능에 액세스할 PSTN(공중 전화망) 전화 번호를 제공하는 설정을 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsVoicemailReroutingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsVoicemailReroutingConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-AutoAttendantNumber <String>] [-Confirm [<SwitchParameter>]] [-Enabled <$true | $false>] [-Force <SwitchParameter>] [-SubscriberAccessNumber <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 Redmond1 사이트에 대해 음성 메일 다시 경로 지정 구성 설정을 사용하도록 설정합니다.

    Set-CsVoicemailReroutingConfiguration -Identity site:Redmond1 -Enabled $True

## 예제 2

이 예제에서는 Redmond1 사이트에 적용되는 음성 메일 다시 경로 지정 설정을 수정하여 구독자 액세스 전화 번호를 +14255551213으로 설정합니다.

    Set-CsVoicemailReroutingConfiguration -Identity site:Redmond1 -SubscriberAccessNumber "+14255551213"

## 자세한 정보

이 cmdlet을 사용하면 Exchange UM 서버에 대한 IP 연결이 끊어진 경우 자동 전화 교환 및 구독자 액세스 통화를 경로 지정할 위치를 지정하는 설정을 수정할 수 있습니다.

자동 전화 교환 및 구독자 액세스는 Exchange UM의 기능입니다. 자동 전화 교환 기능은 외부 발신자가 회사의 전화 시스템을 탐색하여 원하는 부서나 직원에 연결하거나 메시지 가져오기 모드에서 사용자의 메시지를 수락할 수 있도록 음성 인식 및 누름 단추식 제어(DTMF)를 제공합니다. 메시지 가져오기 모드에서는 음성 경로 전환을 사용하는 것이 좋습니다. 구독자 액세스를 사용하면 내부 사용자가 전화로 Microsoft Outlook 사서함에 액세스할 수 있습니다. 원격 사이트의 Lync Server 배포와 데이터 센터의 Exchange UM 간 IP 연결이 끊긴 경우에도 이러한 설정에서 제공하는 번호를 통해 발신자가 Enterprise Voice 사용자에게 음성 메일 메시지를 남기고(AutoAttendantNumber 설정) 이러한 사용자가 음성 메일을 검색할 수 있습니다(SubscriberAccessNumber 설정).

이러한 설정은 Enabled 속성이 True로 설정된 경우에만 사용할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsVoicemailReroutingConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 가져오려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsVoicemailReroutingConfiguration"}

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
<td><p><em>AutoAttendantNumber</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>음성 메일 보관 시도를 다시 경로 지정할 자동 전화 교환의 전화 번호입니다.</p>
<p>이 매개 변수에는 기존 연락처 개체의 LineUri 번호를 제공해야 합니다.</p>
<p>값은 1-9로 시작하는 숫자여야 하며, 필요에 따라 앞에 더하기(+)가 붙고 뒤에 임의 자릿수의 숫자가 올 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Enabled</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>IP 연결이 끊겼을 때 음성 메일에 대한 액세스 시도를 PSTN을 통해 다시 경로 지정할지 여부를 나타냅니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Xds ID</p></td>
<td><p>수정할 구성의 고유 식별자입니다. 이 cmdlet의 경우 Identity는 Global 또는 Site:&lt;사이트 이름&gt;입니다. 여기서 &lt;사이트 이름&gt;은 설정이 적용되는 사이트의 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>음성 메일 다시 경로 지정 구성</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p>
<p>이 개체는 <strong>Get-CsVoicemailReroutingConfiguration</strong> cmdlet을 호출하여 검색할 수 있는 Microsoft.Rtc.Management.WritableConfig.Settings.ExumRouting.VoicemailReroutingConfiguration 유형이어야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SubscriberAccessNumber</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>음성 메일 검색 시도를 다시 경로 지정할 구독자 액세스 번호입니다.</p>
<p>이 매개 변수에는 기존 연락처 개체의 LineUri 번호를 제공해야 합니다.</p>
<p>값은 1-9로 시작하는 숫자여야 하며, 필요에 따라 앞에 더하기(+)가 붙고 뒤에 임의 자릿수의 숫자가 올 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.WritableConfig.Settings.ExumRouting.VoicemailReroutingConfiguration 개체입니다. 음성 메일 경로 지정 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않습니다. Microsoft.Rtc.Management.WritableConfig.Settings.ExumRouting.VoicemailReroutingConfiguration 유형의 개체를 수정합니다.

## 참고 항목

#### 기타 리소스

[New-CsVoicemailReroutingConfiguration](new-csvoicemailreroutingconfiguration.md)  
[Remove-CsVoicemailReroutingConfiguration](remove-csvoicemailreroutingconfiguration.md)  
[Get-CsVoicemailReroutingConfiguration](get-csvoicemailreroutingconfiguration.md)

