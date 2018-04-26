---
title: Lync Server 2013 핵심 파일 및 RTCLocal 데이터베이스 설치
TOCTitle: Lync Server 2013 핵심 파일 및 RTCLocal 데이터베이스 설치
ms:assetid: 206f0c1d-40f7-45b6-aa62-88aaef6cf7f6
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204734(v=OCS.15)
ms:contentKeyID: 49303033
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 핵심 파일 및 RTCLocal 데이터베이스 설치

 

_**마지막으로 수정된 항목:** 2012-10-20_

컴퓨터에 Lync Server 2013 핵심 파일을 설치하려면 다음 절차를 완료합니다. RTCLocal 데이터베이스는 핵심 파일을 설치하면 자동으로 설치됩니다. 감시자 노드에는 SQL Server를 설치할 필요가 없습니다. 대신 SQL Server Express가 자동으로 설치됩니다.

Lync Server 2013 핵심 파일 및 RTCLocal 데이터베이스를 설치하려면 다음을 수행합니다.

1.  감시자 노드 컴퓨터에서 **시작**, **모든 프로그램**, **보조프로그램**을 차례로 클릭하고 **명령 프롬프트**를 마우스 오른쪽 단추로 클릭한 후 **관리자로 실행**을 클릭합니다.

2.  콘솔 창에서 Lync Server 설치 파일의 적절한 경로를 사용하여 다음 명령을 입력한 다음 Enter 키를 누릅니다.
    
        D:\Setup.exe /BootstrapLocalMgmt

핵심 Lync Server 구성 요소가 올바르게 설치되었는지 확인하려면 **시작**, **모든 프로그램**, **Lync Server 2013**, **Lync Server 관리 셸**을 클릭합니다. Lync Server 2013 관리 셸에서 다음 Windows PowerShell 명령을 입력하고 Enter 키를 누릅니다.

    Get-CsWatcherNodeConfiguration

이 명령을 처음 실행하면 감시자 노드 컴퓨터를 아직 구성하지 않았기 때문에 아무런 데이터가 반환되지 않습니다. 명령이 오류를 반환하지 않고 실행되면 Lync Server 설치가 올바르게 완료된 것으로 가정할 수 있습니다.

감시자 노드 컴퓨터가 경계 네트워크 내에 있으면 다음 명령을 실행하여 Lync Server 2013 설치를 확인할 수 있습니다.

    Get-CsPinPolicy

조직에서 사용하도록 구성된 개인 ID 번호(PIN) 정책의 수에 따라 다음과 같은 정보가 반환됩니다.

    Identity             : Global
    Description          :
    MinPasswordLength    : 5
    PINHistoryCount      : 0
    AllowCommonPatterns  : False
    PINLifetime          : 0
    MaximumLogonAttempts :

PIN 정책에 대한 정보가 표시되면 핵심 구성 요소가 올바르게 설치된 것입니다.

