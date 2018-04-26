---
title: Set-CsMediaConfiguration
TOCTitle: Set-CsMediaConfiguration
ms:assetid: 768bc273-5253-4569-895d-5b1127386b92
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398580(v=OCS.15)
ms:contentKeyID: 49304076
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsMediaConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

미디어 설정의 기존 컬렉션을 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsMediaConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsMediaConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-EnableQoS <$true | $false>] [-EnableSiren <$true | $false>] [-EncryptionLevel <SupportEncryption | RequireEncryption | DoNotSupportEncryption>] [-Force <SwitchParameter>] [-MaxVideoRateAllowed <CIF250K | VGA600K | Hd720p15M>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 ID가 site:Redmond1인 미디어 구성 컬렉션을 수정합니다. 특히 이 명령은 MaxVideoRateAllowed 속성 값을 Hd720p15M으로 설정합니다. MaxVideoRateAllowed 매개 변수에 전달된 값은 매개 변수 설명에 지정된 값 중 하나여야 합니다. 또한 값은 대/소문자를 구분하지 않습니다. 여기에서 hd720p15m으로 입력한 값은 적절한 대/소문자(이 경우에는 Hd720p15M)로 자동 변환됩니다.

    Set-CsMediaConfiguration -Identity site:Redmond1 -MaxVideoRateAllowed hd720p15m

## 예제 2

이 예제에서는 EncryptionLevel 값이 DoNotSupportEncryption이 되도록 ID가 site:Redmond1인 미디어 구성 컬렉션을 수정합니다. 이 값은 대/소문자를 구분하지 않습니다. 여기에서 donotsupportencryption으로 입력한 값은 유효한 값으로 허용되며 혼합된 대/소문자(DoNotSupportEncryption)로 자동으로 변경됩니다.

    Set-CsMediaConfiguration site:Redmond1 -EncryptionLevel donotsupportencryption

## 자세한 정보

이 cmdlet은 미디어 구성을 정의하는 설정의 컬렉션을 수정합니다. 이러한 작업은 클라이언트 끝점 간의 오디오 및 비디오 통화와 관련됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsMediaConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsMediaConfiguration"}

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
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableQoS</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>QoS는 네트워크에서 음성 신호의 품질을 모니터링합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableSiren</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>기본적으로 중재 서버는 서버 자체와 다른 Lync 클라이언트 사이의 통화를 위해 사용할 수 있는 코덱으로 Siren을 협상하지 않습니다. 이 설정이 True인 경우 Siren은 중재 서버와 다른 Lync 클라이언트 사이에 사용 가능한 코덱으로 포함됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EncryptionLevel</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.Media.EncryptionLevel</p></td>
<td><p>통합 통신 장치 간의 암호화 수준입니다.</p>
<p>유효한 값:</p>
<p>SupportEncryption - 협상 가능한 경우 SRTP(Secure Real-Time Transport Protocol)가 사용됩니다.</p>
<p>RequireEncryption - SRTP가 협상되어야 합니다.</p>
<p>DoNotSupportEncryption - SRTP를 사용하면 안 됩니다.</p>
<p>이 값은 대/소문자를 구분하지 않습니다. 자세한 내용은 이 항목의 예제를 참고하세요.</p>
<p>기본값: RequireEncryption</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>변경 작업을 수행하기 전에 표시되는 모든 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>변경할 미디어 구성 설정에 대한 고유한 식별자입니다. 이 식별자는 이 구성이 적용되는 범위(전역, 사이트 또는 서비스)를 지정합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>미디어 설정</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Settings.Media.MediaSettings 개체의 인스턴스입니다. <strong>Get-CsMediaConfiguration</strong> cmdlet을 특정 ID와 함께 호출하여 이 개체를 검색할 수 있습니다. 그런 다음, 새 값을 개체 속성에 할당하고 <strong>Set-CsMediaConfiguration</strong> cmdlet으로 개체를 전달하여 이러한 변경 내용을 저장할 수 있습니다.</p></td>
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
<p>이러한 값은 대/소문자를 구분하지 않으며 구성을 만들 때 적절한 대/소문자로 변환됩니다. 자세한 내용은 이 항목의 예제를 참고하세요.</p>
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

Microsoft.Rtc.Management.WritableConfig.Settings.Media.MediaSettings 개체입니다. 미디어 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

**Set-CsMediaConfiguration** cmdlet은 값이나 개체를 반환하지 않습니다. 대신 이 cmdlet은 Microsoft.Rtc.Management.WritableConfig.Settings.Media.MediaSettings 개체의 인스턴스를 구성합니다.

## 참고 항목

#### 기타 리소스

[New-CsMediaConfiguration](new-csmediaconfiguration.md)  
[Remove-CsMediaConfiguration](remove-csmediaconfiguration.md)  
[Get-CsMediaConfiguration](get-csmediaconfiguration.md)

