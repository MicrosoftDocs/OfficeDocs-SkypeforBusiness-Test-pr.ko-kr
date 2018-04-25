---
title: Get-CsVoicemailReroutingConfiguration
TOCTitle: Get-CsVoicemailReroutingConfiguration
ms:assetid: 25e401eb-6a84-468f-b0eb-5b794f20b5bc
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425732(v=OCS.15)
ms:contentKeyID: 49303087
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsVoicemailReroutingConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

Exchange UM 구독자 액세스 및 자동 전화 교환 기능에 액세스하기 위한 PSTN(공중 전화망) 전화 번호를 제공하는 설정을 검색합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Get-CsVoicemailReroutingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsVoicemailReroutingConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## 예제

## 예제 1

이 예제에서는 이 Lync Server 배포에 정의된 모든 음성 메일 경로 재지정 구성 설정을 검색합니다. 예를 들어 Survivable Branch Appliance가 배포된 세 개의 분기 사무실이 있는 경우 이 명령은 세 개의 음성 메일 경로 재지정 구성 집합을 반환합니다.

    Get-CsVoicemailReroutingConfiguration

## 예제 2

이 예제에서는 BranchOffice\_Portland 사이트에 대한 음성 메일 경로 재지정 구성 설정을 검색합니다.

    Get-CsVoicemailReroutingConfiguration -Identity site:BranchOffice_Portland

## 예제 3

이 예제에서는 사이트 이름이 BranchOffice 문자열로 시작하는 모든 사이트(BranchOffice\_Portland, BranchOffice\_Sacramento)에 대한 음성 메일 경로 재지정 설정을 모두 검색합니다.

    Get-CsVoicemailReroutingConfiguration -Filter *:BranchOffice*

## 예제 4

이 예제에서는 활성화되지 않은 모든 음성 메일 경로 재지정 구성을 검색합니다. 이 명령의 첫 번째 부분에서는 **Get-CsVoicemailReroutingConfiguration** cmdlet을 호출하여 모든 음성 메일 경로 재지정 구성 컬렉션을 검색합니다. 이 컬렉션은 **Where-Object** cmdlet에 파이프됩니다. **Where-Object** cmdlet은 Enabled 속성이 False와 같은(-eq) 구성만 포함되도록 컬렉션의 범위를 좁힙니다.

    Get-CsVoicemailReroutingConfiguration | Where-Object {$_.Enabled -eq $False}

## 자세한 정보

이 cmdlet은 분기 사이트의 Lync Server와 데이터 센터에 있는 Exchange UM 서버 간에 IP 연결을 사용할 수 없는 경우 자동 전화 교환 및 구독자 액세스 통화가 경로 지정되는 위치를 결정하는 설정을 검색합니다.

자동 전화 교환 및 구독자 액세스는 Exchange UM의 기능입니다. 자동 전화 교환 기능은 외부 발신자가 회사의 전화 시스템을 탐색하여 원하는 부서나 직원에게 연결하거나 메시지 가져오기 모드에서 사용자의 메시지를 수락할 수 있도록 음성 인식 및 누름 단추식 제어(DTMF)를 제공합니다. 메시지 가져오기 모드에서는 음성 경로 전환을 사용하는 것이 좋습니다. 구독자 액세스를 사용하면 내부 사용자가 전화에서 Microsoft Outlook 사서함에 액세스할 수 있습니다. 원격 사이트의 Lync Server 배포와 데이터 센터의 Exchange UM 간 IP 연결이 끊긴 경우에도 이러한 설정에서 제공하는 번호를 통해 발신자가 Enterprise Voice 사용자에게 음성 메일 메시지를 남기고(AutoAttendantNumber 설정) 이러한 사용자가 음성 메일을 검색할 수 있습니다(SubscriberAccessNumber 설정).

이 cmdlet을 매개 변수 없이 호출하면 모든 음성 메일 경로 재지정 구성이 반환됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalUserAdmins 및 RTCUniversalServerAdmins 그룹의 구성원은 **Get-CsVoicemailReroutingConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsVoicemailReroutingConfiguration"}

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
<td><p>Filter 매개 변수를 사용하면 와일드카드 일치를 기준으로 특정 사이트 집합에 대한 구성 설정을 검색할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>검색할 구성의 고유 식별자입니다. 이 cmdlet에서 Identity는 Global 또는 Site:&lt;사이트 이름&gt;이며, 여기서 &lt;사이트 이름&gt;은 설정이 적용되는 사이트의 이름입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>중앙 관리 저장소 자체가 아니라 중앙 관리 저장소의 로컬 복제본에서 음성 메일 경로 지정 구성을 검색합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.ExumRouting.VoicemailReroutingConfiguration 유형의 개체를 하나 이상 검색합니다.

## 참고 항목

#### 기타 리소스

[New-CsVoicemailReroutingConfiguration](new-csvoicemailreroutingconfiguration.md)  
[Remove-CsVoicemailReroutingConfiguration](remove-csvoicemailreroutingconfiguration.md)  
[Set-CsVoicemailReroutingConfiguration](set-csvoicemailreroutingconfiguration.md)

