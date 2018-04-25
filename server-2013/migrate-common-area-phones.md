---
title: 공통 영역 전화 마이그레이션
TOCTitle: 공통 영역 전화 마이그레이션
ms:assetid: 31bd26fc-861b-45c6-8221-18df16e575de
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688015(v=OCS.15)
ms:contentKeyID: 49885710
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 공통 영역 전화 마이그레이션

 

_**마지막으로 수정된 항목:** 2012-09-29_

공통 영역 전화는 보통 대기실, 주방, 공장 현장 등의 공유 작업 영역이나 공통 영역에 있는 IP 전화입니다. Lync Server UC 기능을 제공하기 위해 공통 영역 전화를 컴퓨터에 연결할 필요는 없습니다. Lync Server 2010 배포를 Lync Server 2013으로 마이그레이션한 후에는 레거시 공통 영역 전화와 연결된 연락처 개체도 마이그레이션해야 합니다. Lync Server 관리 셸을 사용하여 먼저 Lync Server 2010 공통 영역 전화와 연결된 모든 연락처 개체를 검색한 후 Lync Server 2013 풀로 해당 개체를 이동합니다.

**공통 영역 전화 마이그레이션**

1.  Lync Server 2013 프런트 엔드 서버에서 Lync Server 관리 셸을 엽니다.

2.  명령줄에 다음을 입력합니다.
    
        Get-CsCommonAreaPhone -Filter {RegistrarPool -eq "pool01.contoso.net"} | Move-CsCommonAreaPhone -Target pool02.contoso.net

3.  모든 연락처 개체가 Lync Server 2013 풀로 이동되었는지 확인하려면 Lync Server 관리 셸에서 다음을 입력합니다.
    
        Get-CsCommonAreaPhone -Filter {RegistrarPool -eq "pool02.contoso.net"}
    
    이제 모든 연락처 개체가 Lync Server 2013 풀과 연결되어 있는지 확인합니다.

