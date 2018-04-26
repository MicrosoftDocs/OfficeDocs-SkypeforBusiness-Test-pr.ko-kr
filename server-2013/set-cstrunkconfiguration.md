---
title: Set-CsTrunkConfiguration
TOCTitle: Set-CsTrunkConfiguration
ms:assetid: 18152388-68de-4a6b-b5a1-248534ecde72
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398238(v=OCS.15)
ms:contentKeyID: 49302940
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsTrunkConfiguration

 

_**마지막으로 수정된 항목:** 2015-02-27_

PSTN(공중 전화망) 게이트웨이, IP-PBX(Public Branch Exchange) 또는 SBC(세션 경계 컨트롤러)와 같은 서비스 공급자 쪽 트렁크 피어 엔터티에 대한 설정을 설명하는 기존 트렁크 구성을 수정합니다. 이 cmdlet은 Lync Server 2010에서 도입되었습니다.

## 구문

    Set-CsTrunkConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsTrunkConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-ConcentratedTopology <$true | $false>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-Enable3pccRefer <$true | $false>] [-EnableBypass <$true | $false>] [-EnableFastFailoverTimer <$true | $false>] [-EnableLocationRestriction <$true | $false>] [-EnableMobileTrunkSupport <$true | $false>] [-EnableOnlineVoice <$true | $false>] [-EnablePIDFLOSupport <$true | $false>] [-EnableReferSupport <$true | $false>] [-EnableRTPLatching <$true | $false>] [-EnableSessionTimer <$true | $false>] [-EnableSignalBoost <$true | $false>] [-Force <SwitchParameter>] [-ForwardCallHistory <$true | $false>] [-ForwardPAI <$true | $false>] [-MaxEarlyDialogs <UInt32>] [-NetworkSiteID <String>] [-OutboundCallingNumberTranslationRulesList <PSListModifier>] [-OutboundTranslationRulesList <PSListModifier>] [-PstnUsages <PSListModifier>] [-RemovePlusFromUri <$true | $false>] [-RTCPActiveCalls <$true | $false>] [-RTCPCallsOnHold <$true | $false>] [-SipResponseCodeTranslationRulesList <PSListModifier>] [-SRTPMode <Required | Optional | NotSupported>] [-WhatIf [<SwitchParameter>]]

## 예제

## 예제 1

이 예제에서는 ID가 site:Redmond인 트렁크 구성을 미디어 바이패스를 사용하도록 수정합니다. 미디어 우회를 사용하도록 설정하려면 EnableBypass 매개 변수에 $True 값을 할당합니다. 이 구성의 나머지 속성은 기존 값을 유지합니다.

    Set-CsTrunkConfiguration -Identity site:Redmond -EnableBypass $True

## 예제 2

이 예제에서는 ID가 site:Redmond인 트렁크 구성에 대해 정의된 아웃바운드 변환 규칙을 수정합니다. 그러나 이러한 변경 작업을 연습하기 위해 **Set-CsTrunkConfiguration** cmdlet을 실제로 호출하지는 마십시오. **Set-CsOutboundTranslationRule** cmdlet을 사용하여 변경하면 ID가 아웃바운드 변환 규칙 ID의 범위 부분과 일치하는 트렁크 구성에 변경 내용이 자동으로 적용됩니다.

    Set-CsOutboundTranslationRule -Identity site:Redmond/OTR1 -Translation '$1'

## 예제 3

예제 3에서는 사이트 범위에서 정의된 모든 트렁크 구성의 SRTPMode를 Optional로 설정합니다. 명령의 첫 번째 부분은 Filter 매개 변수를 사용하는 **Get-CsTrunkConfiguration** cmdlet을 호출하여 ID가 site:로 시작하는 모든 트렁크 구성, 즉 사이트 수준에서 정의된 모든 트렁크 구성을 검색합니다. 이 구성 컬렉션은 각 구성의 SRTPMode 속성을 Optional로 설정하는 **Set-CsTrunkConfiguration** cmdlet에 파이프됩니다.

    Get-CsTrunkConfiguration -Filter site:* | Set-CsTrunkConfiguration -SRTPMode "Optional"

