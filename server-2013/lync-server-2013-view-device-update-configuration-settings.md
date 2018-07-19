---
title: 'Lync Server 2013: 장치 업데이트 구성 설정 보기'
TOCTitle: 장치 업데이트 구성 설정 보기
ms:assetid: aa6a70a9-bd77-4606-b797-ea6a3bab9cf2
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994059(v=OCS.15)
ms:contentKeyID: 52056915
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 장치 업데이트 구성 설정 보기

 

_**마지막으로 수정된 항목:** 2013-02-20_

Lync Server 관리 셸 및 **Get-CsDeviceUpdateConfiguration** cmdlet을 사용하여 장치 업데이트 서비스 구성 설정을 볼 수 있으며, 이러한 cmdlet은 Lync Server 2013 관리 셸또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다.


> [!NOTE]
> 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"(<A href="http://go.microsoft.com/fwlink/p/?linkid=255876">http://go.microsoft.com/fwlink/p/?linkId=255876</A>)를 참조하세요.





  - 
    
    모든 음성 경로에 대한 정보를 보려면 Lync Server 관리 셸에 다음 명령을 입력한 후 Enter 키를 누릅니다.
    
        Get-CsDeviceUpdateConfiguration
    
    이 명령은 다음과 비슷한 정보를 반환합니다.
    
        Identity               : Global
        ValidLogFileTypes      : {Watson, Config, Diaglog, CELog}
        ValidLogFileExtensions : {.dmp, .clg, .clg1, .clg2...}
        MaxLogFileSize         : 1024000
        MaxLogCacheLimit       : 512000
        LogCleanUpInterval     : 10.00:00:00
        LogFlushInterval       : 00:05:00
        LogCleanUpTimeOfDay    :

이 cmdlet에 대한 자세한 내용은 [Get-CsDeviceUpdateConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsDeviceUpdateConfiguration)의 도움말 항목을 참조하세요.

