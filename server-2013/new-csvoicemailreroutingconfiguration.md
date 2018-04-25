---
title: New-CsVoicemailReroutingConfiguration
TOCTitle: New-CsVoicemailReroutingConfiguration
ms:assetid: 37750c6d-9b75-4dde-aa52-79210afe34c2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425849(v=OCS.15)
ms:contentKeyID: 49303305
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsVoicemailReroutingConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

지점 사이트의 Lync Server에서 데이터 센터에 위치한 Exchange UM 서버에 대한 IP 연결이 불가능할 때 Lync Server가 PSTN(공중 전화망)을 통해 경로 지정하는 전화 번호를 제공하는 설정을 만듭니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsVoicemailReroutingConfiguration -Identity <XdsIdentity> [-AutoAttendantNumber <String>] [-Confirm [<SwitchParameter>]] [-Enabled <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-SubscriberAccessNumber <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 Redmond1 사이트에 적용되는 새 음성 메일 다시 경로 지정 설정을 만듭니다. 이 구성을 설정하기 위해 Enabled 매개 변수를 True로 설정하고, 전화 번호(+14255551212)를 지정하여 호출이 다시 경로 지정될 자동 전화 교환을 지정합니다.

    New-CsVoicemailReroutingConfiguration -Identity site:Redmond1 -Enabled $True -AutoAttendantNumber "+14255551212"

## 예제 2

이 예제에서는 Redmond1 사이트에 적용되는 새 음성 메일 다시 경로 지정 설정을 만듭니다. 전화 번호(+14255551213)를 지정하여 호출이 다시 경로 지정될 구독자 액세스 번호를 지정합니다. 여기에서는 아직 Enabled 매개 변수가 설정되지 않았습니다. Enabled는 기본적으로 False로 설정되므로 Enabled 속성을 True로 설정하기 전까지는 구독자 액세스 호출이 이 번호로 다시 경로 지정되지 않습니다.

    New-CsVoicemailReroutingConfiguration -Identity site:Redmond1 -SubscriberAccessNumber "+14255551213"

## 자세한 정보

이 cmdlet을 사용하면 IP 연결이 끊어졌을 때 PSTN을 통해 자동 전화 교환 및 구독자 액세스 호출을 다시 경로 지정하는 위치를 결정하는 전역 또는 사이트 수준의 설정을 만들 수 있습니다.

자동 전화 교환 및 구독자 액세스는 Exchange UM의 기능입니다. 자동 전화 교환 기능은 외부 발신자가 회사의 전화 시스템을 탐색하여 원하는 부서나 직원에게 연결하거나 메시지 가져오기 모드에서 사용자의 메시지를 수락할 수 있도록 음성 인식 및 누름 단추식 제어(DTMF)를 제공합니다. 메시지 가져오기 모드에서는 음성 경로 전환을 사용하는 것이 좋습니다. 구독자 액세스는 내부 사용자가 전화를 통해 Microsoft Outlook 사서함에 액세스하도록 지원합니다. 원격 사이트의 Lync Server 배포와 데이터 센터의 Exchange UM 간 IP 연결이 끊긴 경우에도 이러한 설정에서 제공하는 번호를 통해 발신자가 Enterprise Voice 사용자에게 음성 메일 메시지를 남기고(AutoAttendantNumber 설정) 이러한 사용자가 음성 메일을 검색할 수 있습니다(SubscriberAccessNumber 설정).

이러한 설정은 Enabled 속성이 True로 설정된 경우에만 사용할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsVoicemailReroutingConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsVoicemailReroutingConfiguration"}

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
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>이 매개 변수는 구성을 적용할 범위를 지정하는 고유한 식별자를 포함합니다. 새 음성 메일 다시 경로 지정 구성은 사이트 수준에서만 만들 수 있으므로 ID는 Site:&lt;사이트 이름&gt; 형식이며, 여기에서 &lt;사이트 이름&gt;은 설정이 적용되는 사이트의 이름입니다. 전역 음성 메일 다시 경로 지정 구성은 기본적으로 존재하며 <strong>New-CsVoicemailReroutingConfiguration</strong> cmdlet을 호출하여 다시 만들 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AutoAttendantNumber</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>음성 메일 보관 시도를 다시 경로 지정할 자동 전화 교환의 전화 번호입니다.</p>
<p>이 매개 변수에는 기존 연락처 개체의 LineUri 값을 입력해야 합니다.</p>
<p>값은 1-9로 시작하고 필요에 따라 앞에 더하기(+)가 붙고 뒤에 임의의 자릿수가 오는 숫자여야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Enabled</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>IP 연결이 끊겼을 때 음성 메일에 대한 액세스 시도를 PSTN을 통해 다시 경로 지정할지 여부를 나타냅니다.</p>
<p>기본값: False</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경 작업을 수행하기 전에 표시되는 모든 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SubscriberAccessNumber</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>음성 메일 검색 시도를 다시 경로 지정할 구독자 액세스 번호입니다.</p>
<p>이 매개 변수에는 기존 연락처 개체의 LineUri 값을 입력해야 합니다.</p>
<p>값은 1-9로 시작하고 필요에 따라 앞에 더하기(+)가 붙고 뒤에 임의의 자릿수가 오는 숫자여야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.ExumRouting.VoicemailReroutingConfiguration 유형의 개체를 만듭니다.

## 참고 항목

#### 기타 리소스

[Remove-CsVoicemailReroutingConfiguration](remove-csvoicemailreroutingconfiguration.md)  
[Set-CsVoicemailReroutingConfiguration](set-csvoicemailreroutingconfiguration.md)  
[Get-CsVoicemailReroutingConfiguration](get-csvoicemailreroutingconfiguration.md)

