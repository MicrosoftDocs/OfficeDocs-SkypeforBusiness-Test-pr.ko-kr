---
title: Set-CsAudioTestServiceApplication
TOCTitle: Set-CsAudioTestServiceApplication
ms:assetid: d2c6880b-58df-43d1-9f26-d2b9f54d3f0b
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398907(v=OCS.15)
ms:contentKeyID: 49305127
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsAudioTestServiceApplication

 

_**마지막으로 수정된 항목:** 2015-03-09_

조직에서 현재 사용 중인 오디오 테스트 서비스 응용 프로그램 대화 상대의 속성 값을 수정하는 데 사용됩니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsAudioTestServiceApplication -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-DisplayName <String>] [-DisplayNumber <String>] [-Enabled <$true | $false>] [-EnabledForFederation <$true | $false>] [-EnterpriseVoiceEnabled <$true | $false>] [-ExchangeArchivingPolicy <Uninitialized | UseLyncArchivingPolicy | NoArchiving | ArchivingToExchange>] [-LineURI <String>] [-PassThru <SwitchParameter>] [-PrimaryLanguage <String>] [-SecondaryLanguages <MultiValuedProperty>] [-SipAddress <String>] [-Type <String>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

예제 1에서는 오디오 테스트 서비스 대화 상대 sip:RedmondAudioTest@litwareinc.com의 기본 언어를 영어(미국)(en-US)로 설정합니다.

    Set-CsAudioTestServiceApplication -Identity "sip:RedmondAudioTest@litwareinc.com" -PrimaryLanguage "en-US" 

## 예제 2

예제 2에서는 오디오 테스트 서비스 대화 상대 sip:RedmondAudioTest@litwareinc.com의 PrimaryLanguage 속성 값을 지웁니다. 이 작업을 수행하기 위해 PrimaryLanguage 매개 변수를 포함하고 매개 변수 값을 $Null로 설정합니다.

    Set-CsAudioTestServiceApplication -Identity "sip:RedmondAudioTest@litwareinc.com" -PrimaryLanguage $Null 

## 예제 3

예제 3에서는 조직에서 사용 중인 모든 오디오 테스트 서비스 대화 상대가 영어(미국)를 기본 언어로 사용하도록 구성합니다. 이 작업을 수행하기 위해 **Get-CsAudioTestServiceApplication** cmdlet을 매개 변수 없이 호출하여 오디오 테스트 서비스 대화 상대 컬렉션을 반환합니다. 이 컬렉션은 컬렉션에 있는 각 대화 상대의 PrimaryLanguage 속성에 영어(미국)(en-Us)를 할당하는 **Set-CsAudioTestServiceApplication**에 파이프됩니다.

    Get-CsAudioTestServiceApplication | Set-CsAudioTestServiceApplication -PrimaryLanguage "en-US"

## 자세한 정보

Lync Server 사용자는 오디오 테스트 서비스를 사용하여 음성 통화를 시작하기 전에 음성 연결을 테스트할 수 있습니다. 이렇게 하려면 Lync 옵션 대화 상자의 오디오 장치 탭에 있는 통화 품질 확인 단추를 클릭합니다. 사용자가 이 단추를 클릭하면 자동화된 오디오 테스트 서비스와 통화가 이루어집니다. 통화에 대한 응답이 제공되고 간단한 안내 메시지가 재생된 후 발신자에게 10초 이내의 간단한 메시지를 녹음하라는 안내가 나옵니다. 메시지를 녹음하고 나면 발신자가 현재 연결을 통해 해당 메시지를 들을 수 있도록 녹음된 메시지가 재생됩니다.

오디오 테스트 서비스는 Active Directory 연락처 개체에 부분적으로 의존합니다. 이러한 개체는 Audio Bot를 설치하면 자동으로 만들어집니다. 이러한 개체를 수동으로 만들 수 있는 방법은 없습니다. 그러나 관리자는 **Get-CsAudioTestServiceApplication** cmdlet을 사용하여 조직에서 현재 사용되고 있는 다양한 테스트 서비스 연락처에 대한 정보를 검색할 수 있습니다. 관리자는 또한 **Set-CsAudioTestServiceApplication** cmdlet을 사용하여 이러한 연락처의 속성을 수정할 수 있습니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsAudioTestServiceApplication** cmdlet을 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsAudioTestServiceApplication"}

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
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>수정할 오디오 테스트 서비스 대화 상대의 SIP 주소입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>DisplayName</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>대화 상대 개체의 Active Directory 표시 이름입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>DisplayNumber</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>DisplayNumber는 유효한 속성이기는 하지만 오디오 테스트 서비스에서 실제로 사용되지는 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Enabled</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>대화 상대 개체가 Lync Server에 대해 활성화되었는지 여부를 나타냅니다. 이 값을 False($False)로 설정하면 대화 상대가 Lync Server에 더 이상 로그온할 수 없으며, 이 값을 True($True)로 설정하면 대화 상대의 로그온 권한이 다시 활성화됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnabledForFederation</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>페더레이션 도메인의 사용자가 이 대화 상대를 사용할 수 있는지 여부를 나타냅니다. False로 설정하면 조직 내부의 사용자만 대화 상대에 액세스할 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnterpriseVoiceEnabled</em></p></td>
<td><p>선택</p></td>
<td><p>System.Boolean</p></td>
<td><p>대화 상대 개체가 Microsoft VoIP(Voice over Internet Protocol)인 Enterprise Voice를 사용하도록 설정되었는지 여부를 나타냅니다. Enterprise Voice를 사용하면 사용자는 표준 전화 네트워크가 아니라 인터넷을 사용하여 전화를 걸 수 있습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ExchangeArchivingPolicy</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.ExchangeArchivingPolicyOptionsEnum</p></td>
<td><p>연락처의 메신저 대화 세션이 보관되는 위치를 나타냅니다. 사용 가능한 값은 다음과 같습니다.</p>
<p>* Uninitialized</p>
<p>* UseLyncArchivingPolicy</p>
<p>* ArchivingToExchange</p>
<p>* NoArchiving</p></td>
</tr>
<tr class="odd">
<td><p><em>LineURI</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>LineUri는 유효한 속성이기는 하지만 오디오 테스트 서비스에서 실제로 사용되지는 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PassThru</em></p></td>
<td><p>선택</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>정책을 할당할 사용자를 나타내는 사용자 개체를 파이프라인을 통해 전달하는 데 사용됩니다. 기본적으로 <strong>Set-CsAudioTestServiceApplication</strong> cmdlet은 파이프라인을 통해 개체를 전달하지 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>PrimaryLanguage</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>오디오 테스트 서비스에 사용되는 기본 언어입니다. 이 언어는 허용되는 언어 코드 중 하나를 사용하여 구성해야 합니다(예: 미국 영어의 경우 en-US, 프랑스어의 경우 fr-FR 등). 사용 가능한 언어 코드 목록을 반환하려면 Windows PowerShell 프롬프트에 다음 명령을 입력합니다.</p>
<p>Get-CsDialInConferencingLanguageList | Select-Object -ExpandProperty Languages</p></td>
</tr>
<tr class="even">
<td><p><em>SecondaryLanguages</em></p></td>
<td><p>선택</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.MultiValuedProperty</p></td>
<td><p>SecondaryLanguages는 유효한 속성이기는 하지만 오디오 테스트 서비스에서 실제로 사용되지는 않습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SipAddress</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>이 매개 변수는 현재 사용되지 않습니다. Set-CsAudioTestServiceApplication을 사용하여 SIP 주소를 변경할 수 없습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Type</em></p></td>
<td><p>선택</p></td>
<td><p>System.String</p></td>
<td><p>배포할 테스트 대화 상대의 유형을 나타냅니다. 기본적으로 대화 상대는 &quot;자동&quot;으로 나열되는데, 이는 대화 상대가 발신자와 상호 작용할 수 있음을 의미합니다.</p></td>
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

**Set-CsAudioTestServiceApplication** cmdlet은 Microsoft.Rtc.Management.ADConnect.Schema.OCSADApplicationContact 개체의 파이프라인된 인스턴스를 허용합니다.

## 반환 형식

**Set-CsAudioTestServiceApplication** cmdlet은 개체나 값을 반환하지 않습니다.

## 참고 항목

#### 기타 리소스

[Get-CsAudioTestServiceApplication](get-csaudiotestserviceapplication.md)

