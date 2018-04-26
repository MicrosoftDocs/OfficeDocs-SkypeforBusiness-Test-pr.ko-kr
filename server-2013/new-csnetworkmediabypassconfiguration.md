---
title: New-CsNetworkMediaBypassConfiguration
TOCTitle: New-CsNetworkMediaBypassConfiguration
ms:assetid: 24055ae5-7fc8-4ca5-9e65-ac3a1f17b405
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg425718(v=OCS.15)
ms:contentKeyID: 49303067
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsNetworkMediaBypassConfiguration

 

_**마지막으로 수정된 항목:** 2015-03-09_

미디어 바이패스에 대한 새 전역 설정을 만듭니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsNetworkMediaBypassConfiguration [-AlwaysBypass <$true | $false>] [-BypassID <String>] [-Enabled <$true | $false>] [-EnableDefaultBypassID <$true | $false>] [-EnabledForAudioVideoConferences <$true | $false>] [-ExternalBypassMode <Off | ICE | Any>] [-InternalBypassMode <Off | ICE | Any>]

## 예제

## 예제 1

이 예제의 명령은 미디어 바이패스를 사용하도록 설정하고 항상 바이패스를 시도하도록 구성합니다. 예제의 첫째 줄은 **New-CsNetworkMediaBypassConfiguration** cmdlet에 대한 호출입니다. 이 cmdlet에 AlwaysBypass와 Enabled의 두 매개 변수를 전달하고 둘 다 True($true)로 설정합니다. Enabled를 True로 설정하면 미디어 바이패스가 사용하도록 설정되고, AlwaysBypass를 True로 설정하면 모든 통화에 대해 미디어 바이패스가 시도됩니다. 이러한 두 매개 변수를 설정하면 BypassID 속성 값이 자동으로 생성됩니다. **New-CsNetworkMediaBypassConfiguration** cmdlet은 메모리에만 개체를 만들기 때문에 해당 개체를 변수 $a에 할당합니다.

미디어 바이패스 구성은 네트워크 구성 설정에 저장됩니다. 따라서 예제의 둘째 줄에서 **Set-CsNetworkConfiguration** cmdlet을 호출하고, MediaBypassSettings 매개 변수에 첫째 줄에서 만든 미디어 바이패스 구성 개체($a)를 전달하여 네트워크 구성에 미디어 바이패스 구성 변경 사항을 저장합니다.

    $a = New-CsNetworkMediaBypassConfiguration -AlwaysBypass $true -Enabled $true
    Set-CsNetworkConfiguration -MediaBypassSettings $a

## 예제 2

Lync Server에는 **Set-CsNetworkMediaBypassConfiguration** cmdlet이 없습니다. 따라서 기존 설정을 수정하려면 예제 1에서 보는 바와 같이 새 구성을 만들어 기존 구성을 바꾸거나 기존 설정을 검색하여 수정한 다음 **Set-CsNetworkConfiguration** cmdlet을 사용하여 변경 사항을 저장하는 방법으로 설정을 수정해야 합니다. 이 예제는 후자 옵션을 사용하여 Always Bypass 옵션을 사용하지 않도록 설정하는 방법을 보여 줍니다.

이 예제의 첫째 줄에서는 기존 미디어 바이패스 설정을 검색합니다. 이 작업을 수행하기 위해 **Get-CsNetworkConfiguration** cmdlet을 호출합니다. 이 cmdlet에 대한 호출은 명령의 다른 부분이 실행되기 전에 완료될 수 있도록 괄호 안에 들어 있습니다. **Get-CsNetworkConfiguration** cmdlet은 전체 네트워크 구성의 모든 설정을 검색합니다. 미디어 바이패스 설정만 검색하면 되므로 이러한 설정만 검색하도록 MediaBypassSettings 속성을 지정합니다. 이러한 설정을 변수 $a에 할당합니다.

둘째 줄에서는 AlwaysBypass 속성에 False 값($false)을 할당하여 변수 $a에 저장된 설정을 수정합니다. 마지막으로 셋째 줄에서는 **Set-CsNetworkConfiguration** cmdlet을 호출하고 MediaBypassSettings 매개 변수에 변수 $a를 전달하여 AllowBypass 속성에 대해 변경된 사항을 저장합니다.

    $a = (Get-CsNetworkConfiguration).MediaBypassSettings
    $a.AlwaysBypass = $false
    Set-CsNetworkConfiguration -MediaBypassSettings $a

## 자세한 정보

이 cmdlet은 오디오 연결의 미디어 바이패스에 대한 전역 설정을 만듭니다.

Lync Server의 대부분의 New- cmdlet과 달리 이 cmdlet은 새 구성을 즉시 저장하지 않고 메모리에만 설정을 만듭니다. 이 cmdlet에 의해 생성된 개체는 변수에 저장된 다음 네트워크 구성의 MediaBypassSettings 속성에 할당됩니다. 자세한 내용은 이 항목의 예제 섹션을 참조하십시오.

