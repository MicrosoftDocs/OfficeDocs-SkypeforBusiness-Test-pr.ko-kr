---
title: 'Lync Server 2013: 음성 메일 다시 라우팅 설정 구성'
TOCTitle: 음성 메일 다시 라우팅 설정 구성
ms:assetid: 7ab6be28-eabb-4a79-a796-648887d71b83
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398606(v=OCS.15)
ms:contentKeyID: 49304129
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 음성 메일 다시 라우팅 설정 구성

 

_**마지막으로 수정된 항목:** 2012-10-18_

SBA(Survivable Branch Appliance) 및 지속 가능 분기 서버는 Exchange 통합 메시징(UM)이 중앙 사이트에 설치되어 있고 Exchange UM 메시지 AA(자동 전화 교환)가 배포되어 있는 경우 WAN이 중단된 동안 분기 사용자에게 음성 메일 지속 가능성을 제공할 수 있습니다. Exchange 관리자가 메시지만 수락하도록 AA를 구성하여 사용자나 교환원에게로 전환하는 등의 다른 일반 기능은 사용하지 않도록 설정하는 것이 좋습니다. 또는 일반 AA를 사용하거나 통화를 라우팅하도록 사용자 지정된 AA를 사용할 수 있습니다.

자세한 내용은 계획 설명서의 [Lync Server 2013에 대한 분기 사이트 복구 요구 사항](lync-server-2013-branch-site-resiliency-requirements.md)에서 "음성 메일 지속 가능성 준비" 섹션을 참조하십시오.

## 음성 메일 지속 가능성을 구성하려면

1.  Exchange 관리자에게 메시지만 수락하도록 AA를 구성하도록 요청합니다(Exchange Shell에서 다음 cmdlet 사용): **Set-UMAutoAttendant \<AA name\> -CallSomeoneEnabled $false**. 메시지 남겨 두기를 허용하도록 지정하는 매개 변수( *SendVoiceMsgEnabled*)는 기본적으로 true입니다.

2.  Lync Server 관리 셸에서 **New-CSVoiceMailReroutingConfiguration** cmdlet을 사용하여 AA 전화 번호를 SBA( SBA(Survivable Branch Appliance)) 또는 지속 가능 분기 서버의 음성 메일 다시 라우팅 구성에 있는 Exchange UM 자동 전화 교환 전화 번호로 설정합니다.
    

    > [!NOTE]
    > 나중에 음성 메일 다시 라우팅 설정을 수정해야 하는 경우 <STRONG>Set-CsVoiceMailReRoutingConfiguration</STRONG> cmdlet을 사용하여 수정합니다. 자세한 내용은 Shell 도움말 항목의 <STRONG>New-</STRONG> 및 <STRONG>Set-CSVoiceMailReroutingConfiguration</STRONG>을 참조하십시오.



3.  분기 사용자의 Exchange UM 다이얼 플랜에 해당하는 Exchange UM 구독자 액세스 번호를 SBA( SBA(Survivable Branch Appliance)) 또는 지속 가능 분기 서버의 음성 메일 다시 라우팅 구성에 있는 Exchange UM 구독자 액세스 번호로 설정합니다.
    

    > [!NOTE]
    > WAN이 중단된 동안 음성 메일 가져오기 기능에 대한 액세스가 필요한 모든 분기 사용자에 연결된 다이얼 플랜이 단 하나만 있도록 Exchange UM 사용자의 다이얼 플랜을 구성합니다.



SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버의 **다음 단계** : [Lync Server 2013의 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버에 사용자 두기](lync-server-2013-home-users-on-a-survivable-branch-appliance-or-server.md).

