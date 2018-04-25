---
title: Lync Server 2013 파일 저장소 지원
TOCTitle: 파일 저장소 지원
ms:assetid: ed66430d-3c19-4267-938c-956a51005073
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/Gg399073(v=OCS.15)
ms:contentKeyID: 49305438
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013의 파일 저장소 지원

 

_**마지막으로 수정된 항목:** 2012-10-16_

Lync Server 2013에서는 모든 파일 저장소에 대해 동일한 파일 저장소를 사용합니다. 파일 저장소 지원에는 다음이 포함됩니다.

  - 파일 저장을 위한 RAID(Redundant Array of Independent Disks), DFS(분산 파일 시스템)를 비롯한 DAS(직접 연결된 저장소) 또는 SAN(저장 영역 네트워크)의 파일 공유. 저장소 요구 사항에 대한 자세한 내용은 계획 설명서의 [Lync Server 2013의 프런트 엔드 서버, 메신저 및 현재 상태에 대한 기술 요구 사항](lync-server-2013-technical-requirements-for-front-end-servers-instant-messaging-and-presence.md) 및 [Lync Server 2013의 디렉터에 대한 하드웨어 및 소프트웨어 요구 사항](lync-server-2013-hardware-and-software-requirements-for-the-director.md)을 참조하십시오. Windows Server 2008 운영 체제용 DFS에 대한 자세한 내용은 Windows Server 2008의 분산 파일 시스템에 대한 단계별 가이드( [http://go.microsoft.com/fwlink/?linkid=202835\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=202835%26clcid=0x412))를 참조하십시오.

  - 파일 공유를 위한 공유 클러스터. 공유 클러스터를 사용하는 경우 Windows Server 2008 또는 Windows Server 2008 R2를 실행하는 클러스터 서버를 사용해야 합니다. 이전 Windows 버전을 실행하는 클러스터 서버를 사용하면 사용 권한 문제가 발생하여 일부 기능을 사용하지 못할 수도 있습니다. 클러스터 관리자를 사용하여 파일 공유를 만듭니다. 클러스터 관리자 사용에 대한 자세한 내용은 Microsoft 기술 자료 문서 284838 "Cluster.exe를 사용하여 서버 클러스터 파일 공유를 만드는 방법()"( [http://go.microsoft.com/fwlink/?linkid=140899\&clcid=0x412](http://go.microsoft.com/fwlink/?linkid=140899%26clcid=0x412))을 참조하십시오.

