---
title: Lync Server 2013에서 트렁크 구성 정보 보기
TOCTitle: Lync Server 2013에서 트렁크 구성 정보 보기
ms:assetid: ebe10e14-08c2-4797-9254-9ed89516d5cd
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721927(v=OCS.15)
ms:contentKeyID: 49886040
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 트렁크 구성 정보 보기

 

_**마지막으로 수정된 항목:** 2013-02-22_

SIP 트렁크 구성 설정은 서비스 공급자의 SBC(Session Border Controller), IP-PBX(IP-Public Branch Exchange), PSTN(공중 전화망) 게이트웨이 또는 중재 서버 간 관계 및 기능을 정의합니다. 이러한 설정은 다음을 지정할 때 해당 기능을 수행합니다.

  - 미디어 바이패스를 트렁크에서 사용할 수 있는지 여부

  - RTCP(실시간 전송 제어 프로토콜) 패킷이 전송되는 조건

  - 각 트렁크에서 SRTP(Secure Real-Time Protocol) 암호가 필요한지 여부

Microsoft Lync Server 2013을 설치할 경우 전역 SIP 트렁크 구성 설정 모음이 만들어집니다. 또한 관리자는 사이트 수준이나 서비스 수준(PSTN 게이트웨이 서비스에만 해당)에서 사용자 지정 설정 모음을 만들 수 있습니다.

## Lync Server 제어판을 사용하여 SIP 트렁크 구성 정보 보기

1.  Lync Server 제어판에서 **음성 라우팅**, **트렁크 구성**을 차례로 클릭합니다.

2.  **트렁크 구성** 탭에는 모든 트렁크 구성 설정 모음 목록이 표시됩니다. 각 모음마다 **이름**, **범위**, **상태** 및 **미디어 바이패스** 속성의 값이 모음과 연결된 **PSTN 사용**, **호출 번호 규칙** 및 **걸린 번호 규칙** 수와 함께 표시됩니다. 트렁크 구성 설정 모음에 대한 자세한 정보를 보려면 **편집**을 클릭하고 **자세한 정보 표시**를 클릭합니다. 한 번에 한 트렁크 구성 설정 모음에 대한 세부 정보만 볼 수 있습니다.

## Lync Server PowerShell Cmdlet을 사용하여 SIP 트렁크 구성 정보 보기

SIP 트렁크 구성 설정은 Lync Server PowerShell과 Get-CsTrunkConfiguration cmdlet을 사용하여 볼 수도 있습니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 원격 세션 Windows PowerShell에서 실행할 수 있습니다. 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876))를 참조하세요.

## SIP 트렁크 구성 정보 보기

  - 모든 SIP 트렁크 구성 설정에 대한 정보를 보려면 Lync Server 관리 셸에서 다음 명령을 입력하고 Enter 키를 누릅니다.
    
        Get-CsTrunkConfiguration
    
    그러면 다음과 같은 정보가 반환됩니다.
    
        Identity                                  : Global
        OutboundTranslationRulesList              : {}
        SipResponseCodeTranslationRulesList       : {}
        OutboundCallingNumberTranslationRulesList : {}
        PstnUsages                                : {}
        Description                               :
        ConcentratedTopology                      : True
        EnableBypass                              : False
        EnableMobileTrunkSupport                  : False
        EnableReferSupport                        : True
        EnableSessionTimer                        : False
        EnableSignalBoost                         : False
        MaxEarlyDialogs                           : 20
        RemovePlusFromUri                         : False
        RTCPActiveCalls                           : True
        RTCPCallsOnHold                           : True
        SRTPMode                                  : Required
        EnablePIDFLOSupport                       : False
        EnableRTPLatching                         : False
        EnableOnlineVoice                         : False
        ForwardCallHistory                        : False
        Enable3pccRefer                           : False
        ForwardPAI                                : False
        EnableFastFailoverTimer                   : True

자세한 내용은 [Get-CsTrunkConfiguration](get-cstrunkconfiguration.md) cmdlet 관련 도움말 항목을 참조하십시오.

