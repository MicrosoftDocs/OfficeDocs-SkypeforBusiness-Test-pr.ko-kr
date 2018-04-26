---
title: Set-CsUCPhoneConfiguration
TOCTitle: Set-CsUCPhoneConfiguration
ms:assetid: f77456aa-992a-47d2-bdc7-5e3cbbfb6926
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413042(v=OCS.15)
ms:contentKeyID: 49305563
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsUCPhoneConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Phone Edition의 관리 옵션을 수정하는 데 사용됩니다. 여기에는 필요한 보안 모드 및 전화가 지정된 시간 동안 비활성 상태일 경우 자동으로 잠글지 여부 등이 포함됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsUCPhoneConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsUCPhoneConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-CalendarPollInterval <TimeSpan>] [-Confirm [<SwitchParameter>]] [-EnforcePhoneLock <$true | $false>] [-Force <SwitchParameter>] [-LoggingLevel <Off | Low | Medium | High>] [-MinPhonePinLength <Byte>] [-PhoneLockTimeout <TimeSpan>] [-SIPSecurityMode <Low | Medium | High>] [-Voice8021p <Byte>] [-VoiceDiffServTag <Byte>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 전역 UC 전화 설정의 SIP 보안 모드를 중간으로 설정합니다.

    Set-CsUCPhoneConfiguration -Identity global -SIPSecurityMode "Medium"

## 예제 2

예제 2에서는 Redmond 사이트에 대해 구성된 UC 전화 설정을 수정합니다. 이 경우에는 PhoneLockTimeout 매개 변수 및 매개 변수 값 "00:30:00"(00시간: 30분: 00초)을 포함하여 PhoneLockTimeout 속성을 30분으로 설정합니다.

    Set-CsUCPhoneConfiguration -Identity site:Redmond -PhoneLockTimeout "00:30:00"

## 예제 3

예제 3은 예제 2에 표시된 명령의 변형입니다. 이번에는 사이트 범위에 구성된 모든 UC 전화 설정에서 PhoneLockTimeout 속성을 수정합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsUCPhoneConfiguration** cmdlet을 호출합니다. Filter 매개 변수 및 필터 값 "site:\*"는 반환되는 데이터를 사이트 범위에 구성된 전화 설정으로 제한합니다. 이 필터링된 컬렉션은 PhoneLockTimeout 매개 변수 및 매개 변수 값 "00:30:00"(00시간: 30분: 00초)을 사용하여 컬렉션의 각 항목에 대해 전화 잠금 시간 제한 값을 30분으로 설정하는 **Set-CsUCPhoneConfiguration** cmdlet에 파이프됩니다.

    Get-CsUCPhoneConfiguration -Filter "site:*" | Set-CsUCPhoneConfiguration -PhoneLockTimeout "00:30:00"

## 예제 4

예제 4에서는 SIP 보안 모드가 낮음 또는 중간으로 설정된 모든 UC 전화 설정의 EnforcePhoneLock 및 PhoneLockTimeout 속성을 구성합니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsUCPhoneConfiguration** cmdlet을 사용하여 조직의 모든 UC 전화 구성 설정을 반환합니다. 이 정보는 SIPSecurityMode 속성이 High와 같지 않은 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. SIP 보안은 Low, Medium 또는 High로만 설정할 수 있으므로 이 절은 SIPSecurityMode가 Low 또는 Medium으로 설정된 모든 설정을 선택하게 됩니다. 필터링된 컬렉션은 EnforcePhoneLock 및 PhoneLockTimeout 매개 변수를 사용하여 전화 잠금 및 전화 잠금 시간 제한 속성을 수정하는 **Set-CsUCPhoneConfiguration** cmdlet에 파이프됩니다.

    Get-CsUCPhoneConfiguration | Where-Object {$_.SIPSecurityMode -ne "High"} | Set-CsUCPhoneConfiguration -EnforcePhoneLock $True -PhoneLockTimeout "00:30:00"

## 예제 5

예제 5에서는 PhoneLockTimeout 속성이 현재 10분 미만인 모든 UC 전화 설정에 대해 전화 잠금 시간 제한 값을 10분으로 설정합니다. 이렇게 설정하면 전체 조직의 최소 전화 잠금 시간 제한이 10분이 됩니다. 이 작업을 수행하기 위해 명령은 먼저 **Get-CsUCPhoneConfiguration** cmdlet을 사용하여 조직에서 현재 사용 중인 모든 UC 전화 설정의 컬렉션을 반환합니다. 이 컬렉션은 PhoneLockTimeout 속성이 10분(00시간: 10분: 00초)보다 작은 설정만 선택하는 **Where-Object** cmdlet에 파이프됩니다. 그런 다음 이 필터링된 컬렉션은 컬렉션의 각 항목에 대해 PhoneLockTimeout 값을 10분으로 설정하는 **Set-CsUCPhoneConfiguration** cmdlet에 파이프됩니다.

    Get-CsUCPhoneConfiguration | Where-Object {$_.PhoneLockTimeout -lt "00:10:00"} | Set-CsUCPhoneConfiguration -PhoneLockTimeout "00:10:00"

## 자세한 정보

Lync Phone Edition은 전화와 Lync Server의 병합을 나타냅니다. Lync Phone Edition은 VoIP(Voice over Internet Protocol) 전화로 작동할 수 있는 특정 하드웨어(즉, Lync 호환 전화)를 사용합니다. 또한 이 하드웨어는 Lync와 같은 끝점 역할을 할 수도 있습니다. 현재 상태를 설정하고, Lync 대화 상대의 상태를 확인하고, 새 대화 상대를 검색하고, Lync를 사용하여 수행하던 기타 여러 작업을 수행할 수 있습니다.

**CsUCPhoneConfiguration** cmdlet을 사용하면 구성 설정을 사용하여 Lync Server를 실행 중인 전화를 관리할 수 있습니다. 예를 들어 전화에 로그온하는 데 사용되는 개인식별번호(PIN)의 최소 길이 및 전화가 지정된 시간 동안 비활성 상태일 경우 자동으로 잠글지 여부 등을 제어할 수 있습니다.

UC(Unified Communications) 전화 구성 설정은 전역 범위 또는 사이트 범위에 적용할 수 있습니다. Lync Server를 처음 설치하면 단일 UC 전화 구성 설정 집합이 생성되어 전역 범위에 적용됩니다. 그러나 이후에 언제든지 **New-CsUCPhoneConfiguration** cmdlet을 사용하여 사이트 범위에서 적용된 설정 컬렉션을 만들 수 있습니다. 이렇게 하면 각 개별 사이트의 고유한 요구 사항에 맞게 UC 전화 관리를 조정할 수 있습니다.

UC 전화 설정의 새 컬렉션을 만드는 것 외에도 **Set-CsUCPhoneConfiguration** cmdlet을 사용하여 기존 컬렉션의 속성 값을 수정할 수도 있습니다. 예를 들어 기본적으로 UC 전화의 로깅은 사용하지 않도록 설정되어 있습니다. 전역 수준에서 로깅을 사용하도록 설정하려면 **Set-CsUCPhoneConfiguration** cmdlet을 사용하여 전역 컬렉션의 LoggingLevel 속성 값을 True로 변경하면 됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsUCPhoneConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsUCPhoneConfiguration"}

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
<td><p><em>CalendarPollInterval</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>UC 장치가 Outlook 일정에서 정보를 검색하는 빈도를 지정합니다. 값은 시간:분:초 형식을 사용하여 지정해야 합니다. 예를 들어 시간 간격을 1시간(최대 허용 간격)으로 설정하려면 -CalendarPollInterval &quot;01:00:00&quot; 구문을 사용합니다. 기본값은 3분(00:03:00)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnforcePhoneLock</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>PhoneLockTimeout에 지정된 시간(분)이 지나면 UC 전화를 자동으로 잠글지 여부를 지정합니다. 기본값은 True입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>UC 전화 구성 설정의 컬렉션에 할당할 고유 식별자를 나타냅니다. 전역 설정을 참조하려면 -Identity global 구문을 사용합니다. 사이트 범위에 구성된 컬렉션을 참조하려면 -Identity site:Redmond와 유사한 구문을 사용합니다. ID를 지정할 때는 와일드카드 문자를 사용할 수 있습니다.</p>
<p>이 매개 변수를 생략하면 <strong>Set-CsUCPhoneConfiguration</strong> cmdlet이 전역 설정을 수정합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>UC 전화 설정 개체</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LoggingLevel</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Policy.Voice.LoggingLevel</p></td>
<td><p>UC 장치에 로깅하는 데 사용됩니다. 유효한 값은 Off, Low, Medium 및 High입니다. 기본값은 Off입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MinPhonePinLength</em></p></td>
<td><p>선택</p></td>
<td><p>System.Byte</p></td>
<td><p>개인식별번호(PIN)에 필요한 최소 자릿수를 지정합니다.</p>
<p>최소값: 4</p>
<p>최대값: 15</p>
<p>기본값: 6</p></td>
</tr>
<tr class="odd">
<td><p><em>PhoneLockTimeout</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>UC 전화가 자동으로 잠기기 전에 유휴 상태로 유지되는 시간(분)을 지정합니다.</p>
<p>이 값은 01:00:00(1시간)보다 작아야 합니다. 기본값은 00:10:00(10분)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>SIPSecurityMode</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Policy.Voice.SIPSecurityMode</p></td>
<td><p>서버가 UC 전화에서 시작된 SIP 세션에 적용할 보안 수준을 지정합니다.</p>
<p>사용할 수 있는 값은 다음과 같습니다.</p>
<p>Low(모든 유형의 인증 또는 전송 허용)</p>
<p>Medium(사용자 인증에 NTLM 또는 Kerberos 필요)</p>
<p>High(사용자 인증에 NTLM 또는 Kerberos 필요, SIP 연결에 TLS 필요)</p>
<p>기본값은 High입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Voice8021p</em></p></td>
<td><p>선택</p></td>
<td><p>System.Byte</p></td>
<td><p>Lync Server 배포 내에서 음성 트래픽의 사용자 우선 순위 값(802.1p 값)을 지정합니다.</p>
<p>이 설정은 스위치와 브리지가 802.1p를 지원하는 네트워크에만 적용됩니다. 이 속성의 최소값은 0이고, 최대값은 7입니다. 기본값은 0입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>VoiceDiffServTag</em></p></td>
<td><p>선택</p></td>
<td><p>System.Byte</p></td>
<td><p>6비트 DSCP(Differentiated Services Code Point) 우선 순위 표시의 소수점 표현을 지정합니다. 이 표시는 이 서버에서 관리하는 UC 전화가 전달한 IP 패킷의 PHB(홉당 동작)를 정의합니다.</p>
<p>이 값은 0-63(포함) 사이에 있어야 합니다. 기본값은 40입니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.UcPhoneSettings 개체입니다. **Set-CsUCPhoneConfiguration** cmdlet은 UC 전화 설정 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Set-CsUCPhoneConfiguration** cmdlet은 값이나 개체를 반환하지 않습니다. 대신에 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Policy.Voice.UcPhoneSettings 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[Get-CsUCPhoneConfiguration](get-csucphoneconfiguration.md)  
[New-CsUCPhoneConfiguration](new-csucphoneconfiguration.md)  
[Remove-CsUCPhoneConfiguration](remove-csucphoneconfiguration.md)