## 예제 4

예제 4에서는 PIDF-LO 지원을 설정하도록 ID가 site:Redmond인 트렁크 구성을 수정합니다. 기본적으로 EnablePIDFLOSupport 매개 변수는 False입니다. 이 예에서는 긴급 통화에 대한 위치 지원을 설정하도록 값을 True로 설정했습니다. 아웃바운드 라우팅 응용 프로그램이 위치 정보를 트렁크로 전송하도록 하려면 EnablePIDFLOSupport를 True로 설정해야 합니다.

    Set-CsTrunkConfiguration -Identity site:Redmond -EnablePIDFLOSupport $True

## 자세한 정보

이 cmdlet을 사용하여 PSTN 게이트웨이 엔터티에 적용되는 트렁크 구성을 수정할 수 있습니다. 각 구성은 PSTN 게이트웨이, IP-PBX 또는 SBC와 같은 서비스 공급자 쪽 트렁크 피어 엔터티에 대한 특정 설정을 포함합니다. 이러한 설정은 이 트렁크에서 미디어 우회를 사용하도록 설정할지 여부, 특정 상황에서 RTCP(Real-time Transmission Control Protocol) 패킷을 보낼지 여부, SRTP(Secure Real-Time Protocol) 암호화를 요구할지 여부 등을 구성합니다.

