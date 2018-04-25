---
title: New-CsMobilityPolicy
TOCTitle: New-CsMobilityPolicy
ms:assetid: 1fba8c3e-087d-4ba4-918b-371f8757df7c
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Hh689987(v=OCS.15)
ms:contentKeyID: 49303021
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsMobilityPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

사이트 또는 사용자별 범위에서 새 모바일 정책을 만들 수 있습니다. 모바일 정책은 사용자가 Lync Mobile을 사용할 수 있는지 여부를 결정합니다. 또한 이러한 정책은 사용자가 회사번호로 전화를 거는 기능을 관리하는데, 이 기능을 사용하면 휴대폰에서 자신의 휴대폰 번호 대신 회사 전화 번호를 사용하여 전화를 걸고 받을 수 있습니다. 또한 모바일 정책을 사용하면 전화를 걸거나 받을 때 Wi-Fi 연결을 사용하도록 지정할 수도 있습니다. 이 cmdlet은 Lync Server 2010용 2011년 11월 누적 업데이트에서 도입되었습니다.

## 구문

    New-CsMobilityPolicy -Identity <XdsIdentity> [-AllowCustomerExperienceImprovementProgram <$true | $false>] [-AllowExchangeConnectivity <$true | $false>] [-AllowSaveCallLogs <$true | $false>] [-AllowSaveCredentials <$true | $false>] [-AllowSaveIMHistory <$true | $false>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-EnableIPAudioVideo <$true | $false>] [-EnableMobility <$true | $false>] [-EnableOutsideVoice <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-RequireWIFIForIPAudio <$true | $false>] [-RequireWIFIForIPVideo <$true | $false>] [-RequireWiFiForSharing <$true | $false>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에 표시된 명령은 Redmond 사이트에 대한 새 이동성 정책을 만들고 정책의 영향을 받는 모든 사용자에 대해 회사번호로 전화 기능을 사용하지 않도록 설정합니다. 이를 위해 EnableOutsideVoice 매개 변수를 False로 설정합니다.

    New-CsMobilityPolicy -Identity site:Redmond -EnableOutsideVoice $False

## 예제 2

예제 2는 새 모바일 정책을 메모리에 만들고, 이 정책의 속성 값을 수정한 다음 **Set-CsMobilityPolicy** cmdlet을 사용하여 가상 정책을 실제 Lync Server 모바일 정책으로 바꾸는 방법을 보여줍니다. 이 작업을 수행하기 위해 이 명령은 먼저 **New-CsMobilityPolicy** cmdlet 및 InMemory 매개 변수를 사용하여 Redmond 사이트에 대한 새 정책을 만듭니다. InMemory 매개 변수는 이 정책이 메모리에만 존재하도록 하기 때문에 결과로 생성되는 개체를 변수($x)에 저장해야 합니다.

명령 2에서는 가상 정책의 EnableOutsideVoice 속성을 False로 설정합니다. 그런 후에 명령 3에서는 **Set-CsMobilityPolicy** cmdlet 및 Instance 매개 변수를 사용하여 Lync Server에 변경 사항을 기록하고 Redmond 사이트에 대한 모바일 정책을 만듭니다. **Set-CsMobilityPolicy** cmdlet을 호출하지 않으면 정책이 만들어지지 않으며, 실제로 Windows PowerShell 명령줄 인터페이스 세션을 끝내거나 변수 $x를 삭제하는 즉시 정책이 사라집니다.

    $x = New-CsMobilityPolicy -Identity site:Redmond -InMemory
    $x.EnableOutsideVoice = $False
    Set-CsMobilityPolicy -Instance $x

## 자세한 정보

Lync Mobile은 사용자가 휴대폰에서 Lync를 실행할 수 있도록 하는 클라이언트 응용 프로그램입니다. 회사번호로 전화 기능을 사용하면 휴대폰에서 전화를 걸지만 해당 휴대폰 번호 대신 회사 전화 번호에서 전화가 걸려 온 것처럼 보이게 할 수 있습니다. 회사번호로 전화 기능을 사용하도록 설정된 사용자는 이를 위해 휴대폰에서 직접 전화를 걸거나 외부 전화 접속 회의 옵션을 사용하면 됩니다. 외부 전화 접속 회의의 경우 사용자는 Lync Server Mobility Service 서버에서 자동으로 전화를 걸도록 할 수 있습니다. 그러면 서버에서는 통화를 설정한 다음 해당 휴대폰으로 다시 사용자에게 전화를 겁니다. 그리고 사용자가 응답하면 서버에서는 통화하는 상대방에게 전화를 겁니다. 이 두 기능은 모두 모바일 정책을 사용하여 관리할 수 있습니다.

Lync Server 2013이 설치된 모바일 장치에서는 표준 휴대폰 네트워크 또는 Wi-Fi 연결을 사용하여 전화를 걸거나 받을 수 있습니다. 모바일 정책을 통해 Wi-Fi 연결을 사용하도록 지정하고 셀룰러 네트워크를 통해서는 통화를 할 수 없도록 차단할 수 있습니다.

Lync Server를 설치하면 모든 사용자에게 적용되는 단일 전역 모바일 정책을 얻게 됩니다. 하지만 관리자는 **New-CsMobilityPolicy** cmdlet을 사용하여 사이트 또는 사용자별 범위에 사용자 지정 정책을 만들 수 있습니다.

회사번호로 전화를 사용하도록 설정하려면 각기 다른 두 속성을 구성해야 합니다. 첫 번째 속성인 EnableOutsideVoice는 회사번호로 전화 기능을 사용하도록 설정할지 여부를 결정하고, 두 번째 속성인 EnableMobility는 사용자가 Lync Mobile을 사용할 수 있는지 여부를 결정합니다. 사용자가 회사번호로 전화 기능을 사용할 수 있도록 하려면 먼저 이러한 두 속성을 True로 설정해야 합니다. EnableMobility를 True로 설정하고 EnableOutsideVoice를 False로 설정하는 경우 사용자는 Lync Mobile을 실행할 수 있지만 회사번호로 전화 기능은 사용할 수 없습니다. EnableMobility를 False로 설정하고 EnableOutsideVoice를 True로 설정하는 경우에는 사용자가 Lync Mobile을 실행할 수 없습니다. 또한 이 경우 EnableOutsideVoice 속성 값과 관계없이 사용자는 회사번호로 전화 기능을 사용할 수 없습니다.

회사번호로 전화 기능을 사용하려면 동시 울림을 허용하는 음성 정책을 통해 사용자를 관리해야 합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsMobilityPolicy** cmdlet을 로컬로 실행할 수 있습니다.

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
<td><p>정책에 할당할 고유한 ID입니다. 사이트 또는 사용자별 범위에서 새 이동성 정책을 만들 수 있습니다. 새 사이트 정책을 만들려면 접두사 &quot;site:&quot;를 사용하고 사이트 이름을 ID로 사용합니다. 예를 들어 다음 구문을 사용하여 Redmond 사이트에 대한 정책을 새로 만들 수 있습니다.</p>
<p>-Identity site:Redmond</p>
<p>새 사용자별 정책을 만들려면 다음과 같은 ID를 사용합니다.</p>
<p>-Identity SalesDepartmentPolicy</p>
<p>전역 정책은 새로 만들 수 없습니다. 대신 <strong>Set-CsMobilityPolicy</strong> cmdlet을 사용하여 전역 정책을 변경할 수는 있습니다. 마찬가지로 ID가 이미 존재하는 새 사이트 또는 사용자별 정책은 만들 수 없습니다. 기존 정책을 변경해야 하는 경우 <strong>Set-CsMobilityPolicy</strong> cmdlet을 사용합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AllowCustomerExperienceImprovementProgram</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True(기본값)로 설정하면 휴대폰 사용자가 Microsoft 사용자 환경 개선 프로그램에 참여할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AllowExchangeConnectivity</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True(기본값)로 설정하면 사용자가 모바일 장치를 사용하여 Microsoft Exchange Server 2013에 연결할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AllowSaveCallLogs</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True(기본값)로 설정하면 사용자가 모바일 장치로 걸거나 받은 통화 기록을 저장할 수 있습니다.</p>
<p>이 설정은 Android 장치에는 적용되지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>AllowSaveCredentials</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True(기본값)로 설정하면 사용자가 모바일 장치에 암호 등의 자격 증명 정보를 저장할 수 있습니다. 이 정보는 자동 로그온 시나리오에 적용할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>AllowSaveIMHistory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True(기본값)로 설정하면 사용자가 모바일 장치에 메신저 대화 및 회의 세션의 대화 내용을 저장할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>관리자가 정책과 함께 표시할 설명 텍스트를 제공하는 데 사용됩니다. 예를 들어 정책을 할당할 사용자에 대한 정보를 설명에 포함할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableIPAudioVideo</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>False로 설정하면 사용자가 모바일 장치를 사용하여 VoIP(Voice over IP) 전화를 걸 수 없습니다. 기본값은 True입니다(VoIP 통화가 허용됨).</p>
<p>이 매개 변수는 Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableMobility</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 사용자가 Lync Mobile을 사용할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableOutsideVoice</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 사용자가 회사번호로 전화 기능을 사용할 수 있게 되며, False로 설정하면 회사번호로 전화 기능을 사용할 수 없습니다.</p>
<p>기본값은 True입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행할 때 발생할 수 있는 심각하지 않은 오류 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>개체를 실제로 영구 변경 내용으로 커밋하지 않고 개체 참조를 만듭니다. 이 매개 변수와 함께 호출된 명령의 출력을 변수에 할당하면 개체 참조의 속성을 변경한 후 이 cmdlet과 일치하는 Set- cmdlet을 호출하여 이러한 변경 사항을 커밋할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>RequireWIFIForIPAudio</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 모바일 장치가 Wi-Fi 네트워크에 연결되어 있는 경우 사용자가 통화에서 IP 오디오를 사용할 수 있습니다. 즉, Wi-Fi를 사용할 경우에만 전화를 걸 수 있고. 표준 휴대폰 네트워크는 사용할 수 없습니다. 기본값은 False입니다.</p>
<p>이 매개 변수는 Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>RequireWIFIForIPVideo</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 모바일 장치가 WiFi 네트워크에 연결되어 있는 경우의 통화에서만 사용자가 IP 비디오를 사용할 수 있습니다. 모바일 장치가 Wi-Fi 망을 벗어나면 비디오 전화를 오디오 전화로만 받을 수 있습니다. 이 속성이 False(기본값)로 설정되면 사용자는 Wi-Fi나 셀룰러 데이터 연결을 사용하여 비디오 전화를 걸 수 있습니다.</p>
<p>이 매개 변수는 Lync Server 2013에서 도입되었습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>RequireWiFiForSharing</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>True로 설정하면 휴대폰 사용자가 응용 프로그램 공유 세션에 참여하기 위해 Wi-Fi 연결을 사용해야 합니다. False(기본값)로 설정하면 휴대폰 사용자가 Wi-Fi 연결 또는 셀룰러(3G/4G) 연결을 사용하여 응용 프로그램 공유에 참여할 수 있습니다.</p>
<p>이 값이 True로 설정되면 사용자가 해당 공유 구성 설정을 변경할 수 없습니다. 이 값이 False로 설정되면 사용자가 옵션 페이지를 통해 해당 공유 구성 설정을 수정할 수 있습니다.</p></td>
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

없음. **New-CsMobilityPolicy** cmdlet은 파이프라인된 입력을 허용하지 않습니다.

## 반환 형식

Microsoft.Rtc.Management.WriteableConfig.Policy.Mobility.Mobility 개체의 새 인스턴스를 만듭니다.

