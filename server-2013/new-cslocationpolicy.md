---
title: New-CsLocationPolicy
TOCTitle: New-CsLocationPolicy
ms:assetid: 167dead6-e4d4-402c-9ea4-91968eae5610
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398231(v=OCS.15)
ms:contentKeyID: 49302918
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsLocationPolicy

 

_**마지막으로 수정된 항목:** 2015-03-09_

E9-1-1(Enhanced 9-1-1) 서비스 및 일반 클라이언트 위치에 대한 위치 식별에 사용할 새 위치 정책을 만듭니다. E9-1-1 서비스를 사용하면 911 전화 응답자가 발신자의 지리적 위치를 확인할 수 있습니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    New-CsLocationPolicy -Identity <XdsIdentity> [-ConferenceMode <oneway | twoway>] [-ConferenceUri <String>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-EmergencyDialMask <String>] [-EmergencyDialString <String>] [-EnhancedEmergencyServiceDisclaimer <String>] [-EnhancedEmergencyServicesEnabled <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-LocationRefreshInterval <Int64>] [-LocationRequired <yes | no | disclaimer>] [-NotificationUri <String>] [-PstnUsage <String>] [-UseLocationForE911Only <$true | $false>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1은 **New-CsLocationPolicy** cmdlet을 사용하여 Redmond 사이트의 모든 사용자가 E9-1-1을 사용할 수 있도록 설정하는 새 위치 정책을 만듭니다. 이 정책을 만들려면 **New-CsLocationPolicy** cmdlet을 호출합니다. 이때 Identity를 설정할 매개 변수 하나를 먼저 지정합니다. 이 경우에는 문자열 site: 다음에 이 정책을 적용할 사이트의 이름을 지정합니다. 그런 다음 EnhancedEmergencyServicesEnabled 속성 값을 True로 설정하는 매개 변수를 지정합니다.

    New-CsLocationPolicy -Identity site:Redmond -EnhancedEmergencyServicesEnabled $True

## 예제 2

이 예제는 사용자별 위치 정책을 만듭니다. 사용자별 정책은 개별 사용자 또는 그룹에게 개별적으로 부여되어야 합니다. 이 정책에는 Reno의 Identity가 있습니다. Description 매개 변수를 사용하여 정책에 대한 자세한 설명을 추가했습니다. 다음으로 지정한 매개 변수는 EnhancedEmergencyServicesEnabled이며 이 정책을 부여할 모든 사용자가 E9-1-1 기능을 사용할 수 있도록 True로 설정되어 있습니다. 다음 매개 변수는 PstnUsage이며 이 경우 값은 Emergency입니다. 이 값은 PSTN 사용 목록의 값과 일치해야 합니다. 이 목록은 **Get-CsPstnUsage** cmdlet을 호출하여 검색할 수 있습니다. 사용은 응급 통화에 사용할 음성 경로에 연결해야 합니다. **Get-CsVoiceRoute** cmdlet을 호출하여 음성 경로를 검색할 수 있습니다. 이 예제에 사용된 마지막 매개 변수 EmergencyDialString은 응급 통화로 연결할 번호를 지정합니다.

    New-CsLocationPolicy -Identity Reno -Description "All users located at the Reno site" -EnhancedEmergencyServicesEnabled $True -PstnUsage Emergency -EmergencyDialString 911

## 자세한 정보

위치 정책은 E9-1-1 기능과 관련된 설정 및 위치 설정을 사용자 또는 연락처에 적용하는 데 사용됩니다. 사용자가 E9-1-1을 사용하도록 설정되어 있는지 여부를 확인하고, 설정된 경우 응급 통화에 대한 행동을 결정합니다. 예를 들어 위치 정책을 사용하여 응급 통화 번호(한국의 경우 119)를 정의하고, 회사 보안 부서에 자동으로 알림을 제공할지 여부, 통화를 경로 지정할 방법 등을 지정할 수 있습니다. 이 cmdlet은 사이트 범위 또는 사용자별 범위에 새 위치 정책을 만듭니다. 전역 범위의 정책은 이미 있습니다.

중요: 위치 정책은 범위 체계와 관련하여 Lync Server의 다른 정책과 다르게 동작합니다. 다른 모든 정책의 경우 정책이 사용자별 범위에 정의되어 있으면 해당 정책이 부여된 모든 사용자에게 정책이 적용됩니다. 사용자에게 사용자별 정책이 부여되지 않았으면 사이트 정책이 적용됩니다. 사이트 정책이 없으면 전역 정책이 적용됩니다. 위치 정책도 동일한 방식으로 적용됩니다. 단, 한 가지 예외는 네트워크 사이트에 사용자별 위치 정책을 할당할 수도 있다는 점입니다. 네트워크 사이트는 서브넷 그룹으로 구성됩니다. 사용자가 조직 내 네트워크 사이트에 매핑된 위치에서 긴급 통화를 걸면 해당 네트워크에 할당된 사용자 수준 정책이 사용됩니다. 이 기능은 해당 사용자에게 부여된 사용자별 정책보다 우선합니다. 사용자가 조직에서 알 수 없거나 매핑되지 않은 위치에서 전화를 거는 경우 표준 정책 범위가 적용됩니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **New-CsLocationPolicy** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsLocationPolicy"}

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
<td><p>위치 정책에 대한 고유 식별자입니다. 이 cmdlet은 사이트 범위 또는 사용자별 범위에 정책을 만드는 데 사용할 수 있습니다. 전역 정책은 기본적으로 존재하며 제거할 수 없습니다. 사이트 범위에 정책을 만드는 경우 이 값은 site:&lt;사이트 이름&gt; 형식이어야 하며 여기서 사이트 이름은 Lync Server 배포에서 정의된 사이트의 이름입니다(예: site:Redmond). 사용자별 범위에 만든 정책에는 Reno와 같은 모든 문자열 값을 할당할 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ConferenceMode</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Policy.Location.ConferenceModeEnum</p></td>
<td><p>ConferenceUri 매개 변수 값을 지정하면 ConferenceMode 매개 변수에서 제3자가 통화에 참가할 수 있는지 또는 들을 수만 있는지를 결정합니다. 사용할 수 있는 값은 다음과 같습니다.</p>
<p>- oneway: 제3자가 발신자와 PSAP(Public Safety Answering Point) 교환원 사이의 대화를 들을 수만 있습니다.</p>
<p>- twoway: 제3자가 발신자와 PSAP 교환원 사이의 대화를 듣고 통화에 참가할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ConferenceUri</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>걸려 온 응급 통화에 함께 응답할 제3자의 SIP URI(Uniform Resource Identifier)(이 경우 전화 번호)입니다. 예를 들어 회사 보안 부서는 ConferenceMode 속성 값에 따라 응급 통화가 걸려 올 때 전화를 받고 통화 내용을 듣거나 참가할 수 있습니다.</p>
<p>이 문자열은 1자에서 256자 사이여야 하며 접두사 sip:로 시작해야 합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 위치에 대한 자세한 설명입니다(예: &quot;Reno corporate users&quot; ).</p></td>
</tr>
<tr class="even">
<td><p><em>EmergencyDialMask</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>EmergencyDialString 속성 값으로 변환되는 전화 번호입니다. 예를 들어 EmergencyDialMask 값이 &quot;212&quot;이고 EmergencyDialString 값이 &quot;911&quot;인 경우, 사용자가 212로 전화를 걸면 911로 전화가 연결됩니다. 이 매개 변수를 지정하면 대체 응급 번호를 사용하여 응급 서비스에 전화를 걸 수 있습니다. 예를 들어 응급 번호가 다른 국가의 사용자가 외국에서 그 나라의 번호 대신 자신의 국가에서 사용되는 번호로 전화를 거는 경우에 유용합니다. 값을 세미콜론으로 구분하여 여러 응급 다이얼 마스크를 정의할 수 있습니다.(예: -EmergencyDialMask “212;414”).</p>
<p>중요. 지정된 다이얼 마스크 값은 통화 대기 파킹된 통화 번호 범위의 번호와 달라야 합니다. 통화 대기 경로 지정은 응급 다이얼 문자열 변환보다 우선합니다. 기존 통화 대기 파킹된 통화 번호 범위를 보려면 <strong>Get-CsCallParkOrbit</strong> cmdlet을 호출합니다.</p>
<p>최대 문자열 길이는 100자이고, 각 문자는 0에서 9사이의 숫자여야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EmergencyDialString</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>응급 서비스에 연결되는 전화 번호입니다. 미국의 경우 이 값은 911입니다.</p>
<p>이 문자열은 0에서 9 사이의 숫자로 구성되어야 하며 1자에서 10자 사이일 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnhancedEmergencyServiceDisclaimer</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>위치 매핑(와이어맵(wiremap))에서 확인될 수 없는 위치에서 연결되고 위치를 수동으로 입력하지 않도록 선택한 사용자에게 표시되는 정보가 포함된 텍스트 값입니다. 위치 정책에서 서비스 고지 사항을 제거하려면 이 속성을 null 값으로 설정합니다.</p>
<p>-EnhancedEmergencyServiceDisclaimer $Null</p>
<p>Lync Server 2013에서는 위치 정책 및 EnhancedEmergencyServiceDisclaimer 속성을 사용하여 E9-1-1 서비스의 고지 사항을 설정해야 합니다. 이 설정 방식은 Set-CsEnhancedEmergencyServiceDisclaimer cmdlet을 사용하여 전체 조직에 대한 전역 고지 사항을 설정했던 Lync Server 2010의 방식과는 다릅니다. 위치 정책을 사용하여 이러한 고지 사항을 설정하면 각 로캘이나 사용자 집합에 대해 서로 다른 고지 사항을 작성할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnhancedEmergencyServicesEnabled</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>이 정책과 연결된 사용자가 E9-1-1을 사용할 수 있는지 여부를 지정합니다. E9-1-1을 사용하도록 설정하려면 값을 True로 설정합니다. 그러면 Lync Server 클라이언트가 등록된 위치 정보를 검색하여 긴급 통화 시 해당 정보를 포함합니다.</p>
<p>기본값: False</p></td>
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
<td><p><em>LocationRefreshInterval</em></p></td>
<td><p>선택</p></td>
<td><p>System.Int64</p></td>
<td><p>위치 정보 서비스 위치 업데이트에 대한 클라이언트 요청 간의 시간을 시간 단위로 지정합니다. LocationRefreshInterval은 1에서 12 사이의 값으로 설정할 수 있으며 기본값은 4입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocationRequired</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.WritableConfig.Policy.Location.LocationRequiredEnum</p></td>
<td><p>클라이언트가 위치 구성 데이터베이스에서 위치를 검색할 수 없는 경우 사용자에게 위치를 수동으로 입력하라는 메시지를 표시하는 데 사용됩니다. 이 매개 변수에는 다음 값이 허용됩니다.</p>
<p>- no: 사용자에게 위치를 묻는 메시지가 표시되지 않습니다. 위치 정보 없이 통화가 이루어지면 응급 서비스 공급자가 통화에 응답하고 위치를 묻습니다.</p>
<p>- yes: 클라이언트가 새 위치에서 등록하면 사용자에게 위치 정보를 입력하라는 메시지가 표시됩니다. 사용자는 정보를 입력하지 않은 상태로 메시지를 취소할 수 있습니다. 정보를 입력하면 911 통화 시 PSAP 교환원(911 교환원)으로 경로 지정되기 전에 먼저 응급 서비스 공급자가 응답하여 위치를 확인합니다.</p>
<p>- disclaimer: 이 옵션은 yes와 같지만 사용자가 메시지를 취소하는 경우 사용자에게 위치 정보 입력 거부에 대한 결과를 알려 주는 고지 사항 텍스트가 표시됩니다. 이 고지 사항 텍스트는 <strong>Set-CsEnhancedEmergencyServiceDisclaimer</strong> cmdlet을 호출하여 설정해야 합니다.</p>
<p>EnhancedEmergencyServicesEnabled가 False(기본값)로 설정하면 이 값이 무시되고 사용자에게 위치 정보를 묻는 메시지가 나타나지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>NotificationUri</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>응급 통화가 걸려 올 때 알림을 받을 하나 이상의 SIP URI입니다. 예를 들어 회사의 보안 부서에서 응급 통화가 걸려 올 때마다 메신저 대화를 통해 알림을 받을 수 있습니다. 발신자의 위치를 파악할 수 있는 경우 해당 위치가 알림에 포함됩니다.</p>
<p>-NotificationUri sip:security@litwareinc.com,sip:kmyer@litwareinc.com과 같이 쉼표로 구분된 목록으로 여러 SIP URI를 포함할 수 있습니다. Lync Server 2013의 릴리스 이후로는 메일 그룹을 알림 URI로 구성할 수 있습니다.</p>
<p>이 문자열은 1자에서 256자 사이여야 하며 접두사 sip:로 시작해야 합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PstnUsage</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 프로필을 사용하는 클라이언트의 응급 통화를 경로 지정하는 데 사용할 음성 경로를 확인하는 데 사용되는 PSTN(공중 전화망) 사용법입니다. 이 사용법과 연결된 경로는 응급 통화에 전용되는 SIP 트렁크를 가리켜야 합니다.</p>
<p>사용법은 전역 PSTN 사용법 목록에 이미 있어야 합니다. 사용법 목록을 검색하려면 <strong>Get-CsPstnUsage</strong> cmdlet을 호출합니다. 새 사용법을 만들려면 <strong>Set-CsPstnUsage</strong> cmdlet을 호출합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>UseLocationForE911Only</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>Lync 클라이언트는 현재 위치를 팀원에게 알리는 등 여러 가지 이유로 위치 정보를 사용할 수 있습니다. 긴급 통화에만 위치 정보를 사용할 수 있도록 하려면 이 값을 True로 설정합니다.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Policy.Location.LocationPolicy 유형의 개체를 만듭니다.

## 참고 항목

#### 기타 리소스

[Remove-CsLocationPolicy](remove-cslocationpolicy.md)  
[Set-CsLocationPolicy](set-cslocationpolicy.md)  
[Get-CsLocationPolicy](get-cslocationpolicy.md)  
[Grant-CsLocationPolicy](grant-cslocationpolicy.md)  
[Test-CsLocationPolicy](test-cslocationpolicy.md)  
[Get-CsPstnUsage](get-cspstnusage.md)  
[Get-CsVoiceRoute](get-csvoiceroute.md)

