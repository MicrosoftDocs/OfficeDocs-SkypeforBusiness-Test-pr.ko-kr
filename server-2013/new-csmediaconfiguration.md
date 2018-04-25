---
title: New-CsMediaConfiguration
TOCTitle: New-CsMediaConfiguration
ms:assetid: 3b60c36f-f824-4948-aa46-6745b40b9641
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425881(v=OCS.15)
ms:contentKeyID: 49303362
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsMediaConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

새 미디어 설정 컬렉션을 만듭니다. 이러한 설정을 사용하여 지원되는 암호화 수준, 허용되는 최대 비디오 해상도 등을 지정할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsMediaConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-EnableQoS <$true | $false>] [-EnableSiren <$true | $false>] [-EncryptionLevel <SupportEncryption | RequireEncryption | DoNotSupportEncryption>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-MaxVideoRateAllowed <CIF250K | VGA600K | Hd720p15M>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 **New-CsMediaConfiguration** cmdlet을 사용하여 ID가 site:Redmond1인 새 미디어 구성을 만듭니다. 이 새 구성은 멀티미디어 대화에 포함된 상대방이 둘 다 암호화를 사용하도록 요구합니다. 이 요구 사항을 적용하기 위해 EncryptionLevel 매개 변수를 추가하고 매개 변수 값을 RequireEncryption으로 설정합니다.

    New-CsMediaConfiguration -Identity site:Redmond1 -EncryptionLevel RequireEncryption

## 예제 2

이 예제에서는 **New-CsMediaConfiguration** cmdlet을 사용하여 Identity가 MediationServer:pool0.litwareinc.com인 새 미디어 구성을 만듭니다. 새 구성의 EnableSiren 값은 True이므로 이 중재 서버와 관련된 통화에 대해 Siren이 사용됩니다.

    New-CsMediaConfiguration -Identity MediationServer:pool0.litwareinc.com -EnableSiren $True

## 자세한 정보

이 cmdlet은 특정 미디어 작업의 동작을 정의하는 새 설정 컬렉션을 만듭니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsMediaConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsMediaConfiguration"}

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
<td><p>이 구성이 적용되는 범위(사이트 또는 서비스)를 지정하는 고유 식별자입니다. 사이트 범위의 구성은 site:&lt;사이트 이름&gt;으로 입력됩니다(예: site:Redmond). 서비스는 &lt;server role&gt;:&lt;fqdn&gt;으로 입력할 수 있습니다(예: MediationServer:pool0.litwareinc.com). 전역 범위의 미디어 구성이 항상 존재하고 이는 제거할 수 없으므로 새 전역 구성을 만들 수 없습니다.</p>
<p>서비스 범위에서 생성되는 미디어 구성은 A/V 회의 서비스, 중재 서버 및 응용 프로그램 서버에 대해서만 만들 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableQoS</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>QoS는 네트워크에서 음성 신호의 품질을 모니터링합니다.</p>
<p>기본값: False</p></td>
</tr>
<tr class="even">
<td><p><em>EnableSiren</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>기본적으로 중재 서버는 서버 자체와 다른 Lync 클라이언트 사이의 통화를 위해 사용할 수 있는 코덱으로 Siren을 협상하지 않습니다. 이 설정이 True인 경우 Siren은 중재 서버와 다른 Lync 클라이언트 사이에 사용 가능한 코덱으로 포함됩니다.</p>
<p>기본값: False</p></td>
</tr>
<tr class="odd">
<td><p><em>EncryptionLevel</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.Media.EncryptionLevel</p></td>
<td><p>통합 통신 장치 간의 암호화 수준입니다.</p>
<p>유효한 값:</p>
<p>SupportEncryption - 협상 가능한 경우 SRTP(Secure Real-Time Transport Protocol)가 사용됩니다.</p>
<p>RequireEncryption - SRTP를 협상해야 합니다.</p>
<p>DoNotSupportEncryption - SRTP를 사용하면 안 됩니다.</p>
<p>기본값: RequireEncryption</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 사항으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 이 cmdlet의 결과를 변수로 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 해당 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MaxVideoRateAllowed</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.Media.MaxVideoRateAllowed</p></td>
<td><p>클라이언트 끝점에서 비디오 신호가 전송되는 최대 속도입니다.</p>
<p>유효한 값: Hd720p15M, VGA600K, CIF250K</p>
<p>Hd720p15M - 해상도가 1280 x 720이고 가로 세로 비율이 16:9인 HD(고화질)입니다.</p>
<p>VGA600K - 해상도가 640 x 480이고 가로 세로 비율이 4:3인 25fps의 VGA입니다.</p>
<p>CIF250K - 해상도가 352 x 288인 15fps의 CIF(Common Intermediate Format) 비디오 형식입니다.</p>
<p>이러한 값은 대/소문자를 구분하지 않으며 구성을 만들 때 적절한 대/소문자로 변환됩니다.</p>
<p>기본값: VGA600K</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.Media.MediaSettings 유형의 개체를 만듭니다.

## 참고 항목

#### 기타 리소스

[Remove-CsMediaConfiguration](remove-csmediaconfiguration.md)  
[Set-CsMediaConfiguration](set-csmediaconfiguration.md)  
[Get-CsMediaConfiguration](get-csmediaconfiguration.md)

