---
title: 여러 사이트 및 풀 마이그레이션
TOCTitle: 여러 사이트 및 풀 마이그레이션
ms:assetid: 3bf677d4-a5af-4f73-8fad-1abf5b668cc1
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ688025(v=OCS.15)
ms:contentKeyID: 49885727
ms.date: 08/10/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 여러 사이트 및 풀 마이그레이션

 

_**마지막으로 수정된 항목:** 2012-08-26_

Lync Server 2013에서는 다중 사이트 및 다중 풀 배포가 지원됩니다. Office Communications Server 2007 R2에서 Lync Server 2013으로 여러 풀을 마이그레이션하는 프로세스에서는 다음을 고려해야 합니다.

1.  Lync Server 2013 파일럿 풀을 배포한 후에는 Lync Server 2013 풀로 이동할 파일럿 사용자의 하위 집합과 사용자 기능의 유효성을 검사하기 위한 방법을 정의해야 합니다.

2.  파일럿 풀에 에지 서버를 배포한 후에는 외부 사용자가 Lync Server 2013 풀과 통신할 수 있는지 검사해야 합니다.

3.  페더레이션 경로를 Office Communications Server 2007 R2 에지 서버에서 파일럿 Lync Server 2013 에지 서버로 전환한 후에는 페더레이션 사용자가 Lync Server 2013 풀과 통신할 수 있는지 검사해야 합니다.

4.  모든 사용자 및 사용자가 아닌 연락처 개체를 이동한 후에는 Office Communications Server 2007 R2 풀이 비어 있는지 검사해야 합니다.

5.  Office Communications Server 2007 R2 풀이 비어 있는지 확인한 후에는 풀을 비활성화할 수 있습니다.
    
    레거시 Office Communications Server 2007 R2 풀 및 서버를 비활성화하는 방법에 대한 자세한 내용은 [단계 10: 레거시 사이트 해제](phase-10-decommission-legacy-site.md)를 참조하십시오.

