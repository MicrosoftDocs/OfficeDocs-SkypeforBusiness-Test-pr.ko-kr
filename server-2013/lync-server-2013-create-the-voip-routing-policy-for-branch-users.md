---
title: 'Lync Server 2013: 분기 사용자에 대한 VoIP 라우팅 정책 만들기'
TOCTitle: 분기 사용자에 대한 VoIP 라우팅 정책 만들기
ms:assetid: 10deca9f-f870-4a42-b25d-e4fc53108658
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398196(v=OCS.15)
ms:contentKeyID: 49302843
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 분기 사용자에 대한 VoIP 라우팅 정책 만들기

 

_**마지막으로 수정된 항목:** 2012-09-23_

분기 사이트의 사용자에 대해 별도의 VoIP(Voice Over IP) 정책을 만드는 것이 좋습니다. 이 정책은 SBA(Survivable Branch Appliance) 게이트웨이 또는 지속 가능 분기 서버 외부 게이트웨이에서 이동하는 경로와, 중앙 사이트의 게이트웨이에서 이동하는 백업 경로를 포함해야 합니다. 사용자가 등록된 위치( SBA(Survivable Branch Appliance)/ 지속 가능 분기 서버의 등록자 또는 중앙 사이트의 백업 등록자 클러스터)에 관계없이 사용자의 VoIP 정책이 항상 적용됩니다.

## 분기 사용자에 대한 VoIP 라우팅 정책을 구성하려면

1.  사용자 수준 다이얼 플랜을 만들어 분기 사용자에게 할당합니다. 작업 설명서에서 [Lync Server 2013에서 다이얼 플랜 만들기](lync-server-2013-create-a-dial-plan.md)을 참조하십시오.

2.  사이트 사용자의 전화 거는 방식에 해당하는 정규화 규칙을 할당합니다. SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버 사용자가 중앙 사이트의 백업 등록자 풀로 장애 조치(failover)되는 경우에는 동일한 다이얼 플랜이 적용됩니다. 작업 설명서에서 [Lync Server 2013에서 다이얼 플랜 만들기](lync-server-2013-create-a-dial-plan.md)을 참조하십시오.

3.  SBA(Survivable Branch Appliance) 게이트웨이 또는 지속 가능 분기 서버 외부 게이트웨이로부터 이동하는 음성 경로를 구성합니다. 작업 설명서에서 [Lync Server 2013에서 음성 경로 만들기](lync-server-2013-create-a-voice-route.md)을 참조하십시오.

4.  SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버 게이트웨이에서 중앙 사이트의 백업 등록자 풀(중재 서버와 함께 배치됨)을 가리키도록 백업 통화 경로를 설정합니다. SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버 공급업체 설명서를 참조하십시오.
    

    > [!NOTE]
    > 이 백업 통화 경로를 설정하면 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버가 유지 관리를 위해 다운되는 경우 등 사용할 수 없을 때 분기 사용자에 대한 인바운드 통화가 작동합니다. SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버의 등록자 및 중재 서버를 사용할 수 없는 경우 사용자가 중앙 사이트의 백업 등록자 풀에 등록되어 있으면 인바운드 통화를 사용자에게 계속 라우팅할 수 있습니다.



**다음 단계**: [Lync Server 2013에서 음성 메일 다시 라우팅 설정 구성](lync-server-2013-configure-voice-mail-rerouting-settings.md)

