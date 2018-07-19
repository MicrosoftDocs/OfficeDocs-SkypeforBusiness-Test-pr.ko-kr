---
title: Lync Server 2013에서 E9-1-1 음성 경로 구성
TOCTitle: Lync Server 2013에서 E9-1-1 음성 경로 구성
ms:assetid: 6933b840-0e7b-4509-ae43-bc9065677547
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398496(v=OCS.15)
ms:contentKeyID: 49303919
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 E9-1-1 음성 경로 구성

 

_**마지막으로 수정된 항목:** 2012-09-17_

E9-1-1을 배포하려면 먼저 응급 통화 음성 경로를 구성해야 합니다. 음성 경로를 만드는 방법에 대한 자세한 내용은 [Lync Server 2013에서 음성 경로 만들기](lync-server-2013-create-a-voice-route.md)을 참조하십시오. 예를 들어 배포에 기본 SIP 트렁크와 보조 SIP 트렁크가 포함된 경우 두 개 이상의 경로를 정의할 수 있습니다.


> [!NOTE]
> E9-1-1 INVITE에 위치 정보를 포함하려면 게이트웨이를 통해 긴급 통화를 라우팅할 수 있도록 E9-1-1 서비스 공급자에 연결되는 SIP 트렁크를 구성해야 합니다. 이렇게 하려면 <STRONG>set-cstrunkconfiguration</STRONG> cmdlet에서 EnablePIDFLOSupport 플래그를 True로 설정합니다. EnablePIDFLOSupport의 기본값은 False입니다. 예: <CODE>set-cstrunkconfiguration Service:PstnGateway:192.168.0.241 -EnablePIDFLOSupport $true.</CODE><BR>대체 PSTN(공중 전화망) 게이트웨이 및 ELIN(Emergency Location Identification Number) 게이트웨이에 대한 수신 위치를 사용하도록 설정할 필요는 없습니다.



음성 경로를 사용하는 방법에 대한 자세한 내용은 Lync Server 관리 셸 설명서에서 다음 cmdlet을 참조하십시오.

  - **Set-CsPstnUsage**

  - **Get-CsPstnUsage**

  - **New-CsVoiceRoute**

  - **Get-CsVoiceRoute**

  - **Set-CsVoiceRoute**

  - **Remove-CsVoiceRoute**

## E9-1-1 음성 경로를 구성하려면

1.  RTCUniversalServerAdmins 그룹의 구성원이거나 CsVoiceAdministrator 관리 역할의 구성원인 계정으로 컴퓨터에 로그온합니다.

2.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

3.  다음 cmdlet을 실행하여 새 PSTN 사용 레코드를 만듭니다.
    
    이 이름은 위치 정책에서 **PSTN** 설정에 사용하는 것과 동일한 이름이어야 합니다. 배포에 여러 개의 전화 사용 레코드가 포함되더라도 다음 예에서는 사용 가능한 현재 PSTN 사용 목록에 "긴급 사용"을 추가합니다. 자세한 내용은 [Lync Server 2013에서 통화 기능 및 권한을 부여하도록 음성 정책 및 PSTN 사용 레코드 구성](lync-server-2013-configuring-voice-policies-and-pstn-usage-records-to-authorize-calling-features-and-privileges.md)을 참조하십시오.
    
        Set-CsPstnUsage -Usage @{add='EmergencyUsage'}

4.  다음 cmdlet을 실행해서 이전 단계에서 만든 PSTN 사용 레코드를 사용하여 새 음성 경로를 만듭니다.
    
    숫자 패턴은 위치 정책의 **긴급 전화 걸기 문자열** 설정에 사용된 것과 동일한 번호 패턴이어야 합니다. Lync에서는 긴급 통화에 "+"를 추가하므로 "+" 기호가 필요합니다. "Co1-pstngateway-1"은 E9-1-1 서비스 공급자에 대한 SIP 트렁크 서비스 ID 또는 ELIN 게이트웨이 서비스 ID입니다. 다음 예에서는 음성 경로의 이름으로 "EmergencyRoute"가 지정됩니다.
    
        New-CsVoiceRoute -Name "EmergencyRoute" -NumberPattern "^\+911$" -PstnUsages @{add="EmergencyUsage"} -PstnGatewayList @{add="co1-pstngateway-1"}

5.  선택적으로 SIP 트렁크 연결을 위해서는 다음 cmdlet을 실행하여 E9-1-1 서비스 공급자의 SIP 트렁크를 통해 처리되지 않는 통화용으로 로컬 경로를 만드는 것이 좋습니다. E9-1-1 서비스 공급자에 연결할 수 없는 경우 이 경로가 사용됩니다.
    
    다음 예제에서는 사용자의 음성 정책에 포함된 사용이 "Local"이라고 가정합니다.
    
        New-CsVoiceRoute -Name "LocalEmergencyRoute" -NumberPattern "^\+911$" -PstnUsages @{add="Local"} -PstnGatewayList @{add="co1-pstngateway-2"}