이 cmdlet을 실행할 수 있는 사용자: 기본적으로 RTCUniversalServerAdmins 그룹의 구성원은 **Set-CsTrunkConfiguration** cmdlet을 로컬로 실행할 수 있습니다. 사용자가 직접 만든 사용자 지정 RBAC(역할 기반 액세스 제어) 역할을 포함하여 이 cmdlet이 할당된 모든 RBAC 역할의 목록을 반환하려면 Windows PowerShell 프롬프트에서 다음 명령을 실행합니다.

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsTrunkConfiguration"}

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
<td><p><em>ConcentratedTopology</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>이 매개 변수 값은 알려진 미디어 종료 지점이 있는지 확인합니다. 알려진 미디어 종료 지점의 예로는 미디어 종료가 신호 종료의 IP와 동일한 PSTN 게이트웨이가 있습니다. 트렁크에 알려진 미디어 종료 지점이 없는 경우에는 이 값을 False로 설정합니다.</p>
<p>기본값: True</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실행하기 전에 확인 메시지를 표시합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Description</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>트렁크 구성의 용도를 설명하는 문자열입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Enable3pccRefer</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>3pcc 프로토콜을 사용하여 전송된 통화가 호스트된 사이트를 바이패스하도록 허용할 수 있는지 여부를 나타냅니다. 3pcc는 &quot;제3자 제어&quot;라고도 하며, 제3자(예: A 사용자로부터 B 사용자에게 전화를 거는 교환원)를 통해 발신자 쌍을 연결하는 경우에 적용됩니다. REFER 메서드는 발신자가 제공한 정보를 사용하여 수신자가 제3자에 연결해야 함을 나타내는 표준 SIP 메서드입니다. 기본값은 False($False)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableBypass</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>이 매개 변수 값은 이 트렁크에 대해 미디어 우회를 사용하도록 설정할지 지정합니다. 우회를 사용하도록 설정하려면 이 값을 True로 설정합니다. 미디어 우회가 제대로 작동하려면 다음과 같은 특정 기능을 PSTN 게이트웨이, SBC 및 PBX에서 지원해야 합니다.</p>
<p>- 분기된 응답을 Invite로 수신할 수 있어야 합니다.</p>
<p>- Lync Server 클라이언트 및 미디어 종료 지점에서 중재 서버를 거치지 않고 직접 통신할 수 있어야 합니다.</p>
<p>- 게이트웨이 서브넷이 클라이언트의 서브넷과 동일한 사이트에 있는 것으로 정의되어 있어야 합니다. 다른 사이트에 있는 경우 사이트가 대역폭이 제한된 WAN 링크로 분리되지 않아야 합니다.</p>
<p>다음과 같은 경우에만 미디어 우회를 사용하도록 설정할 수 있습니다.</p>
<p>- ConcentratedTopology 매개 변수를 True로 설정한 경우</p>
<p>- EnableReferSupport 매개 변수를 False로 설정하고 RTCPActiveCalls 및 RTCPCallsOnHold를 False로 설정하거나 EnableReferSupport를 True로 설정한 경우</p>
<p>EnableBypass가 True이고 EnableReferSupport가 False이면 이후에 전송되는 우회 통화는 우회하지 않게 됩니다.</p>
<p>미디어 우회가 특정 트렁크에 대해 작동하려면 해당 트렁크뿐만 아니라 전역적으로 사용하도록 설정되어야 합니다. 미디어 바이패스를 전역적으로 사용하도록 설정하려면 <strong>New-CsNetworkMediaBypassConfiguration</strong> cmdlet을 사용합니다.</p>
<p>기본값: False</p></td>
</tr>
<tr class="even">
<td><p><em>EnableFastFailoverTimer</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>True로 설정하면 10초 이내에 게이트웨이에서 응답하지 않은 아웃바운드 통화가 사용 가능한 다음 트렁크로 라우팅됩니다. 추가 트렁크가 없으면 통화가 자동으로 끊어집니다. 네트워크 속도와 게이트웨이 응답 속도가 느린 조직에서는 이로 인해 통화가 불필요하게 끊어질 수 있습니다.</p>
<p>기본값은 True입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableLocationRestriction</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>True로 설정하면 지정한 SIP 트렁크 구성 설정 컬렉션에 의해 관리되는 SIP 트렁크를 경유하는 통화에 대해 위치 기반 음성 라우팅이 사용하도록 설정됩니다. 위치 기반 음성 라우팅을 사용할 경우 통화 라우팅 시 전화를 거는 사용자와 전화를 받는 사용자의 위치가 모두 고려됩니다. 이 속성을 True로 설정하면 NetworkSiteId 속성도 설정해야 합니다. 기본값은 False입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableMobileTrunkSupport</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>서비스 공급자가 이동 통신 회사인지 여부를 정의합니다.</p>
<p>기본값: False</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableOnlineVoice</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>SIP 트렁크가 온라인 음성을 지원하는지 여부를 나타냅니다. 온라인 음성을 사용하는 경우 사용자는 온-프레미스 Lync Server 계정을 소유하지만 음성 메일은 비즈니스용 Skype Online을 통해 호스트됩니다. 기본값은 False($False)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>EnablePIDFLOSupport</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>PIDF-LO(Presence Information Data Format Location Object)가 포함된 응급 통화를 지정된 게이트웨이를 통해 경로 지정할지 여부를 정의합니다. 응급 통화를 특정 응급 서비스 공급자로 경로 지정하려면 이 매개 변수를 True로 설정합니다. 이 경우 전화를 통해 위치가 전송됩니다.</p>
<p>기본값: False</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableReferSupport</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>이 트렁크가 중재 서버에서 보낸 Refer 요청의 수신을 지원하는지 정의합니다.</p>
<p>다음과 같은 경우에만 미디어 우회를 사용하도록 설정할 수 있습니다.</p>
<p>- ConcentratedTopology 매개 변수를 True로 설정한 경우</p>
<p>- EnableReferSupport 매개 변수를 False로 설정하고 RTCPActiveCalls 및 RTCPCallsOnHold를 False로 설정하거나 EnableReferSupport를 True로 설정한 경우</p>
<p>EnableBypass가 True이고 EnableReferSupport가 False이면 이후에 전송되는 우회 통화는 우회하지 않게 됩니다.</p>
<p>기본값: True</p></td>
</tr>
<tr class="even">
<td><p><em>EnableRTPLatching</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>SIP 트렁크가 RTP 래치를 지원하는지 여부를 나타냅니다. RTP 래치는 NAT(Network Address Translator) 장치 또는 방화벽을 통한 RTP/RTCP 연결을 설정하는 기술입니다. 기본값은 False($False)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableSessionTimer</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>세션 타이머 사용 여부를 지정합니다. 세션 타이머는 특정 세션이 여전히 활성 상태인지 여부를 확인하는 데 사용됩니다.</p>
<p>이 매개 변수가 False로 설정된 경우에도 원격 연결에 활성화된 세션 타이머가 있으면 세션 타이머를 적용할 수 있습니다. 이 경우 중재 서버는 원격 엔터티에서 보낸 세션 타이머 프로브에 응답합니다.</p>
<p>기본값: False</p></td>
</tr>
<tr class="even">
<td><p><em>EnableSignalBoost</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>이 매개 변수를 True로 설정하면 서비스 공급자 쪽의 PSTN 게이트웨이, IP-PBX 또는 SBC가 중재 서버 또는 Lync Server 클라이언트로 전송되는 음성 스트림의 오디오 볼륨을 증폭시킵니다. 이 값이 False로 설정된 경우에는 중재 서버(우회하지 않는 통화의 경우) 또는 Lync Server 클라이언트(우회 통화의 경우)에서 오디오가 증폭됩니다.</p>
<p>기본값: False</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>변경하기 전에 표시되는 확인 메시지를 표시하지 않습니다.</p></td>
</tr>
<tr class="even">
<td><p><em>ForwardCallHistory</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>트렁크를 통해 통화 기록 정보를 전달할지 여부를 나타냅니다. 기본값은 False($False)입니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>ForwardPAI</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>PAI(P-Asserted-Identity) 헤더를 통화와 함께 전달할지 여부를 나타냅니다. PAI 헤더를 사용하면 발신자 번호를 확인할 수 있습니다. 기본값은 False($False)입니다.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>선택</p></td>
<td><p>XdsIdentity</p></td>
<td><p>트렁크 구성 범위를 포함하는 고유 식별자입니다. 트렁크 구성은 전역 범위, 사이트 범위 또는 PSTN 게이트웨이 서비스에 대한 서비스 범위에 적용될 수 있습니다. site:Redmond(사이트의 경우) 또는 PstnGateway:Redmond.litwareinc.com(서비스의 경우)을 예로 들 수 있습니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>선택</p></td>
<td><p>트렁크 구성</p></td>
<td><p>개별 매개 변수 값을 설정하는 대신 cmdlet에 개체에 대한 참조를 전달할 수 있습니다.</p>
<p>이 매개 변수에는 <strong>Get-CsTrunkConfiguration</strong> cmdlet을 호출하여 검색할 수 있는 Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TrunkConfiguration 개체 유형이 필요합니다.</p></td>
</tr>
<tr class="even">
<td><p><em>MaxEarlyDialogs</em></p></td>
<td><p>선택</p></td>
<td><p>UInt32</p></td>
<td><p>서비스 공급자 쪽 PSTN 게이트웨이, IP-PBX 또는 SBC가 Invite로 수신하여 중재 서버로 보낼 수 있는 분기 응답의 최대 개수입니다.</p>
<p>기본값: 20</p></td>
</tr>
<tr class="odd">
<td><p><em>NetworkSiteID</em></p></td>
<td><p>선택</p></td>
<td><p>문자열</p></td>
<td><p>트렁크 구성 설정 컬렉션과 연결된 네트워크 사이트의 사이트 ID입니다. EnableLocationRestriction 속성을 True로 설정하면 지정한 사이트에 대해 구성된 설정을 사용하여 이 트렁크를 경유하는 위치 기반 음성 라우팅이 관리됩니다.</p>
<p>Get-CsNetworkSite | Select NetworkSiteID</p></td>
</tr>
<tr class="even">
<td><p><em>OutboundCallingNumberTranslationRulesList</em></p></td>
<td><p>선택</p></td>
<td><p>PS 목록 한정자</p></td>
<td><p>트렁크에 할당된 아웃바운드 호출 번호 변환 규칙 컬렉션입니다. 다음 명령을 실행하여 사용 가능한 규칙에 대한 정보를 검색할 수 있습니다.</p>
<p>Get-CsOutboundCallingNumberTranslationRule</p></td>
</tr>
<tr class="odd">
<td><p><em>OutboundTranslationRulesList</em></p></td>
<td><p>선택</p></td>
<td><p>PS 목록 한정자</p></td>
<td><p>아웃바운드 경로 지정에서 처리하는 통화(PBX 또는 PSTN 대상으로 경로 지정되는 통화)에 적용되는 전화 번호 변환 규칙 컬렉션입니다.</p>
<p>이 cmdlet을 사용하여 이 목록과 이러한 규칙을 직접 수정할 수 있지만 <strong>Set-CsOutboundTranslationRule</strong> cmdlet을 사용하여 아웃바운드 변환 규칙을 수정하는 것이 좋습니다. <strong>Set-CsOutboundTranslationRule</strong> cmdlet은 규칙을 수정하고 이러한 수정 사항은 트렁크 구성에 자동으로 반영됩니다. 새 아웃바운드 변환 규칙을 추가하여 트렁크 구성을 수정하려면 <strong>New-CsOutboundTranslationRule</strong> cmdlet을 호출합니다. 범위가 일치하는 트렁크 구성에 새 규칙이 추가됩니다.</p></td>
</tr>
<tr class="even">
<td><p><em>PstnUsages</em></p></td>
<td><p>선택</p></td>
<td><p>PS 목록 한정자</p></td>
<td><p>트렁크에 할당된 PSTN 사용 컬렉션입니다. 다음 명령을 실행하여 사용 가능한 사용에 대한 정보를 검색할 수 있습니다.</p>
<p>Get-CsPstnUsage</p></td>
</tr>
<tr class="odd">
<td><p><em>RemovePlusFromUri</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>이 매개 변수를 True로 설정하면 중재 서버가 URI(Uniform Resources Identifier)에서 앞에 오는 더하기 기호(+)를 제거한 후 서비스 공급자에게 URI를 전송합니다.</p>
<p>기본값: False</p></td>
</tr>
<tr class="even">
<td><p><em>RTCPActiveCalls</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>이 매개 변수는 서비스 공급자 쪽 PSTN 게이트웨이, IP-PBX 또는 SBC에서 활성 통화에 대해 RTCP 패킷을 전송할지 여부를 결정합니다. 여기서 활성 통화란 미디어가 하나 이상의 방향으로 흐르도록 허용되는 통화를 의미합니다. RTCPActiveCalls를 True로 설정하면 RTCP 패킷을 30초 이상 받지 않은 경우 중재 서버 또는 Lync Server 클라이언트에서 통화를 종료할 수 있습니다.</p>
<p>Lync Server 요소에서 활성 통화에 대해 수신된 RTCP 미디어를 확인하지 않도록 설정하면 연결이 끊긴 피어를 검색하는 중요한 안전 장치가 제거되므로 이 설정은 필요한 경우에만 수행해야 합니다.</p>
<p>기본값: True</p></td>
</tr>
<tr class="odd">
<td><p><em>RTCPCallsOnHold</em></p></td>
<td><p>선택</p></td>
<td><p>부울</p></td>
<td><p>이 매개 변수는 대기 상태에 놓여 있고 미디어 패킷이 어느 방향으로도 흐르지 않는 통화에 대해 트렁크를 통해 RTCP 패킷을 계속 전송할지 여부를 결정합니다. Lync Server 클라이언트 또는 트렁크에서 대기 음악을 사용하는 경우에는 통화가 활성 상태인 것으로 간주되며 이 속성이 무시됩니다. 이러한 상황에서는 RTCPActiveCalls 매개 변수를 사용해야 합니다.</p>
<p>Lync Server 요소에서 활성 통화에 대해 수신된 RTCP 미디어를 확인하지 않도록 설정하면 연결이 끊긴 피어를 검색하는 중요한 안전 장치가 제거되므로 이 설정은 필요한 경우에만 수행해야 합니다.</p>
<p>기본값: True</p></td>
</tr>
<tr class="even">
<td><p><em>SipResponseCodeTranslationRulesList</em></p></td>
<td><p>선택</p></td>
<td><p>PS 목록 한정자</p></td>
<td><p>서비스 공급자 쪽 PSTN 게이트웨이, IP-PBX 또는 SBC에서 받은 응답 코드에 적용되는 SIP 응답 코드 변환 규칙 목록입니다. 이러한 규칙을 통해 관리자는 값이 400에서 699 사이이고 트렁크를 통해 수신된 SIP 응답 코드를 Lync Server와 보다 일치하는 새 값에 매핑할 수 있습니다.</p>
<p>이 cmdlet을 사용하여 이 목록과 해당 규칙을 직접 만들 수 있지만 <strong>New-CsSipResponseCodeTranslationRule</strong> cmdlet을 호출하여 SIP 응답 코드 변환 규칙을 만드는 것이 좋습니다. 이 cmdlet은 규칙을 만들어 범위가 일치하는 트렁크 구성에 할당합니다.</p></td>
</tr>
<tr class="odd">
<td><p><em>SRTPMode</em></p></td>
<td><p>선택</p></td>
<td><p>SRTP모드</p></td>
<td><p>이 매개 변수 값에 따라 중재 서버와 서비스 공급자 쪽 PSTN 게이트웨이, IP-PBX 또는 SBC 간의 미디어 트래픽을 보호하는 SRTP에 대한 지원 수준이 결정됩니다. 미디어 우회의 경우 이 값은 미디어 구성의 EncryptionLevel 설정과 호환되어야 합니다. 미디어 구성은 <strong>New-CsMediaConfiguration</strong> cmdlet 및 <strong>Set-CsMediaConfiguration</strong> cmdlet을 사용하여 설정합니다.</p>
<p>유효한 값:</p>
<p>- Required: SRTP 암호화를 사용해야 합니다.</p>
<p>- Optional: 서비스 공급자가 지원하는 경우 SRTP가 사용됩니다.</p>
<p>- NotSupported: SRTP 암호화가 지원되지 않으므로 사용되지 않습니다.</p>
<p>참고: SRTPMode는 게이트웨이가 TLS(전송 계층 보안)를 사용하도록 구성된 경우에만 사용됩니다. 게이트웨이가 TCP(Transmission Control Protocol)를 전송 프로토콜로 사용하여 구성된 경우 SRTPMode는 내부적으로 NotSupported로 설정됩니다.</p>
<p>기본값: 필수</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>선택</p></td>
<td><p>스위치 매개 변수</p></td>
<td><p>명령을 실제로 실행하지 않고도 명령이 실행될 경우 발생할 수 있는 현상을 설명합니다.</p></td>
</tr>
</tbody>
</table>


## 입력 형식

Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TrunkConfiguration 개체입니다. 트렁크 구성 개체의 파이프라인된 입력을 허용합니다.

## 반환 형식

이 cmdlet은 값을 반환하지 않으며 Microsoft.Rtc.Management.WritableConfig.Settings.TrunkConfiguration.TrunkConfiguration 개체 유형을 수정합니다.

## 참고 항목

#### 기타 리소스

[New-CsTrunkConfiguration](new-cstrunkconfiguration.md)  
[Remove-CsTrunkConfiguration](remove-cstrunkconfiguration.md)  
[Get-CsTrunkConfiguration](get-cstrunkconfiguration.md)  
[Test-CsTrunkConfiguration](test-cstrunkconfiguration.md)  
[New-CsOutboundTranslationRule](new-csoutboundtranslationrule.md)  
[Set-CsOutboundTranslationRule](set-csoutboundtranslationrule.md)

