---
title: New-CsCpsConfiguration
TOCTitle: New-CsCpsConfiguration
ms:assetid: bc740858-0e00-48ae-883e-67b3b7a03528
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg412919(v=OCS.15)
ms:contentKeyID: 49304855
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsCpsConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

통화 대기 서비스 설정의 새 컬렉션을 만듭니다. 통화 대기는 사용자가 수신 전화 통화를 "대기"시킬 수 있는 서비스입니다. 통화를 대기시키면 통화가 지정된 범위, 즉 파킹된 통화 번호의 번호로 전송되고 즉시 대기 상태로 전환됩니다. 원래 전화를 받았던 사람뿐만 아니라 모든 사람이 올바른 번호를 입력하여 대화를 다시 시작할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsCpsConfiguration -Identity <XdsIdentity> [-CallPickupTimeoutThreshold <TimeSpan>] [-Confirm [<SwitchParameter>]] [-EnableMusicOnHold <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-MaxCallPickupAttempts <Int32>] [-OnTimeoutURI <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 **New-CsCpsConfiguration** cmdlet을 사용하여 사이트 Redmond에 대한 통화 대기 서비스 구성을 만듭니다. 이 구성은 EnableMusicOnHold를 제외하고 기본값을 사용하여 만듭니다. 여기서는 이 속성이 False로 설정되므로 통화 대기 중인 전화 건 사람에게 아무 것도 재생되지 않습니다. 통화 대기 서비스가 배포되었다고 가정하면 EnableMusicOnHold는 기본적으로 True로 설정됩니다.

    New-CsCpsConfiguration -Identity site:Redmond -EnableMusicOnHold $False

## 예제 2

예제 2에 표시된 명령은 **New-CsCpsConfiguration** cmdlet을 사용하여 사이트 Redmond1에 대한 통화 대기 서비스 구성을 만듭니다. 기본적으로 OnTimeoutURI가 제공되지 않으므로 이 예제에서는 해당 매개 변수에 대한 값을 추가합니다. 이 경우 OnTimeoutURI는 sip:kenmyer@litwareinc.com으로 설정됩니다. 이 매개 변수에 전달된 ��은 문자열 "sip:"로 시작하고 지정된 횟수의 되걸기 시도 후에 여전히 받지 않은 대기 중인 통화를 받게 될 사용자 또는 응답 그룹을 가리켜야 합니다.

    New-CsCpsConfiguration -Identity site:Redmond -OnTimeoutURI sip:kenmyer@litwareinc.com

## 예제 3

이 명령은 **New-CsCpsConfiguration** cmdlet을 사용하여 사이트 Redmond1에 대한 통화 대기 서비스 구성을 만듭니다. 이 사이트의 경우 MaxCallPickupAttempts는 2로 설정되었습니다. 이는 통화가 최대 두 번까지 다시 걸린다는 것을 의미합니다.

    New-CsCpsConfiguration -Identity site:Redmond -MaxCallPickupAttempts 2

## 자세한 정보

이 cmdlet을 사용하여 새 통화 대기 서비스 구성을 만듭니다. 통화 대기 서비스가 설치된 경우 전역 설정이 기본적으로 구성되며 업데이트할 수 있지만 제거할 수는 없습니다. (전역 설정을 "제거"하면 전역 설정이 기본값으로 다시 설정됩니다.) 따라서 이 cmdlet은 사이트별 설정만 만드는 데 사용됩니다.

통화 대기 서비스 구성은 통화가 대기된 후 통화에 수행되는 작업을 지정합니다. 예를 들어 대기된 통화를 일정 기간 동안 받지 않을 경우 관리자 또는 응답 그룹과 같은 누군가에게 자동으로 전달할 수 있습니다. 통화를 잊지 않도록 일정 기간 후에 벨이 울리도록 통화를 구성할 수 있습니다. 또한 통화를 대기하는 동안 전화를 건 사람에게 음악이 들리도록 통화 대기 서비스를 구성할 수도 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsCpsConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsCpsConfiguration"}

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
<td><p>설정을 적용할 사이트입니다. 이 사이트는 site:&lt;sitename&gt;형식으로 입력해야 합니다(예: site:Redmond). 구성은 항상 전역 범위에 존재하며 제거할 수 없으므로 이 cmdlet을 사용하여 전역 구성을 다시 만들 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>CallPickupTimeoutThreshold</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>전화를 받았던 전화기에 벨이 다시 울리기 전까지 통화를 대기하고 있는 시간입니다.</p>
<p>hh:mm:ss 형식으로 입력해야 합니다(hh = 시간, mm = 분, ss = 초).</p>
<p>기본값: 00:01:30(90초), 최소값: 10초(00:00:10), 최대값: 10분(00:10:00)</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableMusicOnHold</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>통화를 대기하는 동안 전화를 건 사람에게 음악이 재생되는지 여부를 결정합니다.</p>
<p>Lync Server에서는 기본 대기 중 음악 파일이 제공됩니다. 대기 중인 동안 다른 음악을 재생하려면 <strong>Set-CsCallParkServiceMusicOnHoldFile</strong> cmdlet을 사용하여 이 파일을 변경할 수 있습니다.</p>
<p>기본값: True</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>MaxCallPickupAttempts</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int32</p></td>
<td><p>통화를 포기하고 대체 URI(Uniform Resource Identifier)에 전달하기 전에 대기된 통화가 전화기에서 다시 울리는 횟수입니다. 대체 URI는 OnTimeoutURI 매개 변수를 사용하여 설정합니다.</p>
<p>기본값: 1, 최소값: 1, 최대값: 10</p></td>
</tr>
<tr class="even">
<td><p><em>OnTimeoutURI</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>응답하지 않은 대기된 통화를 경로 지정할 사용자 또는 응답 그룹의 SIP 주소입니다. MaxCallPickupAttempts 매개 변수를 사용하여 정의한 되걸기 수가 지난 후에 대기된 통화가 경로 지정됩니다. 이 매개 변수가 Null로 설정된 경우 OnTimeoutURI가 무시되고 되걸기 시도 실패 후 대기된 통화가 끊어집니다.</p>
<p>값은 문자열 sip:으로 시작하는 SIP URI여야 합니다(예: sip:rgs1@litwareinc.com).</p></td>
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

없음.

## 반환 형식

이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.CallParkServiceSettings.CallParkServiceSettings 유형의 개체를 만듭니다.

## 참고 항목

#### 기타 리소스

[Remove-CsCpsConfiguration](remove-cscpsconfiguration.md)  
[Set-CsCpsConfiguration](set-cscpsconfiguration.md)  
[Get-CsCpsConfiguration](get-cscpsconfiguration.md)  
[Set-CsCallParkServiceMusicOnHoldFile](set-cscallparkservicemusiconholdfile.md)

