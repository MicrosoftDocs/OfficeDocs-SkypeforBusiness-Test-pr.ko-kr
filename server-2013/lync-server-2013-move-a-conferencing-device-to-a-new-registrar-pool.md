---
title: 새 등록자 풀로 회의 장치 이동
TOCTitle: 새 등록자 풀로 회의 장치 이동
ms:assetid: 26e02ca3-e881-4f90-8bf0-b13649108100
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ994025(v=OCS.15)
ms:contentKeyID: 52056814
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 새 등록자 풀로 회의 장치 이동

 

_**마지막으로 수정된 항목:** 2013-02-20_

**Move-CsMeetingRoom** cmdlet을 사용하여 회의 장치를 등록자 풀 간에 이동합니다. 이 cmdlet은 Lync Server 2013 관리 셸 또는 Windows PowerShell의 원격 세션에서 실행할 수 있습니다.


> [!NOTE]
> 원격 Windows PowerShell을 사용하여 Lync Server에 연결하는 방법에 대한 자세한 내용은 Lync Server Windows PowerShell 블로그 문서인 "빠른 시작: 원격 PowerShell을 사용하여 Microsoft Lync Server 2010 관리"(<A href="http://go.microsoft.com/fwlink/p/?linkid=255876">http://go.microsoft.com/fwlink/p/?linkId=255876</A>)를 참조하세요.




## 새 등록자 풀로 회의 장치 이동

  - 회의 장치를 이동하려면 이동할 회의실 ID를 지정한 후 Target 매개 변수를 장치 이동 대상 등록자 풀의 FQDN(정규화된 도메인 이름)으로 설정해야 합니다. 예를 들면 다음과 같습니다.
    
        Move-CsMeetingRoom -Target "atl-cs-001.litwareinc.com" -Identity "Room 14"

자세한 내용은 [Move-CsMeetingRoom](move-csmeetingroom.md) cmdlet의 도움말 항목을 참조하십시오.

