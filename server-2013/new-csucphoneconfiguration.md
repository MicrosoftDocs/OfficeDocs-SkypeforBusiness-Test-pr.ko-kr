---
title: New-CsUCPhoneConfiguration
TOCTitle: New-CsUCPhoneConfiguration
ms:assetid: 633a593e-565d-4c04-affb-589502050212
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398445(v=OCS.15)
ms:contentKeyID: 49303838
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsUCPhoneConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

Lync Phone Edition을 관리하는 데 사용되는 새 설정 컬렉션을 만듭니다. 이러한 설정을 사용하여 필요한 보안 모드 등을 구성하고 전화가 지정된 시간 동안 비활성 상태일 경우 자동으로 잠글지 여부를 지정할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsUCPhoneConfiguration -Identity <XdsIdentity> [-CalendarPollInterval <TimeSpan>] [-Confirm [<SwitchParameter>]] [-EnforcePhoneLock <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-LoggingLevel <Off | Low | Medium | High>] [-MinPhonePinLength <Byte>] [-PhoneLockTimeout <TimeSpan>] [-SIPSecurityMode <Low | Medium | High>] [-Voice8021p <Byte>] [-VoiceDiffServTag <Byte>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 Redmond 사이트에 대한 UC 전화 설정의 새 컬렉션을 만듭니다. 이 예제에서는 필수 매개 변수와 함께 두 가지 선택적 매개 변수가 포함됩니다. 하나는 일정 폴링 시간 간격을 10분(00시간:10분:00초)으로 설정하는 Identity: CalendarPollInterval이고 다른 하나는 UC 전화 로깅 수준을 Medium으로 설정하는 LoggingLevel입니다. 이 명령이 완료되는 즉시 Redmond 사이트에 새 설정이 적용되고 해당 사이트에서 사용자의 UC 전화가 새 설정으로 관리됩니다. Redmond 사이트에 이미 UC 전화 설정 컬렉션이 있는 경우 이 명령은 실패하게 됩니다.

    New-CsUCPhoneConfiguration -Identity site:Redmond -CalendarPollInterval "00:10:00" -LoggingLevel "Medium"

## 예제 2

예제 2에서는 InMemory 매개 변수의 사용법을 보여 줍니다. 이 매개 변수를 사용하여 메모리에만 존재하는 새 UC 전화 설정 집합을 만들 수 있습니다. 이러한 설정은 $x 변수에 저장됩니다. 이 가상 컬렉션이 생성되면 예제의 둘째 줄과 셋째 줄에 표시된 것과 유사한 명령을 사용하여 메모리 내부 전용 설정을 수정할 수 있습니다. 둘째 줄에서는 CalendarPollInterval 속성이 10분(00시간: 10분: 00초)으로 설정되어 있고 셋째 줄에서는 LoggingLevel 속성이 Medium으로 설정되어 있습니다.

속성 값 수정을 완료한 후 **Set-CsUCPhoneConfiguration** cmdlet을 사용하여 $x에 저장된 가상 설정을 Redmond 사이트에 적용된 실제 설정의 컬렉션으로 전환할 수 있습니다. InMemory 매개 변수를 사용하면 **Set-CsUCPhoneConfiguration** cmdlet을 호출하기 전까지 설정이 실제로 적용되지 않습니다. 이 cmdlet을 호출하지 않으면 Windows PowerShell 세션을 종료하거나 $x 변수를 삭제할 때 가상 설정이 사라집니다.

    $x = New-CsUCPhoneConfiguration -Identity site:Redmond -InMemory
    $x.CalendarPollInterval = "00:10:00" 
    $x.LoggingLevel = "Medium"
    Set-CsUCPhoneConfiguration -Instance $x

## 자세한 정보

Lync Phone Edition은 전화와 Lync Server의 병합을 나타냅니다. Lync Phone Edition은 VoIP(Voice over Internet Protocol) 전화로 작동할 수 있는 특정 하드웨어(즉, Lync Phone Edition 호환 전화)를 사용합니다. 또한 이 하드웨어는 Lync와 같은 끝점 역할을 할 수도 있습니다. 현재 상태를 설정하고, Lync 대화 상대의 상태를 확인하고, 새 대화 상대를 검색하고, Lync를 사용하여 수행하던 기타 여러 작업을 수행할 수 있습니다.

Lync Server에는 Lync Phone Edition을 실행하는 전화를 관리하는 데 사용할 수 있는 다양한 cmdlet이 제공됩니다. 예를 들어 전화에 로그온하는 데 사용되는 개인식별번호(PIN)의 최소 길이 및 전화가 지정된 시간 동안 비활성 상태일 경우 자동으로 잠글지 여부 등을 제어할 수 있습니다.

UC(Unified Communications) 전화 구성 설정은 전역 범위 또는 사이트 범위에 적용할 수 있습니다. 사이트 범위에 적용되는 설정이 전역 범위에 적용되는 설정보다 우선합니다. Lync Server를 처음 설치하면 단일 UC 전화 구성 설정 집합이 생성되어 전역 범위에 적용됩니다. 그러나 이후에 언제든지 **New-CsUCPhoneConfiguration** cmdlet을 사용하여 사이트 범위에서 적용된 설정 컬렉션을 만들 수 있습니다. 이렇게 하면 각 개별 사이트의 고유한 요구 사항에 맞게 UC 전화 관리를 조정할 수 있습니다.

**New-CsUCPhoneConfiguration** cmdlet을 사용하면 사이트 범위에 새 UC 전화 설정을 만들 수 있습니다. 앞서 말했듯이 사이트당 설정 컬렉션을 하나만 만들 수 있습니다. 예를 들어 ID가 site:Redmond인 설정 컬렉션을 만들려고 하는데 Redmond 사이트에 이미 할당된 UC 전화 설정 집합이 있다고 가정해 보겠습니다. 이 경우 명령이 실패하게 됩니다. 대신에 기존 설정을 제거한 다음 **New-CsUCPhoneConfiguration** cmdlet을 사용하여 새 설정 컬렉션을 만들거나 **Set-CsUCPhoneConfiguration** cmdlet을 사용하여 기존 설정을 수정해야 합니다.

전역 범위에는 새 설정 컬렉션을 만들 수 없습니다. 전역 범위에 수행할 수 있는 유일한 작업은 **Set-CsUCPhoneConfiguration** cmdlet을 사용하여 기존 설정을 수정하는 것입니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsUCPhoneConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsUCPhoneConfiguration"}

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
<td><p>UC 전화 구성 설정의 새 컬렉션에 할당할 고유한 식별자를 나타냅니다. 사이트 범위에서만 새 컬렉션을 생성할 수 있기 때문에 ID의 접두사는 항상 &quot;site:&quot;이며 사이트 이름이 오는 &quot;site:Redmond&quot;와 같은 형식이 됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>CalendarPollInterval</em></p></td>
<td><p>선택</p></td>
<td><p>System.TimeSpan</p></td>
<td><p>UC 장치가 Outlook 일정에서 정보를 검색하는 빈도를 지정합니다. 값은 시간:분:초 형식을 사용하여 지정해야 합니다. 예를 들어 시간 간격을 1시간(최대 허용 간격)으로 설정하려면 -CalendarPollInterval &quot;01:00:00&quot; 구문을 사용합니다. 기본값은 3분(00:03:00)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnforcePhoneLock</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>PhoneLockTimeout에 지정된 시간(분)이 지나면 UC 전화를 자동으로 잠글지 여부를 지정합니다. 기본값은 True입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LoggingLevel</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Policy.Voice.LoggingLevel</p></td>
<td><p>UC 장치에 로깅하는 데 사용됩니다. 유효한 값은 Off, Low, Medium 및 High입니다. 기본값은 Off입니다.</p>
<p></p></td>
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
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p>
<p></p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음. **New-CsUCPhoneConfiguration** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Policy.Voice.UcPhoneSettings 개체의 인스턴스를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsUCPhoneConfiguration](get-csucphoneconfiguration.md)  
[Remove-CsUCPhoneConfiguration](remove-csucphoneconfiguration.md)  
[Set-CsUCPhoneConfiguration](set-csucphoneconfiguration.md)

