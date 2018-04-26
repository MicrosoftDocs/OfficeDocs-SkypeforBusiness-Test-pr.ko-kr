---
title: Lync Server 2013에서 토폴로지 작성기에서 트렁크 수정
TOCTitle: Lync Server 2013에서 토폴로지 작성기에서 트렁크 수정
ms:assetid: 81055a82-c6f8-47b2-9779-223b1d842f36
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688110(v=OCS.15)
ms:contentKeyID: 49885844
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013에서 토폴로지 작성기에서 트렁크 수정

 

_**마지막으로 수정된 항목:** 2012-09-21_

다음 단계에 따라 트렁크의 대체 바이패스 식별자 및 대체 미디어 IP 주소를 수정합니다.

## 트렁크의 대체 미디어 IP 주소를 수정하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  Set-CsPstnGateway cmdlet을 실행하고 Lync Server 관리 셸에서 AlternateBypassId 필드를 수정합니다.
    
        Set-CsPstnGateway -Identity "PstnGateway:<peer FQDN> -RepresentativeMediaIP <IP address>

## 트렁크의 대체 바이패스 ID를 수정하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  Set-CsPstnGateway cmdlet을 실행하고 Lync Server 관리 셸에서 AlternateBypassId 필드를 수정합니다.
    
        Set-CsPstnGateway -Identity "PstnGateway:<peer FQDN> -AlternateBypassID <identifier>

