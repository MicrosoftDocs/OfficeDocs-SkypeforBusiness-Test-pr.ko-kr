---
title: 'Lync Server 2013: SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버에 사용자 두기'
TOCTitle: SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버에 사용자 두기
ms:assetid: faf1ebb9-6d7d-4a58-8ff7-801b7b31d3ba
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413066(v=OCS.15)
ms:contentKeyID: 49305598
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버에 사용자 두기

 

_**마지막으로 수정된 항목:** 2014-12-10_

SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버에 사용자를 두는 프로세스는 프런트 엔드 풀 풀에 사용자를 호밍하는 프로세스와 비슷합니다. 중앙 사이트에서 SBA(Survivable Branch Appliance) 또는 지속 가능 분기 서버 절차를 수행합니다.

## Survivable Branch Appliance 또는 지속 가능 분기 서버에 사용자를 두려면

1.  지속 가능 분기 서버 또는 지속 가능 분기 서버로 사용자를 이동하기 전에 Lync Server 관리 셸을 열고 다음 작업을 모두 수행합니다.
    
      - **Test-CsPstnOutboundCall** cmdlet을 실행하여 지속 가능 분기 서버이 실행되고 있으며 PSTN(공중 전화망) 연결이 구성되어 있는지 확인합니다. PSTN 게이트웨이 속성을 수정해야 할 경우 **Set-CsPstnGateway** cmdlet을 사용합니다.
    
      - **Get-CsVoicePolicy** cmdlet을 실행하여 지속 가능 분기 서버에 둘 사용자에게 적합한 VoIP 라우팅 정책이 있는지 확인합니다. VoIP 정책을 수정해야 할 경우 **Set-CsVoicePolicy** cmdlet을 사용합니다.
    
      - **Get-CsVoicemailReroutingConfiguration** cmdlet을 사용하여 음성 사서함 라우팅 설정이 구성되었는지 확인합니다. 음성 사서함 라우팅 설정을 수정해야 할 경우 **Set-CsVoicemailReroutingConfiguration** cmdlet을 사용합니다.

2.  Lync Server 관리 셸에서 **Move-CsUser** cmdlet을 실행하여 사용자를 이동합니다.


> [!NOTE]
> Lync Server 제어판을 사용하여 필수 구성 요소를 확인하고 Survivable Branch Appliance 또는 지속 가능 분기 서버에 사용자를 둘 수도 있습니다.



## 참고 항목

#### 기타 리소스

[Test-CsPstnOutboundCall](test-cspstnoutboundcall.md)  
[Get-CsVoicePolicy](get-csvoicepolicy.md)  
[Get-CsVoicemailReroutingConfiguration](get-csvoicemailreroutingconfiguration.md)  
[Move-CsUser](move-csuser.md)

