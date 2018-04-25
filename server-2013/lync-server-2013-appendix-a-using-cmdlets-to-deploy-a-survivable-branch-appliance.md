---
title: 'Lync Server 2013: 부록 A: Cmdlet을 사용하여 SBA(Survivable Branch Appliance) 배포'
TOCTitle: '부록 A: Cmdlet을 사용하여 SBA(Survivable Branch Appliance) 배포'
ms:assetid: 796a26cf-7ec9-453b-8757-6153a6dd86c5
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg398598(v=OCS.15)
ms:contentKeyID: 49304110
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 부록 A: Lync Server 2013에서 Cmdlet을 사용하여 SBA(Survivable Branch Appliance) 배포

 

_**마지막으로 수정된 항목:** 2012-10-07_

이 항목에서는 Lync Server 관리 셸을 사용하여 SBA(Survivable Branch Appliance)를 배포하는 방법에 대해 설명합니다. 이 절차는 중앙 사이트에서 수행합니다.

## SBA(Survivable Branch Appliance)를 원격으로 배포하려면

1.  [Lync Server 2013에서 토폴로지에 분기 사이트 추가](lync-server-2013-add-branch-sites-to-your-topology.md)의 절차에 따라 새로운 분기 사이트를 추가합니다.

2.  분기 사이트를 도메인에 참가시킵니다.

3.  RTCUniversalSBATechnicians 그룹을 로컬 Administrators 그룹에 추가합니다.

4.  서버를 다시 시작한 다음 RTCUniversalSBATechnicians 그룹의 구성원으로 로그온합니다.

5.  Lync Server 관리 셸에서 다음 명령을 입력하여 자리 표시자를 조직에 대한 올바른 정보로 바꿉니다.
    
        Export-CsConfiguration -FileName C:\CSConfig.zip
        Import-CsConfiguration -LocalStore -FileName C:\CSConfig.zip -Verbose
        Enable-CSReplica -Verbose
        Enable-CsComputer -Verbose
        Request-CsCertificate -New -Type default -CA <YourCA> -Verbose
        Set-CsCertificate -Type Default -Thumbprint <YourCertThumbprint>
        Start-cswindowsservice -verbose

