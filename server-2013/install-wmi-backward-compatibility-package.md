---
title: WMI 이전 버전과의 호환성 패키지 설치
TOCTitle: WMI 이전 버전과의 호환성 패키지 설치
ms:assetid: 38797fbd-06a0-4008-b099-158e7b5d7703
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ204816(v=OCS.15)
ms:contentKeyID: 49303319
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# WMI 이전 버전과의 호환성 패키지 설치

 

_**마지막으로 수정된 항목:** 2012-10-02_

WMI 이전 버전과의 호환성 패키지를 설치하지 않고 토폴로지 작성기 병합 마법사를 실행하려고 하면 다음과 같은 오류가 표시됩니다.

![WMI 오류 메시지](images/JJ204816.a007d2f2-fc85-430c-91eb-382b032469af(OCS.15).jpg "WMI 오류 메시지")

WMI 이전 버전과의 호환성 패키지를 설치하지 않고 **Merge-CsLegacytopology** cmdlet을 실행하려고 하면 다음과 같은 오류가 표시됩니다.

![Windows PowerShell WMI 공급자 오류](images/JJ204816.c510824e-1807-4c7e-bb28-c6cfea2eac1d(OCS.15).jpg "Windows PowerShell WMI 공급자 오류")

WMI 이전 버전과의 호환성 패키지를 설치하려면

1.  설치 미디어에서 \\SETUP\\AMD64\\SETUP\\OCSWMIBC.MSI로 이동합니다.

2.  OCSWMIBC.MSI를 설치합니다.
    

    > [!IMPORTANT]
    > OCSWMIBC.msi는 토폴로지 작성기 병합 마법사가 실행되는 컴퓨터에 설치해야 합니다. 그러나 토폴로지의 모든 프런트 엔드 서버에 OCSWMIBC.msi를 설치하는 것이 좋습니다.

    

    > [!IMPORTANT]
    > Lync Server 2013 핵심 구성 요소 및 Lync Server 2013 관리 셸이 설치되어 있으며 Office Communications Server 2007 R2 토폴로지(AD DS(Active Directory 도메인 서비스) 및 SQL Server에 대한 WMI 공급자)에 액세스할 수 있는 도메인의 모든 컴퓨터에 OCSWMIBC.msi를 설치할 수 있습니다.


