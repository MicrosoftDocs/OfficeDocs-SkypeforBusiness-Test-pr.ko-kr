---
title: 'Lync Server 2013: 서버에서 서비스 시작'
TOCTitle: 서버에서 서비스 시작
ms:assetid: fa26eaed-0529-4f32-9f3f-f32c4bd4b1c8
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg413059(v=OCS.15)
ms:contentKeyID: 49305608
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 서버에서 서비스 시작

 

_**마지막으로 수정된 항목:** 2014-09-03_

이 절차를 성공적으로 완료하려면 RTCUniversalServerAdmins 그룹의 구성원인 사용자로 로그인하거나 올바른 권한을 위임받아야 합니다. 사용 권한을 위임하는 방법에 대한 자세한 내용은 [Lync Server 2013에서 설치 권한 위임](lync-server-2013-delegate-setup-permissions.md) 항목을 참조하세요.

서버에 로컬 구성 저장소를 설치하고 Lync Server 2013 구성 요소를 설치하고 프런트 엔드 서버 또는 프런트 엔드 서버의 인증서를 구성했으면 서버에서 Lync Server 2013 서비스를 시작해야 합니다. 다음 절차에 따라 배포의 각 프런트 엔드 서버에서 서비스를 시작할 수 있습니다.

## Standard Edition Server 또는 프런트 엔드 서버에서 서비스를 시작하려면

1.  Lync Server 배포 마법사의 **Lync Server 2013** 페이지에서 **4단계** 옆에 있는 **실행** 을 클릭합니다.

2.  **서비스 시작** 페이지에서 **다음**을 클릭하여 서버에서 Lync Server 서비스를 시작합니다.

3.  **명령 실행** 페이지에서 모든 서비스가 정상적으로 시작되었으면 **마침** 을 클릭합니다.
    

    > [!IMPORTANT]
    > 서버에서 서비스를 시작하는 명령은 서비스가 실제로 시작되었는지를 보고하는 데는 가장 효율적인 방법이지만, 실제 서비스 상태를 반영하지는 않을 수 있습니다. <STRONG>서비스 시작</STRONG> 을 수행한 직후 <STRONG>서비스 상태(선택 사항)</STRONG> 단계를 사용하여 MMC(Microsoft Management Console)를 열고 서비스가 성공적으로 시작되었는지 확인하는 것이 좋습니다. Lync Server 서비스가 아직 시작되지 않은 경우 MMC에서 해당 서비스를 마우스 오른쪽 단추로 클릭하고 <STRONG>시작</STRONG> 을 클릭하여 서비스를 시작할 수 있습니다.


