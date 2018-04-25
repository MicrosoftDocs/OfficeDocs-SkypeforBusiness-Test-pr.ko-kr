---
title: Lync Server 2013으로 나머지 사용자 이동
TOCTitle: Lync Server 2013으로 나머지 사용자 이동
ms:assetid: 0eb990f0-f720-47a7-aaee-437fbd4c4c33
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ687968(v=OCS.15)
ms:contentKeyID: 49885647
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013으로 나머지 사용자 이동

 

_**마지막으로 수정된 항목:** 2012-09-26_

Lync Server 제어판 또는 Lync Server 관리 셸을 사용하여 새 Lync Server 2013 배포에 사용자를 이동할 수 있습니다. Lync Server 2013으로 효과적으로 전환하기 위해서는 몇 가지 요구 사항을 충족해야 합니다. 이 항목의 절차를 완료하기 위한 필수 구성 요소에 대한 자세한 내용은 [마이그레이션을 위한 클라이언트 구성](configure-clients-for-migration_1.md)을 참조하십시오. 사용자 이동 단계에 대한 자세한 내용은 [단계 6: 파일럿 풀로 사용자 이동](phase-6-move-users-to-the-pilot-pool.md)을 참조하십시오.


> [!IMPORTANT]
> Active Directory 사용자 및 컴퓨터 스냅인 또는 Microsoft Office Communications Server 2007 R2 관리 도구를 사용해서는 레거시 환경의 사용자를 Lync Server 2013으로 이동할 수 없습니다.




> [!IMPORTANT]
> <STRONG>Move-CsLegacyUser</STRONG> cmdlet을 사용하려면 사용자 이름의 형식이 올바른 형식이어야 하며 선행 또는 후행 공백이 없어야 합니다. 선행 또는 후행 공백이 포함된 경우 <STRONG>Move-CsLegacyUser</STRONG> cmdlet을 사용하여 사용자 계정을 이동할 수 없습니다.



사용자를 Lync Server 2013 풀로 이동할 때 사용자 데이터는 새 풀과 연결된 백 엔드 데이터베이스로 이동됩니다.


> [!IMPORTANT]
> 여기에는 레거시 사용자가 만든 활성 모임이 포함됩니다. 예를 들어 레거시 사용자가 <STRONG>내 모임</STRONG> 회의를 구성한 경우, 사용자를 이동한 후에 새 Lync Server 2013 풀에서 해당 회의를 계속 사용할 수 있습니다. 이 모임에 액세스하기 위한 세부 정보도 동일한 <STRONG>회의 URL 및 회의 ID</STRONG> 가 됩니다. 유일한 다른 점은 이제 회의가 Office Communications Server 2007 R2 풀이 아닌 Lync Server 2013 풀에서 호스트된다는 점입니다.




> [!NOTE]
> 사용자의 홈을 Lync Server 2013으로 지정할 때는 업그레이드된 클라이언트를 동시에 배포할 필요가 없습니다. 새로운 기능은 사용자가 새 클라이언트 소프트웨어로 업그레이드한 경우에만 사용할 수 있습니다.



## 마이그레이션 후 작업

1.  사용자를 이동한 후에는 사용자에게 지정된 회의 정책을 확인합니다.

2.  Lync Server 2013에 있는 사용자가 구성한 모임이 Office Communications Server 2007 R2에 있는 페더레이션 사용자와 문제 없이 작동하도록 하려면 마이그레이션된 사용자에게 지정된 회의 정책이 익명 참가자를 허용해야 합니다.

3.  익명 참가자를 허용하는 회의 정책은 Lync Server 2013 제어판에서 **참가자가 익명 사용자를 초대할 수 있도록 허용** 이 선택되고 Lync Server 관리 셸의 **Get-CsConferencingPolicy** cmdlet 출력에 **AllowAnonymousParticipantsInMeetings** 가 **True** 로 설정됩니다.

4.  Lync Server 관리 셸을 사용하여 회의 정책을 구성하는 방법에 대한 자세한 내용은 Lync Server 관리 셸 설명서에서 [Set-CsConferencingPolicy](set-csconferencingpolicy.md)를 참조하십시오.

