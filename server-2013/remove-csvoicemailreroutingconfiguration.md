---
title: Remove-CsVoicemailReroutingConfiguration
TOCTitle: Remove-CsVoicemailReroutingConfiguration
ms:assetid: 758cea84-5979-417c-a0cd-c76748e0da79
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398573(v=OCS.15)
ms:contentKeyID: 49304060
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsVoicemailReroutingConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

Exchange UM 구독자 액세스 및 자동 전화 교환 기능에 액세스하기 위한 PSTN(공중 전화망) 전화 번호를 제공하는 설정을 제거합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Remove-CsVoicemailReroutingConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 Redmond1 사이트에 대한 음성 메일 다시 경로 지정 구성 설정을 제거합니다.

    Remove-CsVoicemailReroutingConfiguration -Identity site:Redmond1

## 예제 2

이 예제에서는 이 Lync Server 배포에 대한 모든 음성 메일 다시 경로 지정 설정을 제거합니다. 명령은 먼저 **Get-CsVoicemailReroutingConfiguration** cmdlet을 호출하여 모든 음성 메일 다시 경로 지정 구성 설정을 검색합니다. 이 호출로 검색된 설정은 각 설정을 제거하는 **Remove-CsVoicemailReroutingConfiguration** cmdlet에 전달됩니다.

    Get-CsVoicemailReroutingConfiguration | Remove-CsVoicemailReroutingConfiguration

## 자세한 정보

이 cmdlet을 사용하면 IP 연결이 끊어진 경우 PSTN을 통해 자동 전화 교환 및 구독자 액세스 호출이 다시 경로 지정되는 위치를 결정하는 설정을 제거할 수 있습니다.

자동 전화 교환 및 구독자 액세스는 Exchange UM의 기능입니다. 자동 전화 교환 기능은 외부 발신자가 회사의 전화 시스템을 탐색하여 원하는 부서나 직원에 연결하거나 메시지 가져오기 모드에서 사용자의 메시지를 수락할 수 있도록 음성 인식 및 누름 단추식 제어(DTMF)를 제공합니다. 메시지 가져오기 모드에서는 음성 경로 전환을 사용하는 것이 좋습니다. 구독자 액세스를 사용하면 내부 사용자가 전화로 Microsoft Outlook 사서함에 액세스할 수 있습니다. 원격 사이트의 Lync Server 배포와 데이터 센터의 Exchange UM 간 IP 연결이 끊긴 경우에도 이러한 설정에서 제공하는 번호를 통해 발신자가 Enterprise Voice 사용자에게 음성 메일 메시지를 남기고(AutoAttendantNumber 설정) 이러한 사용자가 음성 메일을 검색할 수 있습니다(SubscriberAccessNumber 설정).

이 cmdlet을 호출하여 전역 설정을 제거하는 경우 이러한 설정은 기본값으로 다시 설정됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Remove-CsVoicemailReroutingConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsVoicemailReroutingConfiguration"}

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
<td><p>제거할 구성의 고유 식별자입니다. 이 cmdlet의 경우 Identity는 Global 또는 Site:&lt;사이트 이름&gt;이어야 합니다. 여기서 &lt;사이트 이름&gt;은 설정이 적용되는 사이트의 이름입니다.</p></td>
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
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.ExumRouting.VoicemailReroutingConfiguration 개체입니다. 음성 메일 경로 지정 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.ExumRouting.VoicemailReroutingConfiguration 유형의 개체를 제거합니다.

## 참고 항목

#### 기타 리소스

[New-CsVoicemailReroutingConfiguration](new-csvoicemailreroutingconfiguration.md)  
[Set-CsVoicemailReroutingConfiguration](set-csvoicemailreroutingconfiguration.md)  
[Get-CsVoicemailReroutingConfiguration](get-csvoicemailreroutingconfiguration.md)