이 cmdlet을 사용하여 만든 설정은 전역 네트워크 구성의 MediaBypassSettings 속성에 액세스해야만 검색할 수 있습니다. 이러한 설정을 검색하려면 (Get-CsNetworkConfiguration).MediaBypassSettings 명령을 실행합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsNetworkMediaBypassConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsNetworkMediaBypassConfiguration"}

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
<td><p><em>AlwaysBypass</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>이 매개 변수를 True로 설정하면 모든 통화에 대해 미디어 바이패스가 시도됩니다.</p>
<p>CAC(통화 허용 제어)가 비활성화된 경우에만 이 매개 변수 값을 True로 설정합니다. 다음과 같은 배포에 대해서만 이 매개 변수를 True로 설정합니다.</p>
<p>- 대역폭을 제어할 필요가 없는 경우.</p>
<p>- 바이패스가 발생하는 시기를 확인하기 위해 세분화된 구성이 필요하지 않은 경우.</p>
<p>- 게이트웨이와 클라이언트가 완전히 연결된 경우.</p>
<p>Enabled 매개 변수를 True로 설정하고, AlwaysBypass를 False로 설정하면 바이패스 논리가 네트워크 구성 사이트 및 지역을 사용하여 바이패스가 가능한 시기를 확인합니다.</p>
<p>AlwaysBypass를 True로 설정하고, Enabled 매개 변수 값을 True로 설정하지 않으면 'Enabled를 false로 설정하면 AlwaysBypass 설정이 무시됩니다'라는 경고 메시지가 수신됩니다.</p>
<p>AlwaysBypass와 Enabled를 모두 True로 설정하면 바이패스 ID가 자동 생성되어 BypassID 속성에 저장됩니다.</p>
<p>기본값: False</p></td>
</tr>
<tr class="even">
<td><p><em>BypassID</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>미디어 바이패스 ID입니다. AlwaysBypass 매개 변수를 True로 설정하고, 이 매개 변수에 대해 값을 입력하면 이 BypassID가 모든 서브넷과 연결됩니다. AlwaysBypass가 False인 경우 BypassID 값은 네트워크 구성 사이트 및 지역에 없는 모든 서브넷과 연결됩니다.</p>
<p>이 ID는 GUID 형식이어야 합니다(예: 96f14dea-5170-429a-b92b-f1cb909c4bb6). 그러나 일반적으로 이 매개 변수는 설정하거나 변경할 필요가 없습니다. 이 값은 Enabled를 True로 설정하거나 1) AlwaysBypass를 True로 설정하는 경우 또는 2) EnableDefaultBypassID 매개 변수를 True로 설정하는 경우 자동으로 생성됩니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Enabled</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>미디어 바이패스를 사용하도록 설정하려면 이 매개 변수를 True로 설정합니다. 그런 다음 AlwaysBypass 설정 값에 따라 다음과 같이 바이패스를 결정합니다.</p>
<p>- AlwaysBypass가 True인 경우 모든 호출에 대해 바이패스를 시도합니다.</p>
<p>- AlwaysBypass가 False인 경우 네트워크 구성 사이트 및 지역을 사용하여 바이패스가 가능한지 여부를 확인합니다.</p>
<p>기본값: False</p></td>
</tr>
<tr class="even">
<td><p><em>EnableDefaultBypassID</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>이 값은 AlwaysBypass가 False로 설정된 경우에만 적용됩니다.</p>
<p>이 값을 True로 설정하면 기본 바이패스 ID가 자동으로 생성됩니다. 이렇게 자동 생성된 값은 BypassID 속성에 저장됩니다.</p>
<p>이 매개 변수는 대역폭 제한 링크가 있는 원격 사이트와 잘 연결된 핵심 구성 요소가 있는 경우에 유용합니다. 관리자는 네트워크 구성 사이트 및 지역을 통해 원격 사이트와 연결된 서브넷만 정의해야 합니다. 핵심 구성 요소와 연결된 서브넷은 정의할 필요가 없으며 이러한 서브넷 간에는 바이패스가 자동으로 시도됩니다.</p>
<p>기본값: False</p></td>
</tr>
<tr class="odd">
<td><p><em>EnabledForAudioVideoConferences</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>오디오/비디오 회의에 대해 미디어 바이패스를 사용할지 여부를 나타냅니다. 기본값은 False($False)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ExternalBypassMode</em></p></td>
<td><p>선택</p></td>
<td><p>바이패스 모드 열거 유형</p></td>
<td><p>나중에 사용하기 위해 예약되었습니다. 외부 미디어 바이패스는 Lync Server에서 지원되지 않습니다.</p>
<p>기본값: Off</p></td>
</tr>
<tr class="odd">
<td><p><em>InternalBypassMode</em></p></td>
<td><p>선택</p></td>
<td><p>바이패스 모드 열거 유형</p></td>
<td><p>이 매개 변수 값은 조직의 네트워크 내부에서 연결하는 클라이언트가 미디어 바이패스를 시도할 수 있는 시기를 제어합니다. Enabled를 True로 설정하면 이 값이 Any로 자동 변경됩니다. 이 매개 변수의 다른 값은 나중에 사용하기 위해 예약됩니다.</p>
<p>기본값: Off</p></td>
</tr>
</tbody>
</table>


## 입력 형식

없음.

## 반환 형식

Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.MediaBypassSettingsType 유형의 개체 참조를 만듭니다.

## 참고 항목

#### 기타 리소스

[Get-CsNetworkConfiguration](get-csnetworkconfiguration.md)  
[Set-CsNetworkConfiguration](set-csnetworkconfiguration.md)

