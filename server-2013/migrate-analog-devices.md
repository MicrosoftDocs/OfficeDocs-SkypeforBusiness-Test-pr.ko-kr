---
title: 아날로그 장치 마이그레이션
TOCTitle: 아날로그 장치 마이그레이션
ms:assetid: ad072916-87ed-4d44-8289-aab87da86250
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ721846(v=OCS.15)
ms:contentKeyID: 49885922
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 아날로그 장치 마이그레이션

 

_**마지막으로 수정된 항목:** 2012-10-16_

Lync Server에서는 아날로그 장치에 대한 지원을 제공합니다. 특히 지원되는 아날로그 장치가 아날로그 오디오 전화와 아날로그 팩스입니다. Lync Server 환경에서 아날로그 장치 사용을 지원하도록 적격 게이트웨이를 구성할 수 있습니다. Lync Server 2010에서 Lync Server 2013으로 마이그레이션한 후에는 아날로그 장치와 연결된 연락처 개체도 마이그레이션해야 합니다. Lync Server 관리 셸을 사용하여 먼저 Lync Server 2010 아날로그 장치와 연결된 모든 연락처 개체를 검색한 후 이러한 개체를 Lync Server 2013 풀로 이동합니다.

## 아날로그 장치를 마이그레이션하려면

1.  Lync Server 관리 셸 시작: **시작**, **모든 프로그램**, **Microsoft Lync Server 2013**을 차례로 클릭한 다음 **Lync Server 관리 셸**을 클릭합니다.

2.  명령줄에 다음을 입력합니다.
    
        Get-CsAnalogDevice -Filter {RegistrarPool -eq "pool01.contoso.net"} | Move-CsAnalogDevice -Target pool02.contoso.net

3.  모든 연락처 개체가 Lync Server 2013 풀로 이동되었는지 확인합니다. 명령줄에 다음을 입력합니다.
    
        Get-CsAnalogDevice -Filter {RegistrarPool -eq "pool02.contoso.net"}

4.  모든 연락처 개체가 이제 Lync Server 2013 풀과 연결되어 있는지 확인합니다.

