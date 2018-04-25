---
title: Set-CsCpsConfiguration
TOCTitle: Set-CsCpsConfiguration
ms:assetid: 9c2c0ad1-12f8-47b6-a7ec-60d91c9685bf
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412721(v=OCS.15)
ms:contentKeyID: 49304516
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsCpsConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

통화 대기 서비스 설정의 기존 컬렉션을 수정합니다. 통화 대기는 사용자가 수신 전화 통화를 "대기"시킬 수 있는 서비스입니다. 통화를 대기시키면 통화가 지정된 범위, 즉 파킹된 통화 번호의 번호로 전송되고 즉시 대기 상태로 전환됩니다. 원래 전화를 받았던 사람뿐만 아니라 모든 사람이 올바른 번호를 입력하여 대화를 다시 시작할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsCpsConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsCpsConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-CallPickupTimeoutThreshold <TimeSpan>] [-Confirm [<SwitchParameter>]] [-EnableMusicOnHold <$true | $false>] [-Force <SwitchParameter>] [-MaxCallPickupAttempts <Int32>] [-OnTimeoutURI <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 대기된 통화가 전화기에서 다시 울리는 최대 횟수를 2로 설정하여 ID가 site:Redmond1인 통화 구성 서비스 구성을 수정합니다. 이 작업을 수행하기 위해 MaxCallPickupAttempts 매개 변수를 포함하고 매개 변수 값을 2로 설정합니다.

    Set-CsCpsConfiguration -Identity site:Redmond1 -MaxCallPickupAttempts 2

## 예제 2

예제 2는 예제 1에 표시된 명령의 변형입니다. 그러나 이 경우에는 하나만이 아닌 모든 통화 대기 서비스 구성의 MaxCallPickupAttempts 속성 값을 2로 설정합니다. 이 작업을 수행하기 위해 **Get-CsCpsConfiguration** cmdlet을 사용하여 조직에서 사용 중인 모든 통화 대기 서비스 설정의 컬렉션을 검색합니다. 그런 다음, 컬렉션의 각 개별 항목을 가져와 MaxCallPickupAttempts 속성 값을 2로 설정하는 **Set-CsCpsConfiguration** cmdlet에 이 컬렉션이 파이프됩니다.

    Get-CsCpsConfiguration | Set-CsCpsConfiguration -MaxCallPickupAttempts 2

## 예제 3

이 예제에서는 대기된 통화가 다시 울리기 전에 경과하는 시간(CallPickupTimeoutThreshold 속성)을 45초로 설정하여 Redmond1 사이트의 통화 대기 구성을 수정합니다.

    Set-CsCpsConfiguration -Identity site:Redmond1 -CallPickupTimeoutThreshold 00:00:45

## 자세한 정보

이 cmdlet은 기존 통화 대기 서비스 구성을 수정하는 데 사용됩니다. 통화 대기 서비스 구성은 통화가 대기된 후 통화에 수행되는 작업을 지정합니다. 예를 들어, 대기된 통화를 일정 기간 동안 받지 않을 경우 관리자 또는 응답 그룹과 같은 누군가에게 자동으로 전달할 수 있습니다. 통화를 잊지 않게 하려면 일정 기간 후에 벨이 울리도록 통화를 구성할 수 있습니다. 또한 통화를 대기하는 동안 전화를 건 사람에게 음악이 들리도록 통화 대기 서비스를 구성할 수도 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsCpsConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsCpsConfiguration"}

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
<td><p><em>CallPickupTimeoutThreshold</em></p></td>
<td><p>선택</p></td>
<td><p>시간 범위</p></td>
<td><p>전화를 받았던 전화기에 벨이 다시 울리기 전까지 통화를 대기하고 있는 시간입니다.</p>
<p>hh:mm:ss 형식으로 입력해야 합니다(hh = 시간, mm = 분, ss = 초).</p>
<p>최소값: 10초(00:00:10), 최대값: 10분(00:10:00)</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableMusicOnHold</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>통화를 대기하는 동안 전화를 건 사람에게 음악이 재생되는지 여부를 결정합니다.</p>
<p>Lync Server에서는 기본 대기 중 음악 파일이 제공됩니다. 대기 중인 동안 다른 음악을 재생하려면 <strong>Set-CsCallParkServiceMusicOnHoldFile</strong> cmdlet을 사용하여 이 파일을 변경할 수 있습니다.</p></td>
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
<td><p>수정할 구성의 고유한 식별자입니다. 이 ID는 구성이 적용되는 범위로 Global 또는 특정 사이트(site:Redmond와 같은 site:&lt;sitename&gt; 형식)를 지정합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>CallParkServiceSettings</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.CallParkServiceSettings.CallParkServiceSettings 유형의 통화 대기 서비스 구성 개체에 대한 개체 참조입니다. <strong>Get-CsCpsConfiguration</strong> cmdlet을 호출하여 이 개체를 검색할 수 있습니다. 그런 다음, 개체를 변경할 수 있고 이 매개 변수에서 <strong>Set-CsCpsConfiguration</strong> cmdlet에 개체를 다시 전달하여 변경 내용을 저장할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaxCallPickupAttempts</em></p></td>
<td><p>선택</p></td>
<td><p>Int32</p></td>
<td><p>통화를 포기하고 대체 URI(Uniform Resource Identifier)에 전달하기 전에 대기된 통화가 전화기에서 다시 울리는 횟수입니다. 대체 URI는 OnTimeoutURI 매개 변수를 사용하여 설정합니다.</p>
<p>최소값: 1, 최대값: 10</p></td>
</tr>
<tr class="even">
<td><p><em>OnTimeoutURI</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>응답하지 않은 대기된 통화를 경로 지정할 사용자 또는 응답 그룹의 SIP 주소입니다. MaxCallPickupAttempts 매개 변수를 사용하여 정의한 되걸기 수가 지난 후에 대기된 통화가 경로 지정됩니다. 이 매개 변수가 Null로 설정된 경우 OnTimeoutURI가 무시되고 되걸기 시도 실패 후 대기된 통화가 끊어집니다.</p>
<p>값은 문자열 sip:으로 시작하는 SIP URI여야 합니다(예: sip:rgs1@litwareinc.com).</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.WritableConfig.Settings.CallParkServiceSettings.CallParkServiceSettings 개체입니다. 통화 대기 서비스 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.CallParkServiceSettings.CallParkServiceSettings 유형의 개체를 수정합니다.

## 참고 항목

#### 기타 리소스

[New-CsCpsConfiguration](new-cscpsconfiguration.md)  
[Remove-CsCpsConfiguration](remove-cscpsconfiguration.md)  
[Get-CsCpsConfiguration](get-cscpsconfiguration.md)  
[Set-CsCallParkServiceMusicOnHoldFile](set-cscallparkservicemusiconholdfile.md)

