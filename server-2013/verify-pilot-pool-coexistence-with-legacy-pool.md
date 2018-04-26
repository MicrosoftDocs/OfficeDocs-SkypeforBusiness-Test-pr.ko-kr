---
title: 레거시 풀로 파일럿 풀 동시 사용 확인
TOCTitle: 레거시 풀로 파일럿 풀 동시 사용 확인
ms:assetid: fe7e14bb-c7eb-4719-b154-009e99360520
ms:mtpsurl: https://technet.microsoft.com/ko-kr/library/JJ205420(v=OCS.15)
ms:contentKeyID: 49305643
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 레거시 풀로 파일럿 풀 동시 사용 확인

 

_**마지막으로 수정된 항목:** 2012-09-29_

파일럿 풀을 배포한 후 관리 도구를 사용하여 풀 정보를 살펴보면서 두 풀이 모두 존재하는지 확인해야 합니다. Lync Server 2013 풀과 레거시 풀의 경우 Lync Server 2013 제어판 및 토폴로지 작성기 도구를 사용해야 합니다.

## Lync Server 2013 서비스를 시작했는지 확인합니다.

1.  Lync Server 2013 프런트 엔드 서버에서 관리 도구\\서비스 애플릿으로 이동합니다.

2.  다음 서비스가 프런트 엔드 서버에서 실행 중인지 확인합니다.

**Lync Server 2013 서비스**

![시작된 Lync Server 서비스 목록](images/JJ205420.cfff9385-6bf6-461c-982c-e727c9f20b70(OCS.15).png "시작된 Lync Server 서비스 목록")

## Lync Server 2013 제어판을 엽니다.

Lync Server 2013 배포의 프런트 엔드 서버에서 Lync Server 2013 제어판을 열고 Lync Server 2010 풀을 선택합니다. 다음 절차를 반복하여 Lync Server 2013 풀을 엽니다.

**Open Lync Server 2013 제어판**

![URL 선택 대화 상자](images/JJ205420.b1f8e650-9c3c-4563-a403-5069f198342f(OCS.15).png "URL 선택 대화 상자")


> [!IMPORTANT]
> Lync Server 2013에서 Lync Server 제어판을 사용하기 전에 먼저 Silverlight를 Silverlight 버전 5로 업그레이드해야 합니다.



이 토폴로지에는 지금 Lync Server 2010 및 Lync Server 2013 서버 역할이 포함되어 있습니다.

**Lync Server 2013 제어판 토폴로지 페이지**

![Lync Server 제어판 - 토폴로지 페이지](images/JJ205420.4ed1cc7a-cb3e-42f6-82e2-6d4d71d19352(OCS.15).jpg "Lync Server 제어판 - 토폴로지 페이지")

## Lync Server 2010 토폴로지 작성기에서 토폴로지를 열지 마십시오.

Lync Server 2010 토폴로지 작성기를 사용하여 토폴로지를 열려고 할 경우 아래와 같은 오류가 발생합니다. 이 토폴로지는 Lync Server 2013 토폴로지 작성기로만 볼 수 있습니다. Lync Server 2013 토폴로지 작성기는 Lync Server 2013 및 Lync Server 2010 모두에 대한 풀을 만드는 데 사용해야 합니다.

**Lync Server 2010 토폴로지 작성기 오류 메시지**

![Lync Server 토폴로지 작성기 MMC 스냅 오류](images/JJ205420.f6666343-c348-4d81-ae0e-6ba5a44e16c4(OCS.15).png "Lync Server 토폴로지 작성기 MMC 스냅 오류")

